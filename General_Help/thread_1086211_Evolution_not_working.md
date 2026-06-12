---
title: "Evolution not working"
date: 2009-03-03
forum: General Help
---

### Post by ubrox on 2009-03-03
Suddenly evolution stopped working. 

It is unable to move messages (no errors, silent failure)

unable to load folder contents

i am using it with exchange

(evolution:6357): e-data-server-WARNING **: Error in execution: Failed to retrieve message

(evolution:6357): libecal-WARNING **: e-cal.c:318: Unexpected response
Changing the queries (contains? "summary" "") 

(evolution:6357): calendar-gui-WARNING **: e-cal-model.c:1658: Unable to get query

(evolution:6357): libecal-WARNING **: e-cal.c:318: Unexpected response

(evolution:6357): libecal-WARNING **: e-cal.c:318: Unexpected response
calendar-gui-Message: Check if default client matches (1235515942.7816.15@kalyana-laptop 1235515942.7816.15@kalyana-laptop)
calendar-gui-Message: Check if default client matches (1235515942.7816.15@kalyana-laptop 1235516164.6457.7@kalyana-laptop)

(evolution:6357): libecal-WARNING **: e-cal.c:318: Unexpected response

(evolution:6357): camel-exchange-provider-WARNING **: Unable to load Exchage summary for folder personal/My Folders/HPC Customers/ABC: no such table: personal/My Folders/HPC Customers/ABC


(evolution:6357): camel-exchange-provider-WARNING **: Unable to load Exchage summary for folder personal/Journal: no such table: personal/Journal


(evolution:6357): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(evolution:6357): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

---

### Post by ubrox on 2009-03-03
removing exchnage account & adding it back fixed it. Dont know what messed it up. There were a few updates I installed, but nothing related to evolution. 

clsoing thread

---

### Post by manoriax on 2009-04-25
Hey mates,

after I tried to add my Google Calendar in Evolution I partly recieve the same messages. I have already tried to re-add the calendar several times, but it does not seem to be willing to do what I want it to do. :)

_Console log:_
```
phil@phil-desktop:~$ evolution
** (evolution:14764): DEBUG: mailto URL command: evolution %s
** (evolution:14764): DEBUG: mailto URL program: evolution
** (evolution:14764): DEBUG: EI: SHELL STARTUP
camel-imap-provider-Message: Unable to load summary: no such table: [Gmail]

calendar-gui-Message: Check if default client matches (1240655708.14033.1@phil-desktop 1240655708.14033.1@phil-desktop)
calendar-gui-Message: Check if default client matches (1240655708.14033.1@phil-desktop 1228930202.10541.9@phil-desktop)
camel-imap-provider-Message: Unable to load summary: no such table: [Gmail]/Spam

camel-imap-provider-Message: Unable to load summary: no such table: [Gmail]/Starred

calendar-gui-Message: Check if default client matches (1240655708.14033.1@phil-desktop 1228930202.10541.12@phil-desktop)

(evolution:14764): libecal-WARNING **: e-cal.c:320: Unexpected response
```

Is there any solution for this?

Greetings.

---

