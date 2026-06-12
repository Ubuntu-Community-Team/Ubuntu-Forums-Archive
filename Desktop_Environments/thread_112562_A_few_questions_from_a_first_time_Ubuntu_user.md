---
title: "A few questions from a first time Ubuntu user"
date: 2006-01-04
forum: Desktop Environments
---

### Post by neolithic on 2006-01-04
Greetings,

I just installed Ubuntu and it went very painlessly.  I have a few questions.  First, the computer I installed it on recieves an IP via DHCP which was very easy to configure, however everytime I restart so does my configuration forcing me to setup and activate the ethernet card with each reboot.  How can I avoid this? Secondly, I would like to have Lime Wire installed, but it only comes as an rpm.  I downloaded alien to convert to deb, but it says I must be logged in as root.  I only have one user account and it has all priviledges and belongs to the root group.  Lastly, this is installed on a fairly old computer and, while still running much faster than XP did, it is still a bit sluggish.  Are there any services/features I can turn off to help this?  Thanks in advance.

---

### Post by thekiller on 2006-01-04
[QUOTE=neolithic]Greetings,

I just installed Ubuntu and it went very painlessly.  I have a few questions.  First, the computer I installed it on recieves an IP via DHCP which was very easy to configure, however everytime I restart so does my configuration forcing me to setup and activate the ethernet card with each reboot.  How can I avoid this? Secondly, I would like to have Lime Wire installed, but it only comes as an rpm.  I downloaded alien to convert to deb, but it says I must be logged in as root.  I only have one user account and it has all priviledges and belongs to the root group.  Lastly, this is installed on a fairly old computer and, while still running much faster than XP did, it is still a bit sluggish.  Are there any services/features I can turn off to help this?  Thanks in advance.[/QUOTE]

1. If you dont want to start your network configuration during boot, then comment all the lines in /etc/network/interfaces except the one which says lo.  So when you reboot, open a terminal and just do sudo dhclient3 eth0.

2. To install a deb package, use sudo dpkg -i whatever.deb

3. I am not sure about what all to turn off to increase your work speed in ubuntu.

---

### Post by neolithic on 2006-01-04
Its not a deb package, its redhat (I believe, its extension is .rpm) thus I am trying to convert it to deb with alien but it is telling me I don't have root access.

---

### Post by dsjas297 on 2006-01-04
[QUOTE=neolithic]Its not a deb package, its redhat (I believe, its extension is .rpm) thus I am trying to convert it to deb with alien but it is telling me I don't have root access.[/QUOTE]

In your terminal:

```
sudo *command*
```

Replace *command* with whatever command you are using that requires root access.

---

### Post by neolithic on 2006-01-04
I am not sure I understand your response about my network configuration.  I installed it on my brothers computer so I don't want him to have to do anything on boot for the network to work.  I have configured it how I want, I just want it to remain.

^Thanks sudo worked, but I am now getting an error from alien.  I guess I will have to figure that out on my own.

---

### Post by Sef on 2006-01-04
I would download the 'Other' from Limewire and install it from source.  It's the last package listed.

Here's a thread on installing from source: [http://ubuntuforums.org/showthread.php?t=112075]("http://ubuntuforums.org/showthread.php?t=112075")

The basics are below.

To install from source:

1) Open the Terminal or Konsole.

2) ./configure

3) make

4) sudo make install

---

### Post by neolithic on 2006-01-04
I did that a few minutes ago actually using the Starter's Guide to Unbuntu.  I need to install the Java run time environment now as LimeWire won't start.  It is a .bin file, how can I convert this to .deb?

---

### Post by simoncm on 2006-03-03
bin files are binary files.  Similar to EXEcutables in Windows.  
Try:

./(filename).bin

You may need to change file permissions to execute.

---

### Post by akiro.yamamoto on 2006-03-03
To use the alien command:
sudo alien whatever.rpm
That will create whatever.deb
To install the newly created .deb file:
sudo dpkg -i whatever.deb
Done.
Please see the first link in my sig for more info on setting up your Ubuntu System
Welcome to Ubuntu Linux ;)

---

### Post by mgmiller on 2006-03-04
Instead of running Limewire, you should use Synaptic Package manager and install GTK-Gnutella.  It is precompiled for Ubuntu and will log onto all the limewire networks.  It's appearance and functionality are very similar to Limewire.  "It just works".

---

### Post by jamesr on 2006-03-04
Re the network problem :-
what are you having to do get it working? are you using the GUI or the Console.?

---

