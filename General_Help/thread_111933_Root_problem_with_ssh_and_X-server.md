---
title: "Root problem with ssh and X-server"
date: 2006-01-03
forum: General Help
---

### Post by AndyCooll on 2006-01-03
I have three Linux boxes and have installed ssh on them all. They are also all configured to allow X-forwarding. And everything seems to work great. I can open applications on the box in front of me even though they are running on the box in the other room etc etc (Fantastic!). Except...

One box won't allow me to open applications that require sudo (eg. Synaptic). It throws up an error message each time. I can open applications that don't require sudo. I can even use ssh sudo when using the command line only. The other boxes are working fine and I've checked the usual settings to make sure they're the same.

My guess is that the X-server on this box isn't configured to allow root when using ssh :confused:

Anyone got any ideas that might throw some light on this?

---

### Post by AndyCooll on 2006-01-03
Ideas anyone?

---

### Post by schilcha on 2006-01-03
[QUOTE=AndyCooll]It throws up an error message each time.[/QUOTE]
Which error message?

---

### Post by AndyCooll on 2006-01-03
Thanks for your reply.

This message:
```
X11 connection rejected because of wrong authentication.
The application 'synaptic' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.
```

---

### Post by schilcha on 2006-01-03
Huh, never seen that one before... 
Can you forward X-applications run as normal user (i.e. without sudo)?

---

### Post by AndyCooll on 2006-01-03
Yes, no problem.

As I mentioned in my first post I can also use ssh both with and without sudo at  the command line... it's just ssh X-server and sudo...

---

### Post by schilcha on 2006-01-03
I'm really sorry, but it seems that I cannot help you with this one.

Just two thoughts...
Here's a paragraph from ssh's man-page:
> ssh will also automatically set up Xauthority data on the server machine. For this purpose, it will generate a random authorization cookie, store it in Xauthority on the server, and verify that any forwarded connections carry this cookie and replace it by the real cookie when the connection is opened.  The real authentication cookie is never sent to the server machine (and no cookies are sent in the plain).
Maybe your .Xauthority files are fore some reasone screwed. Maybe removing them can help (probably renaming them for backup is better). Though, I don't know if there's an /root/.Xauthority on your server-machine.

The other thing is: have a look at your log-files -- sometimes they contain valuable info.

Hope someone else can help you -- good luck!

---

### Post by AndyCooll on 2006-01-03
Thanks for trying. 

Yeah, I'd had a look at the man pages, however they just confused me (which isn't difficult). I'd read the bit you mentioned and indeed tried did removing the Xauthority file but it just created a new one with the same problems re-occurring.

And I've also been looking at the logs, but again at the moment can't seem to spot anything I understand that might give me a clue.

However... better keep reading and looking. In the meantime, anyone else able to help?
:(

---

