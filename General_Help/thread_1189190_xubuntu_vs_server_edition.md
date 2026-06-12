---
title: "xubuntu vs server edition"
date: 2009-06-16
forum: General Help
---

### Post by Hintzy64 on 2009-06-16
Hello Ubuntu community!

I've been using Mandrake/Mandriva Linux since ~2003, and have Mandriva 2008.1 installed on my work desktop, home desktop, and home web server.  Last week, I got a new (much faster! whee!) desktop box at work.  A few of my coworkers really like Ubuntu, so I decided to give it a try.  There are some differences between Ubuntu and Mandriva (and more noticibly between KDE, which I used previously, and GNOME) I'm getting used to, but on the whole I've been very impressed so far.  

One thing that has caught my attention is the speed of Ubuntu.  My new work desktop is a little more powerful than my home desktop (both are far better than the old work desktop), but they are similar enough, and things like evolution, firefox, OOO, and package installation seem much faster.  

This got me thinking about my home web server.  The server is my wife's old unused desktop, a 450 MHz Pentium III with 384 MB of RAM.  I'm using it as a LAMP server, SSH server, FTP server (though I will likely drop this in favor of SFTP/SCP), and to host the occasional bzflag game.  It has a keyboard, mouse and monitor, but I almost exclusively control it remotely via SSH.  

However, as it's a pretty old machine, my web page runs rather slowly on it.  I've considered once or twice paying for hosting elsewhere and giving up my control over the server to get better speed, but it's way more fun to run it myself if I can.  

So now I'm wondering how well I would do with Xubuntu or Ubuntu server edition on that machine.  Mandriva doesn't really have a lightweight option for older hardware or servers, and now I find that Ubuntu has two choices.  But the question is which one?  Xunbuntu is described as being lightweight and meant for older hardware, but I'm basically using the machine as a server.  I guess my worry is that the server edition is intended more for what I think of as a "typical" corporate server, which would be much more powerful than my little PIII, and would be overkill for what I'm trying to do.

So my question to you is which would you expect to perform better with the hardware and purposes I listed above?  Or do you think I'm completely wrong and won't see much of an improvement over MDV2008.1?  I feel there has to be some way to make a decent server out of this old computer, and I've just set it up as a regular desktop workstation, because that's what I'm used to.

Sorry for the long explanation and thanks in advance for any advice you may have!

Cheers,
-John

---

### Post by sdennie on 2009-06-16
I'm not sure if it will be faster than Madriva but, you would want to use the server version.  The X in Xubuntu just means, "Ubuntu base install with XFCE as the desktop environment".  As you use the machine via SSH, there is no reason to install a desktop environment.

---

### Post by akakingess on 2009-06-16
> **sdennie said:**
> I'm not sure if it will be faster than Madriva but, you would want to use the server version.  The X in Xubuntu just means, "Ubuntu base install with XFCE as the desktop environment".  As you use the machine via SSH, there is no reason to install a desktop environment.
+1, I think you would see some performance improvements, but should definitely go with the server addition, I have done the same as you and have tried different versions of linux on older hardware and have had excellent luck with Ubuntu, speedwise and as long as I was hardwired or had a "supported" wireless, than I think you should be better off. Just my 2 cents though. Let us know what you decide and how it turns out.

akakingess

---

### Post by Cheesemill on 2009-06-16
Ubuntu Server isn't specifically intended for high end server hardware.

The main differences are that there is no GUI with a server install and it uses a kernel that is optimized for server rather than desktop functions.

You'll get better performance than you would with Mandriva running it on old hardware as you don't have the additional overhead of running unnecessary GUI services.

As you say you use SSH to control your current server you should have no problems with the server version. I'd go for 8.04.2 rather than 9.04 as it is more stable and is supported for longer (until 2013).

---

### Post by Hintzy64 on 2009-06-16
> **Cheesemill said:**
> Ubuntu Server isn't specifically intended for high end server hardware.

The main differences are that there is no GUI with a server install and it uses a kernel that is optimized for server rather than desktop functions.

You'll get better performance than you would with Mandriva running it on old hardware as you don't have the additional overhead of running unnecessary GUI services.

As you say you use SSH to control your current server you should have no problems with the server version. I'd go for 8.04.2 rather than 9.04 as it is more stable and is supported for longer (until 2013).
Ah, I hadn't thought about the LTS version, good point.  From reading the "What's new" page for the 9.04 server, it looks like the only things I might miss by going with 8.04 is the "service" command (which I'm used to since Mandriva is a Red Hat derivative), and the Landscape stuff sounds interesting.  Definitely worth considering though.

The thought of setting it up without installing a GUI feels weird, but as far as I can remember, the only times I've ever actually sat down at that computer were to install/upgrade the OS (and I even did my last upgrade via SSH) and when ndiswrapper freaked out (and I can hardwire it where it is now), so I should really be fine!  What's really funny is that in college I preferred Win95/98 to WinNT/XP because it was DOS-based and I could always revert to the command prompt if something went wrong, and now it's reversed, the GUI is my safety net.  :-p

I'll let you know how it goes.  Thanks again!

---

### Post by Hintzy64 on 2009-08-12
Just a quick update...

The server has been running with 8.04LTS for about two months now and it's working great.  I've only had two slight hiccups so far:


[LIST]
[*]When I booted from the installation CD, I was getting a black screen after the message "Trying to enable frame buffer".  Adding vga=771 at the boot prompt fixed this.
[*]After installation, when the system booted for the first time, the keyboard was unresponsive.  However, since SSH is running out-of-the-box (unlike on Mandriva, where you have to start sshd and open a port in the firewall), I just went to my other computer and logged in from there.  I have not tried the keyboard again, since I have no need to sit down at the physical machine.
[/LIST]
Other than that, everything is going extremely well.  The machine definitely runs faster than it did before, for just about everything, including prompting for a password on ssh login, file operations, software/package management, and serving the web page.  Also, I found that the debian_helper_scripts package contains the "service" command that I was looking for.  I'm very, very happy with the change!  :D

Thanks again for the help and advice,
-John
[http://www.rockettrombone.com](http://www.rockettrombone.com)  <-- site running from my 8.04LTS server! :P

---

