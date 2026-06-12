---
title: "HOWTO: running Openbox with Xfce on Natty"
date: 2011-08-25
forum: Desktop Environments
---

### Post by cnbiz850 on 2011-08-25
Why use openbox?  Simple answer is that I find it much more responsive than xfwm4.  Why use Xfce rather than Gnome?  To me, it is more responsive and cleaner - I have been using Gnome with Openbox, but feel Xfce better.  But it is just my own opinion, and I understand people may have different opinions.  If you want to run openbox with Xfce, the following can be of some reference.

I did what follows on Ubuntu 11.04 64bits with xubuntu-desktop installed.  This is just to share my own experience on the topic, and is in no way meant to be authoritative.  I want to write it here because I can't seem to find any other documentation about it and it is not very straight-forward to do.  Maybe someone else can provide better ways than what I share here.  If so, please do so in any regards.

[This page]("http://openbox.org/wiki/Help:XFCE/Openbox") should be authoritative and is straight forward.  Basically, one needs to do this: ```
killall xfwm4 ; openbox & exit
``` in an Xfce session and then logout from and save the session.
 
Among others, one problem I have with this is that the number of virtual desktops is restricted to 1 after a restart of the session, and it can only and need be changed through "obconf" after every login to the session.  That is a pain.

I googled around for solutions and found somewhere saying that it is due to a gdm bug and the workaround is that the following needs to be executed right before starting openbox: ```
xprop -root -remove _NET_NUMBER_OF_DESKTOPS -remove _NET_DESKTOP_NAMES -remove _
NET_CURRENT_DESKTOP
```  But I couldn't easily find where to put it in the Xfce-session startup process.

So here is what I did to resolve it.

0) If you haven't, you need to install xubuntu-desktop and openbox from the default repository.  Then at the gdm login screen, after selecting your login name, choose "Xfce" from the bottom of the screen, then input your password and login.

1) Do ```
killall xfwm4 ; openbox & exit
``` and save session as mentioned above;

2) Create a shell script called "start_openbox.sh" in directory "~/bin" (or some other of your own choice) with the following in it: ```
#! /bin/sh
xprop -root -remove _NET_NUMBER_OF_DESKTOPS -remove _NET_DESKTOP_NAMES -remove _NET_CURRENT_DESKTOP
openbox & 
``` and make it executable with ```
chmod +x start_openbox.sh 
```

3) Then go to directory "~/.cache/sessions".  You will find a file with name like "xfce4-session-My-XPS-L501X:0" where "My-XPS-L501X" should be the same as the output of "hostname" on your machine.  

4) Make a backup of it, then edit it.  While you are editing, make sure to check about a couple things first:

a) somehere it has the following: ```
Client0_CloneCommand=openbox
Client0_RestartCommand=openbox ........
Client0_Program=openbox 
```

b) if you find openbox appear with more than one "Clientn" sections (where n is a number), then you need to delete all the extra "Clientn" sections that has openbox with it and only keep one;

c) if you find xfwm4 appear with some "Clientn" sections, you also need to delete all those "Clientn" sections associated with xfwm4.

Both b) and c) happens with me after xfce saving the session (should be a bug in Xfce).

5) Now replace openbox with start_openbox.sh like in my case: ```
Client0_CloneCommand=/home/cnbiz850/bin/start_openbox.sh
Client0_RestartCommand=/home/cnbiz850/bin/start_openbox.sh
Client0_Program=/home/cnbiz850/bin/start_openbox.sh 
```  I don't know if all the above three need to changed, but it works for me and Client1_RestartCommand definitely has to be changed.

6) You should be able to logout (** Be sure NOT to save your session when logout) and re-login to see that openbox now runs your environment.  

7) If everything works, you may want to backup the file you just have edited in case it get written over by an unintended save session event.  If in any case you feel you don't want to use openbox with Xfce but want to use the original Xfce, you can simply remove everything related to Xfce in directory ~/.cache/sessions, then logout and log back in again.

My cache file is as follows.  In my cached session, I started openbox,  xfce4-panel, xfdesktop, xfce4-settings-helper, nautilus, and xfce4-power-manager.  

```
[Session: Default]
Client0_ClientId=2b934c037-a7b0-42ab-a2d5-7d2c236f338e
Client0_Hostname=local/My-XPS-L501X
Client0_CloneCommand=/home/cnbiz850/bin/start_openbox.sh
Client0_RestartCommand=/home/cnbiz850/bin/start_openbox.sh
Client0_Program=/home/cnbiz850/bin/start_openbox.sh
Client0_UserId=cnbiz850
Client0_Priority=20
Client0_RestartStyleHint=2
Client1_ClientId=26601721c-c9c2-4e20-875d-32b925e1873d
Client1_Hostname=local/My-XPS-L501X
Client1_CloneCommand=xfce4-panel
Client1_RestartCommand=xfce4-panel,--display,:0.0,--sm-client-id,26601721c-c9c2-4e20-875d-32b925e1873d
Client1_CurrentDirectory=/home/cnbiz850
Client1_Program=xfce4-panel
Client1_UserId=cnbiz850
Client1_Priority=25
Client1_RestartStyleHint=2
Client2_ClientId=25b96a864-9ebd-4b45-a18f-35f5019e56a8
Client2_Hostname=local/My-XPS-L501X
Client2_CloneCommand=xfdesktop
Client2_RestartCommand=xfdesktop,--display,:0.0,--sm-client-id,25b96a864-9ebd-4b45-a18f-35f5019e56a8
Client2_CurrentDirectory=/home/cnbiz850
Client2_Program=xfdesktop
Client2_UserId=cnbiz850
Client2_Priority=35
Client2_RestartStyleHint=2
Client3_ClientId=2daa99d9c-2688-4937-bc5a-8a4eb4756a54
Client3_Hostname=local/My-XPS-L501X
Client3_CloneCommand=xfce4-settings-helper
Client3_RestartCommand=xfce4-settings-helper,--display,:0.0,--sm-client-id,2daa99d9c-2688-4937-bc5a-8a4eb4756a54
Client3_CurrentDirectory=/home/cnbiz850
Client3_Program=xfce4-settings-helper
Client3_UserId=cnbiz850
Client3_Priority=50
Client3_RestartStyleHint=2
Client4_ClientId=2e10a39dc-7eac-4663-8cca-b523353d19ad
Client4_Hostname=local/My-XPS-L501X
Client4_CloneCommand=nautilus
Client4_DiscardCommand=/bin/rm,-rf,/home/cnbiz850/.config/session-state/nautilus-1314241288.desktop
Client4_RestartCommand=nautilus,--sm-client-id,2e10a39dc-7eac-4663-8cca-b523353d19ad,--sm-client-state-file,/home/cnbiz850/.config/session-state/nautilus-1314241288.desktop
Client4_DesktopFile=file:///usr/share/applications/nautilus.desktop
Client4_Program=nautilus
Client4_UserId=cnbiz850
Client4_Priority=50
Client4_RestartStyleHint=2
Client5_ClientId=28f6ee38b-d714-44ad-a169-f7babf547ee0
Client5_Hostname=local/My-XPS-L501X
Client5_CloneCommand=xfce4-power-manager
Client5_RestartCommand=xfce4-power-manager,--restart,--sm-client-id,28f6ee38b-d714-44ad-a169-f7babf547ee0
Client5_CurrentDirectory=/
Client5_DesktopFile=/etc/xdg/autostart/xfce4-power-manager.desktop
Client5_Program=xfce4-power-manager
Client5_UserId=cnbiz850
Client5_Priority=50
Client5_RestartStyleHint=0
Count=6
LegacyCount=0
Screen0_ActiveWorkspace=0
LastAccess=1314241288 
```

---

### Post by cnbiz850 on 2011-08-26
Sorry, I still have a problem with the above procedure that I can not resolve.

It occurred to me a couple times after cold start of the machine when I login and got no window manager running.  Don't know why openbox didn't run then.  I had to open a terminal and type "openbox&" to get it working.

---

### Post by JC Cheloven on 2011-08-26
Hi, thanks for the info. 
However, I think I'd advise anyone willing to use openbox (and a lighter desktop aside), to use a lxde based distro, such as LUbuntu. Or even better, installing a command-line system from an alternate cd, and then adding openbox and some few things. 
Starting from a heavier system is unnecesary if that's not what you want to use, IMO.

---

### Post by kerry_s on 2011-08-26
+1 for lubuntu

you might as well have it light from the start. lubuntu is also far easier to tweak.

---

