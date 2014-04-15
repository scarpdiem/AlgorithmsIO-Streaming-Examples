### Transportation Classification Example

Here's a sample [client](http://ws-clients.algorithms.io/geolocation.html) using HTML5 to retrieve and send geolocation data to Algorithsm.io.
First it uses socket.io to connect and open socket to Algorithms.io 

	socket = io.connect('http://ws.algorithms.io:8080');
	
Then it sends data,
		   
	socket.emit('event_save', {
                'authToken': '02cfc86d9992e822510318adebccb4d3',
                'device_id': 'geolocation1',
                'label': $('#input_label').val(),
                'data': {
                    'latitude': position.coords.latitude,
                    'longitude': position.coords.longitude,
                    'accuracy': position.coords.accuracy,
                    'speed': position.coords.speed
                }
            });

The data streamed to Algorithms.io will look like these:

timestamp|latitude|longitude|accuracy|speed|class
:-|:-|:-
1387357180.338160|35.511416|139.619904|65|null|rest
1387357180.346586|35.511416|139.619904|65|null|rest
1387357180.902525|35.511463|139.619745|65|null|rest
1387357182.047721|35.511505|139.620024|65|null|walk
1387357191.938179|35.511496|139.619697|65|null|walk
1387357193.084510|35.511515|139.619998|65|null|run


* Need to implement geodesic function in node.js to calculate speed
* 