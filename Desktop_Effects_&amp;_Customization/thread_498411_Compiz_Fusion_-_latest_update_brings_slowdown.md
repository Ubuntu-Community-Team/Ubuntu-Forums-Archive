---
title: "Compiz Fusion - latest update brings slowdown"
date: 2007-07-11
forum: Desktop Effects &amp; Customization
---

### Post by hyperair on 2007-07-11
I wonder if I'm the only one who has this problem, but after the most recent update from Trevino's repository (git: 20070707) I've been experiencing a slowdown in my Expo and Rotate Cube plugins. When I use them, they appear choppy, where they never did before.

---

### Post by ikkefc3 on 2007-07-11
> **hyperair said:**
> I wonder if I'm the only one who has this problem, but after the most recent update from Trevino's repository (git: 20070707) I've been experiencing a slowdown in my Expo and Rotate Cube plugins. When I use them, they appear choppy, where they never did before.

I had the same problem, until I set my refresh rate to 75 in General Settings of CCSM (compizconfig settings manager).

---

### Post by hyperair on 2007-07-12
I tried that, and enabled Sync to VBlank, but after that everything lagged. As opposed to this (FPS: 200, Sync to VBlank disabled), where only the Cube Rotation and Expo lagged.

---

### Post by FoolsGold_MKII on 2007-07-12
Yeah, same problem.

This happens from time to time. When I first was using Compiz Fusion the latest build was kinda slow, but the update immediately after sped things up. Then an update slowed it down again, then it sped up in another update.

The most recent update slowed things down. It's as if... it's in development still. :)

---

### Post by ikkefc3 on 2007-07-12
> **hyperair said:**
> I tried that, and enabled Sync to VBlank, but after that everything lagged. As opposed to this (FPS: 200, Sync to VBlank disabled), where only the Cube Rotation and Expo lagged.

SET YOUR REFRESH RATE TO 75, NOT 200!

---

### Post by hyperair on 2007-07-12
Well, I just set it to 75 and now everything's laggy. How about that huh. I think I preferred the condition where only the cube and expo lagged.

EDIT: I just updated again, and now it's even worse. My CPU goes up to 100% and there are artifacts on the right side of my screen.

EDIT: I restarted my X server and it's back to normal. Lags for rotating the cube and expo.

---

### Post by skypa on 2007-07-14
Yeah, I suffer from the same symtomps since I upgraded to newer packages a couple of days ago. Everything is smooth apart from Cube rotation and Expo. 

GF4 TI with Ubuntu drivers and latest Compiz Fusion packages.
Let's hope a future update will fix that. :)

---

### Post by hyperair on 2007-07-15
Good to hear I wasn't the only one. The latest update from Trevino's repository fixed that, so performance is top class again, but screwed up a whole lot of other plugins.. something to do with version mismatches. When I updated to this repository's debs:
```

deb http://debs.vorian.org/ feisty extras
deb-src http://debs.vorian.org/ feisty extras

```
everything worked fine again =)

---

### Post by sagara on 2007-07-17
> **hyperair said:**
> Good to hear I wasn't the only one. The latest update from Trevino's repository fixed that, so performance is top class again, but screwed up a whole lot of other plugins.. something to do with version mismatches. When I updated to this repository's debs:
```

deb http://debs.vorian.org/ feisty extras
deb-src http://debs.vorian.org/ feisty extras

```
everything worked fine again =)

what key do I need to install for this repository?

---

### Post by crazyhunk on 2007-07-17
> **sagara said:**
> what key do I need to install for this repository?

here is the key...

```
gpg --keyserver subkeys.pgp.net --recv-keys E504A4BB

gpg --export --armor E504A4BB | sudo apt-key add -
```

and vorian's page...

[http://vorian.org/?p=82](http://vorian.org/?p=82)

---

### Post by hyperair on 2007-07-17
You could actually just go to [http://debs.vorian.org](http://debs.vorian.org) on your web browser and download the GPG key there. Then import it in Software Sources =P. That's what I do. Usually they'll have a page telling you what key you need to authenticate the repository.

---

### Post by sagara on 2007-07-17
> **hyperair said:**
> Good to hear I wasn't the only one. The latest update from Trevino's repository fixed that, so performance is top class again, but screwed up a whole lot of other plugins.. something to do with version mismatches. When I updated to this repository's debs:
```

deb http://debs.vorian.org/ feisty extras
deb-src http://debs.vorian.org/ feisty extras

```
everything worked fine again =)

I upgraded from this repository but I still have the same problem.  Compiz Fusion is still a resource hog unlike beryl  (back when I had edgy).

I still haven't noticed any plugins break.

Any ideas why this CPU issue?

---

### Post by SkiesOfAzel on 2007-07-17
You don't just have to update, you have to completely remove compiz-fusion , disable trevino's repo, update your sources and reinstall compiz fusion.

---

### Post by sagara on 2007-07-17
Just followed your advice... I still have the high CPU usage... I do feel, compiz is somehow more responsive now...

---

### Post by SkiesOfAzel on 2007-07-17
what is your video card and drivers sagara-kun ?

---

### Post by sagara on 2007-07-18
BFG NVIDIA Geforce 6800 256MB
Drivers: 100.14.11

---

### Post by hyperair on 2007-07-18
Hmm there's no reason Compiz should take up too much CPU, considering it runs rather smoothly on my nVidia GeForce 4 MX 440 with 96.31 drivers.

---

### Post by SkiesOfAzel on 2007-07-18
Maybe it has somethings to do with the drivers, i use version 97.55 from the ubuntu repos (nvidia-glx-new) cause when i use different kernel modules, ctrl+alt+backspace doesn't restart my x server. It's just an educated guess though ... Anyway, although i don't have high cpu usage, i do have memory leaks . Compiz.real occupies 50 mb's of memory after one day of use.

---

### Post by hyperair on 2007-07-18
50MB... Mine's at 55MB now. Does that count? I don't really mind, my memory usage is usually so little that I can open VirtualBox with 512MB RAM. I've got 1280MB RAM (1024+256). I don't really notice anything taking up RAM more than usual, except when it exceeds 100MB. Just to test, I've restarted Compiz Fusion, and it begins with 30-33MB of RAM. If after a day's usage it reaches 50, then I doubt it's really serious, though any memory leak is worth checking xD

My high CPU usage is not of Compiz, if present, but more of Xorg. If Compiz Fusion behaves sluggishly, it's Xorg eating up the CPU, not compiz.real.

Also, the Ctrl+Alt+Backspace isn't really a driver thing, it's more of a X server thing. Look for a line in your xorg.conf... ```
Option "DontZap" "true"
```
If that line is present, then the X server will not respond to Ctrl + Alt + Backspace.

---

### Post by SkiesOfAzel on 2007-07-18
Actually compiz fusion should use ~15 mb of ram and thats how much it used since before the latest updates. 
As for the x server thingy , the shortcut worked, the problem was that the xserver would stop but not restart, i had to go to another console and restart it manually.

---

### Post by hyperair on 2007-07-18
I see. So it just stops and leaves a black screen? Anyway I've encountered the bug with the rotating cube and expo again, as my first post had said. pffffft.

EDIT: Whoops, not Compiz Fusion's fault. I recently added the angles and the icon offset to my avant window navigator. It seems that it's AWN which is taking up more CPU, not Compiz Fusion.

---

### Post by BOBSONATOR on 2007-07-18
The latest fusion update took away my borders. emerald --replace, compiz --replace and compiz --replace -c emerald & Dont work.

---

### Post by hyperair on 2007-07-18
So you're saying that the latest update took away your borders, but Compiz Fusion runs? Could you post the output? Anyway you could always wait a few more days til the next update or... reinstall
```

sudo apt-get autoremove --purge "compiz*" desktop-effects emerald
sudo apt-get install desktop-effects compiz "compiz-fusion*" desktop-effects emerald

```

---

### Post by skypa on 2007-07-18
Latest Compiz Fusion updates made things a little more smooth, cube rotation and expose still is quite choppy though. Both effects produce CPU spikes, unlike scale or window animations.
Compiz Fusion is still in an early stage so I`m patient, but I hope the two mentioned effects get a little less CPU hungry in the future.

Feisty, NVIDIA GF4, repo binary drivers (maybe I should use the original nvidia ones again?!)

---

### Post by sagara on 2007-07-18
> **hyperair said:**
> Hmm there's no reason Compiz should take up too much CPU, considering it runs rather smoothly on my nVidia GeForce 4 MX 440 with 96.31 drivers.

How can I downgrade to your NVIDIA driver?  I will like to see if that solves my issue.

---

### Post by marsmissionaries on 2007-07-18
disabling transparency on the cube makes the lag stop for me. i think this is an issue with the way compiz handles transparency.

---

### Post by hyperair on 2007-07-19
@marsmissionaries: My cube is only transparent for mouse rotate, so there shouldnt be any lag during the normal rotation (mousewheel or Ctrl+Alt)

@sagara: Are you using nVidia's driver from their web site? Or the repository ones?

---

### Post by johto on 2007-07-19
In my case compiz because fast again (500-600 fps) using --loose-binding

---

### Post by sagara on 2007-07-19
> **hyperair said:**
> @marsmissionaries: My cube is only transparent for mouse rotate, so there shouldnt be any lag during the normal rotation (mousewheel or Ctrl+Alt)

@sagara: Are you using nVidia's driver from their web site? Or the repository ones?

I'm actually using ENVY to install my NVidia drivers.

---

### Post by skypa on 2007-07-30
> **johto said:**
> In my case compiz because fast again (500-600 fps) using --loose-binding
Pure sweetness! Out of all tips, this actually did it. Full performance again. Thanks very much. :)

---

### Post by Tierman on 2007-12-10
Hi.

When I updated, the problem I had with compiz to start off with is that wobbly windows and other desktop rendering options, like the cube, just stopped working. I tried to run the CCSM, but it crashed each time. 

So I reset and reloaded everything. Now not only does CCSM not work, but the system is still choppy. I mentioned this because somewhere earlier it was stated that the problem could possibly be resolved by changing the refresh rate. I would try it, but unfortunately I can't get to it :(

Here's to hoping the next upgrade solves the problem, and glad to hear that it's not just my computer that's affected.

---

### Post by hyperair on 2007-12-10
Firstly what distro release are you using? Feisty/Gutsy/Hardy?
Secondly what method of installation of Compiz Fusion are you using?
Thirdly what repository do you use, if you use one?
Fourthly, what is your GPU?

---

### Post by Tierman on 2007-12-10
Firstly what distro release are you using? Feisty/Gutsy/Hardy?

Running 7.10 Gutsy with minor Distro upgrades.

Secondly what method of installation of Compiz Fusion are you using?

It was installed as standard, apart from CCSM, it came off the disk and worked.

Thirdly what repository do you use, if you use one?

Main/Universe/Restricted/Multiverse and Gutsy Partner along with all Updates/Security/proposed/Backports

Fourthly, what is your GPU?

erm... Intel - Experimental Modsetting whatsit.

---

