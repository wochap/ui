<template>
  <div class="page padded">
    <div class="columns is-mobile">
      <div class="column is-one-quarter">
        <EndpointsList></EndpointsList>
      </div>
      <div class="column">
        <div class="card">
          <div class="card-content">
            <div class="content">

              <h1>Endpoints</h1>

              <doc name="endpoints1"></doc>

              <h3>Create an Endpoint</h3>
              <endpoint-form @save="endpointCreated"></endpoint-form>

              <doc name="endpoints2"></doc>

            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EndpointForm from '../components/EndpointForm'
import EndpointsList from '../components/EndpointsList'

export default {
  components: {
    EndpointForm,
    EndpointsList
  },
  data () {
    return {
      editMethod: 'GET',
      editPath: ''
    }
  },
  computed: {
    editUrl () {
      return '/endpoints/' + encodeURIComponent(this.editMethod + ' ' + this.editPath)
    }
  },
  methods: {
    endpointCreated (path) {
      this.$router.push({
        name: 'endpoint',
        params: { path }
      })
    }
  }
}
</script>
