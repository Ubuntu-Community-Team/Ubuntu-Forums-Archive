---
title: "Remote Desktop at Startup/Login Screen"
date: 2008-09-06
forum: Desktop Environments
---

### Post by speedgrind on 2008-09-06
I am a newbie to Ubuntu but have installed Ubuntu Server after following some guides. I have done lots of search through the Forums and internet but still could not find a solution for my problem. I am trying to remote control my Ubuntu box at login screen where I could enter username and password and then login. This should be done all remotely. I have try X11VNC but this do not help. Anyone please show me a complete guide to do this.

---

### Post by veloce on 2008-09-08
> **speedgrind said:**
> I am a newbie to Ubuntu but have installed Ubuntu Server after following some guides. I have done lots of search through the Forums and internet but still could not find a solution for my problem. I am trying to remote control my Ubuntu box at login screen where I could enter username and password and then login. This should be done all remotely. I have try X11VNC but this do not help. Anyone please show me a complete guide to do this.

It's not clear what you are actually trying to do but I don't think you'll find a complete guide for this.  

What I think you are after is XDMCP.  This is a standard feature of Ubuntu logins.  You can select to login locally or to a remote machine.

---

### Post by slanbarn on 2008-09-08
If it's the other way around you look for ie. logging in remotely to the ubuntu-box you need to allow XDMCP in GDM settings.

---

### Post by veloce on 2008-09-08
Good point, what are you trying to log in *from*?  

I assumed another Ubuntu box.

---

### Post by speedgrind on 2008-09-12
Yes. I want to remote control the Ubuntu box right at the login screen. This mean, I will remotely send magic packet to wake up the Ubuntu box, then I will remote access the ubuntu box again and I will be able to control the screen with my mouse. The Ubuntu box has a graphical user interface installed. 

Please show me a complete working guide on how to Wake up LAN and remote access at login screen. Thanks.

---

### Post by benjick on 2008-09-12
What's "the other box"? If Ubuntu use XDMCP as suggested.

For the Wake on LAN; see [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

---

### Post by garydauphin on 2008-09-20
I am in a similar position.  I need to setup an Ubuntu server in a remote location, with no monitor or keyboard.

Therefore, when it boots to the login screen, I need to be able to control it remotely from Linux, Windows, and Mac.

Remote Desktop works fine once you're logged in.  I need it to work BEFORE login.

Is there a way to start the RD process before the login screen appears?

Is there a new / better tool that would let me accomplish this?

Thanks,

Gary

---

### Post by veloce on 2008-09-21
> **garydauphin said:**
> I am in a similar position.  I need to setup an Ubuntu server in a remote location, with no monitor or keyboard.

Therefore, when it boots to the login screen, I need to be able to control it remotely from Linux, Windows, and Mac.

Remote Desktop works fine once you're logged in.  I need it to work BEFORE login.

Is there a way to start the RD process before the login screen appears?

Is there a new / better tool that would let me accomplish this?

Thanks,

Gary

XDMCP allows (requires) you to log in to the remote linux machine.

XDMCP will work from linux.  For Windows and Mac you'd need a local x server.

---

### Post by erwall on 2008-09-21
Here's how I've done it on several computers, has worked great.

```
sudo aptitude install x11vnc
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```
then
```
sudo gedit /etc/gdm/Init/Default
```
then
add this line to the bottom above exit:
```
/usr/bin/x11vnc -rfbauth -noxdamage /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```
then
```
sudo gedit /etc/gdm/gdm.conf-custom
```
add the following right below "[daemon]":
```
KillInitClients=false
```
then
```
sudo reboot
```

---

### Post by garydauphin on 2008-10-07
Thanks, but this did not work.

It might be turning X-based remote login, but it doesn't work for VNC.

gd

---

### Post by fermulator on 2008-10-07
I'm also trying to do something similar....
[http://ubuntuforums.org/showthread.php?t=939221](http://ubuntuforums.org/showthread.php?t=939221)

---

### Post by veloce on 2008-10-07
> **garydauphin said:**
> Thanks, but this did not work.

It might be turning X-based remote login, but it doesn't work for VNC.

gd

Is there a reason you don't want to use XDMCP?

---

### Post by garydauphin on 2008-10-20
> **veloce said:**
> Is there a reason you don't want to use XDMCP?
No particular reason.  I just don't know anything about it, and I know there are so many VNC related tools that pre-load as a service on Win and Mac so that you can control a machine BEFORE login, and they are all easy to use and setup.

Am I thinking small?

gd

---

### Post by angel6700 on 2008-11-05
As and additional explanation, I want to point that with VNC you get access to your desktop as the currently-logged-in-user. If there is someone else working in that computer you will move its mouse and all their windows.

With xdmcp you get the log-in window and you can log in the system as another user with any disturbance to any other users logged in this machine.

Regards.

---

### Post by sideshowmel on 2009-05-01
Yes I would like that ability, too... to be able to take over the machine as-is...l the user at the box could see all the movements/commands.  I could reboot and still access.

Sure, SSH works great, but sometimes I'd like to be able to show somebody something remotely without having to generate and send screenshots.

Just curious, thanks.

---

### Post by veloce on 2009-05-03
There appear to be two different use cases here and, IMHO, the best solution for each is different.

If you want to provide user support by "taking over" a users machine then VNC is the way to go.  You don't need to set it up as a service as the user will be logged in.

If you want to log into a machine remotely with a separate session to any current user, then use XDMCP - it's what it's there for. It's much faster.

[And if you want to control several different machines that sit on your desktop then use Synergy]

---

### Post by speedgrind on 2009-05-08
The problem that we always face is - if we RESTART the server,  we can NEVER use VNC to remote again to login. You just cannot connect vith VNC and it give you errors and NO connection

BAD POINT = VNC can ONLY be use after we have logon to desktop.

Any idea how to solve this or workaround? 

Problem: Can you imagine if I was troubleshooting the server remotely and I need to restart the server and I cannot login no more. The lousy workaround is I need someone to be in front of the server to login one time for me and the VNC services will run.

I have tried to put the VNC service in startup but nothing seems to work.

To all experts and professionals, please advice this Novice fellow who is new to Ubuntu.

Many thanks.

---

### Post by krunge on 2009-05-09
> **erwall said:**
> 
```
sudo gedit /etc/gdm/Init/Default
```
then add this line to the bottom above exit:
```
/usr/bin/x11vnc -rfbauth -noxdamage /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```


The above has a typo, the -noxdamage was inserted in the wrong place.  The line should read:
```
/usr/bin/x11vnc -noxdamage -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900
```
This way -rfbauth points to the password file now.

More info on this here:

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)

see that section marked 'Continously' in the above faq item.

---

### Post by veloce on 2009-05-10
> **speedgrind said:**
> The problem that we always face is - if we RESTART the server,  we can NEVER use VNC to remote again to login. 

For this task, you would be better to use xdmcp. What advantage does vnc have in this situation?

---

### Post by motodc on 2009-07-31
This isn't very secure, but how about this guy's solution:
[http://www.lucidtips.com/2008/06/29/enable-remote-desktop-and-auto-login-on-ubuntu/](http://www.lucidtips.com/2008/06/29/enable-remote-desktop-and-auto-login-on-ubuntu/)

---

### Post by mrfantastic on 2010-11-28
Just wanted to share my experience trying to set Ubuntu 10.10 to enable remote VNC logins directly to Ubuntu Login Screen (when no user is logged in yet):

First I had to install x11vcn from Synaptic Package Manager.

Then I had to add password to x11vcn:

```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```And lastly I had to add just one line at the end of [FONT=Courier New]/etc/gdm/Init/Default[/FONT] file (remember to put that line before 'exit 0' line ):

```
/usr/bin/x11vnc -noxdamage -rfbauth /etc/x11vnc.pass -o /var/x11vnc.log -forever -bg -rfbport 5900
```That's it, because Ubuntu 10.10 is using new version of GDM and x11vcn I didn't have to edit any other files to set KillInitClients=false, and now I can login to Ubuntu Login Screen from Windows machine using UltraVNC Viewer by simply using 192.168.1.2:5900 as a VNC  address.

Thanks for all previous posters giving excellent tips.

---

### Post by tkelito on 2010-12-01
mrfantastic - thank you for appending your thoughts to this thread.

Your steps worked perfectly and were simplistic enough to complete over SSH.

---

### Post by alfonso78 on 2011-03-19
> **mrfantastic said:**
> Just wanted to share my experience trying to set Ubuntu 10.10 to enable remote VNC logins directly to Ubuntu Login Screen (when no user is logged in yet):

First I had to install x11vcn from Synaptic Package Manager.

Then I had to add password to x11vcn:

```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```And lastly I had to add just one line at the end of [FONT=Courier New]/etc/gdm/Init/Default[/FONT] file (remember to put that line before 'exit 0' line ):

```
/usr/bin/x11vnc -noxdamage -rfbauth /etc/x11vnc.pass -o /var/x11vnc.log -forever -bg -rfbport 5900
```That's it, because Ubuntu 10.10 is using new version of GDM and x11vcn I didn't have to edit any other files to set KillInitClients=false, and now I can login to Ubuntu Login Screen from Windows machine using UltraVNC Viewer by simply using 192.168.1.2:5900 as a VNC  address.

Thanks for all previous posters giving excellent tips.

Hi guys,

be aware that many people encountered a bug in ubuntu 10.10 due to x11vnc (X crashes and you get log off / log out and back to login screen). Check here: [http://ubuntuforums.org/showpost.php?p=10455539&postcount=20](http://ubuntuforums.org/showpost.php?p=10455539&postcount=20)

using -noxrecord -noxfixes -noxdamage options for x11vnc solved the problem for me (or at least so it seems so far)

---

### Post by rberger on 2011-03-23
Will this work on Ubuntu 10.04?

---

### Post by royoni on 2011-04-10
Hi,

Just one reminder to this helpful x11vnc tip, make sure correct permissions are applied to the x11vnc.pass and x11vnc.log for it to load correctly at start up, else it won't work :)

Thanks!

> **mrfantastic said:**
> Just wanted to share my experience trying to set Ubuntu 10.10 to enable remote VNC logins directly to Ubuntu Login Screen (when no user is logged in yet):

First I had to install x11vcn from Synaptic Package Manager.

Then I had to add password to x11vcn:

```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```And lastly I had to add just one line at the end of [FONT=Courier New]/etc/gdm/Init/Default[/FONT] file (remember to put that line before 'exit 0' line ):

```
/usr/bin/x11vnc -noxdamage -rfbauth /etc/x11vnc.pass -o /var/x11vnc.log -forever -bg -rfbport 5900
```That's it, because Ubuntu 10.10 is using new version of GDM and x11vcn I didn't have to edit any other files to set KillInitClients=false, and now I can login to Ubuntu Login Screen from Windows machine using UltraVNC Viewer by simply using 192.168.1.2:5900 as a VNC  address.

Thanks for all previous posters giving excellent tips.

---

### Post by nmw01223 on 2011-04-10
I'm trying to do something similar that sort of worked - see this thread [http://ubuntuforums.org/showthread.php?t=1725675](http://ubuntuforums.org/showthread.php?t=1725675)

---

### Post by swhetsel on 2011-11-10
> **mrfantastic said:**
> Just wanted to share my experience trying to set Ubuntu 10.10 to enable remote VNC logins directly to Ubuntu Login Screen (when no user is logged in yet):

First I had to install x11vcn from Synaptic Package Manager.

Then I had to add password to x11vcn:

```
sudo x11vnc -storepasswd yourpasswordhere /etc/x11vnc.pass
```And lastly I had to add just one line at the end of [FONT=Courier New]/etc/gdm/Init/Default[/FONT] file (remember to put that line before 'exit 0' line ):

```
/usr/bin/x11vnc -noxdamage -rfbauth /etc/x11vnc.pass -o /var/x11vnc.log -forever -bg -rfbport 5900
```That's it, because Ubuntu 10.10 is using new version of GDM and x11vcn I didn't have to edit any other files to set KillInitClients=false, and now I can login to Ubuntu Login Screen from Windows machine using UltraVNC Viewer by simply using 192.168.1.2:5900 as a VNC  address.

Thanks for all previous posters giving excellent tips.

& 
> **royoni said:**
> Hi,

Just one reminder to this helpful x11vnc tip, make sure correct permissions are applied to the x11vnc.pass and x11vnc.log for it to load correctly at start up, else it won't work :)

Thanks!

&  

I Did this. [http://www.ubuntugeek.com/how-to-install-gdm-gnome-display-manager-theme-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-gdm-gnome-display-manager-theme-in-ubuntu.html) 

   So I am trying to do this on 11.10 and having no luck. I have installed gdm and edited all the files as stated above yet I can not VNC in to the login screen. Any idea? (VNC is working fine when a user is already logged in.)   

EDIT: Ignore the above. I was using tight VNC to no avail, however Regular old VNC viewer worked fine. Sorry and thanks for the info!

---

### Post by irvin on 2012-02-11
Here's something that will work !

before login screen, secure, with password and numeric keys are working !

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

---

### Post by cybergalvez on 2012-02-12
use x2go google it

---

### Post by pbhound on 2012-02-14
> **irvin said:**
> Here's something that will work !

before login screen, secure, with password and numeric keys are working !

[http://www.dannratemal.de/?p=450](http://www.dannratemal.de/?p=450)

this website appears to be in dannish...

---

### Post by Krytarik on 2012-02-14
> **pbhound said:**
> this website appears to be in dannish...
Actually, it's German ;-) ; and the English version is right below the German one (though not easily to spot, yes).

Regards.

---

### Post by perspectoff on 2012-02-14
I recommend a VPN server/client configuration then XDMCP.

Unless something has changed, XDMCP is not secure by itself. Using OpenVPN, though, you can get a secure connection through which you can use XDMCP.

While I use OpenSSH/X11VNC/KRDC many times a day (I use Kubuntu so I use KRDC instead of Vinagre), it is for access to servers that only have 1 user at a time.

For servers that have multiple users at once, XDMCP is superior. So only the secure tunnel (OpenVPN) is then required, and there can be many VPN connections as well.

---

### Post by whiskers751 on 2012-03-20
Just set your login prefs to auto-login :)

---

