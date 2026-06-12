---
title: "FreeNX Windows Client (non exe)"
date: 2006-05-23
forum: Desktop Environments
---

### Post by ypout on 2006-05-23
Hi,

I would like to be able to remotely access my Ubuntu box at home from my work PC (XP locked down), however I can not install exe files etc on my work box (I have non admin rights etc](*,) ).  I have installed the FreeNX server on my Linux box but cannot find a freenx windows client which does not require installation.  I can run the "logmein" web based client from work and access my home Xp machine, so I'm looking for a similar client for a linux remote access tool. It doesn't have to be freenx but that seems like a pretty good package.
PS I'm no expert, I don't mind playing in the command line as long as it's nice cut and paste commands:)

---

### Post by dmizer on 2006-05-24
try putty for windows.  it doen't need to install, just run the stand alone exe.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by ypout on 2006-05-24
Thanks, for the suggestion, I'll download it when I get home ( I am not able to download any .exe files at work either](*,) ) and give it a go,
Cheers

---

### Post by dmizer on 2006-05-24
[QUOTE=ypout]Thanks, for the suggestion, I'll download it when I get home ( I am not able to download any .exe files at work either](*,) ) and give it a go,
Cheers[/QUOTE]
it fits on a floppy.

---

### Post by ypout on 2006-05-24
I've got it, I can download .zip files so I got a zip from the download site.
I can run it at work no problem, now I just need to set up the Ubuntu server end....
Can you run putty client with a freenx server or do I need to do soemthing else with my Ubuntu box.  I would like to be able to run a Gnome session not just xterm, is that possible?
One more thing....

I have been looking a various other threads on putty and freenx, and people seem to have problems connecting through a router, I have a router at home conected via cable modem with a fixed IP, the router assigns IP's (via DHCP) to my local WinXp and Ubuntu box's, will this be a problem, do I need to configure my router to forward ports, or set static IP's etc.  I'm really a newbie at networking, I just plugged everthing into my router and it just worked so I've not played with any settings.

Thanks for your help so far....

---

### Post by dmizer on 2006-05-25
putty will connect to several kinds of servers, you just need to choose which one you want to use.  a few i remember off the top of my head:
telnet, ssh, vnc ... i believe that ssh2 will allow gui interaction.

what service does freenx host?

if you have a router at home, you will need to configure it for port forwarding.  what brand and model of router do you have, i might be able to locate a good tutorial.

---

### Post by simonn on 2006-05-25
What do you actually want to do on your home system?

Webmin ([http://www.webmin.com](http://www.webmin.com)) may be the better tool as you do not need to install ANYTHING on the client. It is purely web driven. However, it does not allow for X forwarding, so no GNOME or KDE.

---

### Post by dmizer on 2006-05-25
that's why i suggested putty, because it also does not require you to install it to use it.  it is not webdriven, and with ssh2, it supports x forwarding.

also, it's fairly fast.

---

### Post by simonn on 2006-05-25
[QUOTE=dmizer]that's why i suggested putty, because it also does not require you to install it to use it.  it is not webdriven, and with ssh2, it supports x forwarding.

also, it's fairly fast.[/QUOTE]

Not meaning to threaten your e-manhood, but putty requires that putty.exe is made available to the windows PC. IOW it needs to be installed, even if installing it is only copying it to a directory on a floppy, usbstick, cd, harddrive, network share etc etc etc. 

It also requires an X server to be installed on the client PC to actually do X11 forwarding.

---

### Post by dmizer on 2006-05-25
[QUOTE=simonn]Not meaning to threaten your e-manhood, but putty requires that putty.exe is made available to the windows PC. IOW it needs to be installed, even if installing it is only copying it to a directory on a floppy, usbstick, cd, harddrive, network share etc etc etc.

It also requires an X server to be installed on the client PC to actually do X11 forwarding.[/QUOTE]
lol ... whatever e-manhood is, i'm sure i don't have it.  i'm not an expert, and i never claimed to be, i merely realize that teaching others is the best vehicle for learning.

but i did try out putty on my windows box in an account without admin privileges before i suggested it.

i've never considered an install to be something that you can run independently of windows registry.  but i'm also willing to concede to knowledge greater than my own.

---

### Post by Ramses de Norre on 2006-05-25
[QUOTE=simonn]It also requires an X server to be installed on the client PC to actually do X11 forwarding.[/QUOTE]
No it doesn't, I run putty a lot on windows machines with x11 forwarding enabled and without X installed. It works like a charm ;)

---

### Post by ypout on 2006-05-25
Hi all, 

Thanks for the help,

I have got hold of the putty client and can run it on my PC at work no problems there.  I would agree that running a stand alone .exe does not constitute installing, but I don't want to get into symantics, I just wanted something I can run on my locked down XP box, and putty seems to run fine.

I thought I might have to install x on windows but it looks like thay may not be the case - thanks Ramses de Norre.

I have no idea what freeNX actully serves but it looks like it supports ssh and x forwarding so I assume putty should be able to work with it.

In terms of what I want to do... 

I would like to be able to remotely access my Ubuntu box as if I was sat in front of it, so Gnome sessions would be ideal, I have no real need to be able to do this, just a desire to make it work and learn something in the process.  

My router is a D-Link AirPlus G DI-524 and I would apprecatie a link to a howto on port forwarding etc.

My biggest problem is finding time, having just become a father for the second time round,having a toddler and a 1 month old baby, seems to absorb all my time and energy.

PS can any one supply e-viagra to help boost my e-manhood:-D

---

### Post by Ramses de Norre on 2006-05-25
There will be a page port forwarding, forwarding rules, virtual server or something like that. Just set a rule there to forward port 22 (ssh) to your ip.

---

### Post by simonn on 2006-05-25
> **Ramses de Norre]No it doesn't, I run putty a lot on windows machines with x11 forwarding enabled and without X installed. It works like a charm  said:**
> 

So you can run a remote gnome-session on a windows machine via putty without having an X server on the windows machine?

My own experience, the experience of others I work with, and the putty doco disputes that:

[http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter3.html#using-x-forwarding](http://the.earth.li/~sgtatham/putty/0.58/htmldoc/Chapter3.html#using-x-forwarding)

"In order to use this feature, you will need an X display server for your Windows machine, such as Cygwin/X, X-Win32, or Exceed. This will probably install itself as display number 0 on your local machine; if it doesn't, the manual for the X server should tell you what it does do."

Hopefully, you are correct as this would be an increadibly handy feature, but I suspect otherwise. If you could let me know how you do it it would be very appreciated.

[QUOTE=dmizer]i've never considered an install to be something that you can run independently of windows registry.

Which is of cource an increadibly windows centric consideration. 

Does that mean I never installed anything before 1995? Does it mean that I did not install Linux on my PC?

The focus on the word "install" is probably wrong anyway. I obviously failed to explain what I meant correctly.

Having webmin installed on my PC at home would allows me to do anything on my home PC, except running gui applications, from a web kiosk. I can even get a terminal through a firewall that does not allow ssh or telnet traffic, without tunnelling (which would of course require more software to available on the client).

This is what I mean by not having to have anything installed on the client. You do not have to rely on the client having anything other than a web browser (with java for some functionality).

---

### Post by dmizer on 2006-05-25
[QUOTE=simonn]Does that mean I never installed anything before 1995? Does it mean that I did not install Linux on my PC?

The focus on the word "install" is probably wrong anyway. I obviously failed to explain what I meant correctly.

Having webmin installed on my PC at home would allows me to do anything on my home PC, except running gui applications, from a web kiosk. I can even get a terminal through a firewall that does not allow ssh or telnet traffic, without tunnelling (which would of course require more software to available on the client).

This is what I mean by not having to have anything installed on the client. You do not have to rely on the client having anything other than a web browser (with java for some functionality).[/QUOTE]
it was a windows centric question thus a windows centric answer.

the web kiosk/webmin solution is interesting to me though.  what kind of resorces does the webmin consume?  ie. how does it compare to openssh-server?

---

### Post by dmizer on 2006-05-25
[QUOTE=ypout]My router is a D-Link AirPlus G DI-524 and I would apprecatie a link to a howto on port forwarding etc.[/QUOTE]
don't have a link for you ... dlink has a sweet router emulator though, so i played with it a bit.

just log into your router and click on the advanced tab.  then click on the firewall button (on the left).  this is where you configure port forwarding.

enable it, then name it.  for "action" select enable.  for source, select WAN from the dropdown menu, and plug in your work ip address in both the iprange start and stop blanks.  you will need to know your work ip, not your work network ip.  to discover your work ip address, browse to [www.whatismyip.com](www.whatismyip.com).

on destination, choose LAN from the dropdown menu, and in both the start and end ip range fields, plug in the ip for the target machine on your local network.  change the protocol to * and add port 22 to both the start and end range.

below that is a schedule ... i would suggest you enable and adjust this function so that this port is only open when you need it to be.

then select apply.  and you should be good to go.  let me know if that works for ya.

edit to add a nifty screen shot:

---

### Post by simonn on 2006-05-25
[QUOTE=dmizer]the web kiosk/webmin solution is interesting to me though.  what kind of resorces does the webmin consume?  ie. how does it compare to openssh-server?[/QUOTE]

The RSS values for sshd and miniserv.pl (the webmin server) on my PC at the mo 1348 & 3016 respectively according to ps.

This is essential the number of kb of memory used by the process.

So, webmin seems to use a little over double the memory.

---

### Post by ypout on 2006-05-25
Thank very much dmizer for the very clear instructions and the screen shot, even I should be able to follow that! , I'll give it a go and let you know how it goes, once I get a break between nappy changes:(

I've had some fun playing around with the various remote tools, I couldn't get naything to comunicate with my ubuntu box even on my own netwrok until I remembered I had set up firestarter, since configuring it to allow access from my home XP machine I have been able to connect through my LAN, using FreeNX, Putty (xterm only) and Tight VNC,  I just need to set Firestarter to allowWAN access from work and all should be well. I can run tight VNC through a flash drive on my Work PC so I'm hoping that will allow me to do what I want.

Thanks very much for everyones help......

---

