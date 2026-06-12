---
title: "How can i edit keyboard shorcuts?"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Rackerz on 2005-12-15
I can do it in Gnome, i got these codes from Gnome so i could use KDE with my keyboard shortcuts working. The codes are like this

0xed - Open music player
0xa2 - play/pause

It goes on like that. So basically were would i find the setting to setup these shortcuts?

Thanks!

---

### Post by aysiu on 2005-12-15
I don't know if KDE will work with your multimedia keys (it doesn't work with mine), but you assign keyboard shortcuts for applications by right-clicking on the KMenu, selecting "edit menu," and then clicking on the application you want a keyboard shortcut for.

---

### Post by jobezone on 2005-12-15
And you can assign shortcuts for functions inside applications. In Kde apps, go to Settings->Configure Shortcuts .

I've also seen that "Configure Shortcuts" is also acessible by right-cliking.
For example, in Kmix, you go to Settings -> Configure Shortcuts, and you have some general shortcuts for the program. Nothing really interesting.
But if you right click on the Master volume control, you also get an option "Configure Shortcuts", and this time it's more more helpful functions related to the Master Volume, like raising and lowering it.

P.S.- If some of your multimedia keys don't work, or aren't understood by KDE's shortcut application, use xbindkeys. See my post at the end of the following thread: [http://ubuntuforums.org/showthread.php?t=79717](http://ubuntuforums.org/showthread.php?t=79717)
The missing final information from my post is how to make KDE allways run xbindkeys, but it's easy. In a console, type:
```
ln -s /usr/bin/xbindkeys /.kde/Autostart/xbindkeys
```
This will create a symlink in KDE's autostart directory to the actual program. Every executable or symlink to an executable you place in that directory gets run by KDE when it starts.

---

### Post by LordRaiden on 2005-12-15
I'm using lineakd for my multimedia keys with great success. I'm not using the lineakd visual output plugin though, it seems broken (works right after install, but not after reboot). I got lineakd from the Adept repository manager, but I forget if it was from the default or the backports (70% sure on it being default).

In addition, i put a small script in my ~/.kde/Autostart folder to get it running after I log in. It works very well. My only complaint is that I have to edit the lineakd file if i want to change anything, because it'd be nice if i could get it to bind to say, my default Internet browser or mail client, instead of hard-coding it.

---

### Post by f1dave on 2005-12-15
xbindkeys, all the way. Works beautifully with my logitech wireless keyboard with it's volume controls and shortcuts to home, email, etc.

---

### Post by Rackerz on 2005-12-16
Thanks for the replys guys. I'll try what you have suggested. Is xbindkeys in the repositories?

---

### Post by jobezone on 2005-12-16
yep, not sure if in Main, or in Universe.

---

### Post by frodon on 2005-12-16
Yep it's in the repositories : [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)
For multimedia keys : [http://ubuntuforums.org/showthread.php?t=27039](http://ubuntuforums.org/showthread.php?t=27039)

---

### Post by Rackerz on 2005-12-16
[QUOTE=jobezone]yep, not sure if in Main, or in Universe.[/QUOTE]

How would i configure it correctly to work with KDE? Is 'amixer' a KDE application? Because you've put 'aximer' in the post you directed me too and correct me if I'm wrong, but i think that applies to Gnome.

---

### Post by Rackerz on 2005-12-16
Anybody there?

---

### Post by jobezone on 2005-12-16
amixer is not a gnome program, maybe an ALSA one(?). Trust me, I've got this thing working under KDE :)

---

