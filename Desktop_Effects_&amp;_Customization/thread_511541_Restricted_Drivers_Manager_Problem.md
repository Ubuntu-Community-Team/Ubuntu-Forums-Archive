---
title: "Restricted Drivers Manager Problem"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by Just-trevor on 2007-07-27
When I click on Restricted Drivers Manager in system administration a window says I don't need any restricted drivers.
How do I enable the nVidia Driver?
When I try to enable Desktop Effects a window says I can't


I feel left out...

---

### Post by zero244 on 2007-07-28
Did you install any video drivers. Check at the top panel and see if there is a little icon that looks like a video card. If that is their your restricted drivers are installed.
1. Why you cant turn on desktop effects I am not sure.
2. Or why Ubuntu claims you don't need them.
One of the above statements is incorrect.
You could download Automatix2 and install your video drivers which should then allow you to run desktop effects.
Good luck
PS I'm running beryl with full effects and it is very cool.
When set up correctly they are very stable.

---

### Post by Just-trevor on 2007-07-28
Well:
I installed automatix and tried to install the nVidia driver but, lo and behold, I guess I don't have an nVidia card, (and I'm pretty sure I do), but wouldn't that mean that desktop effects should install without any hassle? 

If there is an alternative, beryl, then I guess I shouldn't bother with Desktop effects then right?

Thanks for the help - out of 52 visitors you were the only one who wrote anything.

---

### Post by zero244 on 2007-07-29
Ok if you open Automatix and go to the driver section and there is no Nvidia driver listed that probably means you have a ATI Card.
There is really only two video card platforms, nvidia and ati.
If there is a ATI driver you can install that.
Keep in mind once you install the restricted drivers via Feisty the Automaitix drivers will not work correctly or at least Ive never been able to get them to work.
I am using the Automatix drivers on two different computers and they are working fine with full 3d effects using Beryl.
Maybe try a clean install if this is a fairly new setup.
Do a clean install and dont try to enable desktop effects or the Feisty drivers.
Just go for the Automatix drivers.
Now depending on the card type you are going to have to do some adjustments with you Xorg.conf file to get beryl working.
Look around for some How To's that can walk you through the process.
Its not that hard you just have to get familiar with Ubuntu and how things work.
Once you set up beryl a few times you can do it in your sleep.
My guess is since the nvidia drivers did not show in Automatix you have a ATI card. Which can work fine but takes a little more detail work to get it working stable and smooth.
Good luck and keep us posted of any progress.

---

### Post by tupesadilla on 2007-07-30
or another thing you can do is... if your sure you have nvidia, or even if you have ATI. download the envy script and use envy to install.

---

### Post by petermarkab on 2007-08-01
Hi trevor,
have you managed to get your graphics card working? one way of telling what type of card you have is to open a terminal (Applications -> Accessories -> Terminal) and type

```
lspci | grep -i vga
```

and press enter. You should get output saying what kind of vga card you have.
regards,
Peter

---

### Post by jms1277 on 2007-08-01
hi i hyave ati radion 128 ultra and was wondering if it will run desktop effcts or copiz or bereyl i really want to get effects please help

---

### Post by jms1277 on 2007-08-01
hi i checked the ristercied driver manger it say im useing athorros hal

---

### Post by Espreon on 2007-08-01
If the Manager is giving you no options it either means that the manager is screwed or
2.It just hates you
3.Desktop Effects Hates your
4.Your card is not capable of using these effects
5.Your xorg.conf is not configured properly

So do this in a terminal:

```
sudo gedit /etc/X11/xorg.conf
```

 and post the contents of that file.

---

### Post by Espreon on 2007-08-01
> **jms1277 said:**
> hi i hyave ati radion 128 ultra and was wondering if it will run desktop effcts or copiz or bereyl i really want to get effects please help

I think that chip can run special effects, try running the effects since I think that chip is compatible with AIGLX.

---

### Post by jms1277 on 2007-08-01
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"

---

### Post by jms1277 on 2007-08-01
i try but all i get is a white screen just goes white with nothing but the cursor showing waits a min or 2 then comes back

---

### Post by jms1277 on 2007-08-01
please help

---

### Post by Just-trevor on 2007-08-05
Zero,
when I open automatix it has nVidia drivers there and when I try to download it a window says "error
video card not detected as nVIdia"
shouldn't I have the option to download ATI driver?
I didn't check this post for a week so I missed your post till now
i really don't want to risk screwing up my comp until I'm sure desktop effects wont work

Espreon,
I did the thing in terminal,
(gedit:7374): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave

what now???
i don't even know what my xorg.conf is

any ideas anyone?

---

### Post by Just-trevor on 2007-08-05
root@Trevor2:/home/trevor-max# lspci | grep -i vga
02:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
ok... i have an ati card...

---

### Post by laakkus on 2007-10-22
hello!

My problem is that after the upgrade to 7.10, restricted manager doesnt start. it ask for password, but after that nothing happens.. any ideas?

---

