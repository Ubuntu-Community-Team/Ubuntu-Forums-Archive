---
title: "Kubuntu power saving and screensaver"
date: 2006-06-04
forum: Desktop Environments
---

### Post by snowx1000 on 2006-06-04
Kubuntu does not seem to remember my display power saving settings after a reboot. The screensaver also seems to work randomly.

Thanks.

---

### Post by padre999 on 2006-06-04
as mentioned here:

[http://www.ubuntuforums.org/showthread.php?t=188604](http://www.ubuntuforums.org/showthread.php?t=188604)
[http://kubuntuforums.net/forums/index.php?topic=5677.0](http://kubuntuforums.net/forums/index.php?topic=5677.0)

I guess you are using KDE 3.5.3?

---

### Post by snowx1000 on 2006-06-04
From what I see in adept I am actually running 3.5.2, but am experiencing the same. The only upgrades I did were the security ones.

---

### Post by padre999 on 2006-06-04
But you also have the problem with the screensaver as described in the other threads? Is it still starting after a while or not at all anymore?

On my 3.5.3 the screensaver does not start after the configured time anymore at all and I have the same problem with the power saving settings.

---

### Post by snowx1000 on 2006-06-04
The only thing I can think of is that something is triggering the bug in either version, perhaps video drivers or messed up permissions somewhere.

---

### Post by snowx1000 on 2006-06-04
Time for the bug fix! After running systemsettings through the console I discoverd that it uses xset for dpms which loses its effect after each reboot. I was also missing the DPMS option from my Xorg.conf. When I edited the monitor with systemsettings it put two monitors, which I do not have. That was confusing the screensaver.

So here is what to do:

First check for dual monitor entries in /etc/X11/xorg.conf.

Second make sure there is Option "DPMS" in the "Monitor" section.


Edit: Option "OffTime" "30" belongs in the ServerLayout section.
That will turn the monitor off after 30 mins, adjust accordingly.

Hope this helps!

---

### Post by padre999 on 2006-06-05
It's a official KDE bug:

[http://bugs.kde.org/show_bug.cgi?id=128610](http://bugs.kde.org/show_bug.cgi?id=128610)

They say it is resolved, but I don't really get what the solution is?

---

### Post by padre999 on 2006-06-05
[QUOTE=snowx1000]
So here is what to do:

First check for dual monitor entries in /etc/X11/xorg.conf.

Second make sure there is Option "DPMS" in the "Monitor" section.


Edit: Option "OffTime" "30" belongs in the ServerLayout section.
That will turn the monitor off after 30 mins, adjust accordingly.

Hope this helps![/QUOTE]

snowx1000 got it right!

I edited Xorg.conf as suggested. And it works as it should.

It was only 1 monitor in my conf, but the offtime option was missing...

But I don't know if I can change it now via the system settings dialogue. Subject to further testing...

---

### Post by padre999 on 2006-06-05
Well.

During the session you can change it in the menu and it works accordingly. But when you reboot it will revert again to the time that is set now in the offtime option.

So we are just half way there... :-k 

Anyway there is a bug report at [http://bugs.kde.org/show_bug.cgi?id=128696](http://bugs.kde.org/show_bug.cgi?id=128696) where you can participate...

---

### Post by arizonagroovejet on 2006-06-05
[QUOTE=snowx1000]From what I see in adept I am actually running 3.5.2...[/QUOTE]

Run 

$ kcontrol

and it'll tell you what version of KDE you're running.


FWIW I have this same problem. I'm using KDE 3.5.3, but I had it with 3.5.2 as well.

---

### Post by snowx1000 on 2006-06-05
The only way I can see the systemsettings menu having lasting change on power settings is to stop only using xset. It says in the man page that values are lost on reset. It would have to modify xorg.conf, and use xset for the current session so you would not need to restart.

The code fragment on the KDE bug site was not too clear and cut off. It seems to deal mostly with screensaver locking.

---

### Post by nocloud on 2006-06-06
the bug report site is down....

can anybody post detailed instructions on how to fix this bug and set it so that my monitor turns off after 5 minutes?

---

### Post by padre999 on 2006-06-06
the bug site is back up. seems like they tried to fix that bug on their server... :twisted: 

anyway

there is no way yet to fix it. looks like we will have to wait for new packages to arrive. this morning there was a new kde package (had also to do with display control etc). i updated but nothing changed concerning this problem...

there are by the way two bug reports out there, so don't get confused.

[http://bugs.kde.org/show_bug.cgi?id=128610](http://bugs.kde.org/show_bug.cgi?id=128610) (screensaver)
[http://bugs.kde.org/show_bug.cgi?id=128696](http://bugs.kde.org/show_bug.cgi?id=128696) (energy saving settings)

---

### Post by padre999 on 2006-06-06
[QUOTE=nocloud]the bug report site is down....

can anybody post detailed instructions on how to fix this bug and set it so that my monitor turns off after 5 minutes?[/QUOTE]

so far there is only a temporary remedy as desribed above by snowx1000 [http://www.ubuntuforums.org/showpost.php?p=1094840&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1094840&postcount=6). 

You will have to edit the file /etx/X11/Xorg.conf

You have to enter option offtime in the serverlayout section. That's how I did it:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option		"Offtime" "2"
```

Now the screen will be turned off after 2 minutes (reboot necessary first).

---

### Post by arizonagroovejet on 2006-06-06
I've got KDE 3.5.2 on a CentOS box using rpms from kde-redhat. The Display section in kcontrol is different to how it is on Kubuntu. There's three setting there for Standby, Suspend and PowerOff. Changing those values writes to the file

~/.kde/share/config/kcmdisplayrc

E.g. 

[DisplayEnergy]
displayEnergySaving=true
displayPowerOff=30
displayStandby=15
displaySuspend=0

The numbers representing minutes. So the settings persists between sessions. I tried creating these entries on my Kubuntu machine but they get ignored.

So maybe this problem we're having in Kubuntu is not a KDE problem so much as a problem with KDE as provided by the Ubuntu packages.

Writing the value to a file in the users's home directory seems the best method to me. Not only does it persist between sessions, in scenarios where users have a home directory stored on a remote server and use more than one machine it allows the setting to follow the user from machine to machine.

Writing to xorg.conf is fine for a single user machine but very restrictive. Writing the value to xorg.conf would mean having to prompt for a password, prevent different users of a machine having different settings, and prevent users from taking the setting with them from machine to machine. 

I'm curious as to why the Display module (or whatever the technical term is) in Ubuntu only uses xset since the setting is clearly useless if it doesn't persist between sessions.

---

### Post by arizonagroovejet on 2006-06-18
post for anyone subscribed  to this thread who has the screensaver problem (_not_ the energy saver settings problem)

read this - 

[http://www.ubuntuforums.org/showthread.php?t=199381](http://www.ubuntuforums.org/showthread.php?t=199381)

---

