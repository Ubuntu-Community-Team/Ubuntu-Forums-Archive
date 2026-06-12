---
title: "How do I get a faster, smoother startup?"
date: 2009-03-06
forum: General Help
---

### Post by nightrider.36 on 2009-03-06
***Where can I find a list of settings for the optimum start-up configuration?***

**WHAT I SEE:**
I'm confused by the all the options and I screwed up my OS's start-up.  In the STARUP-MANAGER, I unchecked, "Show bootloader menu", "Show boot splash" (no idea what this is), "show text during boot", thinking I wouldn't see anything and would just access the Desktop. That's not what happened.  Instead, I got a "loading, please wait" and a bunch of scrolling text that means nothing to me.

**WHAT I WANT:**
A start-up where you only see a start-up progress bar and then the desktop--nothing else. No password dialog either.

Thanks.
*[COLOR="DarkSlateGray"]P.S. This is by no means a complaint. I'm already impressed at how much faster than Windows the computers starts and exits. In fact, the 8.10 is really slick.[/COLOR]*

---

### Post by Therion on 2009-03-06
> **nightrider.36 said:**
> ***Where can I find a list of settings for the optimum start-up configuration?***
I doubt you can because there is no single configuration that is going to be "optimal" for everyone.

> **nightrider.36 said:**
> ******WHAT I SEE:**
I'm confused by the all the options and I screwed up my OS's start-up.  In the STARUP-MANAGER, I unchecked, "Show bootloader menu", "Show boot splash" (no idea what this is), "show text during boot", thinking I wouldn't see anything and would just access the Desktop. That's not what happened.  Instead, I got a "loading, please wait" and a bunch of scrolling text that means nothing to me.
Maybe, when playing with configuration screens you don't understand, you should start with ONE modification so you can figure out what it does.  Just a little food for thought.

As it is, what you want to do is check "ON" the option for "Show Boot Splash".  You can uncheck "Bootloader Menu".  These steps should eliminate the verbose boot (all that scrolling text you see now).

Lastly, since you don't want to have to log on, let's fix that by going to System/Preferences and clicking on "Login Window".  In the Login Window Preferences, select the Security tab and check the box next to Enable Automatic Login. Select the user account to enable automatic login. Click Close to save settings.

**EDIT:**

Something else to try to speed up your restarts.  Go to System/Administration and click on Sessions.  Here you can remove some startup applications you may not need.  For instance if you're not using any Bluetooth devices you can keep the Bluetooth daemon from starting up automatically and so forth.  It's not going to make a huge difference, but it won't hurt to shut off some unnecessary stuff.  If you're unsure what something is, google it or post and find out before shutting it down.

---

### Post by Slim Odds on 2009-03-06
> **nightrider.36 said:**
> 
**WHAT I WANT:**
A start-up where you only see a start-up progress bar and then the desktop--nothing else. 

That's the default. Why did you change it?

---

### Post by gcvisel on 2009-03-06
> **nightrider.36 said:**
> ****
**WHAT I WANT:**
A start-up where you only see a start-up progress bar and then the desktop--nothing else. No password dialog either.*[COLOR=DarkSlateGray][/COLOR]*

For the no-password bit, go to System / Administration / Login Window and its Security tab.  Click on Automatic Login, and you're there.

Gerry

---

### Post by nightrider.36 on 2009-03-06
> **Slim Odds said:**
> That's the default. Why did you change it?
Actually, the default made me choose a boot loader of some sort. I wanted to eliminate that. Plus, I'm also learning how it works but sometimes I get lost or forget what it used to look like.

---

### Post by Jimmynemo2 on 2009-03-06
Also, since you seem to have a boot loader by default, are you dual booting with windows? If so, you would want to find out if you are running the windows bootloader or gnome. If its the windows bootloader, you want to go into windows, and set the boot load choice time to some very small number (mine if 3 seconds). That way unless you are sitting there pushing up or down, you barely see it give you a choice which OS you want to go into. 

If on the other hand you have just one operating system (not dualbooting to windows/ubuntu), then you can just disable that completely, but Im not sure why it would have defaulted to showing you a choice if you had none...

---

### Post by perpetualcacophany on 2009-03-06
If you have a dual-core processor try this:

```
gksu gedit /etc/init.d/rc
```

From there find the line that says: CONCURRENCY=none

Change that to: CONCURRENCY=shell

This allows some of the startup scripts to run in parallel using both cores. It should shave some time off of your boot.

---

