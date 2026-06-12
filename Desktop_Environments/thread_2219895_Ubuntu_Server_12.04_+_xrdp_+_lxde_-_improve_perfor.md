---
title: "Ubuntu Server 12.04 + xrdp + lxde - improve performance?"
date: 2014-04-25
forum: Desktop Environments
---

### Post by matt_fussell2 on 2014-04-25
In an effort to come up with a cost-effective way to deliver desktop functionality to a mixed-client (Windows/Mac/Linux) small-office environment, a test server running ubuntu server 12.04x64 was set up running an LXDE desktop environment delivered via RDP. This was done because everyone in the office has access to some form of an RD client. I started with server so that the build would be as efficient as possible, and the experiment has yielded fairly positive results so far. I'm wondering if their are any configuration tweaks or software changes that I should consider making to improve responsiveness on the server.

---

### Post by matt_fussell2 on 2014-05-05
The thought is that Linux is a multi-user environment by design - why should the end users all have to sit at the same machine and take turns using it? I've tested this concept on some aged hardware (P4 1.Ghz, 1 GB RAM), and we had three people remoted into the machine and working, albeit slowly at some points, at the same time. Surely there is a way to bring this concept live on newer hardware without spawning individual VMs on Vsphere or Xenserver. Has anyone else tried this?

---

### Post by matt_fussell2 on 2014-05-07
I have made a little progress on this.

The performance can be increased by modifying the xrdp.ini file (backup process noted because backups are important).

```

sudo cp /etc/xrdp/xrdp.ini /etc/xrdp/xrdp.back && sudo nano /etc/xrdp/xrdp.ini
```

In the [globals] section, change max_bpp=24 and add the command to use compression as so:

```

max_bpp=128
use_compression=yes
```

and modify the [xrdp7] section by changing xserver_bpp=24:

```

xserverbpp=128
```

---

### Post by matt_fussell2 on 2014-05-29
This solution works quite well if you don't need sound and simply need access to your remote desktop. The problem with sound is that it requires the server to 'throw' the sound to the client, most often using pulseaudio, which can get quite complicated. I wasn't able to get it to work, but should you feel inclined, there is a tutorial here:

[http://scarygliders.net/2012/04/06/get-audio-with-your-xrdpx11rdp-connections-lan-or-remote/](http://scarygliders.net/2012/04/06/get-audio-with-your-xrdpx11rdp-connections-lan-or-remote/)

I did find and execute what has turned out to be a better solution - details can be found here:

[http://ubuntuforums.org/showthread.php?t=2223938](http://ubuntuforums.org/showthread.php?t=2223938)

---

