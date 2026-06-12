---
title: "Is there a Ubuntu equivalent of &quot;TeamViewer&quot;"
date: 2009-02-21
forum: General Help
---

### Post by bob-linux-user on 2009-02-21
I run Intrepid dual booting with Windows XP. As I wean myself away from Bill Gates I try to find programs that have the same functionality in Ubuntu as Windows programs. ( I have given up on finding a good OCR program though)

My question is- is there a Ubuntu equivalent(if necessary using WINE) of Teamviewer? This is a Windows program which enables the user to remote view/control another PC.Teamviewer will actually run in WINE but I can only support friends PC's running Windows not running Ubuntu.

---

### Post by yeleek on 2009-02-21
Heard of VNC?  Its a widely used remote control application with various sub branches.  VNC works on Windows and *Nix.

A popular one being tightvnc [http://www.tightvnc.com/](http://www.tightvnc.com/)

---

### Post by txcrackers on 2009-02-21
*rdesktop* is the command-line program that will give you Windows remote desktop. There are both Gnome/GTK and KDE GUI apps that make it a bit easier. And you don't have to install anything on the Windows boxes.

But if you can install apps on the remote boxes, VNC is a much better solution in many cases.

---

### Post by Faolan on 2009-02-21
The great advantage of TeamViewer is that it needs zero configuration compared to VNC which more often than not needs a port opened on a router. For non-IT people this is a blessing as it's hard enough to provide support without having to figure out router/firewall settings. All you need is the user number and their password. 

It'll be interesting to see if Linux could provide the same level of functionality.

---

### Post by adrian.tuhut on 2009-10-21
if it helps: i managed to run teamviewer with wine...

---

### Post by raprap30 on 2009-10-21
So did teamviewer also show your ubuntu apps, or only the windows/wine apps?

---

### Post by kestal on 2009-10-21
it would show up under wine apps but during the install it plops an icon on your desktop for easy access. Upon clicking, you mark it as a trusted program and off you go.

Anything installed through wine will often show in the wine category, rather than your ubuntu ones.

---

### Post by kvarley on 2009-10-23
TeamViewer can run through wine.

> sudo apt-get update
> sudo apt-get install wine
> cd ~/Downloads
> wine TeamViewer_Setup.exe

---

### Post by howefield on 2009-10-28
> **vitium said:**
> TeamViewer can run through wine.

Yep, it can and does very well indeed, although one caveat is that it will not connect to a linux box, only windows or mac.

You can give support to windows or mac, but not Linux with teamviewer.

I wish it did, it's a great program.

---

### Post by asim_quazi on 2010-03-16
> **vitium said:**
> TeamViewer can run through wine.


thanks sir its working fine

---

### Post by mikemelen on 2010-03-16
I have tried to use teamviewer5 on ubuntu 9.10 using wine, but it is not working perfect. Always getting connection reset error.

---

### Post by Boxxes on 2010-03-21
I Have been having the same problem and I would like help for it

---

### Post by lewmur on 2010-03-30
Running it in a VirtualBox XP session works fairly well.  No connection problems but does sometimes get confused over mouse control.  I too with there was a Linux version.  You can use VNC in Linux but you are back to the problem of knowing the remote systems IP address.

---

### Post by jcottier on 2010-05-19
Teamviewer now have a deb installer for ubuntu. But it appears to be a wine packaged version like picasa. I have tested this out:- linux to windows and windows to linux and so far it looks very good and works fine. But I have yet to try linux to linux over the internet. The only option not avalialable on the linux version appears to be the webcam.

---

### Post by maddg3241 on 2010-05-19
teamviewer is not for linux so u don't need wine

---

### Post by maddg3241 on 2010-05-19
teamviewer is now for linux so u don't need wine

---

### Post by maddg3241 on 2010-05-19
now

---

### Post by maddg3241 on 2010-05-19
.wysiwyg { 	BACKGROUND: #ffffff; FONT: 11px Verdana, Arial, Tahoma; COLOR: #000000 } P { 	MARGIN: 0px } .inlineimg { 	VERTICAL-ALIGN: middle } teamviewer is not for linux so u don't need wine

---

### Post by maddg3241 on 2010-05-19
.wysiwyg { 	BACKGROUND: #ffffff; FONT: 11px Verdana, Arial, Tahoma; COLOR: #000000 } P { 	MARGIN: 0px } .inlineimg { 	VERTICAL-ALIGN: middle } teamviewer is now for linux so u don't need wine

---

### Post by jcottier on 2010-05-19
Tested now to my home pc over my work adsl (4Mb/s ish) and works well 8.04 local -> 10.04 remote. File transfer, chat work fine. I would say it on par with LogMeIn. There is no VPN or remote reboot available but that can be done outside TeamViewer anyway. Not bad for a beta :)

---

### Post by bob-linux-user on 2010-05-31
I have tested the new deb of Teamviewer and so far so good. "Linux Format" magazine published in the UK (and elsewhere?) has a review on page 24 of the July 2010 edition. Thanks to everyone who replied.

---

### Post by purplepixie on 2010-05-31
Thanks for info just installed and impressed so far, no more running teamviewer under wine :)

---

### Post by NUboon2Age on 2010-06-10
I just discovered this.  Wow!!! it totally rocks!

---

### Post by NUboon2Age on 2010-06-10
I just discovered this.  Wow!!! it totally rocks!  Here's a review. [http://www.the-source.com/2010/04/review-teamviewer/](http://www.the-source.com/2010/04/review-teamviewer/)

If I'm understanding this right, under the covers its running on wine(?)

---

### Post by howefield on 2010-06-11
> **purplepixie said:**
> no more running teamviewer under wine :)

:lolflag:

Think again.


> **NUboon2Age said:**
> If I'm understanding this right, under the covers its running on wine(?)

That's correct, although works very much better than the windows version running in wine, which cannot connect to a linux box.

---

### Post by k0d3g3ar on 2010-08-17
I just tested this on Ubuntu 9.10, and it worked really well.  But there's definitely WINE in there somewhere.  The fonts are not native (Windows fonts) which is a bit disappointing.  However other than that, the performance was good.  I had some issues with running it for someone else to connect to my dual monitor uber desktop.  Initial attempts showed a big black display on their end, but eventually they managed to see my computer.

The only problem was that I lost keyboard and mouse click control shortly afterwards, meaning that they had complete control of my rig, and I couldn't disable them at all.  I see that as a big SECURITY FAIL, as I had to literally power off my computer to protect it.

However this is BETA software that I'm running, per their website.  I suspect they will get that sorted.

I've been looking for a FOSS program like this for years, but never came up with anything.  This is about as close to a solution as I've found.  And no, VNC won't work.  I have to support hundreds of customers of varying skill levels.  I need something that doesn't need a sys admin to configure a firewall to use.  VNC is great, when its setup correctly, but its definitely not ready to sneak its way through my client's firewalls.  

K

---

### Post by howefield on 2010-08-17
> **k0d3g3ar said:**
> I just tested this on Ubuntu 9.10, and it worked really well.  But there's definitely WINE in there somewhere.

Of course there is, double click the downloaded .deb package, and select the "Included Files" tab, that'll tell you what's in there. 

> I had some issues with running it for someone else to connect to my dual monitor uber desktop.

The only problem was that I lost keyboard and mouse click control shortly afterwards, meaning that they had complete control of my rig, and I couldn't disable them at all.  I see that as a big SECURITY FAIL, as I had to literally power off my computer to protect it.

The default settings for full access would allow the other user to disable local input. Perhaps that's what happened.

---

### Post by jack frost on 2010-08-22
> **Faolan said:**
> The great advantage of TeamViewer is that it needs zero configuration compared to VNC which more often than not needs a port opened on a router. For non-IT people this is a blessing as it's hard enough to provide support without having to figure out router/firewall settings. All you need is the user number and their password. 

It'll be interesting to see if Linux could provide the same level of functionality.


Thanks for this post.. I was not able to get logmein to work with controlling ubuntu; but teamviewer is nice!

---

