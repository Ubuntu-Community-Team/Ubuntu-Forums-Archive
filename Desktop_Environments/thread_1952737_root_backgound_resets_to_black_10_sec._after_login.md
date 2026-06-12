---
title: "root backgound resets to black 10 sec. after login"
date: 2012-04-04
forum: Desktop Environments
---

### Post by cornflake000 on 2012-04-04
Greetings...

This is a strange one for me.  I have been running my conky using a script to set the root background to an image for a year and a half.  I did an upgrade the other day and now, the script does what it's supposed to do on login, but after 10 seconds, the root background magically turns black; it's like it resets to black automatically.  All I have to do is manually run my script and the root background image appears and stays the way it's supposed to... till next login.

Does anyone know why or what would reset the root background to black 10 seconds after login?  

I can't find any references to any of the GDM or X scripts that could be running in an rc, bash, local or profile like xsri or xsetroot.  It's a little weird.

Thanks

Edit:  I just added "sleep 12" to the end of my script, then a repeat of my script after that.  So now it just flashes to black for a couple of seconds.  That's good for a laugh, but I still would like to know what is doing this.  I also see nothing in the logs that I can recognize.  Note: I'm using lynx.

---

### Post by Paddy Landau on 2012-04-05
> **cornflake000 said:**
> ... the root background magically turns black
What do you mean, "the root background"? Are you logged in as root? If so, you are breaking the security model of Ubuntu; you are never supposed to do that.

---

### Post by cornflake000 on 2012-04-05
> **Paddy Landau said:**
> What do you mean, "the root background"? Are you logged in as root? If so, you are breaking the security model of Ubuntu; you are never supposed to do that.

No, no... Some programs use the root desktop background for a simulated transparency.  You use utilities to change that desktop background in scripts which display it in program windows like conky.  I.E. If you do a screen shot of your desktop, use a utility to set that as your root desktop background then you can call that to specified windows on your user desktop and it look like a transparency.  Some hardware or systems can't handle a true transparency and this is a way around that.  There are a few different utilities that do this, xsri, xsetroot, Esetroot, gsetroot and feh are a few.

Something is switching my root background back to black after 10 seconds.

---

### Post by Paddy Landau on 2012-04-05
Sorry, I didn't realise. I don't know of anything that does that.

---

