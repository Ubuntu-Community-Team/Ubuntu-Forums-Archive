---
title: "New FVWM Mac OS X  windows manager: give a try !"
date: 2010-08-27
forum: Desktop Environments
---

### Post by frenchn00b on 2010-08-27
Hello Guys, 

I would like to thank you all that contributed to help in making this Windows manager, enhanced from traditional Mac OS X produced by Apple. 

Please find the link to download it, here:
[http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v20.0%5D%2B50+Powertools%21?content=127893](http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v20.0%5D%2B50+Powertools%21?content=127893)

and to install it:
```

tar xvpfz mac-osx.tar.gz  # the tar.gz that you download
cd ; sudo sh .fvwm/install.sh
```

[B]Downloading LINK : [http://www.divshare.com/download/13252939-ef2](http://www.divshare.com/download/13252939-ef2)


Nothing to configure during hours, just unpack and install with install.sh as indicated above. Works for all and from bulk.

Please check the content before. No warranties.

[COLOR="Red"]**Enjoy the MAGIC !**[/COLOR]

**features in 15.2 version:**
[I][B]weather 
sound
fluxbox like, and much faster
power hacking tools
power tools
super extra wget intelligent !!
abook
contact and vocal email feature !!
scanning , automatic
stop watch
torrent
emails embedded with the OS 
burning
sync to pendrive ... 
control of of the OS from lirc remote control
swtich apps with the remote only (lazy hack :) ) 
...
and many more thing[/B][/I]

---

### Post by frenchn00b on 2010-09-16
Here the version is at its [version 9.31 ]("http://box-look.org/content/show.php/Mac+OS+X+FVWM+%5BStable+v4.8%5D+Gold+Edition?content=127893")! Many thanks to the all coders and contributors !

The present version is smoother as fluxbox and openbox :)

Enjoy !! 

I post a screenshot of few features.

---

### Post by kerry_s on 2010-09-16
what is that in the bottom left corner?
what pager/workspace switcher are you using?

see pic

---

### Post by honeybear on 2010-09-17
The FVWM has a pager [http://www.fvwm.org/documentation/manpages/stable/FvwmPager.php](http://www.fvwm.org/documentation/manpages/stable/FvwmPager.php)
it is embedded in itself

edit:
Please find presentation by [http://xwinman.org/fvwm.php](http://xwinman.org/fvwm.php)

---

### Post by frenchn00b on 2010-09-17
Hello Guys!!

Please find the version 10 with window theme selector. 

It is easy you can change your themes with making your own window theme (tar.gz file)

Example of themes are located here: [http://ironphoenix.org/tril/fvwm/configs/fvwm-theme/](http://ironphoenix.org/tril/fvwm/configs/fvwm-theme/)

Enjoy !!

I post you a screenshot with the fvwm theme selector.

[B]Downloading LINK to 10.3 version:
[http://www.divshare.com/download/12581217-f3c](http://www.divshare.com/download/12581217-f3c)[/B]

---

### Post by frenchn00b on 2010-10-05
Hi Guys !!

We have been heavily working on the versino 15.x.

Please find the version 15.2 of the OS / windows manager:

[COLOR="Red"]DOWNLOADS VERSION 15.2:[/COLOR]
**[http://www.divshare.com/download/12738257-f22](http://www.divshare.com/download/12738257-f22)**
website: [http://box-look.org/content/show.php/Mac+OS+X+FVWM+%5BStable+v4.8%5D+Gold+Edition?content=127893](http://box-look.org/content/show.php/Mac+OS+X+FVWM+%5BStable+v4.8%5D+Gold+Edition?content=127893)

**Simply check it, untar and enjoy the magic !!**

**features in 15.2 version:**
[I][B]weather 
sound
fluxbox like, and much faster
power hacking tools
power tools
super extra wget intelligent !!
abook
contact and vocal email feature !!
scanning , automatic
stop watch
torrent
emails embedded with the OS 
burning
sync to pendrive ... 
control of of the OS from lirc remote control
swtich apps with the remote only (lazy hack :) ) 
...
and many more thing[/B][/I]


THANK YOU ALL FOR THE THEMES YOU SENT ME !! I hope that they are all in the window theme, showed by the featuring 15.2, and that I forgot no one of you.

---

### Post by Rodney9 on 2010-10-08
I tried your script -

```
clear 


echo " *********************************************" 
echo "Installer FVWM MAC OS X" 
echo  " Welcome to Debian / Ubuntu ! "
echo " *********************************************"

echo "Installation started of fvwm macosx $(date)"  >> /root/fvwmmacosx_installation.log


if [ "$1" = "-fstab" ] || [ "$1" = "-install" ] || [ "$1" = "--install" ]* || [ "$1" = "--fstab" ] ; then
	echo "*************"

	echo " I will configure /etc/fstab first."
	MOUNTED=`mount | grep "on /home"`
	cp /etc/fstab /root/fstab-backup

	echo " " >> /etc/fstab
	
	if  [ "$MOUNTED" = ""  ] ; then 
	echo "*************"

	echo "Plug a pendrive, wait display change, then press <ENTER>"  ; read kldsjfdsflkj
	dmesg
	echo "*************"

	printf "Enter the pendrive /dev/SDX number;  example: /dev/sda1 ; default is /dev/sdc1 :> " ;  read  SD
	[ "$SD" = "" ] && SD="sdc1"
	echo "${SD}       /media/pendrive       auto    user,rw,auto,umask=0000,uid=1000,gid=1000  0    0 has been added" >> /etc/fstab
	echo "${SD}       /media/pendrive       auto    user,rw,auto,umask=0000,uid=1000,gid=1000  0    0" 
	

	##		echo "/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0"  >> /etc/fstab
	echo "*************"
	printf "Enter the IP of the /home NFS server (you are the client to NFS server)  X:> " ;   read XP
 
	if [ "$XP" != "" ] ; then
		echo "${XP}:/home	/home	nfs	defaults	0	0 has been added to fstab"  >> /etc/fstab
		echo "${XP}:/home	/home	nfs	defaults	0	0" 
	fi
	
	echo "*************"
	printf "Enter the folder of /movies or other: (shared folder on the NFS server, you are the client) it will be into / (default: movies) :> " ;  read movies
	if [ "$movies" != "" ] ; then 
		echo "192.168.1.${XP}:/${movies}	/${movies}	nfs	defaults	0	0"  >> /etc/fstab
		echo "192.168.1.${XP}:/${movies}	/${movies}	nfs	defaults	0	0"
		mount ${movies} 
	fi
	echo "*************"

	printf "Enter username to get audio/video permissions :> "  ; read MYUSER

	mkdir /media/pendrive -p
	mkdir /${movies}
	mkdir  /home/shared

	
	mount /home
	mount ${movies}
		if [ "$MYUSER" != "" ] ; then 
			adduser $MYUSER audio 
			adduser $MYUSER video
			adduser $MYUSER cdrom 
			adduser $MYUSER plugdev 
		fi
	fi

		
	echo "*************"
	
	printf "Configuration of the /etc/fstab and first user performed. Please check the fstab."
	cat /etc/fstab

	echo "*************"
	printf "Type of install: type <ENTER> to normal or type <mini> for a minimum installation for fvwm mac os x with few extras :> " ; read INST
	printf "Press enter to install with apt-get all the packages <ENTER> "  ; read dklsfjfdsljk
	clear
	echo "Sure that the PC works flawless without bugs" 
	apt-get install  -f gpm xserver-xorg xinit xterm  fvwm aumix alsa imagemagick  trayer leafpad audacious2  rox-filer grun  abiword    x11-apps  xserver-xorg screen        feh  vim   libnotify-bin zenity  rxvt  mkisofs cdrecord  nfs-common portmap vim alsa    mencoder mplayer  xterm  file-roller    leafpad less alsa      system-config-printer unzip       mc     leafpad less alsa    linuxlogo fswebcam rsync zenity dialog eog   ssh   gftp aumix   evince    	abook eog  mplayer mutt  galeon   mc   wput      zenity   elinks   jfsutils  iceweasel aumix   elinks rtorrent  reportbug  abiword  htop portmap nfs-common ntp 
	
	apt-get install  -f -y gpm xserver-xorg xinit xterm  fvwm aumix alsa imagemagick 
	# need some emailing stuffs
	apt-get install -f -y sendmail-bin msmtp mutt fetchmail reportbug sux xscreensaver
	apt-get install -f -y conky


	echo "Now installing for a more testing debian install, more risks"
	if [ "minimum" != "$INST" ]*; then 
		apt-get install  galeon gpart gparted nmap hatari kadu gimp audacious2 amule -f -y
		apt-get -f -y install xcompmgr
		apt-get -f -y install transset-df  
		##apt-get install -f -y kspread 

	fi

	apt-get install -f -y lame 
	apt-get install -f -y libmp3lame0 ffmpeg
		
	echo " ***** INSTALLATION FINISHED ***** $(date)" 	

	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	echo "INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "INSTALLATION FINISHED !!!! "   > /dev/tty2
	
	echo "$(date) INSTALLATION FINISHED !!!! "   > /dev/tty1  ;  	echo "$(date) INSTALLATION FINISHED !!!! "   > /dev/tty2

	echo "Installation finished fvwm macosx $(date)"  >> /root/fvwmmacosx_installation.log


	exit
fi


echo " "
mkdir /media/pendrive 
echo "Install the minimum required  packages" 
apt-get install fvwm aumix alsa imagemagick  trayer leafpad audacious2  rox-filer grun  abiword    x11-apps  
apt-get install habak   # has been removed from testing 
apt-get install feh conky  vim   libnotify-bin zenity  rxvt
apt-get install xserver-xorg screen
apt-get install eog mplayer mirage gimp kadu  rsync alsa
apt-get install xinit imagemagick fvwm rox-filer numlockx
apt-get install xinit xserver-xorg
apt-get install  x11-apps
apt-get install mkisofs cdrecord  nfs-common portmap vim alsa 
apt-get install  mencoder mplayer 
apt-get install xterm  file-roller
apt-get install lame  leafpad less alsa
apt-get install fetchmail sendmail-bin mutt msmtp abook
apt-get install  system-config-printer unzip
apt-get install fswebcam  rsync  
apt-get install linuxlogo


## not good :
##apt-get install dict-de-en dict



printf "\033[32m%10s\n\033[0m" "The date is now: $(date)"
echo "Installing gimp leafpad abiword hatari yes/no:"
read rep
if [ "$rep" = "yes" ] ; then
	apt-get install gimp leafpad abiword hatari mirage homebank
	apt-get install kspread  
	apt-get install iceweasel  
	apt-get install mplayer  xinit
fi

##/dev/sr0       /media/cdrom   udf,iso9660 user,noauto     0       0
```

on Lubuntu and when I log out and try FVWM it does not look anything like yours, just ordinary FVWM.

How do I get it to look right ?

Rodney

---

### Post by honeybear on 2010-10-10
.fvwm folder is not well set visibly

---

### Post by frenchn00b on 2010-10-10
> **Rodney9 said:**
> I tried your script -


on Lubuntu and when I log out and try FVWM it does not look anything like yours, just ordinary FVWM.

How do I get it to look right ?

Rodney


then there is a problem. 

try only 
```
apt-get install fvwm xserver-xorg x11-apps imagemagick
```
then 
```
cd ; rm -rf  .fvwm
tar xvpfz fmvwmmacosx.tar.gz # the versio nyou got
```


try my last version !!
[here]("http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v15.7%5D%2B50+Powertools!?content=127893&PHPSESSID=13092a6de6a023db0a645a6f92d9e0fd")

You like ?

---

### Post by frenchn00b on 2010-10-23
The version 16.2 has been released !! 

[http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v16.2%5D%2B50+Powertools!?content=127893](http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v16.2%5D%2B50+Powertools!?content=127893)


have you managed to make it work?  @@Rodney9

---

### Post by frenchn00b on 2010-10-30
New released Version 17 is now available with those powertools! 

```

17.0
- scanning to PDF
- reportbug/wishlist
- tiny changes in the menu
16.8:
-better mplayer video fvwm support
-support for IRDA sending files (usb dongle irda, extra to the irda remote, using irda0)
- Now a better support of the keyboard (taking account of hostname)
16.7:
Firefox internet bookmark context menu (dvdmenu key) has been added
Improved weather, nokia padding, remote keys
16.5:
very powerful mplayer player (folder to playlist, with memory/ and lirc videos replay)
16.3:
nokia script for typing chars/text and firefox surfing from distance with remote controller (great code) !!
powerful control of the pc using remote controller
reverse SSH
15.6:
- Better weather icons with day/night, better .lircrc, some extra sounds for media center
Fvwm media center added pressing HOME key of remote control
- saytime / bigben.sh
- netstat / dmesg / camera-video making video
- Better audacious control

features in 15.2 version:
weather
sound
fluxbox like, and much faster
power hacking tools
power tools
super extra wget intelligent !!
abook
contact and vocal email feature !!
scanning , automatic
stop watch
torrent
emails embedded with the OS
burning embedded with the OS
fvwm clonecd script embedded with the OS
sync to pendrive ...
control of of the OS from lirc remote control
swtich apps with the remote only (lazy hack )
...
and many more thing


```

Download link:
[http://www.divshare.com/download/13019240-f58](http://www.divshare.com/download/13019240-f58)

---

### Post by frenchn00b on 2010-11-09
Please find the version 18.2, very close to mac

Use gtk-chtheme into the main menu (left click on root or right flag on the keyboard) 

[http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v18.2%5D%2B50+Powertools%21?content=127893](http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v18.2%5D%2B50+Powertools%21?content=127893)

Fvwm is really nice environment !

---

### Post by frenchn00b on 2010-11-20
Almost version 20.
Now the top bar is very much nicer

You can also use a mac keyboard with it:

```
rm -rf $HOME/.fvwm
```

get the tar.gz 
then 
You simply then unpack, and run fvwm from your gdm or change .xinitrc then type startx 

```
cd ; tar xvpfz locationofthetargz.tar.gz 
```

and that's it you have a mac

I attach you the compatible keyboard !
**Nothing to configure !! This app does all, or asks you about what you wanna set.** 


[http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v19.8%5D%2B50+Powertools%21?content=127893](http://box-look.org/content/show.php/Mac+OS+X+FVWM%5BGold+v19.8%5D%2B50+Powertools%21?content=127893)

---

### Post by frenchn00b on 2010-12-06
The version 22.7 has been released. Give a try.

- Now there is also the *ONLINE TV Channels !!*

[http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v22.7%5D?content=127893](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v22.7%5D?content=127893)

Enjoy Linux Power !

---

### Post by ThomasAdam on 2010-12-21
I've obviously missed the point of this, but what is this thing supposed to do?

-- Thomas Adam

---

### Post by frenchn00b on 2011-01-29
> **ThomasAdam said:**
> I've obviously missed the point of this, but what is this thing supposed to do?

-- Thomas Adam

The title is maybe a bit wrong, since it is a themes. Ok, the features, it does a lot of things which is embedded themes. Otherwise the purpose of the configuration are destined to be close or superior to windows 2000 and mac os x at the same time. It has numerous improvements since it has the FVWM "core" which leaves much more functionality as the two later.

It is destined for both purposes:
- work (shared library, Desktop, and lot of bindings to work faster..)
- home, leisure, pictures, videos... 

I just made a screenshot.
The config. holds now the version 36.0
[LINK TO THE WM-TH]("http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v36.1%5D?content=127893")

I wish you a pleasant weekend, thomas.

---

### Post by Skara Brae on 2011-02-01
Is that for PPC's or "Intel Macs"?

I have a "1st Generation" iMac G5 (anno 2004), running "Tiger". So, a PPC.

---

### Post by frenchn00b on 2011-03-25
> **Skara Brae said:**
> Is that for PPC's or "Intel Macs"?

I have a "1st Generation" iMac G5 (anno 2004), running "Tiger". So, a PPC.

Hi,

Well you can run it if you can install FVWM. 

[http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v43.9%5D?content=127893&PHPSESSID=5ea2eb390f1f454adbf94ddfe048e512](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v43.9%5D?content=127893&PHPSESSID=5ea2eb390f1f454adbf94ddfe048e512)

Best regards

---

### Post by frenchn00b on 2011-04-03
[http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v50.1%5D?content=127893](http://box-look.org/content/show.php/Ultra+powerful+WM+for+humans%5BGold+v50.1%5D?content=127893)

you have now the Online TV too. Very useful as well.

---

### Post by frenchn00b on 2011-09-14
[B]Theme - Multimedia Mega Powertools Pack
 
[http://box-look.org/content/show.php?content=144581](http://box-look.org/content/show.php?content=144581)[/B]

Lot of improvements
Content: 

```

Extremely fast and powerful OS/WM environment for beginners and advanced users.

- Lot of function in this Configuration of WM:
* Various windows decorations (wd) available
(cf. http://ironphoenix.org/tril/fvwm/configs/fvwm-theme/ )
Choose or edit the wd file easily
* Allow exchange with users of window decoration themes
* Webcam/Web design support
* Automatic Email sending for large files
* Quick internet/screenshot/clipboard functions (shortcuts/keys)
* Online TV (TV streams of the world)
* Fvwm Power Translator (any languages) rapid from cursor and with popup/prompt
* Remote irda home center (A basic Mythtv / Freevo like program)
* Screenshots management
* Sound management
* Fvwm Jotter
* Camera management by fvwm
* Fvwm CDROM/DVD, Cloning
* Quick Windows Key shortcuts
* Shared document / Scanning
* Remote Irda Multimedia Center
* Home made Freevo/Mythtv based on zenity ;)
* EMu
* Cloning
* SSH Port forward for Camel admin
* Encrypting files
* IP geography/location tracker
* Blog maker (Jpg,...)
* PDFtk toolbit fvwm frontend (merging, cropping,...)
* Cut MP3, and convert them
* Convert AVI to other formats
* Record Webcam, or mics, send vocal emails
* Online Radio
* CD-roms and DVD burning and management (Wodim)
* Media pendrive management
* Delayed Outbox and multi-user email sending
* Settings for Mutt
* Learning Alphabet for you
* Easy installer of the packages for this configuration
* Powerful screenshot to shared folder or folder Theming, to never loose data and order when pressing WIN+Printscreen
* Fvwm extra clipboard with storing/pasting templates, date, ...
* lot of functions for Newbies (pdf, converters, website help programs, ...)
* You will discover an advanced way of using the bottom taskbar, for sound management, audacious music management,...)
* IP finder, netstat...
...
* And many many more functions!!

Enjoy LINUX and Share your Code/Developments !!

```

---

