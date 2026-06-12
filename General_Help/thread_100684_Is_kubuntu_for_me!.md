---
title: "Is kubuntu for me?!"
date: 2005-12-08
forum: General Help
---

### Post by comedyt on 2005-12-08
Hi,

I'm a newbie... i have an old laptop with PII 331mhz, 8GB HD, 192mb RAM... May I install ubuntu/kubuntu breezy badger into it... 

Earlier response is much awaited...

Thanks
Comedyt

---

### Post by feathers on 2005-12-08
Well, it will be very slow, kde or gnome. The system will definitely work but you might want to try to use a faster desktop like xfce, which you can install after an installation.

---

### Post by kori.mendocino on 2005-12-08
gnome will run faster then kde, but still, it'd be slow enough. feathers is right about xfce - install it via $ sudo apt-get xubuntu-desktop

---

### Post by tonysathre on 2005-12-08
when u do the initial install, at the boot prompt type server to install ubuntu without a window manager, then run a sudo apt-get install xubuntu-desktop

---

### Post by aysiu on 2005-12-08
[QUOTE=tonysathre]when u do the initial install, at the boot prompt type server to install ubuntu without a window manager, then run a sudo apt-get install xubuntu-desktop[/QUOTE] Don't you have to enable extra repositories first?

Do the server install.
You'll end up at a command prompt.
Log in.
Then, ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Remove the # signs from the beginning of any line that looks like a web address (especially if it has the word *Universe* in it. Save (Control-X), confirm (y), and exit (Enter). Then ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
startx
```

---

### Post by comedyt on 2005-12-09
Dear Friends,

 Thats really amazing...What an instantaneous guidance... I'm planning to install xubuntu on my laptop following ur advices and suggestions... will post u soon after i succeed in my attempt...

 My hearty thanks to all great hearts who came forward to help this newbie... :)

---

### Post by afhp on 2005-12-09
[QUOTE=comedyt]Hi,

I'm a newbie... i have an old laptop with PII 331mhz, 8GB HD, 192mb RAM... May I install ubuntu/kubuntu breezy badger into it... 
Comedyt[/QUOTE]

If at all possible, I'd recommend you jack up the memory to 256 MB. The rest is OK, I'm running Kubuntu Breezy on such a machine -- it's nowhere near blazingly fast, but it's fast enough to be usable for everyday work and internet-related activities. (Obviously, if you're doing heavy-duty graphics, that won't be enough.)

Xfce4 is a good recommendation as well... You might want to look [here]("http://xwinman.org") for an overview of other window managers, there's something for everybody... I personally like Window Maker, it's fast and lightweight, but some people find it confusing.

Whatever you pick, chances are you'll find it in Universe.

---

### Post by gingermark on 2005-12-09
You also might want to check out the [Ubuntu-Lite](http://ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu-lite) project, which uses IceWM as it's Window Manager. It seems pretty solid.

---

