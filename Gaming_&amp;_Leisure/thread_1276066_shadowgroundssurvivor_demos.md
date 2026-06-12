---
title: "shadowgrounds/survivor demos"
date: 2009-09-26
forum: Gaming &amp; Leisure
---

### Post by ELD on 2009-09-26
Can anyone actually get them to run?

Mine errors out with the attached picture.

---

### Post by Sealbhach on 2009-09-27
Shadowgrounds installed OK for me, I'm using Ubuntu 9.04  64-bit.

I haven't tried Survivor.

In your screenshot, it refers to a library, glibc, I looked in my own Synaptic and I've got libglib.

Check to see if you have libglib2.0-0 in your Synaptic.

.

---

### Post by MaximB on 2009-09-27
It installs and runs fine, except random crashes.

---

### Post by ELD on 2009-09-27
I have "libglib2.0-0" installed i checked via synaptic .

Edit > Weird just tried it again and the installer works.

---

### Post by Perfect Storm on 2009-09-27
> **MaximB said:**
> It installs and runs fine, except random crashes.

Aye, but I guess they are working on a patch. But overall very nice game(s), really catchy and the eerie atmosphere makes me jump sometimes LOL. It's just a matter of 2 days that I have my boxed version of Shadowgrounds and this morning I ordered the Survivor.

---

### Post by ELD on 2009-09-27
I doubt they will let the crashes go on for too long, after a i reboot i should be able to play it fine (installed ati drivers - fresh install of ubuntu).

Edit > Just played demo for 20 minutes for it to totaly crash to the desktop heh, seems like a really good game though!

---

### Post by MaximB on 2009-09-27
The problem with Shadowgrounds series is that you cannot save at will, therefore if the game crashed after 30 minutes of play - all is lost.

I also had many crashes at Sacred Gold, but I could save at will and not lose too much time, the crashes stabilized somehow.

LGP blames the ATI drivers for the crashes, and justly so - but they still MUST support ATI .

---

### Post by ELD on 2009-09-27
> **MaximB said:**
> The problem with Shadowgrounds series is that you cannot save at will, therefore if the game crashed after 30 minutes of play - all is lost.

I also had many crashes at Sacred Gold, but I could save at will and not lose too much time, the crashes stabilized somehow.

LGP blames the ATI drivers for the crashes, and justly so - but they still MUST support ATI .

Games that don't allow me to save where i want ruin the whole experience for me, especially when things like this happen.

All the more reason my to buy list has an nvidia graphics card in it for next time.

I got too bored with Sacred, haven't touched it in a long time.

---

### Post by Perfect Storm on 2009-09-27
Had only one crash with the nvidia card. It was 20 min. Next time I tried I've played 3 hours straight without any issue.

> Games that don't allow me to save where i want ruin the whole experience for me, especially when things like this happen

It seems working quite well with shadowgrounds as it saves between the scenarios. And the each stages doesn't seems to be too large that it will ruin the gameplay.

> LGP blames the ATI drivers for the crashes, and justly so - but they still MUST support ATI .
They actually do, but if the ATI driver is buggy etc. it's a bit hard to make the game stable.

---

### Post by iloutzu on 2009-11-12
I've been playing the Survivor demo, and it crashes every time while loading the second level (I have an nvidia card, so no ATI problem; it just says "localization missing", and then crashes). 

Anyone had the same problem? Is it because the demo has just the first level?

---

### Post by jpv2 on 2009-11-13
> **iloutzu said:**
> 
Anyone had the same problem? Is it because the demo has just the first level?


Same here. The demo has only first episode.

BTW: it runs fine for me, haven't experienced any crashes (NVidia on board).

---

### Post by iloutzu on 2009-11-13
> **jpv2 said:**
> Same here. The demo has only first episode.

BTW: it runs fine for me, haven't experienced any crashes (NVidia on board).
Oh, good! I didn't have any other crashes (played that level 4 times). I guess I'll have to buy the full game soon... ;)

---

### Post by afrodeity on 2010-08-17
Loader comes up but it refuses to run

```

[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF
TApplication.HandleException Unable to create file "/home/afrodeity/.lgp/survivor_demo/Config/launcher.txt"
  Stack trace:
  $08099E32
  $080A0EB7
  $0808B41E
  $0817E164
  $081BF14F
  $081BF735
  $081BFC91
  $081BEFEA
  $0806A4A9
  $08174942
  $081FA4D7
  $0828CB80
  $00128DCC
  $0011B252
  $0012F99D
  $00130DB4
  $00131256


```

---

### Post by afrodeity on 2010-08-17
Loader comes up but it refuses to run

```

[WARNING] Out of OEM specific VK codes, changing to unassigned
[WARNING] Out of unassigned VK codes, assigning $FF
TApplication.HandleException Unable to create file "/home/afrodeity/.lgp/survivor_demo/Config/launcher.txt"
  Stack trace:
  $08099E32
  $080A0EB7
  $0808B41E
  $0817E164
  $081BF14F
  $081BF735
  $081BFC91
  $081BEFEA
  $0806A4A9
  $08174942
  $081FA4D7
  $0828CB80
  $00128DCC
  $0011B252
  $0012F99D
  $00130DB4
  $00131256


```

---

### Post by rettichschnidi on 2010-08-18
What does this say:

```
ls -lR1 /home/afrodeity/.lgp/survivor_demo/
```

Edit: or better just wait, [someone capable]("http://blog.linuxgamepublishing.com/2010/08/18/customer-services-update-for-august-2010/comment-page-1/#comment-1798") will take care of you. :)

---

### Post by Zero_Dogg on 2010-08-18
Hi afrodeity,
could you check the permissions on ~/.lgp ? Make sure that all of the directories there are owned by your user and are writable. A "chown -R $USER ~/.lgp" followed by "chmod u+w -R ~/.lgp" should do it. Then try to run the game again.

If that does not work, download and run the LGP test tool ([http://demofiles.linuxgamepublishing.com/lgp_testtool/](http://demofiles.linuxgamepublishing.com/lgp_testtool/)) and see if that reports any problems. If it doesn't, feel free to e-mail [email]support@linuxgamepublishing.com[/email] with your problem, along with the error message and the output of the LGP test tool and our support staff will help you further.

Cheers,
Eskild Hustvedt (Zero_Dogg)
Community manager, Linux Game Publishing

---

### Post by afrodeity on 2010-08-19
> **Zero_Dogg said:**
> Hi afrodeity,
could you check the permissions on ~/.lgp ? Make sure that all of the directories there are owned by your user and are writable. A "chown -R $USER ~/.lgp" followed by "chmod u+w -R ~/.lgp" should do it. Then try to run the game again.


Works like a charm, thank you Zero Dogg & rettichsnidi. Just one thing, I know my pulseaudio setup is a bit buggy, i probably need to reinstall the subsystem - but is there a way to run with alsa or sdl?

Game started but no sound, so I assume the game either uses pulse, or is not doing what its supposed to do?

I'll download the check tool to see if it reports anything.

BTW Survivor looks great

---

### Post by Zero_Dogg on 2010-08-19
Excellent, glad to hear it worked. 

Sadly pulseaudio redirects all access made directly to alsa to itself. The game should however work just fine with pulseaudio. If not, you may be able to work around the problem by starting the game under "pasuspender" (ie. pasuspender shadowgrounds), under "padsp" (ie. padsp shadowgrounds) or simply by killing off pulseaudio before starting the game.

Cheers,
Eskild Hustvedt (Zero_Dogg)
Community manager, Linux Game Publishing

---

### Post by naikon89 on 2010-08-19
Has Frozenbyte/LGP managed to purge the random crash bug from the Shadowgrounds games yet? Really good games, but the segmentation faults are a big, big, big minus.

---

