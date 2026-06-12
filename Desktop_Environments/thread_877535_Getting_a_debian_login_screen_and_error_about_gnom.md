---
title: "Getting a debian login screen and error about gnome loading"
date: 2008-08-01
forum: Desktop Environments
---

### Post by spintel on 2008-08-01
I put this in the General Help forum but didn't know if it would be better suited here.

All week my laptop has loaded fine into the regular Ubuntu login screen. Today when I took my laptop home from work I got the Debian login screen. I logged in fine but when I went to launch any system apps it told me the apps are meant for GNOME and I might be using desktop environment.

Anyone know why this might be happening?


I tried searching for help on it but it was hard to phrase it into a good search.

---

### Post by pytheas22 on 2008-08-01
I'm not sure what exactly is going on.  Could you please describe in more detail what you mean by a "Debian login screen," or take a picture of it?  It would also help if you could paste here the exact error message that you get when you try to launch applications.  With that information we should be able to figure out what's going on.

---

### Post by falkTX on 2008-08-02
Have you tried to set the session to gnome?
Are you running gdm?

Please chack out those and tell us

---

### Post by spintel on 2008-08-02
I'm getting something similar to this for the log in: [http://www.linuxelectrons.com/images/debian_review/gnome_login.jpg](http://www.linuxelectrons.com/images/debian_review/gnome_login.jpg)
except there is no option for session.

If I try to go to System>Administration>Login I get the message "GDM is not running".

When I do sudo gdm start I get a message saying display 0 is in use, will try on display 1 and I get the standard Ubuntu login.  I tried doing chkconfig --list gdm but I guess that command is not used in Ubuntu?

---

### Post by pytheas22 on 2008-08-02
> If I try to go to System>Administration>Login I get the message "GDM is not running".

But when you login does it still bring you to Gnome?  Or is it something else?  You say, "I logged in fine."

It's also really strange that you have a Debian login screen on your machine...are you sure you didn't install anything that may have put that there?  I don't think anything like that comes with Ubuntu.

---

### Post by spintel on 2008-08-02
Yeah, GNOME still loads which is what is making this really confusing.

The only extra repos I added in were for AWN which shouldn't have changed anything; i also downloaded the NVIDIA X Server plugin to configure it for multiple monitors.

I can still get around fine with everything (Add/Remove & Synaptic Package).  The only things, so far, that are odd is the login screen and when I go to shutdown there is no shutdown option; I have to do sudo shutdown -H now in order for it shutdown.

And like I said, if I do sudo GMD start it flashes and a screen pops up saying "Display :0 is in use, attempting to use :1"

---

### Post by pytheas22 on 2008-08-02
> I can still get around fine with everything (Add/Remove & Synaptic Package).

So you can run applications now, or do you still get the problem where "when I went to launch any system apps it told me the apps are meant for GNOME and I might be using desktop environment?"

---

### Post by spintel on 2008-08-02
Functionality is pretty much all there.  Only thing giving me the error is the login screen option and when I try to shutdown.  I have to shutdown by command prompt.

---

### Post by pytheas22 on 2008-08-02
I don't know what's up with the login screen.  Can you change it in System>Administration>Login Menu?

As for being unable to shutdown: how are you trying to do it--using System>Quit or the little red Gnome applet?  And are you getting an error message (if so, what is it exactly)?

---

### Post by spintel on 2008-08-02
If I try to change it the way you mentioned is when I get the GDM error.  Which, as far as I can tell, seems to be the only time I'm getting it.

If I do System>Quit or the Power button in the corner, I don't see shutdown or restart.  To shutdown I have to run sudo shutdonw -P now  No error message.

---

