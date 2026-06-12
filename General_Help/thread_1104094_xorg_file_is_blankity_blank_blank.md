---
title: "xorg file is blankity blank blank"
date: 2009-03-23
forum: General Help
---

### Post by cardboard fox on 2009-03-23
...

---

### Post by DGortze380 on 2009-03-23
> **cardboard fox said:**
> hey all what's up
i'm trying to edit my xorg.conf file, i finally found it that mysterious little file was hard to find but i finally find it, so i click on open with text editor so i can edit that mother to get my gysaptics to start working and the entire file is blank
what's up with this
thanks

try this

```

gksudo gedit /etc/X11/xorg.conf

```

---

### Post by cardboard fox on 2009-03-23
...

---

### Post by SuperSonic4 on 2009-03-23
What video card are you using? 
nvidia users can do ```
sudo nvidia-xconfig
```

otherwise ```
sudo Xorg-configure
``` should generate a new xorg. Easiest would probably be to go to Fix X server in the recovery mode during grub

---

### Post by Claus7 on 2009-03-23
Hello,

a female friend of mine tells me to tell you that you are a GOD! In our place this is not an offence, just that someone "wrote on paper", which means that you are sugoi, or you have it, or you are the man or whatever, you got the point!

Blank as sugar, eh? Interesting... I would suggest you to go to /etc/X11 and type an ls command to see what is there. In case there is nothing at all, I cannot figure out how you are able to speak to us via your pc, cause your graphical environment should not be working.

Thank you for the nice evening. I enjoyed greatly your way of writing.

Regards!

---

### Post by cardboard fox on 2009-03-23
...

---

### Post by cardboard fox on 2009-03-23
> **Claus7 said:**
> Hello,

a female friend of mine tells me to tell you that you are a GOD! In our place this is not an offence, just that someone "wrote on paper", which means that you are sugoi, or you have it, or you are the man or whatever, you got the point!

Blank as sugar, eh? Interesting... I would suggest you to go to /etc/X11 and type an ls command to see what is there. In case there is nothing at all, I cannot figure out how you are able to speak to us via your pc, cause your graphical environment should not be working.

Thank you for the nice evening. I enjoyed greatly your way of writing.

Regards!

wow thanks. tell that girl she can pm me her number

and yeah man there's nothing there. so i don't know how i'm using this pc.  must just be one of the incongruities of life

---

### Post by Claus7 on 2009-03-23
Hello,

lspci will do the trick. See there where the string "vga" exists.
Also nicely it would be to type sudo dpkg-reconfigure -phigh xserver-xorg
That way you will generate a new xorg.conf file if something else is not messed up.

Regards!

---

### Post by Nostalos on 2009-03-23
in 8.10  Xorg moved away from static Xorg.conf files.   Its blank because Xorg runs autoconfig on startup.    Only thing you should have to put in your Xorg.conf file out of the box is specialized setups.  Such as Virtual Desktops for dual screen support. 

Example my Xorg.conf below for dual screen lappy

> 
Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	SubSection "Display"
		Virtual	2720 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection



---

### Post by DGortze380 on 2009-03-23
> **Nostalos said:**
> in 8.10  Xorg moved away from static Xorg.conf files.   Its blank because Xorg runs autoconfig on startup.    Only thing you should have to put in your Xorg.conf file out of the box is specialized setups.  Such as Virtual Desktops for dual screen support. 

Example my Xorg.conf below for dual screen lappy

:roll:

now I remember hearing that... sorry, haven't run 8.10 sticking with LTS for now so it never occurred to me that it might actually be blank, and blank for a reason.

---

### Post by rolandrock on 2009-03-23
Hi, great handle foxy

Since Hardy(?), you don't need an xorg.conf unless you have some weird setup.  On my main pooter, I use xorg.conf to configure a dualhead and override some default settings to make my crappy MS wireless mouse work (I know - the shame of it).

My other 3 computers (Hardy/Intrepid/eeebuntu2) have their hardware autodetected at boot and don't need xorg.confs.

---

### Post by cardboard fox on 2009-03-23
> **Nostalos said:**
> in 8.10  Xorg moved away from static Xorg.conf files.   Its blank because Xorg runs autoconfig on startup.    Only thing you should have to put in your Xorg.conf file out of the box is specialized setups.  Such as Virtual Desktops for dual screen support. 

Example my Xorg.conf below for dual screen lappy

wellllll to be honest i don't really understand a lot of what you say. so let me put my problem in other words for everyone. basically the vertical scrolling speed on my laptop with my touchpad is ridiculously slow. when i was running big bad vista the scrolling speed was smooth and real fast. so i gathered through some elementary research that i needed this thing call gysaptics. well i get that from the add remove thing on my applications. well when i try to run it, guess what? well i'll tell you what Nostalos, another problem that's what. here's what it says:
GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

so it was this point where i began my quest for the xorg file. eventually it came to pass that i found it. and when i find it. it is blank. just sitting there is some text editor, completely blank yet staring at me. true. will you now say that i am mad? i've experienced many things, how then will you say that i am mad? observe how calmly i've recounted my story.

---

### Post by cardboard fox on 2009-03-24
update: i downloaded some graphics driver but it has not helped

---

### Post by Nostalos on 2009-03-24
I am not 100% sure the best way to configure this as I don't use a Synaptics.   I would assume (please note the use of "assume")  that you could just add your device listing to /etc/X11/xorg.conf


> 
Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
          Option "SendCoreEvents"          "True"
          Option "Protocol"                "auto-dev"
          Option "Device"                  "/dev/psaux"
          Option "SHMConfig"               "True"
EndSection



If this does not work,  I would recommend having Xorg build a static xorg.conf file.  Static xorg.conf is not the norm, but it does still work.

Once you are sitting at the login screen after boot up.  alt + ctrl + F1  to open the first tty console and login commandline.

> 
sudo /etc/init.d/gdm stop
sudo Xorg -configure
sudo cp /root/xorg.conf.0 /etc/X11/xorg.conf


should generate a working xorg.conf file which you can modify to include your needed options.

---

