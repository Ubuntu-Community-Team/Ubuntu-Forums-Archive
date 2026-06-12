---
title: "Interrupted synaptic, now everything is broken - HELP!?"
date: 2009-04-23
forum: General Help
---

### Post by Psychopump on 2009-04-23
Hello all,

I have a huge problem.
Synaptic told me that I had 2 broken perl packages, so I found them with the broken filter and (in my stupidity) changed the slection from remove to completely remove.

Soon I realised that synaptic started to systematically remove all my applications, so I (in even more massive idiocy) killed synaptic with xkill and rebooted my system.

>To my horror I no longer had a logon screen, just command line interface.
I tried startx but nothing happened.

Rebooted into recovery mode, tried to repair broken packages but it left some unrepaired. Tried the repair X option and after it finished rebooted normally.

Again no GUI. Logged in and typed startx.
Now it gave me abeige textured screen and a mouse cursor but nothing else.

I have no live-cd, my dvd drive is shot, and all I have to work with is my wifes netbook. PLEASE can anyone help me recover my system?

---

### Post by ubu-for on 2009-04-23
Try this.

[http://ubuntuforums.org/showpost.php?p=7128360&postcount=2](http://ubuntuforums.org/showpost.php?p=7128360&postcount=2)

---

### Post by Psychopump on 2009-04-23
Thanks for your quick response.
Unfortunately it made no impact on my problem.

I am also getting a "resolve generated breaks" error in apt.

---

### Post by ubu-for on 2009-04-23
In case your X Server is broken, my first link should help but in case of a broken Ubuntu try the following as root.

[http://ubuntuforums.org/showpost.php?p=7124272&postcount=2](http://ubuntuforums.org/showpost.php?p=7124272&postcount=2)

---

### Post by Psychopump on 2009-04-23
OK, I am downloading the jaunty livecd (which will atek about 7 hours today).
My intention is to create a bootable USB stck so I can try to recover my system.

Problem is, my wife's netbook is running hardy and I cannot seem to get Unetbootin running on it.

How can I create the bootable USB stick from Hardy?


Also, if I manage to create the stick and use it, can I upgrade to jaunty to fix my problems? Will that destroy data? If so can I move data around from the livecd environment before upgrading?


PLEASE - this laptop is our family's entire entertainment system. We are all sitting here without music or movies and everyone is angry with me.

---

### Post by ubu-for on 2009-04-23
I'm just a user, so I have no further ideas how to solve your problem.

Try this ...

[http://ubuntuforums.org/showpost.php?p=7038127&postcount=2](http://ubuntuforums.org/showpost.php?p=7038127&postcount=2)

... or the following command.

```
sudo apt-get dist-upgrade
```

---

### Post by Psychopump on 2009-04-23
> **ubu-for said:**
> In case your X Server is broken, my first link should help but in case of a broken Ubuntu try the following as root.

[http://ubuntuforums.org/showpost.php?p=7124272&postcount=2](http://ubuntuforums.org/showpost.php?p=7124272&postcount=2)

Tried the instriuctions in the link.
"correcting dependencies: failed"

Do you have any more suggestions?
(or answers to my questions in my last comment?)

---

### Post by Psychopump on 2009-04-23
> **ubu-for said:**
> 

... or the following command.

```
sudo apt-get dist-upgrade
```

I tried this too.
It still tells me I have packages with unmet dependencies and will not let me upgrade.

---

### Post by ubu-for on 2009-04-23
> **Psychopump said:**
> Do you have any more suggestions?
(or answers to my questions in my last comment?)

No, I'm sorry!

---

### Post by por100pre1 on 2009-04-23
Removing some libraries can really break the system. Try this in recovery:

```
apt-get install ubuntu-desktop
```

Let us know which output do you get...

---

### Post by Psychopump on 2009-04-23
> **por100pre1 said:**
> Removing some libraries can really break the system. Try this in recovery:

```
apt-get install ubuntu-desktop
```

Let us know which output do you get...


did this...

I get a massive amount of data...of which I can only read the last page.

```
Recommends:  <name of application> but it is not going to be installed
```

This line is repeated many times, each time with the name of another application in it.

The last line is:

```
E: Unmet depencies. Try 'apt-get -f install' with no packages (or specify a solution)
```

....

Thanks for your efforts so far guys!

I have downloaded the Jaunty liveCD (quicker thasn I thought).
I am thinking of booting the liveCD (on USB) - moving all my files to my other partition and seeing if I can upgrade to jaunty from there.

If it all goes wrong and tghe upgrade wipes the partition, at least I still have my files.

Can anyone advise me on the best way forward before I go ahead?

---

### Post by por100pre1 on 2009-04-23
You can try this command:

```
aptitude
```

and check for any held packages. Press Shift+Q to close it. If any packages were found they can be unheld this way:

```
aptitude unhold NAME-OF-HELD-PACKAGE
```

---

### Post by 0per4t0r on 2009-04-23
reinstall ubuntu. all your apps are gone anyway, so you've got nothing to lose.

---

### Post by por100pre1 on 2009-04-23
> **0per4t0r said:**
> reinstall ubuntu. all your apps are gone anyway, so you've got nothing to lose.

It's actually easier to reinstall. Mount the /home folder from a LiveCD and copy its content to an external hard disk drive...

and then reinstall. Don't reinstall without backing up!

---

### Post by Psychopump on 2009-04-24
OK, I am going to reinstall. Going for Jaunty.
I have the iso downloaded, but am running into some difficulties:

I am familiar with unetbootin under windows, as a GUI based app to put a linux distro onto a bootable usb drive.
I downloaded unetbootin onto my wifes hardy machine, but it is totally different. I need to reboot and choose unetbootin from grub.

When I do, it is very complicated, and takes HOURS to download stuff (I have no option for using the iso I already downloaded) and when it is finished I cannot boot from it on my troubled machine.

I have been working at this for hours now, it is past 6am and I think I am getting so tired I will make mistakes. I think I will go to bed for a few hours.

In the meantime, can anyone tell me an easy(ish) way to make the jaunty iso bootable from usb, using a hardy machine to create it? (preferably GUI)

I would really appreciate it.
:):)

---

### Post by ubu-for on 2009-04-24
> **Psychopump said:**
> In the meantime, can anyone tell me an easy(ish) way to make the jaunty iso bootable from usb, using a hardy machine to create it? (preferably GUI)

I would really appreciate it.
:):)


**Syslinux**

> Ubuntu Linux (Live Version) von USB Stick booten

Ein USB Stick ist i.d.R. bereits mit FAT16 formatiert und braucht daher nicht extra formatiert werden. Ansonsten hilft das HP USB Disk Storage Format Tool. Ubuntu als ISO Downloaden und auf den USB Stick entpacken. Dann mit Syslinux den USB Stick bootfähig machen: syslinux -f usb-drive:. BIOS umstellen, so dass von USB gebootet wird.


Translation:

Boot Ubuntu Linux (Live version) from USB stick

A USB stick is already formated with FAT16 and so it's not necessary to format the USB stick again. Otherwise the HP USB Disk Storage Format Tool helps. Download Ubuntu as ISO and extract it to the USB stick. After that make the USB stick bootable with [Syslinux]('http://www.kernel.org/pub/linux/utils/boot/syslinux/'): syslinux -f usb-drive:. Change the BIOS settings to be able to boot from USB.

[http://lars-schenk.com/ubuntu-linux-von-usb-stick-booten/50](http://lars-schenk.com/ubuntu-linux-von-usb-stick-booten/50)

[http://translate.google.de/translate?prev=hp&hl=de&js=n&u=http%3A%2F%2Flars-schenk.com%2Fubuntu-linux-von-usb-stick-booten%2F50&sl=de&tl=en](http://translate.google.de/translate?prev=hp&hl=de&js=n&u=http%3A%2F%2Flars-schenk.com%2Fubuntu-linux-von-usb-stick-booten%2F50&sl=de&tl=en)


**USB Creator**

[http://wiki.ubuntuusers.de/Live-USB](http://wiki.ubuntuusers.de/Live-USB)

[http://translate.google.de/translate?prev=hp&hl=de&js=n&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FLive-USB&sl=de&tl=en](http://translate.google.de/translate?prev=hp&hl=de&js=n&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FLive-USB&sl=de&tl=en)

[img]http://wiki.ubuntuusers.de/_image?width=250&target=Live-USB%2Fscreenshot.png[/img]

---

### Post by unutbu on 2009-04-24
Psychopump, do you know what caused this to happen? Synaptic does not usually autoremove so many packages. Do you use multiple package managers? If so, which ones?

---

### Post by Psychopump on 2009-04-24
Thanks Ubu-for, I am tryning this right now. I will let you know how I get on...

> **unutbu said:**
> Psychopump, do you know what caused this to happen? Synaptic does not usually autoremove so many packages. Do you use multiple package managers? If so, which ones?

I think the problem is that when I wanted to remove perl via synaptic that I changed the default remove options to "mark for complete removal".
I do not use other package managers.

---

### Post by ubu-for on 2009-04-24
> **Psychopump said:**
> I think the problem is that when I wanted to remove perl via synaptic that I changed the default remove options to "mark for complete removal".

And a new installation of Perl was without success?

P.S. I've edited my last post to point out that there are two different ways.

---

### Post by Psychopump on 2009-04-24
Thanks guys!

I have succesfully upgraded to Jaunty without any data-loss!

:KS:KS:KS:KS:KS

---

