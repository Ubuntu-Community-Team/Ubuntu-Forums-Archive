---
title: "evolution &lt;-&gt; Microsoft 2003 Exchange Server"
date: 2006-01-24
forum: Desktop Environments
---

### Post by Mona on 2006-01-24
I have installed Ubuntu for the first time. 
Now I have great diffculties with connecting evolution to our Microsoft 2003 Exchange Server.
Emails are working quite fine. That means I can read the emails, that came in _after_ I installed evolution. But when I try to read older emails, I just see a blank page.
Even more problems do I have with the contacts and the calendar: It worked perfectly at the beginning. But when I restartet evolution, the calendar and the contacts are empty. When I reset the "check" in the left menu, I get an error message: Could not connect to server.

I do not want to go "home" to Microsoft: Does anybody have an idea where to look for the problem?

---

### Post by slux on 2006-01-24
You're using the evolution exchange plugin that connects thru the exchange webmail interface? Can you get to the webmail with a browser when this happens?

---

### Post by Mona on 2006-01-24
Yes, "outlook webaccess" works perfectly, even when evolution hangs. 

When I delete the account and then add it again everything works until the next restart of evolution. Is there a debug modus? I think the problem is the authentication between the Exchange Server and the client.

---

### Post by Mona on 2006-01-26
Trying to open the calendar generates these errors:

(evolution:9502): calendar-gui-CRITICAL **: gnome_calendar_add_source: assertion  `E_IS_SOURCE (source)' failed

(evolution:9502): calendar-gui-CRITICAL **: gnome_calendar_add_source: assertion  `E_IS_SOURCE (source)' failed



Any ideas?

---

### Post by slux on 2006-01-31
The errors are probably nothing related to the exchange plugin. evolution tends to be a bit noisy on the console.

I'm using the exchange connector currently, but haven't got the same problem and I'm stumped unfortunately... I don't use the calendaring so I'd get along even with using standard pop/imap pretty well though, could you? Sorry for not being able to be of more assistance here.

---

### Post by Mona on 2006-02-09
[back from illness]. 

Evolution really drives me crazy. Does anybody knows what this means:

"adding hook target 'source'

(evolution:12096): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:12096): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:12096): e-canvas.c-CRITICAL **: e_canvas_item_grab_focus: assertion `GTK_WIDGET_CAN_FOCUS (GTK_WIDGET (item->canvas))' failed

(evolution:12096): e-canvas.c-CRITICAL **: e_canvas_item_grab_focus: assertion `GTK_WIDGET_CAN_FOCUS (GTK_WIDGET (item->canvas))' failed

(evolution:12096): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:12096): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed

(evolution:12096): calendar-gui-CRITICAL **: gnome_calendar_add_source: assertion `E_IS_SOURCE (source)' failed

(...)"

---

### Post by tomriz on 2006-02-09
Hi, 
I experience exactly le same problem! Is the problem eventually in the data-storage part of evo? Where are the account settings?

---

### Post by zxee on 2006-02-09
I don't know if this is any help but you might want to look at
[http://www.mozilla.org/projects/thunderbird/](http://www.mozilla.org/projects/thunderbird/)  
I'm not sure if it has all the features you require but I've always preferred it to evo.

---

### Post by tomriz on 2006-02-09
is there a plugin/extension that enables the use of Exchange Server? Mail, Tasks, Contacts, Appointments?

If yes: whats the name of the package?

--------------------------------------------

Using Evo on Exchange 2003 without the "local synchronisation option for offlinework"  it was stable (so far :mrgreen: )! 

I also changed the Exchange-User settings. From simply USER to DOMAIN\USER.

---

### Post by slux on 2006-02-20
No, there's no exchange plugin for Thunderbird as far as I know.

I've been using the exchange connector in evo for a while and it's been fine for me except for some crashes when deleting messages but maybe the secret has been that I used the settings tomriz mentions here all along.

---

