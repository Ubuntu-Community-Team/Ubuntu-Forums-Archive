---
title: "Kiosk dilemma, need help"
date: 2009-03-27
forum: General Help
---

### Post by lykwydchykyn on 2009-03-27
I'm building a kiosk using Ubuntu and firefox.  I've done this a million times, and in the past it worked great.  But now I've run into some snags and I need to get some advice.

I basically need the browser to be:
 - full screen
 - locked down (can't exit, change settings, etc)
 - reset after a set period of inactivity.

In the past I used a combination of extensions to accomplish these goals, but not all the extensions have been updated to work with FF3.  In particular, autoreset browser does not work with FF3, even after I managed to hack it so that it would install, it doesn't actually work.

I've tried opera because it has all the features I need, but it won't work because (a) it's dog slow on the hardware I'm using and (b) it doesn't render the html correctly (and I have no control over the html).

So I'm brainstorming: 
 - is there a way to log out of X after a set period of inactivity?  I'm currently using openbox as the wm, but that can change.
 - is there a way to perform an action (such as killing a program) after a certain amount of inactivity?
 - is there another browser with good kiosk facilities?
 - Does anyone know how to get autoreset-browser working with FF3?
 - any other ideas?

Thanks for the help.

---

### Post by decoherence on 2009-03-27
> 
 - is there a way to log out of X after a set period of inactivity?  I'm currently using openbox as the wm, but that can change.
 - is there a way to perform an action (such as killing a program) after a certain amount of inactivity?


For both of these, you might be able to make use of xautolock, available from Synaptic. Basically it watches input devices and after a certain amount of time with no input, runs a command of your choosing. In your case, you'd tell it to restart X. If you're using GDM to auto-login, the command would be

```
sudo /etc/init.d/gdm restart
```

Hope that gets you closer...

---

### Post by lykwydchykyn on 2009-03-27
That looks like it may do the trick.  I'm running firefox in an endless loop via the .xsession script, so I can just tell it to pkill firefox (and thus not give my kiosk user sudo privs ;-)).

Thanks decoherence!

---

### Post by lykwydchykyn on 2009-03-27
This worked perfectly.  

I was even able to do a 10 second warning with a little help from xcowsay.

---

