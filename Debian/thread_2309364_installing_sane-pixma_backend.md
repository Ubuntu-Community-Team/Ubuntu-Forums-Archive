---
title: "installing sane-pixma backend"
date: 2016-01-09
forum: Debian
---

### Post by Luxx on 2016-01-09
If someone could help straighten me out on file placement for installing the sane-pixma backend in Debian I would really appreciate the help. I can only find OLD directions for Ubuntu and Mandriva. Instructions aren't working for me, but the last commit on the package was just a few hours ago, so that looks promising and supposedly supports a range of the Canon PIXMA machines. 

The instructions I've come across are here:
[Give your scanner a new fresh SANE installation, April 22, 2008]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")

[Alioth.debian.org, pixma: backend version 0.17.25]("http://anonscm.debian.org/cgit/sane/sane-backends.git/log/")
To download: ```
git clone git://git.debian.org/sane/sane-backends.git
```
May first need to: ```
sudo apt-get install git
```

It's a fresh Debian git file and I'm thinking this should be good. The instructions are for Ubuntu from 2008. But I figure if I can get things in the right place the thing might work.
I'm pretty sure I have this in the wrong directory, but haven't found anything that makes it clear where it should all go. The sane-pixma page at sane-project.org specifies files in /usr/lib64/sane/ where I don't have a lib64 folder.

Ultimately I'm hoping to get the scanner to actually work over wifi as well as the printer part of it does. As of now I can't get sane to start. When using a graphical interface it just hangs and starting by terminal has either no result or an error.

My current system is a custom AMD build with Debian Jesse with backports enabled and updated kernel, required for graphics drivers.

---

### Post by arochester on 2016-01-10
What is the model of the apparatus you are trying to install?

---

### Post by Luxx on 2016-01-10
The scanner is model Cannon PIXMA MX492. Apparently this particular model hasn't been tested with this backend.
Nmap shows it as Canon Pixma IP4000R printer. Crap. I thought I fixed that.

I have read a lot of stuff over the last few days on Sane and network scanners. There is a lot of conflicting information on configuration.
I actually got saned to start, so that's something.

*Update:*

Getting familiar with what goes in the conf files and the syntax involved seems to be the key now. I have a permissions issue. Sane will now look for scanners according to Canon's bjnp rules, but only run as root, and I can't seem to get it quite right.

Error:
> [bjnp] Cannot resolve host: printername.192.168.1.104 port 8612

I typed in "printername" because the printer's name is actually a string of numbers and letters and it isn't clear that it's the name of the printer.

Sane is running (if run as root), and is looking for the scanner, but I'm not convinced it's looking over wifi. Maybe it is. I seemed to be getting nowhere before installing xinetd and editing the xinetd.conf file. I read somewhere the backend should support wifi, but of course it's not guaranteed.

I'm a bit baffled that nmap continues to show the printer as a completely different printer. I did end up with the wrong driver installed when I was trying to install another backend for the scanner, but I undid all that. The current driver is correct.

I haven't found any simple answers, but there is information that may have got my thinking closer to the right track:
[Sane Project; sane-pixma.5]("http://www.sane-project.org/man/sane-pixma.5.htmlhttp://")
[SaneDaemonTutorial]("https://help.ubuntu.com/community/SaneDaemonTutorial")
[How to map network scanner]("https://askubuntu.com/questions/200915/how-to-map-network-scanner")
[Installation of saned with systemd (no inetd or xinetd) - saned refuses connection]("http://superuser.com/questions/985254/installation-of-saned-with-systemd-no-inetd-or-xinetd-saned-refuses-connecti")
[Howto: configure xinetd service under Linux or UNIX systems]("http://www.cyberciti.biz/faq/linux-how-do-i-configure-xinetd-service/")

There were others. There were things that weren't explained clearly or completely, and that were clarified elsewhere, sometimes in posts not directly related to this particular issue. Man-pages are always a good read, but don't always explain exactly what you're trying to do.

---

### Post by arochester on 2016-01-11
Have you tried the Linux drivers from Canon?   [http://supportdrivers.info/canon-pixma-mx492-driver/](http://supportdrivers.info/canon-pixma-mx492-driver/)

---

### Post by Luxx on 2016-01-12
> **arochester said:**
> Have you tried the Linux drivers from Canon?   [http://supportdrivers.info/canon-pixma-mx492-driver/](http://supportdrivers.info/canon-pixma-mx492-driver/)

Yes. I dowloaded the printer driver from the Canon website when I first got the printer and the printer part of it works great. This doesn't do anything for the scanner part of it though. I have reinstalled the driver a few times, and even tried downloading the scangear portion of it from other sources, but haven't been able to get the scangear thing to do anything.

As far as I understand, the scangear tool is set up to detect the scanner from a direct LAN connection and not over wifi. I do not have the printer connected to anything except by wifi, because I can't find a cable with the mini-USB interface that matches the port on the printer and another interface on the other end that will connect it to anything. The mini-USB (not micro) to USB cables may have once been common, but nobody uses them for anything anymore, except apparently for this printer. My only other option for a LAN connection is the RJ-11 telephone jack port, but I have nothing to connect that to, either. 

The printer works fine over wifi. The scanner should as well, since it is the same machine. Supposedly, Windows and Apple users can operate the scanner over wifi with Canon's proprietary software. I have been able to use other scanners over wifi on Linux with considerably less effort in the past, proprietary software notwithstanding... thanks to dedicated open-source developers, of course.

---

### Post by Luxx on 2016-01-12
I discovered my printer may be using a different ip address for the scanner, so I have included that ip address in my conf files.

I tried removing the printername from the conf files. Running xsane in terminal without root I am getting the following error:
> [bjnp] udp_command: no data received
[bjnp] Cannot read mac address, skipping this scanner
[bjnp] udp_command: no data received
[bjnp] Cannot read scanner make & model: bjnp://192.168.114.1
* same result under root

I haven't seen any documentation on including the MAC address in the conf files. While the sane-project.org website has the following example of a device name, I'm not sure what to do with it, or if this is even what xsane was asking for:
> Example: pixma:MF4800_192.168.1.45 is a  MF4800  Series  multi-function peripheral.
This is following the device  names  for  BJNP/MFNP  devices, but this example doesn't really help. The syntax is incorrect. Anything with ":" is read as a port and the other documentation I have seen has "." instead of an underscore. My brain is a little fried at this point.
I guess I'll try some things and see if anything works out.

Information in CUPS (maybe there's a clue):
> Driver:	Canon MX490 series Ver.5.10 (color, 2-sided printing)
Connection: cnijbe2://Canon/?port=net&serial=60-12-8B-65-7C-47

Latest attempt:
As for now I'm out of ideas. 
I edited the bjnp lines in the conf files to read:
```
bjnp://pixma_MX492.192.168.1.104
bjnp://60-12-8B-65-7C-47.192.168.114.1
```

I'm now getting:
> [bjnp] Cannot resolve host: pixma_MX492.192.168.1.104 port 8612
[bjnp] Cannot resolve host: 60-12-8B-65-7C-47.192.168.114.1 port 8612

Ports 8610 and 8612 are open. According to sane-pixma documentation the backend should listen at 8612. I don't know what I've missed.

---

### Post by Luxx on 2016-01-12
Update:

I have discovered I can now run scangearmp2 from terminal and it says no scanners found, but then lets me update the scanner list and finds Canon MX490 series (60-12-8B-65-7C-47). I can scan from here once and save the scan on my computer, but can't find the scanner from any other program, Xsane, Simple Scan, GIMP, nothing. The next time I run scangearmp2 I have to select the scanner all over again. At least now I can get a scan onto my computer. It may not be what I was hoping for, but it's partially working......

.....that is, Canon's scangear driver for Linux is working from terminal, but not sane-pixma as I had hoped.

The version of sane-pixma that could possibly get things working should be included in libsane-common (1.0.25-2), which according to Debian packages was just added to Stretch. Jessie has libsane-common (1.0.24-8). I tried downloading and installing again manually but dependencies are broken, so I'll wait until I can install it from backports. Until then I will just use scangearmp2 started from terminal.

---

