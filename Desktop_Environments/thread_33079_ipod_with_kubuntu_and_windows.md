---
title: "ipod with kubuntu and windows?"
date: 2005-05-09
forum: Desktop Environments
---

### Post by Arandil on 2005-05-09
Hi,

i'm kinda new to the linux-scene and i'm trying to familiarize myself with kubuntu. Untill that has happened, i still boot everyday into windows, for instance to transfer new songs to my ipod. I've read the whole "ipod-on-linux"-thread, but i'm still wondering if i can use my ipod with windows and kubuntu at the same time, so that i can transfer songs from whatever system that i have currently booted. My question is probably unnecessary, but i want to play it safe... I don't like to format my ipod and re-transfer all the songs because i read something wrong!

---

### Post by !nkubus on 2005-05-09
First is it a ipod shuffle because if it's a shuffle the nex trick will not work?

ok the first thing you need to do it's :

EDIT  I FORGOT THAT:
```

sudo mkdir /mnt/ipod

```

```

sudo kwrite  /etc/fstab

```


then add the following line and save it

```

#Small hack to make my ipod working under amarok :)
/dev/sda2 /mnt/ipod vfat defaults,user,noauto,sync,umask=000 0 0

```

----------------The part above sould be done only once --------------------------------

then plug your ipod you should see an icon on the desktop named IPOD

click on it will mount it.

start or restart the program called amarok you should be able to send files through it with the media device icon.

then to remove it completly  open a terminal and type:
```

kdesu eject /dev/sda2

```
(it's the same as clicking on the eject button on Itunes)

I suggest  you to put an icon on your task bar to do that so you will only have to click on it to remove your ipod.

hope this helps, if you need anything else please let me know :)

Sorry for my bad english.

---

### Post by Octane on 2005-06-20
Great post. THANK YOU VERY MUCH!

---

### Post by allforcarrie on 2005-06-21
did this worK?

---

### Post by Octane on 2005-06-21
[QUOTE=allforcarrie]did this worK?[/QUOTE]
Yes, everything except for the how to eject part -- that crashes my system see [http://ubuntuforums.org/showthread.php?t=43170](http://ubuntuforums.org/showthread.php?t=43170)

Edit: Visit my journal if Ubuntu is giving you problems detecting your ipod via firewire.

---

### Post by !nkubus on 2005-06-21
[QUOTE=Octane]Yes, everything except for the how to eject part -- that crashes my system see [http://ubuntuforums.org/showthread.php?t=43170](http://ubuntuforums.org/showthread.php?t=43170)

Edit: Visit my journal if Ubuntu is giving you problems detecting your ipod via firewire.[/QUOTE]

Funny , the eject part always worked for me :(, maby because your ipod is firweire and mine is usb2?.

EDIT:
ooops I just read your journal and you fixed the issue I'm happy for you :)

---

### Post by TDave on 2005-06-21
Just tried this on my latest Kubuntu install (not yet tried it on the desktop...that comes after I finish this game...).

Whilst the detection works fine for me (using USB2, again, firewire comes later [when I find the cable...]) when I use aMarok and the Media Devices all I get is the list of files on the 'Pod (unopenable/playable) and all in different characters (I'm not sure but some look Far-Eastern, others just squares and dots, apart from the _no_album ones).

Any clue why this is/what I need to update?

Thanks

Dave

PS - Any conflict when using USB Memory sticks?

---

### Post by !nkubus on 2005-06-21
For the Characters i think it's an amaroK trouble, or a con figuration in your id3 tags.

as far as i know usbstick, they might be mounted as /mnt/ipod but amarok will not see anything and will not crash, but ir never happened to me.

EDIT:

do you have a screenshot?

---

### Post by TDave on 2005-06-21
Screenshot... :-)

And yes..I realize that I have no music as such in the library to drag across yet... that's stage 2! :-) Thanks, Dave.

Any idea why the 41M Removable appears at the same time?

[http://217.19.134.138/td/pics/snapshot1.png](http://217.19.134.138/td/pics/snapshot1.png) 
[http://217.19.134.138/td/pics/snapshot2.png](http://217.19.134.138/td/pics/snapshot2.png)

---

### Post by !nkubus on 2005-06-21
For the Characters, I actually have no idea :S:S, you might want to head down to [http://amarok.sf.net](http://amarok.sf.net) for help on that one, I Have no clue at all


but for the 41 mo drive it's actually the flash drive that contains the ipod OS, so this is not a bug, it's totally normal.

---

### Post by Octane on 2005-06-22
[QUOTE=TDave]Any idea why the 41M Removable appears at the same time[/QUOTE]
thats the first partition (/dev/sda1, thats why you mount /dev/sda2)

---

