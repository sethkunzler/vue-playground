<template>
  <div class="binding-exercise container">
    <div class="row">
      <div class="col-12">
        <div class="border p-1">
          <h5>One Way Data Binding</h5>
          <p>
            Use the property "message" on the data object in our component for
            one way data binding to display the message in our template. Replace
            the comment with the property name "state.message" in the curlies.
            Check out what happens below. Now go change the value of message in
            our components script area and see what happens.
          </p>
          <p>{{state.message}}</p>
        </div>
        <div class="border p-1">
          <h5>Two Way Data Binding</h5>
          <p>
            Use a v-model to bind an input value from our html to a property in
            the components data object. Then reference that data property in the
            html to display the value. Notice Vue will rerender each time the
            value changes.
          </p>
          <!-- add a v-model to this input that will reference "myName" within the state object-->
          <input v-model="state.myName" />
          <!-- reference "myName" from the state -->
          <p>{{state.myName}}</p>
        </div>
        <div class="border p-1">
          <h5>Class Binding</h5>
          <p>
            Use class binding to reference a property(isActive) in the
            components data object to determine when to add the class to the
            elements class list. Then change the value of that data
            property(isActive) to true. Notice Vue will rerender each time the
            value changes.
          </p>
          <div class="red">
            <!-- add a class binding attribute to the p tag that references the state isActive value -->
            <p :class="{ active: state.isActive }" >This text will turn green on active</p>
          </div>
          <button @click="changeColor()" type="button" class="btn beautiful-button">Change Color</button>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
import { reactive } from "vue";
export default {
  name: "binding-exercises",
  setup() {
    // NOTE typically state will be abstracted to a global AppState
    const state = reactive({
      message: "My Super awesome message drew to the page correctly!",
      //create a property called myName and set its value to "type your name here"
      myName: "type your favorite animal here",
      //change isActive to true
      isActive: true,
    });
    return { 
      state,
      changeColor() {
        if (!state.isActive) {
          state.isActive = true
        }
        else if (state.isActive) {
          state.isActive = false
        } 
      }
    };
  },
};
</script>


<style scoped>
.red {
  color: red;
}
.beautiful-button {
  background-color: rgba(23, 23, 225, 0.855); 
  border-radius: 16px;
  color: white;
  text-shadow: 2px 2px 5px black;
  font-weight: bold;
}
.active {
  color: green;
}
</style>