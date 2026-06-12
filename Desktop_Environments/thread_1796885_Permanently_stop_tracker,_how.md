---
title: "Permanently stop tracker, how?"
date: 2011-07-04
forum: Desktop Environments
---

### Post by isync on 2011-07-04
Newer version of Ubuntu ship with tracker. And despite it might be helpful, I don't like it recursively indexing my filesystems.

From what I've read on threads and from trying to uninstall tracker via apt, it seems it is too deeply tied with the desktop to remove it without harming Ubuntu.

And now, since I am tired of switching it to "stop" after every reboot via the little icon, I'd like to change the config to permanently stop it. But how?

The config files are in ~/.config/tracker/, but what is the option equivalent of checking "Stop indexing" in the applet?

---

### Post by IanW on 2011-07-04
Wonder if you can disable it in "System/Preferences/Startup Applications"?

---

### Post by isync on 2011-07-04
No, not possible there.

(But thanks for pointing out as I stumbled over the zeitgeist daemon there which I've wanted to disable for ages as well.)

---

### Post by isync on 2011-07-11
Anyone?
Am I doomed to have tracker scour my file-system forever? :(

---

### Post by Frogs Hair on 2011-07-11
It may be possible to clear Nautilus history with Bleachbit run as sudo , but I am not on my own computer right now and can't look at it . I don't how or if Unity would work very well with out Zeigiest .
 
I'm guessing you may not be the only person using your account . I am the only user on my computer , so I'm not concerned about covering my tracks . I can understand not liking  having your computer activities tracked or having to store a log of those activities .

---

### Post by wildmanne39 on 2011-07-11
Hi, if you are using unity have a look at this link. Scroll down the page a little and you will see actitvity log manager read what that says.
[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

---

### Post by isync on 2011-08-07
Zeitgeist and Tracker enabled by default and inseparable glued into Ubuntu and Unity.
Unity instead of GNOME with all-new usage paradigms.
The OS thinking for me and my actions seeping into secrete channels.
Buttons on the left hand side of windows.
etc. pp. this and that.

Could it be Ubuntu, in it's quest to mimic OS X, is starting to suck? :(

---

### Post by wildmanne39 on 2011-08-07
Hi, did you try what I mentioned in post #6?

If you are wanting it not to track your recent documents what is listed on the link works.

---

### Post by isync on 2011-08-08
@wildmanne39:
Yes, I did install activity-log-manager (with all the hassle of updating zeitgeist first...) and set it to "red light": logging stopped.

Which turned out to be not related to the tracker's indexing, as it is yet another daemon logging stuff. (Zeitgeist logging all activity - scary enough that this is "on" by default!)

So my status as of now is:
1. I was able to stop zeitgeist from logging my *actions*.
2. I am unable to start the system with tracker in state "indexing stopped" preventing it from starting to scan my *files/filesystem(s)* on every startup.
3. Removing zeitgeist and/or tracker is not easily possible.

1 + 2 + 3 = suck-o-meter going into the red.

---

### Post by webdr on 2011-08-09
It seemed easy to me.
click applications ---> ubuntu software center--->installed software
search
enter zeitgeist
remove the three entries that show in results...then close ubuntu software center
next...
click --->system--->administration--->login screen
unlock
select ubuntu classic no effect as default session
close
relogin in or restart

viola! no more "Guardian Spirit / Sign of the times ZeitGeist"

---

### Post by isync on 2011-08-10
Ubuntu software center first hides it behind the GUI but synaptic clearly states beforehand (and software center then later on also it) that removing zeitgeist also removes:
-unity-place-applications
-unity-place-files
It this a bad thing? I don't know. This was what prevented me from deinstalling it so far. Once synaptic removed my half xorg or so via dependencies... Since then I am hesitant when libraries pop up that hace something to do with the user-interface... Andyway, this time the above 2 seem to be expandable. And, as you said, it removes zeitgeist. [1/2 SOLVED]

BUT: Tracker is still there!
Today, as a last resort, although a lot of users said it breaks nautilus, I removed it via synaptic... And guess what: Nautilus didn't explode and works okay. [2/2 SOLVED]

Last thing: What is changing the Login Screen supposed to do with zeitgeist/tracker? This thread here is not meant against Unity as such!

---

