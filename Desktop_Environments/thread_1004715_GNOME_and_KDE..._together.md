---
title: "GNOME and KDE... together?"
date: 2008-12-07
forum: Desktop Environments
---

### Post by Wisp558 on 2008-12-07
Yes, you read the title right. I actually want to use BOTH! I think there should be a sticky outlining how to make the two desktop giants work together. But Until then, I have a few problems. But first, I should say... My systme started out as a clean Kubuntu install. After a while path I found the apt-get install ubuntu-desktop command and used it to install both GNOME and XFCE (though I haven't used it much yet...) . It is currently set using a GDM login screen, and I usually use GNOME as the default session. However, my problems  are as follows...

1) The view ~/Desktop plasmoid in KDE lags like hell. It sucks, and I hate it. This is the primary reason I use GNOME over KDE as my default session.

2) Many Icons in the System Tray (Or whatever its called in KDE) have a white square around them, instead of being part of the bar... It looks ugly. 

3) Firefox is my web browser. Period. It looks ugly in KDE. Any button just looks... intolerable, and check-boxes in the internet look bad too. I hate it. --solved

4) In GNOME, all the shortcuts from the KDE desktop plasmoid show up as icons, that do nothing. Aggravating. How do I make them disappear in GNOME, but stay in KDE.

5) How do I theme KDE apps to look nice in GNOME, and vice versa. I like the app selection about evenly down the middle. --Solved for GNOME in KDE

6) Is there any possible way I could implement the KMenu bar in GNOME? I really like it a lot more than Gnomes. 

I really like them about equally, but a sticky, or just some answers to my questions would be very, very appreciated.

~Wisp

Also, I've attached a screenshot which shows what I mean about the check-boxes, and the white squares around the system tray items.

---

### Post by MarblePanther on 2008-12-07
to fix the firefox problem, go to appearances in kde and change the gtk settings from oxygen to a real gtk theme like glossy or something similar

i'm using kde 4.2 and gnome right now

edit: click on use another style instead of the use kde style option

---

### Post by Wisp558 on 2008-12-07
Whoooo! Perfect. Exactly what I was looking for. You sir, earn a cookie. 


Oh, and something I missed.

How do you change what the pointer looks like in KDE? Is it just part of a theme, or can you set it separately?

---

### Post by MarblePanther on 2008-12-07
Keyboard and Mouse in System Settings

---

### Post by Wisp558 on 2008-12-07
Okay. I feel stupid. I can't believe I missed that. :facepalm:

---

### Post by MarblePanther on 2008-12-07
Oh, no I agree kde4 is confusing and cluttered

dont feel stupid

Gnome is so much easier to configure

I like aspects of both DE's though

---

### Post by Wisp558 on 2008-12-07
KDE has everything in obscure places, but it has more. It should take a look at GNOME for ideas on how to make customization features easier to find...  I like GNOME, because its simpler, and and also because its wireless assistant actually likes my card. Knetworkmanager doesn't like me.
(D-Link WUA-1340) But I'm not really annoyed at that, because the GNOME version works fine, and knet works great for other people.

Oh. Another thing... I run games in Wine, and a lot of them don't work quite as smoothly with compiz, so I made a script to change to metacity, and then check to see if the game process is running every 5 seconds or so... if it isn't running anymore, it runs compiz --replace again. Like so:

[CODE]
#!/bin/bash

metacity --replace
env WINEPREFIX="/home/wisp558/.wine" padsp wine "F:\Program Files\World of Warcraft\Launcher.exe" 
null=""
string="`ps -A|grep WoW.exe`"
echo string=$string
while [ -n "$string" ]; do
	sleep 5
	string="`ps -A|grep WoW.exe`"
	echo string=$string
done
compiz --replace &
[\CODE]

So, can I use an If then statement to check whether KDE or GNOME is running? What should I ps -A | grep for?

---

### Post by MarblePanther on 2008-12-07
You can install wicd to replace networkmanager (google wicd's main site and add their repo)

In kde go to System Settings, click the tab advanced and then go to autostart

uncheck networkmanager and add a script with shellscript wicd-client


Wicd is so much better for gnome and kde

I love it!
 

EDIT:

Here's a pic:

[ATTACH]95575[/ATTACH]

---

### Post by Wisp558 on 2008-12-07
note: I edited my last post... so... let it not be lost. I didn't realize Marble posted again.

Oh, and I'll try wicd.

---

### Post by MarblePanther on 2008-12-07
The best option for playing games (what i do) is login to fluxbox or icewm instead of gnome or kde.  Works like a charm

edit: or if you like masochistic wm's you can use twm ;)

---

### Post by Wisp558 on 2008-12-07
Yeah, but I'm a bit spontaneous. I like just clicking. I know I'm spoiled but... I have it running great in GNOME. (it being WoW)

---

### Post by MarblePanther on 2008-12-07
Idk, perhaps metacity or kwin

---

### Post by Wisp558 on 2008-12-07
Hmm... but I'm usually running compiz, so wouldn't meta and kwin not be running?

Oh, and I installed wicd. works like a charm. I'll remember that. Thanks for the idea.

---

### Post by Wisp558 on 2008-12-07
Oh, Here's my ps -A 
```
wisp558@wisp558-desktop:~$ ps -A
  PID TTY          TIME CMD     
    1 ?        00:00:01 init    
    2 ?        00:00:00 kthreadd
    3 ?        00:00:01 migration/0
    4 ?        00:00:55 ksoftirqd/0
    5 ?        00:00:00 watchdog/0 
    6 ?        00:00:00 migration/1
    7 ?        00:00:27 ksoftirqd/1
    8 ?        00:00:00 watchdog/1 
    9 ?        00:00:02 events/0   
   10 ?        00:00:01 events/1   
   11 ?        00:00:00 khelper    
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:01 kblockd/0    
   55 ?        00:00:00 kblockd/1    
   57 ?        00:00:00 kacpid       
   58 ?        00:00:00 kacpi_notify 
  143 ?        00:00:00 cqueue       
  147 ?        00:00:00 kseriod      
  193 ?        00:00:04 pdflush      
  194 ?        00:00:09 kswapd0      
  236 ?        00:00:00 aio/0        
  237 ?        00:00:00 aio/1        
 1188 ?        00:00:00 ksuspend_usbd
 1189 ?        00:00:00 khubd        
 1246 ?        00:00:00 khpsbpkt     
 1378 ?        00:00:40 ata/0        
 1414 ?        00:00:01 ata/1        
 1482 ?        00:00:00 ata_aux      
 1873 tty9     00:06:49 Xorg         
 1904 ?        00:00:00 gnome-keyring-d
 1914 ?        00:00:00 startkde       
 1976 ?        00:00:00 dbus-launch    
 1977 ?        00:00:01 dbus-daemon    
 1985 ?        00:01:18 scsi_eh_0      
 1986 ?        00:00:00 scsi_eh_1      
 1993 ?        00:00:00 scsi_eh_2      
 1996 ?        00:00:00 scsi_eh_3      
 2006 ?        00:00:00 knodemgrd_0    
 2017 ?        00:00:00 kdeinit4       
 2018 ?        00:00:00 klauncher      
 2020 ?        00:00:03 kded4          
 2025 ?        00:00:00 kwrapper4      
 2026 ?        00:00:00 ksmserver      
 2085 ?        00:00:00 nepomukserver  
 2086 ?        00:00:04 krunner        
 2088 ?        00:00:00 nepomukservices
 2089 ?        00:00:00 nepomukservices
 2090 ?        00:00:00 nepomukservices
 2092 ?        00:00:57 plasma         
 2099 ?        00:00:00 kaccess        
 2122 ?        00:00:00 kmix           
 2127 ?        00:00:00 gconfd-2       
 2128 ?        00:01:54 python         
 2130 ?        00:00:05 emerald        
 2133 ?        00:00:48 alarm-clock    
 2134 ?        00:00:02 python         
 2135 ?        00:00:00 nm-applet      
 2139 ?        00:00:00 python         
 2141 ?        00:00:00 ksmserver <defunct>
 2146 ?        00:00:06 knotify4           
 2147 ?        00:00:16 python             
 2148 ?        00:00:00 kblueplugd         
 2150 ?        00:00:00 klipper            
 2158 ?        00:02:02 amarokapp          
 2160 ?        00:00:01 notification-da    
 2171 ?        00:00:00 gvfsd              
 2172 ?        00:00:00 kdeinit            
 2177 ?        00:00:23 kjournald          
 2181 ?        00:00:00 dcopserver         
 2184 ?        00:00:00 klauncher          
 2187 ?        00:00:00 gvfs-fuse-daemo    
 2196 ?        00:00:01 kded               
 2213 ?        00:00:00 python             
 2340 ?        00:00:00 kio_file           
 2352 ?        00:00:00 udevd              
 2362 ?        00:00:00 knotify            
 2380 ?        00:00:00 ruby               
 4388 ?        00:00:35 mount.ntfs-3g      
 4392 ?        00:17:08 mount.ntfs-3g      
 4394 ?        00:00:00 kjournald          
 4666 tty4     00:00:00 getty              
 4667 tty5     00:00:00 getty              
 4672 tty2     00:00:00 getty              
 4673 tty3     00:00:00 getty              
 4674 tty6     00:00:00 getty              
 4851 ?        00:00:00 acpid              
 4904 ?        00:00:00 kondemand/0        
 4905 ?        00:00:00 kondemand/1        
 4978 ?        00:00:00 syslogd            
 5034 ?        00:00:00 dd                 
 5036 ?        00:00:00 klogd              
 5059 ?        00:00:18 dbus-daemon        
 5081 ?        00:00:00 avahi-daemon       
 5082 ?        00:00:00 avahi-daemon       
 5128 ?        00:00:00 cupsd              
 5348 ?        00:00:02 nmbd               
 5350 ?        00:00:00 smbd               
 5391 ?        00:00:00 smbd               
 5421 ?        00:00:01 winbindd           
 5429 ?        00:00:00 winbindd           
 5440 ?        00:00:00 yum-updatesd       
 5469 ?        00:00:00 console-kit-dae    
 5613 ?        00:00:48 firefox            
 5623 ?        00:00:00 bluetoothd         
 5629 ?        00:00:00 btaddconn          
 5630 ?        00:00:00 btdelconn          
 5650 ?        00:00:00 krfcommd           
 5697 ?        00:00:00 nm-system-setti    
 5723 ?        00:00:00 gdm                
 5750 ?        00:00:00 system-tools-ba    
 5784 ?        00:00:00 atd                
 5812 ?        00:00:00 cron               
 5884 tty1     00:00:00 getty              
 6267 ?        00:00:00 evolution-data-    
 8727 ?        00:00:00 kio_file           
10110 ?        00:00:00 loop0              
12878 ?        00:00:00 gdm                
13187 ?        00:00:00 evolution-data-    
13413 ?        00:00:00 dbus-daemon
13415 ?        00:00:00 dbus-launch
13433 ?        00:00:00 kdeinit4
13434 ?        00:00:00 klauncher
13437 ?        00:00:00 kded4
13460 ?        00:00:00 kio_file
14810 ?        00:00:00 konsole
14812 pts/1    00:00:00 bash
15781 ?        00:00:25 rt73usb
16079 ?        00:00:00 wicd
16101 ?        00:00:00 wicd-monitor
16304 ?        00:00:00 sh
16305 ?        00:00:01 wicd-client
17006 ?        00:00:00 wpa_supplicant
17140 ?        00:00:00 dhclient
19002 ?        00:00:00 winbindd
19003 ?        00:00:00 winbindd
19306 pts/1    00:00:00 ps
25781 ?        00:00:00 gvfs-hal-volume
25783 ?        00:00:00 gvfs-gphoto2-vo
25785 ?        00:00:00 trackerd
27823 ?        00:00:57 artsd
29339 ?        00:00:03 hald
29340 ?        00:00:00 hald-runner
29365 ?        00:00:00 hald-addon-inpu
29394 ?        00:00:00 hald-addon-cpuf
29396 ?        00:00:00 hald-addon-acpi
29466 ?        00:01:12 hald-addon-stor
29830 ?        00:00:00 sh
29831 ?        00:00:00 compiz
29883 ?        00:00:38 compiz.real
30551 ?        00:00:00 kwalletd
31511 ?        00:00:00 pdflush
32079 ?        00:00:00 kwalletmanager

```

Sooo.... maybe klauncher, kinit, or plasma?

---

### Post by MarblePanther on 2008-12-07
all of those would be good choices since they have to be running, go with plasma

---

### Post by Wisp558 on 2008-12-07
So... anyone have any ideas for the other problems I mentioned?

Is there a way to do in GNOME what Marble suggested I do in KDE with the GTK styles? That would make KDE more integrated into GNOME?

Also, as far as I found, I should use kdeinit (for the determining of whether KDE of GNOME is running)


As such...

 Startkde Script

The KDE startup sequence starts with the startkde script. In most cases this script gets called from the display manager (KDM) once the user has been authenticated. There are two very important lines in the startkde script:

LD_BIND_NOW=true kdeinit +kcminit +knotify

and

kwrapper ksmserver $KDEWM

The first line starts the kdeinit master process. This process is used to start all other KDE processes. The arguments behind kdeinit are the names of additional services to be started. The + indicates that kdeinit needs to wait till the service has finished.

The second line asks kdeinit to start the ksmserver session manager process. The session manager determines the lifetime of the session. When this process exits, the user is logged out. 


I found that on a website. So, kdeinit is THE master process that should definitively tell if KDE is running.

---

### Post by Wisp558 on 2008-12-07
I've been working on the WoW script. It currently stands at

```
#!/bin/bash

string1="`ps -A|grep gnome-session`"
string2="`ps -A|grep plasma`"
if [ -n "$string1"]; then
	metacity --replace
elif [-n "$string2"]; then
	kwin --replace
fi
env WINEPREFIX="/home/wisp558/.wine" padsp wine "F:\Program Files\World of Warcraft\Launcher.exe" WINEDEBUG=warn-all
null=""
string="`ps -A|grep WoW.exe`"
echo string=$string
while [ -n "$string" ]; do
	sleep 5
	string="`ps -A|grep WoW.exe`"
	echo string=$string
done
compiz --replace &
```


But it does nothing. I think there is something wrong in the string comparison. I'm a relatively new scriptor. Could someone please look it over or make suggestionss? Please?

Oh, and kdeinit is infact running on a GNOME session.

---

### Post by Wisp558 on 2008-12-07
Ah, c'mon. surely SOMEONE has some more insight! Don't leave me hanging here!

---

### Post by Wisp558 on 2008-12-08
Okay...bump?

---

