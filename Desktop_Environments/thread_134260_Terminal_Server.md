---
title: "Terminal Server?"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Kiotie on 2006-02-21
Hello everyone!

Due to the nature of my question I figured this might be the correct forum instead of the 'Absolute beginner' forum.  If not, let me know and I'll re-post.

I consider myself to be an advanced user when it comes to hardware and windows but I am 100% new to linux.  I am a telco tech so I'm not new to using a CLI to get things done.  Being new to linux I do not know any of the commands yet.  I have a copy of SuSe 8.x and have installed it a few times but never used it.  I read about Ubuntu in MaxPC and decided to give it a try now that I have an extra PC layin around.

My question is how to set up a Terminal Server so that I can access my Ubuntu PC from a windows PC?  I saw in the applications that Ubuntu comes with TS client software but I need it to work the other way around.

Thanks in advance for any help you can provide.
Kiotie

---

### Post by carlosqueso on 2006-02-21
I'm not 100% clear on what a terminal server is, but if all you're looking for is text-based use of your box, it's really easy.   You need to install openssh-server with ```
sudo apt-get install openssh-server
```  [https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto) has more info.  Then use putty ([http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)) on your windows box to get into your ubuntu box.  If you want stuff with GUI, I can't help you but I know it can be done.

---

### Post by Harleen on 2006-02-21
If you just want to access a text console, you can use OpenSSH as described or install an (insecure) telnet daemon (package telnetd).
If you want to start graphical applications from that console, you have to be running an X-Server on your Client PC. For Windows I'm using Exceed, but that's quite expensive...
It seems, that there's now a free alternative available. The Cygwin project has ported x.org to Windows. ([http://x.cygwin.com/](http://x.cygwin.com/)) But I haven't tried it yet.

Another solution would be exporting your whole Desktop using VNC. This protocoll is much faster for Unix and Linux than it is when exporting Windows sessions. So don't damn it if you have tried it with Windows before and experienced a sluggish handling.
I haven't installed a VNC server yet in Ubuntu, but on SuSE it has never been a problem. You can get a free VNC client for Windows here: [http://www.realvnc.com/](http://www.realvnc.com/)
Ubuntu offers some packages for VNC servers. I'd try to use "vncserver".

---

### Post by carlosqueso on 2006-02-21
I've used the cygwin x and ssh...It's sloooooooooooooooooooow...I'd reccommend some sort of vnc if that's what your looking for.  ssh is good for text, but definitely not paired with cygwin.

---

### Post by Kiotie on 2006-02-21
thanks for the input!  RealVNC was the ticket.  Seems to work good.  It's not as snappy as sitting at the termial obviously but not very slow at all.  Once I get up to speed on commands I may go the ssh route but not just yet as I'm a NOOB. ;)

---

### Post by nubious on 2006-02-22
I myself used to have ubuntu running (Hoary release) on an athlon 600 with 384 megs of ram, and I'd connect to it using VNC on my amd 2400+ behind my 100 mbit router, and it worked like a charm...  what was really cool was because I run dual monitors on my Windows machine, I just had VNC maximized on my second monitor, and I could even drag Windows windows (heh) overtop of my linux desktop, and when I clicked on the vnc window they would dissappear behind..  

Sorry.. I couldn't find a screenshot..  but trust me - tres cool!

---

