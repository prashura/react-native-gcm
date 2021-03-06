#	Google Cloud Messaging for React Native

## Install

install react-native-gcm
```
$ npm install react-native-gcm
```

Add GCM Pod to your Podfile
```
pod Google/CloudMessaging`
```

Add Source files to your project
- `GCM.swift`
- `GCMBridge.h`
- `GCMBridge.m`

Add ObjC / Swift Bridge Header
```
#import "RCTBridge.h"
#import "RCTBridgeModule.h"
#import "RCTEventDispatcher.h"
#import <Google/CloudMessaging.h>
```

## Usage
```js
import gcm from 'react-native-gcm';
```

### Register for Push Notifications
```js
// Default permission {alert: true, badge: true, sound: true}
gcm.register(/*permission*/)
```

### Set App Badge Value
```js
// Set App Badge to value
gcm.setAppBadge(2, (newBadgeVal) => { });

// Increment App Badge value
gcm.setAppBadge(2, true, (newBadgeVal) => { });
```

### Get App Badge Value
```js
gcm.getAppBadge((badgeVal) => { });
```

### Subscribe to topic
```js
gcm.topicSubscribe('/topics/test', (err, res) => {});
```

### Unsubscribe from topic
```js
gcm.topicUnsubscribe('/topics/test', (err, res) => {});
```

### Send upstream message
```js
gcm.sendMessage({
	id: '' // unique message id
	to: '', // recip id
	ttl: 500 // optional time to live
	message: {}, // msg data
});
```

## Events
GCM has all "EventEmitter" methods.

```js
// Connected to GCM socket
gcm.on('connection', (res) => {});

// Disconnected from GCM socket
gcm.on('disconnect', (res) => {});

// Client registered with gcm
gcm.on('registeredClient', (res) => {});

// Application entered background
gcm.on('enteredBackground', (res) => {});

// Application became active again
gcm.on('becameActive', (res) => {});

// Received message from GCM
gcm.on('message', (res) => {});
```

## License

MIT
