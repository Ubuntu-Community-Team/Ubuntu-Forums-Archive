---
title: "Home network organization"
date: 2013-04-04
forum: Desktop Environments
---

### Post by dargaud on 2013-04-04
Hello all,
I have a question about working remotely with (k)ubuntu in a CPU and data intensive context.

At home I currently have an older desktop which works for multiple things (apache+NFS server, several large disks with archive of images, personal desktop, etc). It's getting old (random reboots) and slow. In particular I need to run WinXP in Virtual box for some image processing and its dead slow. Even more important, I need to reclaim the space where my desk is in the near future (no more destop).

So I'm thinking to replace it with a small headless file server and a laptop. I see 3 ways to work with it:
- either store all files on the server and run everything (virtualbox, image processing software, etc) on the laptop and access the files via NFS. Seems too slow for wifi and probably also for PLC (I have the plugs, but not tested, I believe they run at 100Mbps). Also it means buying a beefed up laptop which is more expensive than a beefed up homemade PC.
- or run everything on the server and access it via VNC or X11. The lack of responsiveness is going to be annoying fast I feel.
- or try to keep what I'm working on on the laptop and use scripts to sync everything (I have several Tb of images, so not everything can be on the laptop).

I cannot run a 1Gbps Ethernet line through the home without breaking all the walls... So wifi or PLC it is.
I'm open to suggestions in both hardware and software.
In particular I remember reading about some way to run a remote KDE desktop but I can't find that info.
Or some way to cache NFS directories locally on a 'as needed' basis ?
Or some other network filesystem ?

What would you do ?
Thanks.

---

### Post by kungfupete on 2013-04-04
dargaud: I'm afraid I can't give you any great advice on you specific situation, but thought I would share a couple things on my own setup:

* PLC:  I had a similar performance problem with WiFi sometime back, and solved it with some Belkin adapters.  The have worked well and no longer have the issues of pulling/posting large media files over WiFi.  I think 100mpbs is best case, but I never really tested thoroughly.

* Used stuff:  Depending on your location, I have had great luck on used laptops as everyone seems to want the "shiny & new".  Several years ago I ditched all my desktops, and placed my headless server on a used Thinkpad R61.  I used external USB device for primary data storage and another for backup (rsnapshot), offsite encrypted backup to Amazon S3.  Quiet, low power consumption, reliable, built-in battery backup/keyboard/display.... no complaints.  I use a separate laptop for other stuff, including running a dozen or so VMs via Virtualbox (security related testing).

---

### Post by dargaud on 2013-04-05
Thanks for your comment. I'm trying to get various inputs such as yours.

---

### Post by SeijiSensei on 2013-04-05
I have everything on a server in my office and access it via a wired network in my office and 802.11g wireless everywhere else.  I don't experience it as slow at all.  I can watch 720p H.264 video over the wifi using NFS without it missing a beat.  My server also runs Samba for Windows clients, network printing, email, local DNS, and provides one end of an OpenVPN tunnel to my remote servers in the cloud at Linode.  It also manages nightly offsite backups from the cloud servers. 

This is a 6-7 year-old [Dell Poweredge 400SC](http://www.dell.com/downloads/global/products/pedge/en/400sc_specs.pdf) with a Pentium P4, 256 MB of physical memory, and 512 MB of swap running CentOS 5.8.

---

### Post by dargaud on 2013-04-12
I'm thinking about another way to do it. Since I'll be working only one room away from the server, what about using a blutooth keyboard/mouse and a remote display. I've seen some solutions that can carry DVI/displayport over ethernet. *Anybody has experience with those?*

I don't do games so a high framerate doesn't matter as long as I have the original image quality in whatever high resolution I want.

---

