---
title: "PC speaker beep - revisited!"
date: 2009-03-19
forum: General Help
---

### Post by yang on 2009-03-19
I've been using my system through several versions of Ubuntu, and just today I start getting PC speaker beeps whenever I (e.g.) try to move/backspace the cursor past the beginning/end of a text box.  This appears to be happening for all Gnome/GTK text boxes.

This may have something to do with the fact that I had disconnected then reconnected my monitor and USB keyboard/mouse today.  What setting(s) might have changed / should I be looking at?

Is there a clean way to disable the beeps again without resorting to something as heavy-handed as modprobe -r pcskpr, which I've never had to do and which does not get at the source of the problem?  (One way to think about this: I'd rather have the system not even attempt to make the alerts, than silence the alerts that the system tries to make.)

---

### Post by fieroboom on 2009-03-19
I'm not sure what you consider heavy-handed, but according to [launchpad](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/280625), there isn't a 'fix' for the default system beep yet... IMHO, I don't personally see it as a problem that needs to be fixed, but there appears to be another way to disable it according to this thread here on ubuntuforums:

[http://ubuntuforums.org/showthread.php?t=126746](http://ubuntuforums.org/showthread.php?t=126746)

By the way, rmmod does *exactly* what you're saying you want to do... It doesn't mute the speaker, it removes the OS's ability to use it (by disabling the module/ aka 'driver'), whereas any other method *will* simply mute it.
:D
-Paul

---

### Post by yang on 2009-03-19
> **fieroboom said:**
> I'm not sure what you consider heavy-handed, but according to [launchpad](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/280625), there isn't a 'fix' for the default system beep yet...

I'm fairly certain I have never experienced this problem before on this system for the past n years.

> **fieroboom said:**
> By the way, rmmod does *exactly* what you're saying you want to do... It doesn't mute the speaker, it removes the OS's ability to use it (by disabling the module/ aka 'driver'), whereas any other method *will* simply mute it.

But GTK (or whatever the source is) is still making the syscall.  But that's besides the point, which is to just get to the *source* of the problem.

---

### Post by scottuss on 2009-03-19
I used to get annoyed at that too on my Ubuntu system. I'm on Arch now and just don't load the module for PC speaker.. it's clean and effective I find.

---

### Post by dcstar on 2009-03-19
> **yang said:**
> I've been using my system through several versions of Ubuntu, and just today I start getting PC speaker beeps whenever I (e.g.) try to move/backspace the cursor past the beginning/end of a text box.  This appears to be happening for all Gnome/GTK text boxes.

This may have something to do with the fact that I had disconnected then reconnected my monitor and USB keyboard/mouse today.  What setting(s) might have changed / should I be looking at?

Is there a clean way to disable the beeps again without resorting to something as heavy-handed as modprobe -r pcskpr, which I've never had to do and which does not get at the source of the problem?  (One way to think about this: I'd rather have the system not even attempt to make the alerts, than silence the alerts that the system tries to make.)

System-Preferences-Sound-System Beep.

---

### Post by yang on 2009-03-19
> **dcstar said:**
> System-Preferences-Sound-System Beep.

That tab no longer exists, but it led me to the proper solution.  Full details follow.

First I went to Sound Preferences, but saw nothing about System Beep.  Googling turned up:

[http://ubuntuforums.org/showthread.php?t=943710](http://ubuntuforums.org/showthread.php?t=943710)

The OP writes that one can adjust the setting via gconf-editor, and I did indeed find that /apps/compiz/general/allscreens/options/audible_bell was set.  However, clearing it and closing gconf-editor didn't affect the current session's behavior.

Going back to the post, the replier points out:

[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/282906](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-control-center/+bug/282906)

One of the comments near the bottom mentions that this same preference can be adjusted in:

CompizConfig Settings Manager > General Options > General tab

Toggling the checkbox there did the trick.

---

