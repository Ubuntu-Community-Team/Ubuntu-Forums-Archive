---
title: "Warsow crash when disconnecting"
date: 2009-12-31
forum: Gaming &amp; Leisure
---

### Post by MindFusion on 2009-12-31
Hi everyone,

I recently installed Warsow and decided to try it out. It's a great game, i love it, i don't lagg, it runs quite smoothly on my laptop, the only problem is, when i decided to stop playing and pressed ESC and then 'Disconnect', my screen completely froze. I pressed all sorts of button combinations but nothing helped, i had to plug out my laptop...

Does anyone have any ideas? I'm running a 64-bit system if that might be of any help.

---

### Post by aeon.flux on 2010-01-16
hi, im playing warsow on 32bit jaunty. i have the same problem once upon a time, only thing that works is to press Ctrl+Alt+Delete and wait 1 minute, the system will correctly shut down, or the same does (on my notebook) the HW shut down button. beside it no idea how to fix that, only idea (when it happens to you) is to not press Esc and Quit and switch to window and close warsow : ) it shouldnt happen. 

btw i tryed to run warsow on Karmic, but the sound crashed every time by 1 - 5 minites, and than the game did what u written up here. on jaunty it happened 1 or 2 times (for last 4 months)

btw2 i tryed to search on warsow forums whats up with the koala and warsow and nobody knew why is it doing...

---

### Post by 5nak3 on 2010-01-16
This could be a problem with the sound files that are installed on Karmic by default. 

I believe there is a thread that explains the problem

[http://ubuntuforums.org/showthread.php?t=1309656](http://ubuntuforums.org/showthread.php?t=1309656)

Essentially what my suggestion will be if indeed this is the problem is:

Open up synaptic

Search for libsdl1.2debian

Uncheck libsdl1.2debian-alsa

Check and install libsdl1.2debian-pulse

Restart and try again. 

With any luck this should correct the problem. However if the game still freezes you can try the following once your system freezes.

"ctrl+alt+f1"

enter your username and password

then type "top" to get a list of the programs using the most CPU and if you see the Warsow, make a not of the PID.

Press "k"

Enter Warsow's PID (should be four numbers)

Press enter, and then press "y" when asked to kill the process with signal 15.

If you can't find warsow after using the "top" command, press "q" to escape from the "top" list and instead type:

"killall war"

press tab and you should find the command auto corrects itself and should display "killall warsow" then press enter and the Warsow program should be killed.

Then to get back to your desktop pres "ctrl+alt+f7".

---

### Post by aeon.flux on 2010-01-16
i've found 1 guy on warsow server and he told me that almost everyone who upgraded from jaunty to karmic had problem with sound and when i want karmic, i have to remove/install whole system, than should be everything ok.
i upgraded from jaunty to karmic and my problems with sound wasn't only in warsow, the sound crashed often and all i could do was restart the system (i don't use ubuntu a long time, so i know just a few of commands) but thanx a lot for help! : )

---

### Post by 5nak3 on 2010-01-16
So did what I suggest work? If not and the problem is indeed a sound related issue, before going back to Jaunty you might want to look at removing pulseaudio and try ALSA or OSS audio systems instead.

There are a lot of topics on the forum, but I do not want to suggest one because I do not know your exact problem. Have a search I am sure you will be able to find something similar to your problems.

---

### Post by aeon.flux on 2010-01-16
actually im using jaunty, so i can't tell you if it will work, but i tried it [cause i had problem (that mentioned MindFusion) yesterday] and it uninstalled all the software what uses libsdl1.2debian-alsa, so i had to install warsow again :( and i cant test it now, because i have hills of work to do until tomorrow : (

---

### Post by aeon.flux on 2010-01-22
i've installed karmic yesterday because of lcd tablet and it's using pulse audio by default, and there are no problems with sounds. :lolflag:

---

