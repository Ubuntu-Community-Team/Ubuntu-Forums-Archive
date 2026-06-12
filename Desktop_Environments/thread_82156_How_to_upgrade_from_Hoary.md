---
title: "How to upgrade from Hoary?"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jlist on 2005-10-26
I found the upgrade note for ubuntu:
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

But much of it is about ubuntu, not kubuntu. Is there a similar upgrade instruction for upgrade kubuntu to 5.10?

---

### Post by SGC on 2005-10-26
The wiki page works for both ubuntu and kubuntu, except that if you don't have synaptic installed to follow the first or the second methode of upgrading then either install it or use the third methode "apt-get" with only changing this **gedit /etc/apt/sources.list** into **kwrite /etc/apt/sources.list**

Also see this post:
[http://ubuntuforums.org/showpost.php?p=398274&postcount=2](http://ubuntuforums.org/showpost.php?p=398274&postcount=2)

---

### Post by daller on 2005-10-26
Well, it's quite simple!

Do this:

sudo perl -pi.bak -e 's|hoary|breezy|g' /etc/apt/sources.list

sudo perl -pi -e 's|deb cdrom|\#deb cdrom|g' /etc/apt/sources.list

sudo apt-get update

sudo apt-get dist-upgrade

Reboot :( ... :)

...If anything goes wrong, simply run "sudo mv /etc/apt/sources.list.save /etc/apt/sources.list"

---

### Post by tmmuk on 2005-10-29
I might try this but I dont want to mess it up. in the first link, do I need to uninstall all the software that I have added before upgrading? Will I lose it anyway if I upgrade?
What would happen if it were to fail?

Just was wondering before I tried

tmmuk

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]I might try this but I dont want to mess it up. in the first link, do I need to uninstall all the software that I have added before upgrading? Will I lose it anyway if I upgrade?
What would happen if it were to fail?

Just was wondering before I tried

tmmuk[/QUOTE]
No, you don't need to uninstall anything. Normally you will not lose anything by the upgrade(i didn't), 
but of course you have backup's like every normal person.;)  Wether you use the first link or the method Daller showed you, 
both things do exactly the same, but I like daller's way more :) (substitution with perl, nice!)
Daller's way also comments out the (hoary) cd-rom entry, which you don't need anymore after upgrading to breezy.

---

### Post by tmmuk on 2005-10-29
Ok i just did the upgrade, and after a reboot I no longer have a windowing system or kde or a GUI etc. all i have is the full screen terminal. It says at the top "breezy badger" and I can log in alright, but i dont want to be restricted to the terminal. How to I get kde and everything else working? or how can I at least get what I had before back?

I dont know what went wrong, exept that after many things it had errors about something like: eg_gb:gb problems, reverting to normal C compiler or something - I cant really remember.

any help would be great as I would like to make my computer usable again.

tmmuk

EDIT: should I post this in a new thread?

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]
any help would be great as I would like to make my computer usable again.

tmmuk

EDIT: should I post this in a new thread?[/QUOTE]

Stay calm, we'll fix it, don't worry.
Did you issue both commands?

sudo apt-get upgrade 
and
sudo apt-get dist-upgrade ?

Login in your terminal and run both commands again
Regards, Steve

---

### Post by tmmuk on 2005-10-29
So you reckon I should try upgrading again, even though I already have? Ill try it and see what i get...

EDIT: after doing this it removed about 3 packages and upgraded kismet (odd?) but im back to the terminal ( even after reboot)

any more ideas?

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]So you reckon I should try upgrading again, even though I already have? Ill try it and see what i get...

EDIT: after doing this it removed about 3 packages and upgraded kismet (odd?) but im back to the terminal ( even after reboot)

any mroe ideas?[/QUOTE]

Did you use BOTH commands again? I first did apt-get upgrade, then dist-upgrade, then had to do the apt-get upgrade again to get x back

---

### Post by tmmuk on 2005-10-29
Yes i typed:
```
sudo apt-get upgrade

sudo apt-get dist-upgrade
```

still at the terminal...

EDIT: ... even after another reboot

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]Yes i typed:
```
sudo apt-get upgrade

sudo apt-get dist-upgrade
```

still at the terminal...[/QUOTE]

What happens if you type startx in the terminal ?
If x doesn't start, what's your output

---

### Post by tmmuk on 2005-10-29
I typed:
```
startx
```
and got a blank (grainy? - it was covered in tiny white and black dots) screen with a black X-shaped cursor.

what should I do next?

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]

what should I do next?[/QUOTE]

Something f*cked up the x-server.
try ```
 sudo dpkg-reconfigure xserver-xorg 
```
from your terminal
Good luck 
Steve

---

### Post by tmmuk on 2005-10-29
i ran that command and it opened the configuring wizard for the X server. I went through it, leaving evrything as it was as I think it was all correct. When it came to setting screen colour depth, it stopped and went back to the terminal.

now what?

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]i ran that command and it opened the configuring wizard for the X server. I went through it, leaving evrything as it was as I think it was all correct. When it came to setting screen colour depth, it stopped and went back to the terminal.

now what?[/QUOTE]

Pffffffff if this doesn't work, i don't know anymore :( 
The reconfigure thing should fix it normally.

---

### Post by tmmuk on 2005-10-29
should I have changed anything in the configure thing? I practically just hit enter the whole way through (and reading it as well)

do you know anyone who might be able to help?

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]should I have changed anything in the configure thing? I practically just hit enter the whole way through (and reading it as well)

do you know anyone who might be able to help?[/QUOTE]

If you just hit enter, it takes the settings that are in your config file now, in other words you don't change anything :-) Are you sure the settings are correct? Is your screen resolution set ok?

---

### Post by tmmuk on 2005-10-29
I think so

but even If it was wrong, wouldnt I at least see part of the right thing?

---

### Post by tmmuk on 2005-10-29
If its any help then the error I get after the config wizard is:

```
: error: backup xorg.conf file /etc/X11/xorg.conf.200510292207 already exists;
please remove it and try again 
```

---

### Post by tmmuk on 2005-10-29
Please can someone reply

EDIT: im making a new thread to link to this

---

### Post by greatshape on 2005-10-29
[QUOTE=tmmuk]If its any help then the error I get after the config wizard is:

```
: error: backup xorg.conf file /etc/X11/xorg.conf.200510292207 already exists;
please remove it and try again 
```[/QUOTE]

Ok, remove that file 
```

sudo rm -f /etc/X11/xorg.conf.200510292207 
```
Then do this:
```

sudo  cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

```

Good luck

---

### Post by tmmuk on 2005-10-29
after typing:

```
sudo sh -c 'md5sum /etc/X11/xorg.conf
> /var/lib/xfree86/xorg.conf.md5sum'
```
i got
```
f3679b6818752b6f482db04136252079 /etc/X11/xorg.conf
sh: line 1: /var/lib/xfree86/xorg.conf.md5sum: Permission denied
```

im not sure I really understand the code you gave anyway

EDIT: after the last command, it complains that the package 'xserver-org' is not installed and that it has no info on it.

---

