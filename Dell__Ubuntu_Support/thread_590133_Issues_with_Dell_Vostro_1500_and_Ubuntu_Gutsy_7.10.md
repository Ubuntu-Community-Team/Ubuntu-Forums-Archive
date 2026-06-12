---
title: "Issues with Dell Vostro 1500 and Ubuntu Gutsy 7.10 - Help!"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by mushroomcloudwarrior on 2007-10-24
I have tried to find potential fixes from previous fixes on the Ubuntu forums, and i'm posting this thread after being unable to find a solution (and being a beginner to Linux)

I bought a Dell vostro about a week ago, and had someone install the new Gutsy 7.10 on it..the installation happened without any glitches,.some things like sound weren't working but i did dix it with the information on various posts (i love the people on here for it, wouldn't know what to do without it) 

The following are some of the problems that i'm facing right now, and maybe more people out there are right now (considering the number of people buying it) i'll try and be as precise as i can, forgive me for any mistakes (english is not my first language)

Note: I'm writing all the important/urgent problems in bold
 
1. Touch pad:
The touch pad started working fine right after i installed Kubuntu. However, i realised that i can't use the scrolling on the touch pad at all. Is there a fix for this? 

2. Keyboard shortcuts;
I'm too used to pressing 'backspace' to go back while viewing my files and using an internet browser. Could you tell me how i could get 'backspace' to do what it does on windoes.

3. Jerky scrolling; **[SOLVED]**
I've read about jerky scrolling on Firefox, but i'm facing it even while using it with dolphin, Konquerer, Firefox (basically, anything that needs scrolling) and it's annoying when you have 2 gig ram

Now i'm not sure why it's doing this, i have installed the drivers, but i can't be too sure since i can't tell it a method worked or not (i didn't notice any changes after i installed the drivers - i have a 128 mb GE force Nvidia 8400 GS) I looking at the performance monitor and there's nothing eating up memory (it doesn't go above 15% tops)

4. DVD rom;
The DVD rom is not functioning, i can put a DVD in there and it doesn't detect it at all. Advice?

[B]5. Sound card problem;
As i said, there is sound..although when i try to connect a headphone jack, the speakers still continue to give out sound. There is sound on the headphones, i just want the speakers to stop when the headphones are connected.Also, there's the media direct buttons after the mouse pad which are supposed to control sound/mute..i can control sound, but it doesn't mute even when it says 'mute on' [/B]

Reading NTFS file partitions:
It's reading my windows C: but it's not opening an NTFS partition on a removable drive. I tried the fix mentioned on the forums but it didn't quite work.

Hybernate/Suspend
I don't think there is a fix for this one, but if there is one, i would love to use these functions.

Apart from this, is there any way, i can control the brightness on the monitor when it's on battery (in order to save battery life)**[SOLVED]**

Can i connect it to a projector for presentations and things like that? 

Please remember that i'm a newb who wants to learn, so i would appreciate it if you kind of explained the commands etc.

Thanks thousand times over..

---

### Post by mushroomcloudwarrior on 2007-10-26
Bump!

nobody has anything to say about it?

---

### Post by professor fate on 2007-10-26
I feel your pain.  I've been working on sound for a Vostro 1400 for two days, and I get nothing.

---

### Post by mushroomcloudwarrior on 2007-10-26
> **professor fate said:**
> I feel your pain.  I've been working on sound for a Vostro 1400 for two days, and I get nothing.

Ah, i'm glad i atleast have some sound..Dell should maybe start assembling dual boot computers (on demand of course!) and i bet they will increase their customer base by atleast ten thousand more laptops a year (which is quite miniscule for any company to care) 

I'm not able to use my laptop in public places because of the issue with the speakers even when i plug in the headphones..apart from that, the jerking scrolling is more motivation to boot up windowz ex pi :(

If anyone reading this has any clue about installing drivers/touch pad/speakers then please post here or link me!

---

### Post by saru411 on 2007-10-26
i have a vostro 1500 running feisty fawn. i followed the installation guides here and had none of the issues you have here.

---

### Post by mushroomcloudwarrior on 2007-10-26
Well,

I didn't install it, but there seems to be big differences in the how to pages i saw. Could you link me to what you referred to? 

I also can't figure out which nvidia driver to download (from the Nvidia home page), it would be great if you could help me there..i have a 128 MB Nvidia GEforce 8400M GS and a Core2Duo T7100 1.80 GHz 800.2M

(and i'm using Gutsy, does that make any difference?)

---

### Post by charles_elwood on 2007-10-31
OK, being the guilty party that helped with the install here's some suggestions

And for the record this was a Kubuntu install, so answers will be kubuntu specifuc

> **mushroomcloudwarrior said:**
> 
1. Touch pad:
The touch pad started working fine right after i installed Kubuntu. However, i realised that i can't use the scrolling on the touch pad at all. Is there a fix for this? 
if it's a synaptics touchpad, install ksynaptics (nothing to do with synaptic) and you'll have a config option in your *System Settings*

> 
2. Keyboard shortcuts;
I'm too used to pressing 'backspace' to go back while viewing my files and using an internet browser. Could you tell me how i could get 'backspace' to do what it does on windoes.

IN which browser Firefox? Konqueror?, and what browser are you trying to emulate IE? MSN Explorer? Firefox?
> 
[B]3. Jerky scrolling;
I've read about jerky scrolling on Firefox, but i'm facing it even while using it with dolphin, Konquerer, Firefox (basically, anything that needs scrolling) and it's annoying when you have 2 gig ram

Now i'm not sure why it's doing this, i have installed the drivers, but i can't be too sure since i can't tell it a method worked or not (i didn't notice any changes after i installed the drivers - i have a 128 mb GE force Nvidia 8400 GS) I looking at the performance monitor and there's nothing eating up memory (it doesn't go above 15% tops)[/B]


can you run ```
restricted-manager-kde
``` from a konsole and verify you are using the restricted drivers? Try *not* using the restricted driver and see if that makes a difference?

Also see what the your CPU clock speed is doing (KPowersave) I've noticed a lot of weirdness when clock speeds change, but i only get this when running jackd. Set CPU Frequency Policy to Performance and see if it makes any difference

> 
4. DVD rom;
The DVD rom is not functioning, i can put a DVD in there and it doesn't detect it at all. Advice?

OK, look in /etc/fstab, can you find an entry relating to it? can you mount the disk by hand? 'Drive not working' and 'kde can't detect when i insert a disk' are 2 very different problems, if you can isolate which one is which we're at least getitng somewhere

[B]5. Sound card problem;
As i said, there is sound..although when i try to connect a headphone jack, the speakers still continue to give out sound. There is sound on the headphones, i just want the speakers to stop when the headphones are connected.Also, there's the media direct buttons after the mouse pad which are supposed to control sound/mute..i can control sound, but it doesn't mute even when it says 'mute on' [/B]

> 
Reading NTFS file partitions:
It's reading my windows C: but it's not opening an NTFS partition on a removable drive. I tried the fix mentioned on the forums but it didn't quite work.

Which fix? post the instructions you've followed and I don't have to make a blood sacrifice for a mind-reading ritual :-p 

Off the top of my head it's because it's not listed in /etc/fstab

> 
Hybernate/Suspend
I don't think there is a fix for this one, but if there is one, i would love to use these functions.

Here be dragons!

> 
Apart from this, is there any way, i can control the brightness on the monitor when it's on battery (in order to save battery life)

KPowersave any help here? I can't rember if it's installed by default, i know it *does stuff* but it's been a long time since i had a laptop to fiddle with

> 
Can i connect it to a projector for presentations and things like that? 

Should 'just work' You may need to use some obsure hardware specific shortcut (Function + F(something) on most) and maybe fiddle with you screen resolution. We can test this using a seporate monitor, this may be a bring it round to mine and it'll just work on whatever we try and test it with because it's scare of me :-p

> 
Please remember that i'm a newb who wants to learn

You may find you get better help if you post 1 topic per problem. It also helps people with similar problems find the answers.

---

### Post by saru411 on 2007-10-31
[http://ubuntuforums.org/showthread.php?t=521753&highlight=vostro](http://ubuntuforums.org/showthread.php?t=521753&highlight=vostro)

i used this link to install feisty fawn back in august. please notice i had an issue that i solved further down on that page.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

to install the nvidia drivers it is easiest to use envy. this is an automated script that will install the correct driver for your machine. the only issue i had(albeit only once, and i have installed fiesty fawn on numerous pc/laptop) was having to change my screen resolution.

in terminal

> sudo nvidia-settings

x server display configuration>resolution>pick the correct setting here>save to x conf file  and you are done.

[http://ubuntuforums.org/showthread.php?t=405990&highlight=1390](http://ubuntuforums.org/showthread.php?t=405990&highlight=1390)

if you have broadcom/dell 1390 wireless card you can use this link to do the work for you.
 
any other help can be found by searching the forums with the correct key words. normally searching for the model name/number will pull up some good information. i found all of this ifo with search. save me some typing by using this wonderful function =)

hope all goes well :)

---

### Post by mushroomcloudwarrior on 2007-10-31
Update:

Kpowersave wasn't installed on the computer, but now is..i can control my power options and go into powersave mode! which is a great option to have..

Installed Ksynaptics, but it won't let me access it, but gives me this error message instead;

[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/snapshot4.png[/IMG]

So when i did open that file, this is the code that i got in there, and there was no mention of anything called 'touch pad'
Here's the file;
[HTML]```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Oct  4 10:33:51 PDT 2007


Section "ServerLayout"
	Identifier	"Layout0"
  screen 0 "Screen0" 0 0
	Inputdevice	"Keyboard0"	"CoreKeyboard"
	Inputdevice	"Mouse0"	"CorePointer"
EndSection

Section "Files"
	Rgbpath		"/usr/lib/X11/rgb"
EndSection

Section "Module"
	Load		"dbe"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
	Load		"glx"
EndSection

Section "InputDevice"
	
	# generated from default
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"Protocol"	"auto"
	Option		"Device"	"/dev/psaux"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "InputDevice"
	
	# generated from default
	Identifier	"Keyboard0"
	Driver		"kbd"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"Unknown"
	Horizsync	30.0	-	110.0
	Vertrefresh	50.0	-	150.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Device0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection





```[/HTML]

^ i know i'm only a step away, but don't know how to get it to work.

Nvidia drivers;

i realised i was being stupid and not opening Envy all this time..it was too easy with Envy, 

No more jerky screens now, it was indeed the graphic drivers!

Right guys, two MAJOR problems *almost* solved, do you have any suggestions about the sound? i have good sound on my laptop as explained earlier, just that the speakers won't shut up even after connecting the headphone jack...

---

### Post by mushroomcloudwarrior on 2007-10-31
My Fstab file..

[HTML]```


# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=e645986e-d871-450c-98bb-72e05a41cc3c / jfs defaults,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=c822527f-e6c6-4d76-bdc5-835db4f3f70f /home ext3 defaults 0 2
# Entry for /dev/sda6 :
UUID=733d86e8-ef85-4007-9bef-b9cf4c113605 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0



```
[/HTML]

---

### Post by professor fate on 2007-10-31
I was able to get the sound card working on a Dell Vostro 1400 with an Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


At the terminal type in: sudo gedit /etc/modprobe.d/alsa-base
Then paste this into the file: options snd-hda-intel model=5stack

---

### Post by mushroomcloudwarrior on 2007-11-01
^

Thanks for the reply man, didn't work for me though..

(i'm just going to keep doing what your sig says)

---

### Post by Dark Seraphim on 2007-11-02
go to the terminal and paste this in 

sudo aptitude install linux-backports-modules

that might fix the sound it fixed mine anyway

---

### Post by mptpro on 2007-11-04
I have Dell Vostro 1500 and Ubuntu 7.1

The sound was not working, and after trying Dark Seraphim idea, it WORKED!

thanks!

---

### Post by mushroomcloudwarrior on 2007-11-06
When i tried logging in to do this, linux just seems to have crashed..or something like that :|

Here;s the thread link
[http://ubuntuforums.org/showthread.php?p=3717982#post3717982](http://ubuntuforums.org/showthread.php?p=3717982#post3717982)

---

### Post by StefAndrew on 2007-11-09
I'll have to try the backports to get my sound working.  AFAIK, that's the only thing left for me to get working on my Vostro 1500.  Everything else is working wonderfully.

---

### Post by mushroomcloudwarrior on 2007-11-18
> **Dark Seraphim said:**
> go to the terminal and paste this in 

sudo aptitude install linux-backports-modules

that might fix the sound it fixed mine anyway

Thanks for the tip, but it didn't really work for me.

I'll keep looking.

---

### Post by StefAndrew on 2007-11-19
> **StefAndrew said:**
> I'll have to try the backports to get my sound working.  AFAIK, that's the only thing left for me to get working on my Vostro 1500.  Everything else is working wonderfully.

Yep, did the trick, but the sound levels are a little off.  It doesn't have a lot of middle level volume when making it louder or softer, it pretty loud at max, not as loud as Windows, but then when it's barely halfway turned down, it's completely silent.

---

### Post by mushroomcloudwarrior on 2007-11-19
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Lot of help related to sound on there. Method A worked for me for a bit, but it's still strange.

After editing the /etc/modprobe.d/alsasomething i rebooted

sound seemed to be working through the laptop speakers when i started,
I plugged in the headphones, and voila..the laptop speakers cut off, happiness? not yet..
Unplugged the speakers and laptop speakers didn't work while the headphones worked fine. Rebooted it in the morning to find that sound was working just fine on the laptop speakers, but not on the headphones i.e. back to square one.

i hope the link works for you though

---

### Post by mushroomcloudwarrior on 2007-11-19
Issue:

after the re-install, there's a 86 gig partition that's supposed to work as the bridge between linux and windows. It's mounted as /media/sda6 , it's an ext3 partition and the permission says that i can view and modify content. However, i still can't move or copy any files into the partition. Here's a snapshot;

[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/snapshot1.png[/IMG]

---

### Post by mpgarate on 2007-11-19
im about to buy a new laptop and was about to buy this one, but lucky I googled 'vostro 1500 ubuntu' first. do you think that its bad enough to be worth looking at other laptops? this one is such a good price!!

---

### Post by StefAndrew on 2007-11-20
> **mpgarate said:**
> im about to buy a new laptop and was about to buy this one, but lucky I googled 'vostro 1500 ubuntu' first. do you think that its bad enough to be worth looking at other laptops? this one is such a good price!!

Not at all.  I think the Vostro 1500 is right about the best bang for your buck right now when it comes to laptops.  Not much else comes close the price for the options you can choose from.  I got mine with everything but RAM and HD maxed out and it was right at $1500 shipped.

---

### Post by mpgarate on 2007-11-20
nice! thats what im doin. ordering a 1.8ghz dual core with 2gb ram and 9 cell batt for about 700 or so

---

### Post by mushroomcloudwarrior on 2007-11-20
First off,

oh man, i'm waiting the the avatar chapter 12 off season 3 episode!

Secondly, the Laptop is actually quite good for the price. Possible downsides could be that it's slightly more bulky and heavy than some others out there, if you don't plan to travel around with, or only plan to travel with it once in a while, it's great.

I now have most hardware on it running..still have some issues, but i'm sure it'll get fixed with time. I'd say go for it.

---

### Post by mpgarate on 2007-11-20
haha yeah cool! I dont know all that much about avatar actually, I just thought it would make a tight avatar

PUN

---

### Post by ManasT on 2007-11-21
> **professor fate said:**
> I was able to get the sound card working on a Dell Vostro 1400 with an Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


At the terminal type in: sudo gedit /etc/modprobe.d/alsa-base
Then paste this into the file: options snd-hda-intel model=5stack

That worked for me... :)

---

### Post by mushroomcloudwarrior on 2007-11-24
> **Dark Seraphim said:**
> go to the terminal and paste this in 

sudo aptitude install linux-backports-modules

that might fix the sound it fixed mine anyway

Couldn't install it because of 
```
nikhil@nikhil-laptop:~$ sudo gedit /etc/modprobe.d/alsa-base
[sudo] password for nikhil:

** (gedit:10059): WARNING **: Throbber animation not found

** (gedit:10059): WARNING **: Throbber fallback animation not found either

```

---

