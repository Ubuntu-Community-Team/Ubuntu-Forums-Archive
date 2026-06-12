---
title: "How do I get/install Ubuntu Netbook Remix?"
date: 2009-03-06
forum: General Help
---

### Post by markw10 on 2009-03-06
I want to try Ubuntu Netbook remix and want to run it on two environments.

First, I want to use it on a Mac Pro using VMWare for a virtual machine.  I plan to do this first.

I also am planning on purchasing a netbook within the month of March and will be purchasing the Acer Aspire 10" model.  

Will it run okay on these two machines?

Most of all I'm confused because I see how you can download the various versions of Ubuntu, Kubuntu, etc. but I don't see how you can download Ubuntu Netbook Remix.

I see some links talking about how you need a lot of experience to do it so do I have to do some type of compiling?
Is there an actual Ubuntu Netbook Remix CD that I can download?

Or do I install Ubuntu and then do a software update and download the Netbook Remix desktop?

Thank you for your help.

---

### Post by mikewhatever on 2009-03-06
It's not quite simple because there are several options.
1. [https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)
2. [http://www.eeebuntu.org/index.php?page=main](http://www.eeebuntu.org/index.php?page=main)
3. [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)

---

### Post by blazemore on 2009-03-06
```
sudo su

echo deb http://ppa.launchpad.net/netbook-remix-team/ubuntu hardy main >> /etc/apt/sources.list && echo deb-src http://ppa.launchpad.net/netbook-remix-team/ubuntu hardy main >> /etc/apt/sources.list && apt-get update && apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet  -y --force-yes && gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false 
```

If your theme didn't update, select the Human Netbook theme in the usual way.

Then add maximus and netbook-launcher to the list of startup items in Preferences->Sessions

As there isn't a configuration package available yet, you will need to setup the gnome-panel to mimic the standard UNR set-up. The applet order is as follows: 

go-home-applet | window-picker-applet | notifcation-area-applet | mixer-applet | clock

---

### Post by Danny Rafferty on 2009-03-08
I've tried this, but it did not apppear to work and I cannot find the theme to install afterward.
Here's what I get:
root@Ubuntu-Aspire:/home/danny# echo deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) hardy main >> /etc/apt/sources.list && echo deb-src [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) hardy main >> /etc/apt/sources.list && apt-get update && apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet  -y --force-yes && gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IE                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release.gpg                        
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Translation-en_IE
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release.gpg
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [46.7kB]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IE
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Packages        
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Sources               
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Sources         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Sources       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Sources 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Packages  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Fetched 308B in 0s (625B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  go-home-applet: Depends: libgnome-desktop-2 (>= 1:2.22) but it is not installable
  netbook-launcher: Depends: libgnome-desktop-2 (>= 1:2.22) but it is not installable
E: Broken packages


I have libgnome-desktop-2-7 (1:2.24) installed, but does not seem to be having an effect.

All help really appreciated.

D.

---

### Post by mikewhatever on 2009-03-08
Looks like you need to be running hardy to install that stuff.

Edit: No you don't, there is a repository for Intrepid too.

[https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation](https://wiki.ubuntu.com/UNR#Ubuntu%208.10%20(Intrepid)%20UNR%20Package%20Installation)

---

### Post by blazemore on 2009-03-08
Sorry about that. Here's the updated instructions for Intrepid:
```
sudo su

echo deb http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main >> /etc/apt/sources.list && echo deb-src http://ppa.launchpad.net/netbook-remix-team/ubuntu intrepid main >> /etc/apt/sources.list && apt-get update && apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet  -y --force-yes && gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false 
```

If your theme didn't update, select the Human Netbook theme in the usual way.

Then add maximus and netbook-launcher to the list of startup items in Preferences->Sessions

As there isn't a configuration package available yet, you will need to setup the gnome-panel to mimic the standard UNR set-up. The applet order is as follows: 

go-home-applet | window-picker-applet | notifcation-area-applet | mixer-applet | clock

---

### Post by jsett21 on 2009-03-09
blazemore,
I just tried your recommendation for Intrepid.  The Netbook interface is forefront on the screen, however when trying to pull up a window it will only display for a second before going off.  The app is still down on the taskbar and moving the mouse pointer over the where the window should be it displays but doesn't stay.  Maybe I didn't follow the instructions exactly b/c I'm a noob, but I appreciate your help.

---

### Post by jespdj on 2009-03-09
I don't have my Dell Mini 9 yet, but here's a guide to installing Ubuntu Netbook Remix on it. I guess this will work the same on other netbooks (or even laptops or other computers).

[http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-netbook-remix.html)

---

### Post by markw10 on 2009-03-10
I followed the above directions but the final step asked me to:

Add netbook-launcher (if using 8.10) to your startup programs. Go to System>Preferences>Sessions and add entry for this command.

I went to sessions to do it and see Netbook Launcher listed and selected to add it but it prompts me with the following menu:

Name
Command
Comment

What do I put in these blanks so that I can set this up?  For Command it gives me the option to browse.

---

### Post by Danny Rafferty on 2009-03-10
Sorry for not getting back for acouple of days, I've been a bit busy.
I get the same result from the command line you gave for Intrepid.
It's like I have two windows managers competing, and therefoe have no satisfactory windows manager.
I didn't record the response on my first installation, but here's what I get now. All help very much appreicated.

Danny.

root@Ubuntu-Aspire:/home/danny# echo deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main >> /etc/apt/sources.list && echo deb-src [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main >> /etc/apt/sources.list && apt-get update && apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet  -y --force-yes && gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Translation-en_IE
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IE            
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Translation-en_IE
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IE
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IE
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IE
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IE
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Packages         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/main Sources               
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/restricted Sources         
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Packages      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/main Sources       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/restricted Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Packages  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/universe Sources   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) intrepid-updates/multiverse Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Fetched 308B in 0s (424B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
go-home-applet is already the newest version.
human-netbook-theme is already the newest version.
maximus is already the newest version.
netbook-launcher is already the newest version.
window-picker-applet is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Error setting value: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

---

### Post by blazemore on 2009-03-11
> **markw10 said:**
> I followed the above directions but the final step asked me to:

Add netbook-launcher (if using 8.10) to your startup programs. Go to System>Preferences>Sessions and add entry for this command.

I went to sessions to do it and see Netbook Launcher listed and selected to add it but it prompts me with the following menu:

Name
Command
Comment

What do I put in these blanks so that I can set this up?  For Command it gives me the option to browse.

The only one that matters is command. add netbook-launcher to that, and it doesn't matter what you put in the other two.

---

### Post by Danny Rafferty on 2009-03-11
Yip that's there alright.
The new environment starts, it just seems like the old one is still there in the background interfering.
My windows seem to have no controls and the task bar at the top is invisible unless i click on it.
Perhaps I should just wait until they produce a proper package and config.

:(

---

### Post by Danny Rafferty on 2009-03-11
Oh, by the way, this is what I get if I run netbook-launcher from the shell:
root@Ubuntu-Aspire:/home/danny# netbook-launcher

(netbook-launcher:4224): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.
** (netbook-launcher:4224): DEBUG: CONFIG: Low graphics mode: False
** (netbook-launcher:4224): DEBUG: CONFIG: Font dpi: 96.000000
** (netbook-launcher:4224): DEBUG: CONFIG: Font changed: Sans 10

** (netbook-launcher:4224): DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting

** (netbook-launcher:4224): WARNING **: Failed to open file '/usr/share/netbook-launcher/default.svg': No such file or directory


** (netbook-launcher:4224): CRITICAL **: launcher_util_texture_set_from_pixbuf: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(netbook-launcher:4224): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(netbook-launcher:4224): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(netbook-launcher:4224): GVFS-RemoteVolumeMonitor-WARNING **: cannot connect to the session bus: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
** (netbook-launcher:4224): DEBUG: PLACES: No gtk-bookmarks file. Cannot load places

---

### Post by Danny Rafferty on 2009-03-12
I got it fixed.:P:
I had compiz running!:redface:
Feel stupid now.
Have to give thanks to a guy in another thread for suggesting it.
Can't find the mixer-applet but I'm sure I'll survive.

Thanks for all the help Blazemore:KS.  

Couldn't have done it without you.

BIG RESPECT.

D.

---

### Post by markw10 on 2009-03-13
I also had similar problems.
I got Ubuntu Netbook Remix going and at bootup I would see it boot up Gnome for a split second and then load the NBR desktop on top of it. I had to remove the bottom bar from the screen but I had a lot of problems with NBR running slow, 'crashing' and going back to Gnome, icons being blurred, etc.  I ended up realized I had to remove Compiz. I have not used NBR much since then but think that may have solved my problem.

---

### Post by blazemore on 2009-03-13
No problem.
I wish they hadn't removed the Thanks feature.

---

### Post by dhughes on 2009-03-14
I wanted to add that I just installed Ubuntu Netbook Remix (UNR) and it's gorgeous! I had a stock Xubuntu install on it and it was OK but it had problems but probably nothing that couldn't be fixed; dialog boxes too big, wifi/network trouble, couldn't logout or shut it off (power off with button OK though).

 It's so good I may use UNR as my main OS on my desktop, it would also look very nice on a touch screen computer such as HP's TouchSmart since the way UNR is setup makes the desktop simple to use with big icons.

 It's very easy to install just use ImageWriter app to put the UNR image on a USB flashdrive/USB key, reboot, press F12 to select the USB key and it's all automatic. The only thing you have to do after about 15 minutes (takes a while) is create a user/password and enter your timezone.

 Speed is great although it's not super fast, some clicks take 1/2 second to happen, overall I find it faster that my messed up (my fault) Xubuntu install and faster than the Windows install it came with (must remove that sticker!!).

 Even Standby works! :P

 My one problem was wireless connection (didn't try wired at that point) I had to reboot to get it to work but that was immediately after an install when I tried it. After the reboot it was there, wifi icon on the top panel.

 My only concern is keeping the install small, since I only have 8GB and probably 1GB or more is the OS I'm worried any new updates via Update Manager may bump that up to 2GB.

 If you have a netbook and are an Ubuntu fan I highly recommend Ubuntu Netbook Remix.

---

### Post by An_Dynas on 2009-03-14
for whatever it's worth, +1 for UNR.  I have an Acer Aspire One and, after great experimentation, always keep eeebuntu's UNR installed.  It is astonishingly cushy, easy-to-use, yet pretty quick.  But be forewarned, once UNR is on there, much of the customization that, at least I, had gotten used to with Gnome is gone.

I also keep a leaner OS, too.  Right now, it's Crunchbang lite with kuki sickboy's kernal.

---

