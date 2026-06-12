---
title: "No Desktop ... only Background !!!"
date: 2014-07-19
forum: Desktop Environments
---

### Post by NoXon21 on 2014-07-19
Hello,

My problem starts yesterday ... after ```
sudo apt-get upgrade
``` the system for the first time

The laptop boots normally ... Enter password to log in .... I type the password and Enter .... nothing happen, just the background

then I have to Ctrl+Alt+F2 ... startx again to see my desktop folders

and in terminal ```
gnome-panel
``` to see my panels

can someone help me fixing this issue ??

Thanks in advanced

Best regards!

---

### Post by grahammechanical on 2014-07-19
At that blank desktop with just the wallpaper you could try right clicking the desktop. If that brings up a menu then select Change Desktop Background. That will open System settings and from there you may be able to get to Additonal Drivers and experiment with video drivers.

I have not tried this on Ubuntu Gnome and I am a bit confused by that command of gnome-panel. Gnome 3 does not use Gnome panel. It uses Gnome shell. This is my understanding. Perhaps you can give us a much clearer understadning of the desktop environment and the user interface that you are using.

Regards.

---

### Post by NoXon21 on 2014-07-19
Oh sorry ... I forget to told that I'm using gnome-session-flashback

what I did now :

```

sudo apt-get purge gnome-session-flashback

rm -r ~/.cache/compizconfig-1

unity-tweak-tool --reset-unity
```

reboot ... I think it's works fine but a bit slow

I will test it ... and back to here

---

### Post by NoXon21 on 2014-07-19
Ok seems like gnome-session-flashback causing the problem [ if I'm not wrong ]

I tried to reinstall gnome-session-flashback but the problem back

so I remove it and clean cache and run ```
[COLOR=#000000][FONT=Ubuntu Mono]unity-tweak-tool --reset-unity
```

[/FONT][/COLOR]every thing good now .

---

### Post by deadflowr on 2014-07-19
You should have had two sessions for gnome-fallback.
With effects and without effects.
Did you try the one without effects?

I have seen problems with the effects one before, since it uses compiz and so does unity, the compiz profile for it tends to be set with no plugins running, for some reason or another.
I normally have to launch ccsm when I first run fallback with effects because of said weird behavior. Then I set the plugins I would like to use and typically they remain as I set it from then on.

That said, the without effects option has never failed me, and always loads without any problems.

---

### Post by NoXon21 on 2014-07-19
Yeah I tried both modes

they both wont work ... they were work two days ago

now I have a new problem ... my unity take 2~3 minutes to start :(

what's going on ?

---

### Post by NoXon21 on 2014-07-19
pfff finally

I removed .gnome* .gconf* from my home dir and now everything works well

my boot from bios to full desktop takes less than 55 seconds now

and I can flashback to gnome again :guitar:

Thanks for your replies guys :p

---

### Post by NoXon21 on 2014-07-19
BTW I'm facing some issues with audio now ... I think removing config folder did that

trying to fix

---

### Post by deadflowr on 2014-07-20
A day late reply, but you have told us nothing about either the machine or the OS version.
Both or either could be helpful, to some extent.

---

### Post by NoXon21 on 2014-07-22
I think upgrade missed up the whole system (I have no Idea)

everything gone bad after upgrade

so I decided to reinstall clean system ( I moved from Ubuntu 14.04 to Kubuntu 14.04 )

It's so much better GUI BTW

Thanks !

---

