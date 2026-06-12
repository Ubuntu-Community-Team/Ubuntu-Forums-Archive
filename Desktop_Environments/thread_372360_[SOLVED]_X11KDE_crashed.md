---
title: "[SOLVED] X11/KDE crashed"
date: 2007-02-28
forum: Desktop Environments
---

### Post by ithaka on 2007-02-28
Hi,

Yesterday was one of those days I never should have come out of bed. The day started at 5:30am, horrible day at the job. It ended at 9:17pm when my screen went black.

I am running Ubuntu 6.10 (desktop, upgrade from 6.06), switched to KDE 3.5.x when upgrading to 6.10. Having it for some months now I started looking around.
Just as I did with Windows installations, I wanted to shut down unnecessary services.

I will never forget what I did. Do not ask what I was thinking (I do not think I was at that very moment...)

Going through the list of active services I saw kdm and gdm active. I was figuring, with running KDE as active window manager, so why would I need gdm?
I do not know where it went wrong in the figuring but the moment Linux presented a text mode black screen with a white cursor going berserk, I knew it, this was wrong, very wrong.

Luckily I know my way around and I hoped that a reboot would do the thing. I could do a clean reboot but X11 did not restart. As a last resort I tried
a dpkg-reconfigure but this only resulted in a gray screen with the large x-shaped cursor, nothing else.

How can I get things working again?
And if this is not possible, how can I from the prompt copy my home directory to my wives computer? I did not automated this yet, first thing on the list when everything is back!).


Thanks for your help!

Olivier

---

### Post by renzokuken on 2007-02-28
have you tried

```
sudo apt-get install gdm
```

to reinstall/repair gdm

also, is your wives computer networked to your broken ubuntu box? and is it running linux or windows?

---

### Post by ithaka on 2007-02-28
> **renzokuken said:**
> have you tried

```
sudo apt-get install gdm
```

to reinstall/repair gdm

also, is your wives computer networked to your broken ubuntu box? and is it running linux or windows?
Thanks for the apt-get, did not think of that. Will try that this evening at home.
My wives pc is indeed networked to mine. Running WinXP.

---

### Post by renzokuken on 2007-02-28
cant guarantee reinstalling gdm will work but its worth a try

as for backing up the home folder to your wifes pc........i suppose one way to do it would be to set up samba on your ubuntu box (this is fairly easy to do with the right guide from the command line) so that your XP machine can "see" and "copy" files from the ubuntu machine across the network. there are simple guides in the wiki and scattered about the forums.

i suppose another option could be to zip up your home folder, and burn it to cd from the command line. i'm not sure of the exact command for the cd burning but zipping it up should be fairly straight forward. EDIT: or copying it to a USB key would be even easier. obviously this depends how big your home folder is

i'm not an expert on this, merely throwing in my two-cents, so i expect other people would have some better ideas

---

### Post by ithaka on 2007-02-28
I probably would go for the usb key, but how about mounting? To which dev are usb-keys mounted? Or does this go on the fly?

Thanks for the ideas already!!

---

### Post by renzokuken on 2007-02-28
in gnome it would automount, but not sure about the command line. if it does automount it will mount in the media folder e.g /media/usb so you could run

```
cp /home /media/usb
```

....or would it mount in /dev .....hmmm

even if it doesnt automount you can mount it manually with the mount command.......dont actually know it off hand but it will be in the help pages or wiki or in the forums somewhere

sorry if my answers seem a bit vague, i'm having one of those days where i cant remember anything off hand and i havent got time to look it up........but its all easy to do dont worry

---

### Post by ithaka on 2007-02-28
renzokuken,

The sudo apt-get install gdm was the hint I needed. Install did not work however, I first had to uninstall it first.
When the package was reinstalled I could choose which dm to work with. Again I choose kdm and now only kdm is running, my initial goal.
On the backup I quickly set up an ftp server on my wives pc. The amount of data was a little too big for my usb stick.

Thanks again for the help!

---

