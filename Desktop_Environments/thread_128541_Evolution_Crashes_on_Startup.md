---
title: "Evolution Crashes on Startup"
date: 2006-02-11
forum: Desktop Environments
---

### Post by kpturvey on 2006-02-11
I've been using evolution for some time.  I'm actually quite happy with it for the most part.  It is still a bit unstable and not all the features are really usable, but it is getting there.  For what I need it performs adequately.

Unfortunately, today I went to campus and I ran evolution to send a couple of emails I have sitting in the outbox that I wrote on the train.  Well evolution came up and gave me a warning about the certificate of my ISP (a regular problem, not evolution's fault) and I accepted the key.  Then evolution spun out of control and started eating 100% of the CPU time.  I eventually killed it and then restarted it.  Now it dies every time I restart it.  I can't get to my email at all.  I've had this problem in the past and I've solved it by randomly deleting files in the .evolution directory, but I would rather not use that haphazard approach. 

Does evolution have a "safe mode" or "recovery mode" or some such thing that might handle this kind of thing?

The error I'm getting on the command line follows:

-- Snip --
kt@volkswagon:~$ evolution
adding hook target 'source'

(evolution:9283): camel-WARNING **: camel_exception_get_id called with NULL parameter.

(evolution:9283): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
The application 'evolution' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
-- end snip --

Any help would be appreciated.  If you use jabber, and you get this in the next couple of hours, feel free to contact me at [email]kpturvey@jabber.org[/email] and I can try various solutions interactively.  It would be nice if we could work out a general solution to this kind of problem (crashing on startup).  I'm sure other people have had similar issues.  

Thank you.

---

### Post by dcstar on 2006-02-11
[QUOTE=kpturvey]
.......
Any help would be appreciated.  If you use jabber, and you get this in the next couple of hours, feel free to contact me at [email]kpturvey@jabber.org[/email] and I can try various solutions interactively.  It would be nice if we could work out a general solution to this kind of problem (crashing on startup).  I'm sure other people have had similar issues.  

Thank you.[/QUOTE]
Rename your hidden .evolution directory and start Evolution again, if it behaves ok you can reconfigure the new profile and then start copying e-mail data from the old profile.

---

