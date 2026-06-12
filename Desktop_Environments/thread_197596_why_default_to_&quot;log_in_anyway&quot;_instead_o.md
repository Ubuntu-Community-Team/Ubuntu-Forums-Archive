---
title: "why default to &quot;log in anyway&quot; instead of &quot;return to previous login&quot;?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by SpectralDesign on 2006-06-16
when re-logging in to a suspended session, why default to "log in anyway" instead of "return to previous login"?

Or is it possible to change this on an individual installation?  Going with the seeming preferred choice just causes problems because of existing lock-files and whatnot...  I'd expect "return to previous login" to be the default, or even the only option, so clearly there's a (possibly large) part of the picture I'm missing here.

Tangent:

I also notice that when switching users, it always asks for the password twice... once from the GDM login, then again from the screen-lock -- this is irregardless if screen-locking is enabled in the screensaver setup...  Again, is this too something that can be changed?  It's my wifes only gripe about my switching us to linux (that she has to enter her password twice when switching to her login...)

Specific to Dapper Drake:

I also notice that the new unlock dialog in 6.06 has a "switch user" button, but it shows all users, not the ones specified to be shown in the GDM login -- it would certainly be nice if this feature only showed the accounts allowed to be shown in the GDM login....

Sorry for posting three things in one thread, but they all seem related to me!  Thanks to anyone for help in working around or fixing these issues, or simply explaining why it is the way it is -- but best of all, thanks to any Devs that can perhaps see to gettting the interface(s) modified to be more intuitive and admin/user-friendly!!!!

Ubuntu Rocks!
^Curtis

---

### Post by H.E. Pennypacker on 2006-06-16
Something's gotta be wrong there, because I never have to enter my password twice..Gnome Display Manager log-in and lock password.  

When I go to Shutdown > Lock, and leave the laptop monitor up (and not closed), the lock screen remains, and I only have to enter the lock screen password.  If I close the monitor, it goes back to the GDM log-in screen, and I have to enter the password there, and that's the only time it asks for the password.

In any case, I am only asked for the password once, and I haven't changed any options from default.

---

### Post by SpectralDesign on 2006-06-16
I may have been unclear -- the behaviour you describe is what I get as well -- as long as one of us, and only one of us is logged in.....

As soon as we use the switch-user feature, whoever has an active session (be it one or both of us) has to enter a password twice. 

I.E. I boot the system and login, and read some slashdot... Then I go to run errands.  Meanwhile, my wife uses Switch-User so my session remains alive and my work in progress is not lost. So, at this point she enters her password once in the GDM login and viola, she's logged in.

Now, sometimes, when we use the switch-user tool it goes directly to the lock-screen dialog, however other times it goes back to the GDM login, verifies the credentials, *then* goes back to the lock-screen dialog leading to a double entry of credentials to re-enter a live session.

---

### Post by mannheim on 2006-06-16
> when re-logging in to a suspended session, why default to "log in anyway" instead of "return to previous login"?

I filed a bug on this: see [here.]("https://launchpad.net/distros/ubuntu/+source/gdm/+bug/39936") Of course, it's not clear if filing a bug constitutes progress.

For your tangent, this is what I did, and it helped a lot. Go to synaptic (or apt-get) and install "fast-user-switch-applet". The applet is something you can add to your panel: do so, by right-clicking on the panel and selecting "Add to panel ... ". If you can't see the fast-user-switch applet available in the list, maybe log out and try again.  

Now, having got the fast-user-switch applet in the panel, right-click on it and go to "Preferences". Uncheck the check-box which says "Lock screen after switching users."  To customize it further and keep things pretty, you can open up gconf-editor, and navigate in gconf-editor to apps->fast-user-switch-applet. Check "Show active users only".

Install the applet on your wife's panel also. Now, whenever you want to switch users, left-click the applet in the panel. If your wife left her session open on the desktop, but your session is still running in the background, then you will see your name in the drop-down list: and that will take you straight to your desktop, with zero passwords. If you were not previously logged in, select "Other" from the list, and log in.

If security and access to the machine is a concern, be aware that, even if your wife locks her screen manually and walks away, anyone can switch to your previous session (unlocked) by hitting Ctrl-Alt-F[7 or 8 or 9].

---

### Post by SpectralDesign on 2006-06-16
Ahhh!  I had no idea there was such an applet... I'd been using primarilly gdmflexiserver to switch users.  That solves that issue!

I'll keep my eyes on that bug report, mayhaps I ought to file a bug report on the function of the unlock dialog in Dapper Drake showing all users instead of those selected for display in the GDM login window (or, active sessions as allowed in the applet you've mentioned...)

Thanks alot for the tip!

---

