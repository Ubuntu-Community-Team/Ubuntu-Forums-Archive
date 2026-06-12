---
title: "Make games run faster"
date: 2006-08-28
forum: Gaming &amp; Leisure
---

### Post by Darrious on 2006-08-28
How would I go about making games run faster in ubuntu. I have a 3d game that's very choppy. I can't run any cool 3D game and it's driving me crazy.

Processer speed: 830
RAM: 670 meg
Graphics Card: Nvidia Gforce 8300

Thanks.

---

### Post by GregaS on 2006-08-28
GeForce 8300? What the hell is that?

---

### Post by Scythe!? on 2006-08-28
> **Darrious said:**
> 
Graphics Card: Nvidia Gforce 8300

Thanks.
Wow. Can I have a 8300? Thats like...the future.

Ok, seriously now, do you have graphics card drivers installed?

---

### Post by Darrious on 2006-08-28
Yes, I do.

---

### Post by KingBahamut on 2006-08-28
No such thing as an Nvidia geforce 8300. 

So , Try again with your card type please.

---

### Post by HAARP on 2006-08-28
Open terminal, type
```
lsmod | grep nv
```
what does it say?

---

### Post by fatsheep on 2006-08-28
I think he means a geforce **6**300...

---

### Post by Darrious on 2006-08-28
When I type in 

```
lsmod | grep nv

```

It says this 

```
nvidia               4550772  0
i2c_core               21904  3 i2c_acpi_ec,nvidia,i2c_piix4
agpgart                34888  2 nvidia,intel_agp

```

I don't know why I typed 8300. I do am though getting a new 5200 card installed, very soon:mrgreen:

---

### Post by crane on 2006-08-28
What games are you trying to run? Make sure your not pushing the limits of your system as well. (check Game Specs).
 So what model is it.
 I got the following from grep:

nvidia               4553140  12
i2c_core               23168  3 i2c_acpi_ec,nvidia,i2c_viapro
agpgart                37072  2 nvidia,amd64_agp


 I am running a 6600

---

### Post by Darrious on 2006-08-29
Right now I'm trying to run FlightGear and another game called [PlaneShift.]("http://www.planeshift.it/main_01.html")
I'm not sure why it isn't working. I have enough RAM, and my graphics card is fine. It could be because my processer speed is only 850 mghz.
PlaneShift I can actually see on there, but I runs very slow.
FlightGear doesn't even run at all. It just comes up with a window that freezes up.

---

### Post by justin whitaker on 2006-08-29
> **Darrious said:**
> Right now I'm trying to run FlightGear and another game called [PlaneShift.]("http://www.planeshift.it/main_01.html")
I'm not sure why it isn't working. I have enough RAM, and my graphics card is fine. It could be because my processer speed is only 850 mghz.
PlaneShift I can actually see on there, but I runs very slow.
FlightGear doesn't even run at all. It just comes up with a window that freezes up.

Start checking services. You must be running something that is hogging CPU cycles. 

Also, one of the things I do when gaming is to switch to a minimal WM like Openbox/Fluxbox/etc....less background resources means more resources for gaming.

---

### Post by Darrious on 2006-08-29
Right now I'm going to try and run it without any gui.

---

### Post by Darrious on 2006-08-29
It is a little bit faster without the gui, but it's still very slow.

---

### Post by Tomosaur on 2006-08-29
Hmm. If you're upgrading TO a 5200, the gfx card you currently have must be pretty old, which could well be the cause of your problems. Still, I don't know the req specs for those games, so I can't really comment. I have a 5200 too, and they do run fine (aswell as some more graphically challenging games like HL2 and FarCry on windows :P ). Your processor could probably do with upgrading, but if you're getting a new gfx card anyway, you should hold out and see if it improves at all.

---

### Post by Darrious on 2006-08-30
Well, one of the games that I'm trying to run right now, is a game called [PlaneShift]("http://www.planeshift.it/main_01.html")

---

### Post by DoktorSeven on 2006-08-30
Do you get this?

```
~$ glxinfo | grep direct
direct rendering: Yes

```

---

### Post by Darrious on 2006-08-31
This is what It shows up when I type this command.

```
$glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

---

### Post by Darrious on 2006-09-04
It says direct rendering no. So what do I do now?

---

### Post by Omnios on 2006-09-04
Just a note I used to have a Gforce2 64meg and could not get  FlightGear to run as it was unplayable, maybe I will trying now as I git a MX4000 128meg card now.

 The other game Plane Shift is a odd game in that it has very heavy ram requirments, think it was 500megs recomended to play

---

### Post by Darrious on 2006-09-05
Well I have 640 megs in my computer total.

 Also, there is a really neat game called [Freelancer.]("http://www.microsoft.com/games/freelancer/")
It's a really neat game for windows. Since I'm running ubuntu, I can't install that. It only requires 256 ram to play, so it worked on my windows machine.

Is there some type of other game that's similar to PlaneShift that requires lower requirements. I'm just not able to run the best games right now. 

I'd also like a game similar to [VegaStrike]("http://doc.gwos.org/index.php/Vega_Strike") just with fewer requirements and is multiplayer.

---

### Post by WalmartSniperLX on 2006-09-05
Linux drivers arent up to par for one thing. Well at least i know the ati ones arent. Maybe nvidia is like that. If you ever ran ur system in win and its much faster than it is then its the drivers for sure.

---

### Post by DoktorSeven on 2006-09-06
If you get Direct Rendering: No, you should [follow this guide](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to enable direct rendering with your NVidia card.

---

### Post by Lord Illidan on 2006-09-06
> **WalmartSniperLX said:**
> Linux drivers arent up to par for one thing. Well at least i know the ati ones arent. Maybe nvidia is like that. If you ever ran ur system in win and its much faster than it is then its the drivers for sure.

Don't give half information. Nvidia's Linux drivers are as good as Windows, and have been for quite some time.

The ATI drivers still have to improve.

It is most probably the drivers which you have trouble with. Install the drivers from synaptic.

---

### Post by Darrious on 2006-09-08
> **DoktorSeven said:**
> If you get Direct Rendering: No, you should [follow this guide](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) to enable direct rendering with your NVidia card.

Thanks for the url. Although I'm having problems with actually running the games now. They can't even start up now. It says that it's missing some type of plugins or something for the driver. I'll have to check it in a little bit.

---

### Post by Darrious on 2006-10-04
I got a brand new computer, and now all of the games I tried to run are running just fine now. I was also wondering if XGL can be ran on an Intel Graphics card?

---

### Post by tuxcantfly on 2006-10-04
yes, but aiglx will work better if you use edgy

---

### Post by tuxcantfly on 2006-10-04
and xgl will play opengl games very slow. aiglx is faster for playing 3d games

---

### Post by Darrious on 2006-10-04
I don't think that aiglx will work with work with my computer. I have an Intel Graphics Chip. I tried XGL on it and it failed. I'd like to try this aiglx though.

If available for Ubuntu.

---

### Post by tuxcantfly on 2006-10-05
use edgy. it has xorg 7.1, with aiglx built in

---

### Post by Darrious on 2006-10-07
No thanks, I'll just stick with ubuntu. I'll try to get XGL to run.

---

### Post by tuxcantfly on 2006-10-08
edgy is ubuntu. it's the codename for ubuntu 6.10, the next version

---

### Post by tuxcantfly on 2006-10-08
and also, the AIGLX built into edgy's xorg7.1 gives much better performance and more features (like the ability to run opengl games without starting a new xserver) than XGL. It also needs a lot less effort to set up, since it's built into edgy's xorg7.1 xserver and needs no extra stuff.

---

### Post by jcrnan on 2006-10-09
xgl doesnt work well with intel. aiglx is definitvly the way to go. Ive had it running on several intel cards very smoothly :)

---

### Post by airtonix on 2006-10-09
> **Darrious said:**
> It says direct rendering no. So what do I do now?

Get a better video card.....unfortunatly.

plus you'll need more system ram. and a possibly a mother board with a decent bus speed.....yeah decent bus speeds definitly are a great start....

> no use having a 5,000,000litre through-put when your using 5mm conduit

---

### Post by Darrious on 2006-10-09
A coulple of questions.

One, when is edgy scheduled to come out.
Two, where could I find some good webcamera software.

---

### Post by tuxcantfly on 2006-10-09
edgy is scheduled to come out this month, but you can already use it. just download the edgy beta and install it, or if you're using dapper, just change your /etc/apt/sources.list to edgy repos and apt-get dist-upgrade

---

### Post by tuxcantfly on 2006-10-09
[http://us.releases.ubuntu.com/edgy/](http://us.releases.ubuntu.com/edgy/) is where you can download the edgy beta

---

### Post by tuxcantfly on 2006-10-09
as for webcam software, try out camorama

---

### Post by Darrious on 2006-10-09
Thanks for all the info tuxcantfly. 
Going actually back to the topic, I'm trying PlaneShift and everytime I start it in the terminal it says Segmentation Fault. When I looked at what poped up it says "indirect rendering may indicate a flawed OpenGL setup, If you run on a local X Server" 

P.S. I ran it at least 30 times just to read the message it said, because every time I ran planeshift, it closed within 2 seconds.

---

### Post by simplyw00x on 2006-11-13
That means you haven't set up your graphics card drivers properly. Consult the wiki link and try again until you get 'Direct Rendering: Yes', because until you do, games will be unplayable. Also, XGL == not work on intel graphics card but AIGLX will.

---

### Post by Darrious on 2006-11-16
I'm going to try to just re-install it and it see how that turns out. 

I've heard of AIGLX before but never really tried it. Since I have an Intel Graphics card this might actually work unlike XGl.

---

### Post by WalmartSniperLX on 2006-11-16
> **GregaS said:**
> GeForce 8300? What the hell is that?

Im terribly sorry for posting this useless post but HAHAHA that gets me every time :D  ;)

---

### Post by Darrious on 2006-11-17
That person just does not understand or know what it is.

---

