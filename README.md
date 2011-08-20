# Arduino Pusher Client, a Pusher client developed for use on Arduino devices

[Pusher] (http://www.pusherapp.com) is a Push Notification service that uses Websockets for relaying messages back and forth between clients.  This allows real time messaging between a diverse range of applications running on Web browsers, mobile devices and now� Arduinos.  It is my hope that allowing devices to easily send information about themselves as well as respond to messages received from applications and other devices will result in some interesting applications.

## Installation instructions

Once you've cloned this repo locally, copy the ArduinoPusherClient directory into your Arduino Sketchbook directory under Libraries then restart the Arduino IDE so that it notices the new library.  Now, under File\Examples you should see ArduinoPusherClient.  To use the library in your app, select Sketch\Import Library\ArduinoPusherClient.

## Examples

Included with this library is an example, called RobotExample, that uses Pusher events to drive two Servos.  This example connects to a channel named "robot-channel" and binds to 5 events: forward, backward, turn_left, turn_right, and stop.  When the events are received the appropriate method gets called and adjusts the angle of the servo motors, driving the robot.

## How To Use This Library

### Connecting to Pusher

''''PusherClient client("your-api-key-here");

if(client.connect()) {

  //Connected!

}

else {

  //Uh oh.

}

void loop() {

  client.monitor();  //Must have a call to monitor() inside loop()

}''''


### Subscribing to a Public Channel

client.subscribe("my-channel");

### Subscribing to a Private Channel

client.subscribe("private-my-channel", "my-auth-token");

### Subscribing to a Presence Channel

client.subscribe("presence-my-channel", "my-auth-token", 123); //123 = user_id

### Unsubscribing from a Channel

client.unsubscribe("my-channel");

### Binding to Events

client.bind("my-event", handleMyEvent);

void handleMyEvent(String data) {

   //Do stuff here

}

### Triggering Events

client.triggerEvent("my-event", "some data about my-event");

### Binding to all Events

client.bindAll(handleAllEvents);

void handleAllEvents(String data) {

   //Do stuff here

}

## Credits

Arduino Pusher Client uses the HashMap library developed by Alexander Brevig.