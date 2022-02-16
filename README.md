# ifttt_webhook_helium_integration

Sign up on IFTTT and head over to https://ifttt.com/maker_webhooks

click on DOCUMENTATION to get your personal API Key

Scroll down to To trigger an Event with an arbitrary JSON payload and copy your web request:
https://maker.ifttt.com/trigger/{event}/json/with/key/yourprivatekeywillshowhere

create new Applet: If This > search for webhooks

select Receive a web request with a JSON payload
and type in your event name like: helium_sensor (try to avoid any special characters or blank spaces)

Create Trigger, select Then That > search for notifications and select Send a notification from the IFTTT app

insert following Message content `"{{EventName}}" has {{JsonPayload}}` and create Applet, hit continue

Name your Applet Title to something meaningful yet short.

head over to console.helium.com

add integration > http and give it a name e.G. IFTTT_Notification

fill in your Endpoint URL from step 3) while replacing {event} with your Ifttt Event name: helium_sensor
https://maker.ifttt.com/trigger/helium_sensor/json/with/key/yourkeywillbehere

select Show Details from ADVANCED - JSON MESSAGE TEMPLATE (OPTIONAL)

paste the following code into your empty TEMPLATE BODY and hit save:

`{{{#decoded}}{{#payload}} "alarm": "{{ALARM}}", "door-open": "{{DOOR_OPEN_STATUS}}", "door-open-count": "{{DOOR_OPEN_TIMES}}", "last-open-duration": "{{LAST_DOOR_OPEN_DURATION}}", "battery-volts": "{{BAT_V}}", "mod": "{{MOD}}", {{/payload}}{{/decoded}} "name": "{{name}}", "reported_at": "{{reported_at}}"}`

adjust your variables according to your decoder function and save again

head over to Flows, add and connect your new Integration to your decoder
