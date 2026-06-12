---
title: "screen blanks after 10 minutes. anger rising."
date: 2006-06-20
forum: Desktop Environments
---

### Post by thebrade on 2006-06-20
This was never a problem w/ previous ubuntu versions. going to my power management or screensaver preferences yields nothing. I've read about ways to address this by modifying the xorg.conf file, but I'd like to avoid that if possible. this question is all over the forums, but no one can answer it--seems like such an easy thing, no? I would have hoped a developer might have an answer for this by now...

---

### Post by Turtle.net on 2006-06-20
I don't think we can help you if you do not describe a little bit more your problem.
And you know modifying xorg.conf manualy is not a big deal (create a backup of this file just in case anyway).
And last point. I do not think "developers" are aliens, or semi-god like creatures. The people who can help you are simply some ordinary people who already encountered the same kind of problem.

---

### Post by bryanl on 2006-06-20
Dapper and the newer versions of Gnome seem to be a bit anal in screen blanking compared to Breezy. I find I have to hit both power management and screen saver in system preferences after updates - and sometimes twice - to check to make sure power management is off and the screen saver is not to activate.

---

### Post by thebrade on 2006-06-20
more details? sure.
I have my screensaver set not to activate when idle (I tried setting it to the max of 2 hours but I still had the screen blank after 10 minutes).
I go to power prefs and I have "put display to sleep" and "put computer to sleep" both set to "never." when I go to the built-in help in ubuntu, their screenshot shows a third slider that controls screen blanking time, but I don't have that bar. believe me, i'd love to set screen blanking to "never" as well.

for my setup I prefer to use a "lock screen" button on my task bar everytime I'm not using my comp, which switches it to screensaver. otherwise I usually have a webpage w/ baseball scores refreshing, and I hate having the screen go black when I look over at my monitor 15 or 20 minutes later. It's a pretty obnoxious problem, and I'd like to get the dang thing solved.

---

### Post by Anduu on 2006-06-20
Check your BIOS settings...mine has its own built in power savings which I have disabled.

---

### Post by larsemil on 2006-06-21
[QUOTE=Anduu]Check your BIOS settings...mine has its own built in power savings which I have disabled.[/QUOTE]


i have got the same problem, and i dont think its the bios, then i would have had the same in breezy as well.

---

### Post by thebrade on 2006-06-21
yes, exactly. this problem didn't start until dapper. i'll check the bios but that's highly unlikely to be the problem. i'm in disbelief that a quick and easy fix still isn't readily known for this--there are posts from the early dapper betas about this and no one had an answer then either...

---

### Post by wpshooter on 2006-06-21
Just to let you know that from my experience in Gnome there is also some strange relationship between the working of the power management (for monitor) and the screen saver function that I am not used to (at least in my past experience with M/S windows). In windows the monitor power saving function and the screen functions were two completely independent working functions. But it appears to me that in Ubuntu that these two functions are tied together in their functioning.

I my experience with Gnome, you have to enable both of these functions, then let them operate and then turn them each off and on in the proper sequence in order to get the desired results. Like in my case, I do not want a screensaver function, so I have to get them both operating, say screensaver 2 minutes and power saving 3 minutes, then preferably restart/reboot and then turn off the screen saver and leave the power management on to blank my screen in so many minutes.

It looks like to me that they still need to do some work on these.

Good luck.

---

### Post by mjziegle on 2006-06-21
I have this problem with a box I use for mythtv.  Obviously I want to screen on at all times and hate having to get up and jiggle the mouse.

Two solutions:
1.  Turn off all screensavers, blank modes, whatever in the GUI settings
2.  use "xset -dpms" to turn off energy star configuration

or 

1. same as above
2. edit xorg.conf and add Options "DPMS" "false" to your monitor section

Here's a reference

[http://linuxreviews.org/howtos/power/xorg_dpms/](http://linuxreviews.org/howtos/power/xorg_dpms/)

---

### Post by thebrade on 2006-06-21
thanks! I'm gonna try that, since that's the basic advice I've seen at a couple places. that's a good link...

---

### Post by larsemil on 2006-06-22
[QUOTE=mjziegle]I have this problem with a box I use for mythtv.  Obviously I want to screen on at all times and hate having to get up and jiggle the mouse.

Two solutions:
1.  Turn off all screensavers, blank modes, whatever in the GUI settings
2.  use "xset -dpms" to turn off energy star configuration

or 

1. same as above
2. edit xorg.conf and add Options "DPMS" "false" to your monitor section

Here's a reference

[http://linuxreviews.org/howtos/power/xorg_dpms/](http://linuxreviews.org/howtos/power/xorg_dpms/)[/QUOTE]


well that did not solve it for me.. 

anyone else has a tip?

---

### Post by Lunar_Lamp on 2006-06-22
I use Brightside.

This is a program used to add reactivity to the corners and/or edges of the screen.  After installing it you can run brightside-config (or something similar) to configure it.  I have it set up so that resting my mouse in the bottom right hand corner disables the screensaver.  Voila - I can watch a DVD without hassle.

---

### Post by larsemil on 2006-06-22
[QUOTE=Lunar_Lamp]I use Brightside.

This is a program used to add reactivity to the corners and/or edges of the screen.  After installing it you can run brightside-config (or something similar) to configure it.  I have it set up so that resting my mouse in the bottom right hand corner disables the screensaver.  Voila - I can watch a DVD without hassle.[/QUOTE]

yes that is great. allthough it should not be needed. on my breezy i could watch dvds without a problem..


i was thinking, could it have anything to do with the kernel configuration. like acpi or something?
there is a file in /etc/acpi/ called screenblankening.sh but i dont understand it.. :)

---

### Post by larsemil on 2006-06-22
bumpy bumpy?

---

### Post by mjziegle on 2006-06-22
> grep DPMS /var/log/Xorg.0.log

Post the output.



[QUOTE=larsemil]well that did not solve it for me.. 

anyone else has a tip?[/QUOTE]

---

### Post by HippoMan on 2006-06-24
Here are some more things to check:

Look in **/etc/default/acpi-support **and see what the setting is for **USE_DPMS**.   Make sure that is set to **false**.

Also, in **/etc/console-tools/config**, make sure that the following values are set:

  [B]BLANK_TIME=0
  BLANK_DPMS=off
  POWERDOWN_TIME=0[/B]  # I think that this is right; the docs are unclear

---

### Post by talktwomey on 2006-06-24
try adding the following in /etc/X11/xorg.conf (leave afforementioned "DPMS" option intact)

```

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

```

This was driving me nuts, seems to have done the trick

---

### Post by larsemil on 2006-06-26
[QUOTE=talktwomey]try adding the following in /etc/X11/xorg.conf (leave afforementioned "DPMS" option intact)

```

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
EndSection

```

This was driving me nuts, seems to have done the trick[/QUOTE]


yep that solved it for me! thx bro!
Edit: Dont forget to restart x after editing xorg.conf!

---

