---
title: "Ubuntu-Powered MAME Cabinet"
date: 2009-01-17
forum: Gaming &amp; Leisure
---

### Post by SmellyGeekBoy on 2009-01-17
Hello all...

I'm converting an old arcade cab to a PC running MAME and being a Ubuntu user at home, I'd like to use it to run my cab as well. I've got MAME itself up and running (SDLMAME and XMAME seem to work just as well as each other from what I can see) and working fine with the kxmame package from Synaptic.

Trouble is, I'm after a much better interface, something along the lines of Wah!Cade or AdvanceMenu, so I can use the joysticks on the cab to navigate the menus.

Does anyone have any experience with these? I have compiled AdvanceMAME and AdvanceMenu (after going through dependancy hell) but I am struggling to get them to work, and Wah!Cade just comes with with a load of Python errors.

Does anyone have any experience setting up a MAME cabinet running a modern version of Ubuntu? Anyone have any good frontends they can recommend which they have working?

Thanks guys, I'll put up some pictures of the cab once it's finished!

---

### Post by Corey4666 on 2009-01-17
Can you post a picture of your errors? I am not entirely sure if I will be of much help but I can make and attempt. I never used any other MAME emu other than MAME32k (which is for windows) I had it running nicely under wine just perfectly! even on netplay!! using p2pclient.

By the way I also wanna make a table cabinet! post me pictures when you finish it? :popcorn: I would like to see how it turns out.

EDIT: btw I have no clue how to control the menu's with the joysticks, but I have seen a lot of machines setup with a small keyboard built under the Joystick panel.

---

### Post by SmellyGeekBoy on 2009-01-18
Hi Corey, hadn't considered trying something in WINE. That could work quite well actually - I'll give it a go!

You can actually control most of the frontends with the joysticks - if you have a joystick controller like one of the IPAC interfaces, they're just mapped to keyboard keys anyway. P1 joystick is up, down, left, and right on the keyboard so you can navigate most menus easily!

---

### Post by Corey4666 on 2009-01-18
Good luck man! I had good success with Mame32k using 0.64 client under wine. 

Here is MAME32k:
[http://www.emulator-zone.com/download.php/emulators/arcade/mame/mame32_kaillera/mame32-067-414-ka09.exe](http://www.emulator-zone.com/download.php/emulators/arcade/mame/mame32_kaillera/mame32-067-414-ka09.exe)

Here is the .64 mame client:
[http://www.anti3d.com/dl/mame32k0.64en.zip](http://www.anti3d.com/dl/mame32k0.64en.zip)

Here is Openp2p Kaillera client: (if you wanna netplay)
[http://kaillera.movsq.net/stable/kailleraclient.dll](http://kaillera.movsq.net/stable/kailleraclient.dll)

All these specific files worked well under wine for me, except net play was a bit weird for me sometimes. But this is the only kaillera.dll client that works under wine that I know of. 

Make sure when your setting up your MAME32k under wine you redirect your rom paths and have the bios. :guitar:

---

### Post by vulcanfk on 2009-01-19
> ..I am struggling to get them to work, and Wah!Cade just comes with with a load of Python errors.

Does anyone have any experience setting up a MAME cabinet running a modern version of Ubuntu? Anyone have any good frontends they can recommend which they have working?

I just downloaded the newest version of wah!cade, installed it in 8.10, and its working no problems.  Do you have an old version?  The latest is 0.99pre5.1.  Direct link: [wah!cade 0.99pre5.1]("http://www.anti-particle.com/projects/wahcade/wahcade_0.99pre5.1_all.deb")

---

### Post by lordbah on 2009-01-22
sdlmame was horribly slow for me. I had to go to xmame.SDL, which is working fine. I know it's not being actively maintained, but the games I like are all from the 70s and 80s anyway.

I'm also using wah!cade. My current problem is that it won't recognize a pushbutton mapped to launch a game. xmame does recognize the button so I know that the buttons and joysticks are all wired up correctly. That's about the only reason I still have a keyboard attached full-time.

---

### Post by FranMichaels on 2009-01-22
lordbah, sdlmame is of course more up to date, try this.

in your mame.ini

```
#
# VIDEO OPTIONS
#
video                     opengl

#
# OpenGL-SPECIFIC OPTIONS
#
filter                    0
prescale                  1
```

Having the filter on made it like a slug for me, now it flies!

---

### Post by Corey4666 on 2009-01-23
Hey its great to see other people so interested in emulators. I have been into emulators for 5+ years now. :D

@ FranMichaels

I like your emulation blog, I bookmarked it and i will dig on it later because I have never used emulators on Linux yet! I been a window user for way to long.

---

### Post by slave-zeo on 2009-05-16
You might want to check out my thread located at 

[http://ubuntuforums.org/showthread.php?t=840863](http://ubuntuforums.org/showthread.php?t=840863)

it might help you set up a really slick arcade interface.

---

### Post by chaoszerox on 2009-06-19
I ran MAME32k 0.64 fine under windows XP OS, but when I had to switch to Ubuntu, it doesn't run fast enough =( I did install restricted drivers

---

### Post by williamts99 on 2009-10-24
I am using SDLmame and Wahcade for my converted cab.  They have repos and debs for both.  The only issue I had was SDLmame and pulseaudio not playing nice with each other.  I would start a game and it would get so slow, 100%cpu usage and then I would kill pulseaudio and then it would work again.  The fix for me was to install libsdl1.2debian-pulseaudio.

```
sudo apt-get install libsdl1.2debian-pulseaudio
```

One thing that would be nice is for SDLmame to add the expected Wahcade default rom path to /etc/sdlmame/mame.ini so you wouldn't have to add it manually.

Best Regards,
Williamts99

---

### Post by WarrenSH on 2010-05-06
I would liek to knwo if your project got up & running. Can we see some pictures of your arcade build plz ;)

---

### Post by WarrenSH on 2010-05-17
> **WarrenSH said:**
> I would liek to knwo if your project got up & running. Can we see some pictures of your arcade build plz ;)


Is this member still active on this site? I would like to know how the project went. I am having a hell of a time with MAME & my usb game pads!

---

