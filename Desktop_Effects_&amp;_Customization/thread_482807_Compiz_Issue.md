---
title: "Compiz Issue"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by Salazar420 on 2007-06-24
Below is the results of my trying to run compiz after a fresh install. I'm kinda wondering what this means; is my computer not capable of running compiz? If this is so, "DAMN," but there's always hope. I'm also having issues installing the right drivers for my video card -- i think they're the fglrx drivers, but I'll post that in the proper section of the forums, despite the fact that they could be related.
> xenouser@XeNoCoMp:~/Desktop$ compiz
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

---

### Post by Alex&amp;Linux on 2007-06-24
Well, I use beryl, but it looks like thats a problem with the rendering path (texture from pixmap)
Can you change any advanced settings?

---

### Post by Salazar420 on 2007-06-26
I actually think I managed to correct this issue by gedit -ing the /etc/X11/xorg.conf file. Sorry about the delay in responce. I'm actually having alternate issues with the comp now... actually, ever since messin' with compiz... even after reinstalling I have errors. For one, when I attempt to reinstall it says > 100% diskspace in use on /mnt/migrationmanagement.

And then when I actually achieve a reinstall it says 
> 
Here are the results of my attempts at a 'sudo apt-get update' and 'sudo aptitude update':
Quote:
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

> And here is 'sudo aptitude update':

Quote:
Fetched 10.7kB in 1s (6393B/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems

Also, system update in the system tray says
> 
Error: BrokenCount > 0

IDK... It's kinda frustrating... 101

---

