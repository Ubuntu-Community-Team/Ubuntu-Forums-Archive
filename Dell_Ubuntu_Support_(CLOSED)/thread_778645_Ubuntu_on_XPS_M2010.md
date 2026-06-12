---
title: "Ubuntu on XPS M2010"
date: 2008-05-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marbellapink on 2008-05-02
Hi,

I've installed Ubuntu on an XPS M2010 laptop (or tank, how I rather call it). All seems to work fine, especially when I used hardy instead of feisty (ati drivers and such), works like a bliss... except..

- My soundcard works, at least when I use headphones (listening to my youtube playlist right now). However, I want to have my mighty machine to blow that sound out of the speakers. I tried various things like linux-backports, but that apparantly broke my synaptics (its listed under broken, and thats most likely because I am using a 2.6.24-16 kernel image). I know it should be possible, because the soundcard works and the speakers work (system beep). Is there a way I can alter alsa configuration to do accomplish that?

- The buildin webcam is like detected in the hardware, but it doesn't work. How can I fix that?

For the rest, my synaptic package manager is like being dead. How can I manually remove a package like that linux backports??

thanks for your help!

---

### Post by marbellapink on 2008-05-02
roland@roland-laptop:~$ sudo apt-get install -f
[sudo] password for roland: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Reading state information... Klaar
De volgende pakketten zullen VERWIJDERD worden:
  linux-backports-modules-2.6.22-14-generic
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 1 te verwijderen en 61 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
After this operation, 6119kB disk space will be freed.
Wilt u doorgaan [J/n]? J
(Database inlezen ... 123855 bestanden en mappen geïnstalleerd.)
linux-backports-modules-2.6.22-14-generic wordt verwijderd ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: fout bij afhandelen van linux-backports-modules-2.6.22-14-generic (--remove):
 subproces post-removal script gaf een foutwaarde 1 terug
Fouten gevonden tijdens behandelen van:
 linux-backports-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
roland@roland-laptop:~$ 

So my software manager is still broken :(

---

### Post by marbellapink on 2008-05-02
I fixed the Synaptic issue with the broken package.

sudo gedit /var/lib/dpkg/status

Search through the file for any reference to linux-backport-blabla and delete the entry (all of it).Save and you can have a working update manager again.

Now, I found out that there should be a setting within Alsa that allows to use line in as source, I think that should be enabling my speakers.

---

### Post by mmb169 on 2008-08-12
Hi.  I know it's been a while since you posted, but did you ever get the laptop speakers to work?  Did that Alsa setting fix the problem?

I'd like to buy an M2010, but not if the laptop speakers don't work, and I haven't found anyone on the net who has encountered success yet.

Thanks,

---

### Post by sinnadyr on 2009-05-20
If anyone having the same problem, I fixed this using another sollution.

As marbellapink suggested:
> I fixed the Synaptic issue with the broken package.

sudo gedit /var/lib/dpkg/status
just really messed up my system. Had installed the linux-phc for undervolting of the CPU, and when I removed all references to the linux-backports... the undervolting went crazy and my system froze after about 10 seconds in x-server.

What I had to do was start the computer in shell-prompt, remove the linux-phc lines from /etc/apt/sources.list and then run:

```
apt-get purge linux-phc && apt-get update && apt-get install dist-upgrade
```

Remember that I had already removed the lines in /var/lib/dpkg/status

---

