---
title: "Emulator Nintendo 64 ? Which one runs fast ?"
date: 2006-02-12
forum: Gaming &amp; Leisure
---

### Post by patrick295767 on 2006-02-12
Mupen64 is very slow (on a good pc)
  
fake64 is rather very difficult to make it installed ... 
  
How to install / which program can emulate the Nintendo 64 ?

Thnak you very much

Kind regards, 

Patrick

---

### Post by patrick295767 on 2006-02-12
In Linux, there is definitely no good emulation of Nintendo 64...
  
I just learned that today after trying them ... 

:-(

If you have any further information, plz let me konw ... 

Greezt

---

### Post by greyhound4334 on 2006-02-13
Mupen64 runs fairly well on my AMD64 3200+ machine.

It runs Zelda Ocarina of Time Master Quest nearly perfectly.  Paper Mario pretty well.  Has trouble with Tony Hawk's, though I haven't tried hard to get that working yet.  Overall, I'm very pleased with it.

---

### Post by patrick295767 on 2006-02-13
[QUOTE=greyhound4334]Mupen64 runs fairly well on my AMD64 3200+ machine.

It runs Zelda Ocarina of Time Master Quest nearly perfectly.  Paper Mario pretty well.  Has trouble with Tony Hawk's, though I haven't tried hard to get that working yet.  Overall, I'm very pleased with it.[/QUOTE]
  
Whao !
Nice information. I was about to give up. 
Did you try the regular MARIO ?
This is very laggy on my AMD 2200 about...
Is it coming from the CPU ? 
Which video plugin are u using ? Me, I do use the 0 (the default one)
  
If u'd like MARIO, I have it
(patrick295767@hotmail.com (msn messenger))
Where are u used to dwld the Roms for the N64 ?
(I have only one good website)

Thank you,  & greetings, 

Patrick

---

### Post by Destroyer of evil on 2006-02-13
I also use Mupen64. Most games work well, using video plugin 4 (the glide64 one).

One question - do you have proper video card drivers installed? Mupen was laggy for me until I installed the proper drivers.

I would give you a rom link, but I'm not sure if it's allowed on these forums.

---

### Post by patrick295767 on 2006-02-13
[QUOTE=Destroyer of evil]I also use Mupen64. Most games work well, using video plugin 4 (the glide64 one).

One question - do you have proper video card drivers installed? Mupen was laggy for me until I installed the proper drivers.

I would give you a rom link, but I'm not sure if it's allowed on these forums.[/QUOTE]
  
Hi Destroyer, 
Thank you for your reply
  
So, I will have a look this evening to get the name of the used plugin. 
Concernign my video card, I didnt install particularly any drivers because of it's  a ATI all in Wonder video card (with tv tuner also) but this card is not easy to make this tuner tv works. The video cards always behaved very well. I will try to find some drivers for linux via google. I looked on the website of ati and of course, no drivers are available for linux. That's normal. 
  
And, indeed, my mupen64 is laggy ...

Since I received some queries on how to install mupen64, I am gonna write it here: 
that may be insteresting too:
(I try to make an how to without linux box next to me)
  
1/ first: website to download the guy :
small overview of its possibilities: [http://mupen64.emulation64.com/shots.htm](http://mupen64.emulation64.com/shots.htm)
then, the downloading: [http://mupen64.emulation64.com/down.htm](http://mupen64.emulation64.com/down.htm)
or direct dwloding : [http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2](http://mupen64.emulation64.com/files/0.5/mupen64-0.5.tar.bz2)
  
2/ Then to unpack it very very easily (nothg to recall):
```
apt-get -f -y tar mc
apt-get -f -y zip
apt-get -f -y unzip
```
  
then type:
mc 
then, go to the downloaded archive, type enter, enter into the archive, 
then press COPY (F5), and unpack this file where u want.
  
3/It's now unpacked in ur harddisk

4/to make it run: 
then type:

```
sh mupen64
```
or
```
./mupen64
```
  
If I recall well, I did not do any : 
```
make 
make install
```

5/ U can also copy the folder into /usr/... and make it available for other users ... 

6/ When program starts, and may open/load the rom that you finally managed to download :-) 
  
7/ Try Zelda or Mario for instance.
My great favourite is Mario: Amazing colors, wonderful and dreamt land of Mario.
U may also notice at the beginning, the birds in the trees and the waterfall ... Nicely Programed ! :-)
===================
  
Greetings, 
   
Patrick

---

### Post by liquideath on 2006-02-14
Run fglrxinfo at the terminal. If it says "Mesa," then you don't have 3D acceleration, and the emulator will be slow. If its "ATI Radeon," then everything's good (driver-wise, at least). There is a ATI linux driver, and its in the repositories.

---

### Post by greyhound4334 on 2006-02-14
I think I use the ricevideo plugin for most games.  I haven't experimented that much yet.  It would be great if there were a database or something where people could keep track of which combination of settings works best for each game.

One other thing -- I'm not sure what the default setting is, but you should tryu to use dynamic recompilation (instead of Interpreter or Pure Interpreter) -- for most games, this seems to eliminate lag.

Regarding ROMs, I don't think you're allowed to mention sites here.  But google is your friend.  With some persistence, you'll find some sites.

---

### Post by patrick295767 on 2006-02-14
Hi, 

Back with Mupen64 !
  
So, I installed :
```
apt-get -f install gatos
apt-get -f install xorg-driver-fglrx
```
  
I tried :
Mupen64 CPU:     Interpreter      and Dynamic Recompiler.
  
I tried: 1-glN64 v0.4.1 
and 3-RiceVideoPlugin
for the MARIO Game.
  
With 2-jttl's SDL Plugin 1.3 for the sound
1-audio plugin    gives no sound.
==========
  
The results looks rather similar but a faster indeed. 
But it's still laggy
Can it come from the Audio, where the sound is rather laggy (I dont know how to say laggy - sound :-) ) ?
I have kidn of impression that the soudn is maybe makign this N64 slow , no ?
   
   
Would you have any idea what to do how to make it work ? 
 
Thank you very much of your precious help !!
  
Kind regards, 

Patrick

=========
btw, I can also post my server linux installation script.
That can help maybe someone who would like to install it as server first with a fvwm.
  ```
#!/bin/bash
echo "I hope u didnt forget to start enter the name of the main user"
echo " If right, press space otherwise, quit with ctrl Z or ctrl c"
echo "wait functino ?"
echo " Processing ..."
##mkdir "/home/$1/.fvwm"
cp "/etc/apt/sources.list" "/etc/apt/sources.list-backup"
cp "/root/sources.list" /etc/apt/sources.list
##cp "/root/.fvwm2rc" "/home/$1/.fvwm/.fvwm2rc"
apt-get update
apt-get -y upgrade
apt-get -f -y install mc 
apt-get -f -y install ssh
apt-get -f -y install ftp
apt-get -f -y install openssh-server
apt-get -f -y install x-window-system-core
apt-get -f -y install xserver-xorg
apt-get -f -y install 
apt-get -f -y install 

apt-get -f -y install nfs-common
apt-get -f -y install nfs-kernel-server
apt-get -f -y install portmap
apt-get -f -y install nfs
apt-get -f -y install proftpd
apt-get -f -y install autofs
apt-get -f -y install idesk
apt-get -f -y install xloadimage
apt-get -f -y install samba
apt-get -f -y install unzip
apt-get -f -y install openssh-server

apt-get -f -y install growisofs
apt-get -f -y install 
apt-get -f -y install 
apt-get -f -y install smbclient xloadimage

apt-get -f -y install dhcp3-server
apt-get -f -y install 
echo " You can go now for a cup of coffee !"
echo " Enjoy & see you later !"
apt-get -f -y install numlockx
apt-get -f -y install xterm
apt-get -f -y install mc
apt-get -f -y install gnome-chess
apt-get -f -y install abiword gnome-gv
apt-get -f -y install xmms xlock
apt-get -f -y install fvwm
apt-get -f -y install xpdf xzgv 
apt-get -f -y install xpdf-reader
apt-get -f -y install rar
apt-get -f -y install tar
apt-get -f -y install zip
apt-get -f -y install scrot
apt-get -f -y install gdesklets
apt-get -f -y install idesk
apt-get -f -y install krusader
apt-get -f -y install 


apt-get -f -y install mozilla-firefox dillo
apt-get -f -y install sylpheed lynx gedit
apt-get -f -y install gnumeric
apt-get -f -y install digikam
apt-get -f -y install audacity kaudiocreator
apt-get -f -y install gparted
apt-get -f -y install qtparted
apt-get -f -y install k3b mplayer-386
apt-get -f -y install k3bsetup
apt-get -f -y install
apt-get -f -y install cdrdao
apt-get -f -y install kadu gftp xpdf
apt-get -f -y install sylpheed
apt-get -f -y install imagemagick
apt-get -f -y install idesk 
apt-get -f -y install gimp
apt-get -f -y install gnome-panel
apt-get -f -y install xloadimage
apt-get -f -y install dvd+rw-tools
apt-get -f -y install growisofs mozilla
apt-get -f -y install mozilla-firefox
apt-get -f -y install openoffice.org
apt-get -f -y install inkscape
apt-get -f -y install openoffice.org-bin
apt-get -f -y install dvd+rw-format
apt-get -f -y install 
apt-get -f -y install imagemagick mozilla-browser
apt-get -f -y install gaim

apt-get -f -y install opera
apt-get -f -y install nfs
apt-get -f -y install mozplugger
apt-get -f -y install kopete

apt-get -f -y install xlockmore
apt-get -f -y install kfmclient
apt-get -f -y install xfce
apt-get -f -y install samba
apt-get -f -y install kaffeine
apt-get -f -y install kadu
apt-get -f -y install xine
apt-get -f -y install

apt-get -f -y install gnome-volume-manager
apt-get -f -y install amule alien
apt-get -f -y install rcconf
apt-get -f -y install vpnc
apt-get -f -y install kcron
apt-get -f -y install cron 
apt-get -f -y install libqt3c102-mt
apt-get -f -y install crond gpdf kpdf gs kghostview
apt-get -f -y install xzgv mplayerplug-in

apt-get -f -y install xmltv
apt-get -f -y install audacity gcc
apt-get -f -y install digikam kmail kaddressbook mtools annoyance-filter khelpcenter kleopatra
apt-get -f -y install nfs nfs-common
apt-get -f -y install libpt-plugins-v4l kmail
apt-get -f -y install kontact kmail
apt-get -f -y install kicker
apt-get -f -y install konsole gxine
apt-get -f -y install kmines 
apt-get -f -y install camorama kbear gftp
apt-get -f -y install klondike
apt-get -f -y install kmahjongg
apt-get -f -y install kate grip
apt-get -f -y install synaptic alsamixergui
apt-get -f -y install synaptics
apt-get -f -y install wine gimp hatari 
apt-get -f -y install audacity
apt-get -f -y install ardour rezound ksim
## this 3  lines for amsn 0.95
apt-get -f -y install tcl8.4 sun-j2re1.5 flashplayer-mozilla
apt-get -f -y install tk8.4
apt-get -f -y install tk8.4-dev
apt-get -f -y install xawtv
apt-get -f -y install gcc
apt-get -f -y install gcc-3.4
apt-get -f -y install gweather
apt-get -f -y install gdesklets
apt-get -f -y install 

# hb
apt-get -f -y install libwxgtk2.4-dev
apt-get -f -y install tcltls planner kweather knewsticker korn wine






apt-get -f -y install gqcam qcam qc-usb-source qc-usb-utils
apt-get -f -y install 

echo " the startup of Linux $(uname -r) "
echo "#!/bin/bash" > "/etc/init.d/patrickrcs70.sh"
echo "chmod 666 /dev/dsp" >> "/etc/init.d/patrickrcs70.sh"
chmod +x /etc/init.d/patrickrcs70.sh

cd /etc/init.d/
ln -s patrickrcs70.sh /etc/rc2.d/S70patrickrcs70.sh
echo "*** LINUX$(uname -r) startup file to be modified !"

cd ~
apt-get -f -y install rox-filer dgen xscreensaver xlockmore gnome-screensaver
apt-get -f -y install sun-j2re1.5
apt-get -f -y --force-yes sun-j2re1.5
apt-get -f -y install azureus
apt-get -f -y install
apt-get -f -y install sun-j2sdk1.5
apt-get -f -y install
apt-get -f -y install
apt-get -f -y install azureus
apt-get -f -y install

echo "***"
echo "*** please go and get opera, skype and gaim, install them rox-filer***"
echo "** crossover is nice prg for windows apps**"
echo "fvwm" > "/home/$1/.Xsession"
echo "/home/$1/.Xsession"
echo "set up the fvwm as default"
apt-get -f -y install 
echo "Please choose gdm "
apt-get -f -y install 
apt-get -y install gdm
apt-get -y install x-window-system-core
apt-get -f -y install xserver-xorg

apt-get -f -y install 
dpkg-reconfigure xserver-xorg
apt-get -f -y install 
apt-get clean
/etc/init.d/gdm restart


cd /usr/lib/mozilla-firefox/plugins
mv libtotem_mozilla.a libtotem_mozilla.la libtotem_mozilla.so libtotem_mozilla.xpt /home
apt-get -f -y install mplayer-386
apt-get -f -y install mozilla-mplayer
apt-get -f -y install mplayer-fonts flashplayer-mozilla
sudo apt-get -f -y install gstreamer0.8-plugins
sudo apt-get -f -y install gstreamer0.8-lame
sudo apt-get -f -y install gstreamer0.8-ffmpeg
sudo apt-get -f -y install w32codecs
sudo apt-get -f -y install libdivx4linux
sudo apt-get -f -y install lame
sudo apt-get -f -y install sox
sudo apt-get -f -y install ffmpeg
sudo apt-get -f -y install mjpegtools
sudo apt-get -f -y install vorbis-tools
apt-get -f -y install acroread 
apt-get -f -y install flashplayer-mozilla
apt-get -f -y install mozilla-acroread
apt-get -f -y install mplayerplug-in
apt-get -f -y install totem-xine
apt-get -f -y install mozplugger
apt-get -f -y install libflash-mozplugin
apt-get -f -y install libstdc++5
apt-get -f -y install w32codecs 
apt-get -f -y install libdvdcss2 
apt-get -f -y install gstreamer-mad xmms vlc wxvlc gvlc vlc-esd
apt-get -f -y install beep-media-player mozilla-mplayer
##apt-get -f -y install totem-xine-firefox-plugin


wget http://www2.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2
mkdir /usr/lib/win32
tar -xjf essential-20050412.tar.bz2
mv essential-20050412/* /usr/lib/win32
  
##never forget this for all the users
echo "zoom=yes" >> ~/.mplayer/config


apt-get -f -y install xorg-driver-fglrx
## gatos also possible

######################## INSTALLATION OF PACKAGE FOLDER ##################"


# now installing realplayer from the file placed in /root/RealPlayer10GOLD.bin
chmod 777 /root/RealPlayer10GOLD.bin
##And if you have mplayer associated to the rpm-files (check with: about: plugins), do also:
cd /usr/lib/mozilla-firefox/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla-firefox/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

cd /usr/lib/mozilla/plugins
mv mplayerplug-in-rm.so mplayerplug-in-rm.so_backup
cd /usr/lib/mozilla/components
mv mplayerplug-in-rm.xpt mplayerplug-in-rm.xpt_backup

## now the cedega
mkdir /root/patrickpackages
cd /root/patrickpackages

gzip -d cedega_4.4.3-1.i386.tgz
# un-tgz
tar -xvf cedega_4.4.3-1.i386.tar
## once done
##/usr created 
##you'll have to place it in /usr

tar -jxvf cdemu-0.7.tar.bz2.tar





########################### end of patrick packages
apt-get -y remove numlockx
apt-get -f -y install

apt-cache pkgnames gnome 



echo "*** dont forget to enable the XDMCP as true ":
echo "please do: gedit /etc/X11/gdm/gdm.conf &"
echo "gdmsetup should be done too !"
echo "Installation Done !!"


```

---

### Post by patrick295767 on 2006-02-15
[QUOTE=liquideath]Run fglrxinfo at the terminal. If it says "Mesa," then you don't have 3D acceleration, and the emulator will be slow. If its "ATI Radeon," then everything's good (driver-wise, at least). There is a ATI linux driver, and its in the repositories.[/QUOTE]
  
It is indeed saying MESA .. 
I did that to install my video:
```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver
```
     And it's saying mesa !!

I will try this:
```
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
```
  
...
  
Tried !
Ok so when I do sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver
the startx  or /etc/init.d/gdm start 
doesnt work anymore. I rebooted and similar.
  
I then dont know how to install the fglrx or maybe my ati all in wonder is not accepted. 
I dont konw how to get this mupen64 working without being laggy.
  
Greetz

Pat

---

### Post by patrick295767 on 2006-04-09
since ...
 
I just had to install the nvidia g force 5200 ...
I installed it, and mupen works fine ! (not laggy at all)
 
 (still prob with gamepad not recognized)
  
Grreetz

---

### Post by Lanky Juggler on 2006-07-24
I got the controller error to go away by going to "Input Settings" from the Options menu.  From there (the picture of the controller) you can set up what buttons should be what fairly simply.

Now here is the part that got me stuck up, and is probably where you are having problems as well.  The three boxes on the screen ("Plugged" "Mem Pak" and "Enable Mouse") all start off as being a darker grey, which apparently means that they are *unchecked*.  Simply click on "Plugged" (and "Mem Pak" if you want) to make them switch on (they'll turn into the background color, the lighter grey).

Also, make sure that the dark box in the top right corner says "Keyboard" (or whatever input device you want to use) instead of "None".
.
Doing that stopped the error for me, and I can play pretty easily now.

---

### Post by benplaut on 2006-07-25
the best gamepad plugin for mupen is Blight...

i've never had any problems with it, everything runs as it should, at proper speed (and a crap card!!) :)

---

### Post by patrick295767 on 2006-08-03
mupen64 is working great.
  
But what about fake64, I installed it. 
When you start the program  : fake64 myrom.rom,
some troubles with the modules ?
Which ones are recommended to be selected /choosen ?
 
 Thanks !

---

### Post by segalion on 2008-09-17
mupen64plus has all than mupen64 and more features:
- initial rumble support
- initial gameshark
- comand line interface
- osd, volume control, etc.

The fast is a video pluging question. You need 3D dri available in driver Xorg grafic card (i.e. you need to be able to run compiz).

---

### Post by tjwoosta on 2008-09-17
> mupen64plus has all than mupen64 and more features:
- initial rumble support
- initial gameshark
- comand line interface
- osd, volume control, etc.

The fast is a video pluging question. You need 3D dri available in driver Xorg grafic card (i.e. you need to be able to run compiz).

i agree

i use mupen64plus with an intel pentium dual @ 1.47 GHZ and 1GB Ram

it runs perfectly with most games  

it also rums **alot** faster if you check the box that says "disable memory expansion" in the options

you would only need to re-enable it if the game you are trying to play requires an expansion pack

---

### Post by sirdilznik on 2008-09-18
> **segalion said:**
> mupen64plus has all than mupen64 and more features:
- initial rumble support
- initial gameshark
- comand line interface
- osd, volume control, etc.

The fast is a video pluging question. You need 3D dri available in driver Xorg grafic card (i.e. you need to be able to run compiz).

I also agree.  Mupen64Plus works like a charm on my Dual Core Opteron 165 and plays most games really well.

---

### Post by dfreer on 2008-09-18
I also also agree...


...That you guys just bumped a 2 year old thread for no reason, come on guys :(

---

