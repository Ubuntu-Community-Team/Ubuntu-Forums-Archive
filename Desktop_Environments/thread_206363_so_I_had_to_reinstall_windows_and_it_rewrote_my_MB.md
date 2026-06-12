---
title: "so I had to reinstall windows and it rewrote my MBR..."
date: 2006-06-30
forum: Desktop Environments
---

### Post by cwncool on 2006-06-30
I reinstalled XP to get some hardware working, and (as I knew it would) wrote over my master boot record so now I can only boot to windows.  How can I reinstall GRUB on my HD, so I can choose whether to boot into ubuntu or XP, thanx!

---

### Post by simonn on 2006-06-30
Boot into linux somehow (boot disk/cd/dvd etc).

As root start grub:

```

% grub

```

In grub:

```

> root (hd?,?)
> setup  (hd?)

```

Where ? is a number. Grub drive numberings are similar to:

hda = hd0
hda1 = hd0,0
hda2 = hd0,1
hdb = hd1

etc 

If you have SCSI or SATA substitute hd with sd, e.d. sda = hd0, sda1 = hd0,0, etc above.

Things can get tricky if you have SATA, SCSI and IDE drives in the same system as the bios will decide which one is hd0, hd1 etc and you have to play around a bit, assign devices with /boot/grub/device.map (see man grub) etc.

---

### Post by cwncool on 2006-06-30
waht is the second "?" in "root (hd?, ?) for.... what do I put there? and I only have the live install cd... will that work?

---

### Post by coffeecat on 2006-06-30
[quote=cwncool]waht is the second "?" in "root (hd?, ?)[/quote] 
It's the partition number. Look at simonn's post. He did it explain it quite clearly. Remember that Grub counts from zero. So, as simonn said, hda1 = hd0,0, etc. For the setup command, you only specify the drive, so hd0 (grub) = hda (Linux), hd1=hdb, and so on.

In my experience this sometimes works from the live CD, sometimes not. It's best to boot into the HD install, but if you can't, boot up with the live CD and try the grub commands simonn listed ('sudo grub' in a terminal to get into grub), but you should do 'quit' at the grub command after 'root' and 'setup'. (Always polite to say goodbye. :wink: )

If that doesn't work post back and I'll give you a link to SmartBootManager. I can't lay my hands on the url just now - it's in a bookmark in another installation. You can use SmartBootManager on a bootable disc to boot into Linux or Windows. Handy to have around.

---

### Post by deathbyswiftwind on 2006-06-30
If youhave the alternative ubuntu cd (the now live install system) there is an option right in the boot manager to restore grub. Id ditch the live cd personally I didnt like it everytime Id try to custom partition my hd the installer would crash

---

### Post by cwncool on 2006-06-30
i only have the live CD with the installer built in, so i'll try it and report back here :)

---

### Post by cwncool on 2006-06-30
i couldn't get the terminal thing to work from the live cd, is there another way?

---

### Post by simonn on 2006-06-30
Meant in a genuinely friendly helping out new user way...

How do you expect us to help you when you say things like:

> 
i couldn't get the terminal thing to work


What happened? Are we meant to just guess? Would you be able to help someone if they just said that?

Have a read of [http://www.catb.org/esr/faqs/smart-questions.html](http://www.catb.org/esr/faqs/smart-questions.html).

Asking good questions will help you in life outside of computing as well.

To answer your question, you need to use a terminal to fix this.

Once you have booted up from the live CD, try pressing ctrl + alt + F1. Do you go to a terminal?

---

### Post by darkshadow on 2006-06-30
Even though the answers already posted should be enough I will still give this link as it is real good
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by shoot2kill on 2006-07-01
HMMM, THE FIRST ANSWER DID NOT WORK BUT DARKSHADOWS DID...

1. Pop in the Live CD, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "grub"

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

5. Type "setup (hd0)", ot whatever your harddisk nr is.

6. Quit grub by typing "quit".

7. Reboot. 


ONLY THING NOW, I CANT BOOT TO WINDOWS... NO OPTION IN GRUB MENU.. NO OPTIONS AT ALL...

sorry for caps lock, only just noticed


-- Sorry, wrong Thread --

---

### Post by simonn on 2006-07-02
[QUOTE=shoot2kill]HMMM, THE FIRST ANSWER DID NOT WORK BUT DARKSHADOWS DID...
[/quote]

Because:

[quote=shoot2kill]
3. Type "grub"

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

5. Type "setup (hd0)", ot whatever your harddisk nr is.
[/QUOTE]

Is soooo different to:

> 
% grub
> root (hd?,?)
> setup  (hd?)


:rolleyes:

---

### Post by darkshadow on 2006-07-03
Add the following to the end of /boot/grub/menu.lst You may have to change to root line.



title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

