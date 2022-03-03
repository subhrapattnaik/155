# 155

physics in A-Frame VR
static and dynamic body of the physics system
control the physics system bodies in A-Frame VR.
---------------------------------------------

when the flight entity is colliding with other entities like two objects interact with each other in the real world.

Any two objects must follow physics laws in nature like gravity, collision etc.

---------------------------------------------
A-Frame provides components which can be attached to the entities to make them physical bodies in the 3D scene.

These components are a part of the aframe physics system library of their own- “aframe-physics-system” which is built using CANNON.js,
the JavaScript physics engine library, to render physics-based 3D scenes.

include this A-Frame library in the index.html

static-body: These are fixed-position objects (or animated objects). Static bodies are not affected by gravity and collisions, but these can interact with other objects in the scene.
dynamic-body: These are freely-moving objects. Dynamic bodies have mass; they fall if gravity is enabled, and bounce off or collide with other objects.


dynamic-body and static-body components can be attached to any <a-entity> that contains 3D objects.
In general, <a-scene> will have at least one static-body for the ground, and one or more dynamic-body for the player to interact with.
  
  
  activity:
  the box must be static, so that it does not let the torus and the sphere to pass through it.
  
 You can now see the torus and sphere bouncing off the box for some time and then come to rest instead of passing through the box.
Now, in the real world when objects/bodies come in contact there is always some friction, restitution (and other physical properties) between those two bodies.
  
  
  Friction is a force between any bodies in contact;
  restitution is the property which tells about the bounciness of the body.
  
  n A-Frame these properties of physics can be configured using the physics component.
Let’s set these properties globally to all the physics bodies in the scene.
  
  
  
  -------------------
  Do you remember there’s always some invisible shape surrounding the physics body to detect if they are colliding with any other physics body?
In A-Frame also we see those shapes and modify them.
To the colliding shape we can use the “debug” property and set it to true
  --------------------
  
  The default shape of the collider comes automatically based on the object.
The default shape of the collider can be changed with the help of the shape property of the dynamic and static body component.
  ----------------------
  shape around the torus from box to sphere.
For this we can set the shape to a sphere.
And if we want to modify the radius of the collider sphere we can use sphereRadius property.
-------------------------------
  ##########################################################################################
let’s add it in our flight simulation.

@Set the attributes of the gLTF models to static and dynamic body
● Write a component to detect collision between entities.
  
  
  add the physics simulation in our flight simulation?
  Add the A-Frame physics system library.
  
  we need to make entities as static-body and dynamic-body.
--------------------
  Rings and the birds make them static
  
  Since these entities are created through components, how can we set the static-body component of the rings and birds?
  We will use the setAttribute() method.
  
  We need one dynamic body in the scene.
Since our flight is going to interact with the rings and the birds, we’ll set the flight as the dynamic-body.
  
  as soon as we set the plane as a dynamic body it falls down because of gravity.
  
  we do not want the flight to fall down, 
why everything falls down because of gravity in the real world?
The reason why everythings falls down is because every object has some mass.
So if we don't want the flight to fall down we can set its mass as 0.
  
  A-Frame, dynamic-body and static-body components have mass property.
  
  --------------------------------------------------------
  
  
  
  detect when the flight collides with the rings and birds.
  
  
  we can use the collide event to detect the collision between these entities.
Let’s write a “game-play” component to add the “collide” event.
  
  Now, let’s take a variable in the schema which will be used to set the element id of the entity to which the component will be attached.
  
  define our own function to isCollided() and take the argument as elementId.
  we can add an event listener to trigger a “collide” event.
For this we need to select on which element the event can be fired.
Till now we have been triggering events on the window.
But we can select a particular element using querySelector() and then add a listener on that element using element.addEventListener().
  
  once the event will be fired, we can check if the variable elementId has the string “#ring” or “#hurdle”.
For this we can use the JavaScript method includes() which finds whether the one string is the part of the other string value.
  
  Now let’s call the function inside the .update() handler of the A-Frame component and pass this.data.elementId.
  
  the “game-play” is the custom component written by us but it can be used as any other component.
Since this elementId will have unique ids of the ring and the bird element, we need to get these values for the “game-play” component to detect collisions.
Let’s add the “game-play” component to the ring and the bird element using setAttribute() and set it’s property elementId using template literal ${} and test the output.
  
