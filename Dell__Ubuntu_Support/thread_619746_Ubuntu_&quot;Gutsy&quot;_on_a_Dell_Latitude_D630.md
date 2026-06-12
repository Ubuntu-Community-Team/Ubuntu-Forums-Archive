---
title: "Ubuntu &quot;Gutsy&quot; on a Dell Latitude D630"
date: 2007-11-21
forum: Dell  Ubuntu Support
---

### Post by marcusdwight on 2007-11-21
hello All,

i'm new to Ubuntu and new to Linux and new to this forum (and i have a corny sense of humor, so be glad i didn't say i was "gnu", ok?)

anyway, after a great start and then a serious crash with Mandriva, i have spent the past 4 days installing Ubuntu 7.10 on my Dell D630. i went with Ubuntu because of the community here (one of my favorite words... i run a nonprofit in San Francisco, we are ALL ABOUT community).  

the community here was a huge help the past few days (i didn't post a single message, i found everything i needed already here). i have seen people out there on the Net struggling to get Linux onto one of these D630's... all it takes is a little patience and to not be afraid of the command line  ;-)

so if anyone is looking for help to get your D630 working (like the sound, CompizFusion, wifi) drop a note here, i'll guide you to the stuff i found on the forums to get you running right.

and thanks to the Ubuntu Community... you guys are ok in my book!

marc

---

### Post by samer58 on 2007-11-22
I am looking for D631 drivers for ubuntu, can't find any!

---

### Post by marcusdwight on 2007-11-22
> **samer58 said:**
> I am looking for D631 drivers for ubuntu, can't find any!

hi,  most of everything i needed to run my D630 is already in Ubuntu, you just need to tweak a few things... only once did i need to put the installation CD back in my machine to add a file to get things working... but the D630 is Intel... the D631 is AMD, isn't it?  i don't know if your particular AMD processor is supported in Ubuntu, but they do have AMD support listed in the Ubuntu Wiki, my guess is that some of the folks around here could get you up and running. 

i am a linux/Ubuntu newbie, but i found the "fixes" very easy to perform, and i can tell you that the amount of tweaking is minimal compared to how much this laptop ROCKS with Ubuntu working properly on it. i can honestly say that even with using the terminal window to type in things (to add & change some files), the installation and tweaking are easier and take less time than it did whenever i had to reinstall XP on this laptop.

if you can't find any forum posts about your laptop, start a new post with your model number in the title, and somebody is bound to have already loaded a D631 with Ubuntu... if i can help with anything else though, let me know.

marc

---

### Post by Schuby on 2007-11-22
I got everything working dandy on my D600.

Let me know if anyone needs help!  I'm a newb compared to Ubuntu, but I did get wireless working like a charm!

---

### Post by qwill on 2007-11-22
Hi there;
I installed gutsy also on my D630; and am still struggling for a few things.
WIFI works like a charm; I managed to get sound playing; but here's are the few glitches I'm struggling with : 

* Video : (but that's maybe not specific to D630). When used undocked; it works like a charm. When Docked; I use 2 external screens (DELL 2007FP) 1 via the VGA outlet; the second via the DVI output. When launchong ubuntu; the text displays in the DVI external monitor; but then X11 starts on the internal (laptop) screen !!! I don't know if there is any possibility to have this dual config working autmotacically...

* Sound recording : not working. Either ESD, OSS, ALSA ... I just get a "broken pipe" error mesaage...

* Suspend / Hibernate : While suspend works so so ( it gives a lot of error messages onscreen about usb) hibernate feature is not working.  One of the cause of the problem I suspect is due to the fact that I have 2 gig RAM but only 1 gig Swap partition. (But its weird to freeze more than 2 gig swap space; while ubuntu use the swap space very seldomly...


If you have any pointer for these; I would really appreciate.

Qwil

l:KS

---

### Post by swazzler on 2007-11-30
Hey Guys,

I'm seriously looking into picking up a D630, but would like some tips on the configuration.
I'm considering the following:
Intel® Core 2 Duo T7100
14.1" Wide Screen WXGA
DDR2 667MHz de 1GB (2X512MB)
Intel Graphics Media Accelerator (GMA) X3100

Any comments/complaints/suggestions?

Thanks in advance :)

---

### Post by sciurus on 2007-12-02
> **qwill said:**
> 

* Video : (but that's maybe not specific to D630). When used undocked; it works like a charm. When Docked; I use 2 external screens (DELL 2007FP) 1 via the VGA outlet; the second via the DVI output. When launchong ubuntu; the text displays in the DVI external monitor; but then X11 starts on the internal (laptop) screen !!! I don't know if there is any possibility to have this dual config working autmotacically...

If you have intel video, try [this]("http://ubuntuforums.org/showthread.php?t=617934").

---

### Post by manzurul on 2007-12-03
Hello,

I have used ubuntu 7.04 previously on my DELL Latitude D630. At that time the sound was working fine. And also I was able to install nvidia driver. But now I have installed a fresh copy of 7.10 and I am facing the following 2 problems.

1. Sound problem:

My sound is not working. I have checked with lspci command and saw the audio driver listed. But still the sound is showing muted. In ubuntu 7.04 it was fine but in 7.10 its not working.

the sound carde : sigmatel HD audio

2. Graphics:

Graphic lokks fine. But I cant install the nvidia. Previously in 7.04 I installed it but now in new 7.10 I have applied the same process with no result . 

Thanks.

Manzurul

---

### Post by manzurul on 2007-12-03
Please check the followings. It might help you to find out the problem of my sound card. :::

manzur@manzuzr-laptop:~$ cat /proc/asound/modules
manzur@manzuzr-laptop:~$ cat /proc/asound/modules
manzur@manzuzr-laptop:~$ clear
manzur@manzuzr-laptop:~$ cat /proc/asound/modules
manzur@manzuzr-laptop:~$ cat /etc/modprobe.d/alsa-base 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by marcusdwight on 2007-12-04
> **swazzler said:**
> Hey Guys,

I'm seriously looking into picking up a D630, but would like some tips on the configuration.
I'm considering the following:
Intel® Core 2 Duo T7100
14.1" Wide Screen WXGA
DDR2 667MHz de 1GB (2X512MB)
Intel Graphics Media Accelerator (GMA) X3100

Any comments/complaints/suggestions?

Thanks in advance :)

hey swazzler,

i love the D630... i could have gotten a cheaper Dell laptop and had Ubuntu pre-installed, but i wanted the extra power and business look... so here i am.

if you get the D630, get it with all Intel parts. _including the wif_i... get the basic intel wifi card... it's a "non-free" driver, but it's directly supported in Ubuntu, it will load during installation and will be listed under "System => Administration => Restricted Drivers Manager". as for the rest of the laptop, the hardware you listed will work just fine in Ubuntu... with a couple of tweaks you will be up and running and the CompizFusion graphics ROCK!

if you have questions with the tweaking, let me know...

marc

---

### Post by gsalem on 2007-12-04
I have a good working 7.1 on d630. For the sound look at 
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")
as for the video using 2 screens, try using virtual devices in you /etc/X11/xorg.conf,
like this
Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Virtual 2720 1924
        EndSubSection
        SubSection "Display"
                Depth           4
                Virtual 2720 1924
        EndSubSection
        SubSection "Display"
                Depth           8
                Virtual 2720 1924
        EndSubSection
        SubSection "Display"
                Depth           15
                Virtual 2720 1924
        EndSubSection
        SubSection "Display"
                Depth           16
                Virtual 2720 1924
        EndSubSection
        SubSection "Display"
                Depth           24
                Virtual 2720 1924
        EndSubSection
EndSection

and then use xrandr to manage your screen (man xrandr for help)

The only pblm I still have is the hibernate/suspend. It's not working.
rgds

---

### Post by marcusdwight on 2007-12-04
> **manzurul said:**
> Hello,

I have used ubuntu 7.04 previously on my DELL Latitude D630. At that time the sound was working fine. And also I was able to install nvidia driver. But now I have installed a fresh copy of 7.10 and I am facing the following 2 problems.

1. Sound problem:

My sound is not working. I have checked with lspci command and saw the audio driver listed. But still the sound is showing muted. In ubuntu 7.04 it was fine but in 7.10 its not working.

the sound carde : sigmatel HD audio

2. Graphics:

Graphic lokks fine. But I cant install the nvidia. Previously in 7.04 I installed it but now in new 7.10 I have applied the same process with no result . 

Thanks.

Manzurul

hey Manzurul,

i don't know about the "docked vs undocked", i just have the laptop itself (although i'm thinking of getting a docking station, so i may have to pick your brain later)... however, i had the same sound problem. the hardware was recognized, but no sound... so i went searching in the Ubuntu forums and found a fix. this is how i got my sound working on my D630...

open your terminal window.  at the prompt enter the following:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Note:  at one point in this process you might be prompted to insert your Gutsy installation CD into your laptop.. just pop it in and hit enter, when it's done with what it needs, you can then continue with the process... i apologize, but when i wrote this fix in my "Linux command line / shell notebook" (i'm trying to teach myself as much linux as i can) i forgot to write down at what point i was prompted for the CD. but don't worry, it tells you when to give it the CD... Unbuntu is very smart and friendly...

i hope this works. let us know what happens...

marc

---

### Post by sigma_solutions on 2007-12-05
this question is especially for schuby- how did you get the tv out working on the d600? i assume you have the ati mobility radeon 9000. i have tried to get it to work numerous times with no avail. help from anyone would be greatly appreciated! thanks

---

### Post by marcusdwight on 2007-12-05
Hey all,

an update for all you D630 users and those with similar Latitude laptops...

i just got my new Sierra Wireless Aircard 595U up and running on my Sprint account. it rocks right along. the software that comes with the Aircard is only for windows, but the drivers for the USB Aircard modems are already in Ubuntu 7.10.  it just takes a little manual set up... 

so if anyone is looking to install one of these, let me know and i'll tell you how i got it done...  ;-)

marc

---

### Post by auspea on 2007-12-11
Marc

You make it sound easy, but I cant find any info on ettin my wifi to work on a dell d630 and ubuntu 7.10. 

Any assistance would me great.

Aus

---

### Post by bluedragon436 on 2007-12-11
I was able to overall get everything to work with Ubuntu 7.10 on my D610, with only a few tweaks here and there.  I have yet to actually connect and use a wireless connection, I can connect to them but when I try to use it the signal fluctuates and I am not able to actually use it, but yet I am right next to the router, so I know it is a lack of signal.... but other than that for the most part I haven't had an issue....

---

### Post by qwill on 2007-12-11
An update on using a D630 with 2 external screen (when docked).

I have the nvidia nv135m graphic card.

I finally got it after trying many configurations trial. They can't be always reproduced; I finally cath that the order in which you activate / deactivate screens is important.

I use the nvidia driver.
I got my extyernal screens running with the help of the nvidia-settings application.

I figured out that I had to activate the internal screen with one external screen first.

Then deactivate the internal lcd and activate the 2nd external screen.

When I got it running; I made the nvidia-settings app to weite the xorg.conf. (AND I KEEP IT PRECIOUSLY !!!)

You will find it in annex - in case it mighthelp.

Sounds now work wih the alsa driver tricks found in previous post.

Standby/resume doesn't sork too well, as I have a dual boot XP + Ubuntu.

WIFI works like a charm ( worked out of the box).

My next job is now to be able to virtualize the existing WinXP partition with virtualbox. There are plenty of posts about doing it with WMWare but only few with virtualbox....

Qwill

---

### Post by marcusdwight on 2007-12-12
> **auspea said:**
> Marc

You make it sound easy, but I cant find any info on ettin my wifi to work on a dell d630 and ubuntu 7.10. 

Any assistance would me great.

Aus

hey Aus,

what is your wifi hardware?  the D630 comes with 5 options for wifi:  either the good ol' Intel wifi cards or Dell's fancier wifi cards.  i have the Intel 3945 mini-card recommended for Centrino machines, and it "just worked"...  let me know  what you're running and then i can direct you in getting started...  if i don't know the answer i can help you find it  ;-)

marc

---

### Post by marcusdwight on 2007-12-12
> **bluedragon436 said:**
> I was able to overall get everything to work with Ubuntu 7.10 on my D610, with only a few tweaks here and there.  I have yet to actually connect and use a wireless connection, I can connect to them but when I try to use it the signal fluctuates and I am not able to actually use it, but yet I am right next to the router, so I know it is a lack of signal.... but other than that for the most part I haven't had an issue....

bluedragon,

i started with simply using Gnome's network manager found under System=>Administration=>Network... it works great when you save your wifi network's profile, but i had to connect manually each time i turned on my laptop... so i now use "Wicd" to manage my wireless connections, and it not only connects to my preferred networks automatically, it NEVER lets go of them once it's connected... 

here's the website with install instructions:  _[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)_     (there's a download link as well)

good luck, let me know how it goes...

marc

---

### Post by auspea on 2007-12-12
Marc, i have the Intel 3945 mini-card recommended for Centrino machines too. I dont seem to be pulling an ip address from DHCP.

thanks

Aus

---

### Post by lily22 on 2007-12-13
Hi, I'm new to linux and I just installed ubuntu 7.10 on my Dell Latitude D630, I've got 3 big problems now, 

Internal Modem : I just can't get ubuntu to recognize my modem, can someone help me? cause I really need the modem to work :confused:

Sound : I tried this : 

sudo aptitude install linux-backports-modules
sudo gedit /etc/modprobe.d/alsa-base

and add the following line to alsa-base file (within the editor):

options snd-hda-intel model=dell-m42

I've got the terminal "beep" ing now, but none of the music players "play" music! :D

Bluetooth device : my bluetooth device doesn't work either

thanks a lot,

---

### Post by auspea on 2007-12-13
I solved the Intel 3945abg mini not working.

Tip from Linux Reality podcast to de-enble and then re-enble all the network contections in Network Manager worked like a charm.

---

### Post by adrian.oneclick on 2007-12-15
just finished installing gutsy on my d630 it worked great out of the box, just had to fixed sound.

just wanna say thnx to all, great forum support, helped a lot. :)


Cheers*

---

### Post by marcusdwight on 2007-12-16
> **auspea said:**
> Marc, i have the Intel 3945 mini-card recommended for Centrino machines too. I dont seem to be pulling an ip address from DHCP.

thanks

Aus

Aus,

having Wicd currently installed on my D630, the normal Gnome network manager is "disabled" (by Wicd, it does it automatically)... so i can't review it for you without un-installing everything...

However, i know that Gnome's wifi manager is temperamental with the D630, so i HIGHLY recommend using WICD, (here's the hompage)  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)   -   which should make setting up your wireless connection much easier, and i can help you with any problems you have in  Wicd... here's how you get it set up:

First, you have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) gutsy extras 

where gutsy is your version of Ubuntu (Dapper, Edgy, Feisty, Gutsy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you.  This will also keep you automatically up to date with the latest and greatest version of Wicd (also, i don't know if the installation then requires a reboot, but it never hurts) 

In GNOME, to get the tray icon to automatically appear at boot,  go to Wicd in the Applications menu (under Internet), right-click it, and select "add this launcher to panel".

Once you have it installed, you will find all the "usual" preferences and settings that you find in other wifi managers.  you can select your network, fill in the neccessary information and click the box "automatically connect to this  network" so that when you turn on your D630 it's ready to go...

try this and i think you will solve your wifi worries... let me know it you run into problems, but i think you will be ok... i found Wicd to work MUCH better than the basic Gnome network manager (at least for this laptop, i'm not knocking Gnome, 'cause i love it!)

i have found Ubuntu 7.10 to work very well with my wifi, so if Wicd doesn't work for you, you might need to look at your wireless router.  i have found some routers to be easier to work with than others... the easiest i have ever used was Netgear, the most difficult was my current one, an inexpensive Belkin.

marc

---

### Post by marcusdwight on 2007-12-16
> **lily22 said:**
> Hi, I'm new to linux and I just installed ubuntu 7.10 on my Dell Latitude D630, I've got 3 big problems now, 

Internal Modem : I just can't get ubuntu to recognize my modem, can someone help me? cause I really need the modem to work :confused:

Sound : I tried this : 

sudo aptitude install linux-backports-modules
sudo gedit /etc/modprobe.d/alsa-base

,

Lily,

i have only tried to get the modem working once (i prefer a broadband connection, so i got a USB modem from Sprint for those times i can't get a free wifi connection).  that one attempt to get the internal modem working was a failure... i admit that i gave up pretty quick.  but the problem was getting it working, not that it was not recognized... when you open the Gnome network manager, you should see the modem listed after the wireless and wired connections.

if i come across anything that will help i will let  you know...

as for the **sound**, here's what you need to do:

open your terminal window. at the prompt enter the following:

[COLOR="Blue"]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa[/COLOR]

(note: at one point in this process you might be prompted to insert your Gutsy installation CD into your laptop.. just pop it in and hit enter)

that will get your sound working.  let me know if there's something else... i'm not an expert, but i will try to help...  :-)

marc

---

### Post by Kynnzak on 2008-02-24
> **marcusdwight said:**
> Lily,

i have only tried to get the modem working once (i prefer a broadband connection, so i got a USB modem from Sprint for those times i can't get a free wifi connection).  that one attempt to get the internal modem working was a failure... i admit that i gave up pretty quick.  but the problem was getting it working, not that it was not recognized... when you open the Gnome network manager, you should see the modem listed after the wireless and wired connections.

if i come across anything that will help i will let  you know...

as for the **sound**, here's what you need to do:

open your terminal window. at the prompt enter the following:

[COLOR="Blue"]sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa[/COLOR]

(note: at one point in this process you might be prompted to insert your Gutsy installation CD into your laptop.. just pop it in and hit enter)

that will get your sound working.  let me know if there's something else... i'm not an expert, but i will try to help...  :-)

marc

I am a novice to Linux, but I can follow instructions fairly well.  I have installed Ubuntu 7.10 multiple times on my D630, and NONE of the recommended actions for making the sound work have accomplished anything.

Every time I follow any of the recommended actions; I get prompted that linux-backports-modules nor module-assistant nor any other required files can be found.  I am attempting to get the sound working with the CD in the drive.

Help?!?!?

Thanks in advance,

Kevin

---

### Post by syn4k on 2008-02-25
I have Gutsy on my DELL Latitude D630. lspci output: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

My sound is not working and I have tried all of the following:

sudo aptitude install linux-backports-modules-generic
sudo apt-get install linux-backports-modules

For Dell Latitude D630/D830 and Dell Precision M6300, also do the following (if you don't, the volume will increase with every sound played):

       sudo gedit /etc/modprobe.d/alsa-base

      In the editor, add the following line at the end of the file:

       options snd-hda-intel model=dell-m42

      Save the file and reboot to get sound working correctly.

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c [http://launchpadlibrarian.net/9021234/patch_analog.c](http://launchpadlibrarian.net/9021234/patch_analog.c)
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

None of this works..HELP?

---

### Post by marcusdwight on 2008-02-26
> **griffin.ray@gmail.com said:**
> I have Gutsy on my DELL Latitude D630. lspci output: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

My sound is not working and I have tried all of the following:

sudo aptitude install linux-backports-modules-generic
sudo apt-get install linux-backports-modules

For Dell Latitude D630/D830 and Dell Precision M6300, also do the following (if you don't, the volume will increase with every sound played):

       sudo gedit /etc/modprobe.d/alsa-base

      In the editor, add the following line at the end of the file:

       options snd-hda-intel model=dell-m42

      Save the file and reboot to get sound working correctly.

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c [http://launchpadlibrarian.net/9021234/patch_analog.c](http://launchpadlibrarian.net/9021234/patch_analog.c)
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

None of this works..HELP?

I have spent some time getting to know Ubuntu, but i really am stumped on some of the problems people have been having with getting the sound to work on their Dell D630's...

when i used the solution that i posted here, it had worked for me, so i never had to try any other work-around. if you have tried several "fixes" with no luck, you might want to email Ubuntu support directly and see what they suggest... sorry i couldn't be of more help.

marc

---

### Post by syn4k on 2008-02-26
Got an e-mail addy?

---

### Post by syn4k on 2008-02-27
Why doesn't the lack of response surprise me? :lolflag:

---

### Post by SergeantPepper on 2008-02-27
I just got a new Latitude D630 and just finished installing 7.10, but my wifi doesn't work either. Network Manager doesn't see it and I installed  wicd but it didn't help find my wifi card nor get connected.

I'm not sure which type of wifi card I have installed. How would I find that out?

Thanks

---

### Post by cacycleworks on 2008-02-27
> **marcusdwight said:**
> 
i have found Ubuntu 7.10 to work very well with my wifi, so if Wicd doesn't work for you, you might need to look at your wireless router.  i have found some routers to be easier to work with than others... the easiest i have ever used was Netgear, the most difficult was my current one, an inexpensive Belkin.

marc

Another data point:
My D630 will not work with a cheap belkin (bought at home depot), but has with any other brand I've tried. NetGear, Linksys, Buffalo are 3 I remember.

:) Chris

---

### Post by syn4k on 2008-02-28
Well, I have started a thread over at [https://answers.launchpad.net](https://answers.launchpad.net). We will see what comes of it.

---

### Post by benbelly on 2008-02-28
I got my Dell D630 last night.  Installed Ubuntu 7.10 64bit immediately.  The sound didn't work, and the wifi didn't work.  I followed the directions at the wiki ([https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)) method G, and now my sound works, but I'm at a loss for the wifi.

  I installed wicd, but it lists "none" as my wireless network connection in preferences.  Which is not helpful.  According to the order page, my Latitude has a "Dell Wireless 1395 WLAN Mini Card".

  Can anyone give me any pointers?  I'm comfortable with command line stuff (came to Ubuntu from Gentoo), but this is my first laptop and wireless experience.

Thanks,
-Ben

---

### Post by Mordac85 on 2008-02-28
I've stuck w/ndiswrapper since it's the most reliable method for wifi on the Latitudes.

---

### Post by cacycleworks on 2008-02-29
> **griffin.ray@gmail.com said:**
> Well, I have started a thread over at [https://answers.launchpad.net](https://answers.launchpad.net). We will see what comes of it.

Well, my fear has been confirmed. This morning, I confirmed the problem is not hardware. I got on the net and moved the cable back to the original port on the router.

Another day like that and I'm going to a different distribution on this notebook. I must not have windows-like behavior. Looking around the forums, Gutsy seems to have introduced a LOT of instability. All the new laptops are nearly identical ... and the HPs with our same intel and ICH8 chipset are having huge problems.

- Chris

---

### Post by cacycleworks on 2008-02-29
> **benbelly said:**
> I got my Dell D630 last night.  Installed Ubuntu 7.10 64bit immediately.  The sound didn't work, and the wifi didn't work.  I followed the directions at the wiki ([https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)) method G, and now my sound works, but I'm at a loss for the wifi.

  I installed wicd, but it lists "none" as my wireless network connection in preferences.  Which is not helpful.  According to the order page, my Latitude has a "Dell Wireless 1395 WLAN Mini Card".

  Can anyone give me any pointers?  I'm comfortable with command line stuff (came to Ubuntu from Gentoo), but this is my first laptop and wireless experience.

Thanks,
-Ben

Hi Ben,

Please check out my write up from installing on the D630:
[http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

I went around and around with the D630! I couldn't ever get sound AND wireless working simultaneously. Ultimately, I never did bother with sound. 

My D630 was working really well with fiesty and then the gutsy install ruined a few things. I haven't gotten flash working again and don't care too much. This laptop is all about my productivity. If I need to screw around, I've got other computers for that.

I'm quite optimized for KDE, which bums me out a touch. I have xubuntu on my older notebook (as well as a P4 at work) and absolutely love it. I briefly tried vector linux on same older laptop and was flat stunned by its speed. Off-to-desktop in about 30 seconds! I stay with ubuntu because it has been reliable and I have learned a lot tweaking it and can fix problems quickly.

I'm working on a backup over sshfs in to a work server ... if this Kubuntu Gutsy on my D630 acts up again, I'll try out vector or archlinux or something. And if that isn't seamless, I'll load up Fiesty again. I can get it from zero to 60 in about an hour. :)

Chris

---

### Post by Mordac85 on 2008-02-29
Ummm.  It's interesting that I've installed Kubuntu Gutsy on a D430, D630, M65 and M4300 without much trouble.  Sound, video, SD cards, smartcard readers all working fine (sorry no BT).  Wireless w/ndiswrapper is more involved, but a piece of cake (even tho the cake is not real).  But I have the Broadcom chip not the Intel.

Once I get my company certs loaded, and I work out any problems authenticating in Firefox or using S/MIME, I should be good to go to finish my conversion to Linux.  Maybe that run in w/xserver-core gave you more problems than you think?

---

### Post by cacycleworks on 2008-02-29
Hi Mordac,

32 bit or 64 bit? Mine's the 64 bit. I knew I was going the path lesser travelled, but I wanted to make use of all my resources.

Chris

> **Mordac85 said:**
> Ummm.  It's interesting that I've installed Kubuntu Gutsy on a D430, D630, M65 and M4300 without much trouble.  Sound, video, SD cards, smartcard readers all working fine (sorry no BT).  Wireless w/ndiswrapper is more involved, but a piece of cake (even tho the cake is not real).  But I have the Broadcom chip not the Intel.

---

### Post by Liet_Kynes on 2008-02-29
Has any of you managed to get the 3G/HSDPA card working in gutsy? I had it working in feisty but in gutsy no go.

---

### Post by Mordac85 on 2008-02-29
32, especially with the newer hardware.  I don't mind sacrificing a little performance for stability.

As for the 3G/HSDPA, I barely use my wireless card, but live through my VPN connection.  I have never worked with one, Windows or Linux, sorry.

---

### Post by Liet_Kynes on 2008-02-29
No problem Mordac, I just think it's weird that the card was picked up in feisty but now it doesn't seem to be in gutsy.

Other than that my ubuntu experiences has been pretty trouble free on my laptop. wireless and sound just worked :) 

I'm using the 64bit version of gutsy BTW

EDIT: I managed to get it up and running :)

---

### Post by cacycleworks on 2008-02-29
> **Liet_Kynes said:**
> No problem Mordac, I just think it's weird that the card was picked up in feisty but now it doesn't seem to be in gutsy.

Other than that my ubuntu experiences has been pretty trouble free on my laptop. wireless and sound just worked :) 

I'm using the 64bit version of gutsy BTW

EDIT: I managed to get it up and running :)

Wow! Dumb question from me: did you type ANYthing special during install? Like from CD until login to desktop ... nothing special? And then you could click on network manager and connect to a wireless network? I am curious ... I would have no problems reinstalling the OS using ubuntu cd and make the last step apt-get install kubuntu desktop

Hmmmm, and you are using ubuntu and not kubuntu? 



Overall, from what I've read all over ubuntuforums.org, Gutsy is considered unreliable and everyone is going back to fiesty.

---

### Post by Liet_Kynes on 2008-02-29
I didn't have to type in any special commands at all. Just the standard CD. Maybe you _should_ try the Ubuntu one if Kubuntu is giving you problems.

---

### Post by syn4k on 2008-03-01
Yep, I can confirm that method G as listed previously does the trick. Here's the thing though...

If you have a Dell Latitude D630 like me and you are using Ubuntu and can't get your sound card to work, do not try anything else until you have tried this because, if you do, as I have found out, you will not be able to fix it (at least, that I'm aware of).

In the terminal:
sudo aptitude install linux-backports-modules
sudo gedit /etc/modprobe.d/alsa-base

Append this to the end of the file, save and reboot:
options snd-hda-intel model=dell-m42

FINALLY!!

---

### Post by benbelly on 2008-03-01
> **Mordac85 said:**
> I've stuck w/ndiswrapper since it's the most reliable method for wifi on the Latitudes.

That did the trick.  Thanks!!

-Ben

---

### Post by iNotaRobot on 2008-03-01
Hi Hi (Norwegian hello) or G'day (Australian hello)

Well I have a Dell 630 that has internal HD with Windows XP sp2.

Now about a week ago I purchased a Western Digital 160Gb usb Passport hard drive. Neat little black drive. Computer shop burnt me a CD copy of Ubuntu 7.11. Simple easy purchase of drive and operating system. 

Now for the fun. I wanted to install Ubuntu on this USB drive and have it boot and run WITHOUT the internal HD present or at least enabled.

Without going into details why at this moment, I removed internal HD and plugged in my new USB drive. Turned on computer and put the CD into drive. As D630 was starting up, I hit F12 and choose CD boot.

At that point Ubuntu Install came up, I choose nothing special as I recall. I choose Gnome as my desktop. The install went WITHOUT a problem and upon completion, I had a fully working system including HiFi network. 

All done on front counter at computer shop in short time.

Back to hotel and try in my room.. Works perfect except for sound.

Today I ran the G mod as described here exactly. Sound now works be it a little low in volume out of internal speaker.

For those fokes that are interested I got a second one of these Western Digital USB drives and tried to install XP on it. Again without my internal HD installed.  Did i get that install to work NO WAY.. damn microscoft rubbish. Got the blue boot screen. Tried for 3 days with NO success.Seems windows XP does not like to book of a plug and play device.

Anyways I am on the D630 using WiHf  and sound with no problems.

was magically easy.

Hope this helps others.

regards 
David 

an Australian living in Norway


ps sometimes the D630 wont boot Ubuntu 7.11 first time after a previous run with  XP on the internal HD. I simply go round boot sequence ctl/alt/del and it then boots Ubuntu fine

---

### Post by lgmdaniel on 2008-03-04
> **marcusdwight said:**
> 

open your terminal window. at the prompt enter the following:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

(note: at one point in this process you might be prompted to insert your Gutsy installation CD into your laptop.. just pop it in and hit enter)

that will get your sound working.  let me know if there's something else... i'm not an expert, but i will try to help...  :-)

marc

Well I'm going to say cheers, I did this, rebooted my laptop and hey presto sound.

Also it seems my wife worked first time with the latest Ubuntu 7.10 "Gutsy Gibbon" - Release i386.

---

### Post by shakyamuni on 2008-03-31
> **lgmdaniel said:**
> Well I'm going to say cheers, I did this, rebooted my laptop and hey presto sound.

Also it seems my wife worked first time with the latest Ubuntu 7.10 "Gutsy Gibbon" - Release i386.

Hi guys...

I tried the method described above, but when I did an upgrade and rebooted my dell D630 now I have sound through the internal speaker even though I have a headset pluged in. Does anyone knows how to fix that?

thanks a lot in advance.

regards,
Carlos.

---

