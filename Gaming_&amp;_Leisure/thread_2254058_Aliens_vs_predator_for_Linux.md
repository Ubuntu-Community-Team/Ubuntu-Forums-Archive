---
title: "Aliens vs predator for Linux"
date: 2014-11-24
forum: Gaming &amp; Leisure
---

### Post by mateo14 on 2014-11-24
Hi

Many years ago, I used AvP: Gold Edition to run this game on Linux. Recently I decided to use AVP from GOG, and I don't know which version for Linux I should use to run this game.
There are three versions:

[https://github.com/mbait/avpmp](https://github.com/mbait/avpmp)

I think that is the old version from icculus.org because the multiplayer mode was not finished in the Linux version of AvP.

I noticed that newer version of AvP exists, but the author decided to stop working on it:

[https://www.assembla.com/code/avp_source_code_mod/git/nodes](https://www.assembla.com/code/avp_source_code_mod/git/nodes)

"Since fastfile support was removed all *.ffl needs to be extracted
with extract_ffl found in the util directory.

cd fastfile/ && for i in *.ffl; do extract_ffl "${i}" ../; done

All *.rim files need to be converted to png.

find /home/some_user/avp_data/graphics/ -name "*.rim" \
-execdir /home/some_user/avp_src/util/rim_utils/rim2png {} \;

The root directory should atleast contain

avp_huds avp_rifs fastfile graphics sound

and directory fastfile need only to contain

aliensound.dat marsound.dat predsound.dat queensound.dat

Everything needs to be in lowercase; run this from root of the game content.
You will need write access to files and directories for this to work

find . -depth -execdir perl -e "rename('{}',lc('{}'))" \;

In order to build one would need libpng, SDL, OpenAL, OpenGL, and OpenSSL(for md5).

[email]daniel.langnas@gmail.com[/email]"

This Instruction is quite confusing, but the list of changes is long:

[https://www.assembla.com/code/avp_so...commits/master](https://www.assembla.com/code/avp_so...commits/master)

The last project is similar to the previous one, but script: extract.sh doesn't work correctly because I noticed many errors.

[https://www.assembla.com/code/avp_mod/git/nodes](https://www.assembla.com/code/avp_mod/git/nodes)

The list of changes:

[https://www.assembla.com/code/avp_mo...commits/master](https://www.assembla.com/code/avp_mo...commits/master)

"Game data files need to extracted and in some cases converted to open formats.


To do this, run extract.sh in the directory avp_mod.


This is work in progress

[email]daniel.langnas@gmail.com[/email]


Current status

Npc marine, mostly done.
Npc predator, not done.
Npc xenoborg, unknown status.
No multiplayer.
No ingame movies.
Player hud bounding box, missing.
Player predator hud, is not done.
Menus are text only.
Basic console."

I ignored these errors, and I typed a command make in the terminal to finish the installation process. Unfortunately, I noticed that the
background in the menu of the game is in a black color. In AvP: Gold Edition this problem didn't exist, and I'm pretty sure that I didn't install this game in a correct way.

I'm wondering which version of AvP for Linux did you use to run this game? I know that AvP was an unpopular game among Linux users. Now more people have access to the version of AvP from GOG, but I did not find any active projects for Linux.

---

### Post by R33D3M33R on 2014-11-25
I'm using AvP with Wine and it works great.

---

### Post by mateo14 on 2014-11-25
> **R33D3M33R said:**
> I'm using AvP with Wine and it works great.

Thanks for the answer.

Unfortunately, I do not plan to run a Windows version of this game under Wine because a Linux version exists for this operating system.


I have to admit that is a really depressing fact that the open source project like AvP has so many shortcomings on the open source operating systems like Linux and Aros

[http://arosgamer.blogspot.co.uk/2012/06/alien-vs-predator-old-acid-still-burns.html](http://arosgamer.blogspot.co.uk/2012/06/alien-vs-predator-old-acid-still-burns.html)

I noticed that some people made many efforts to create a better version of this games for commercial operating systems like Windows or MorphOS: 

"On top of just getting it running I felt that it needed some additional polish which I implemented:


- MUI dialog and installer for when you dont have the data files in the game drawer.
- FMV playback (intros + ingame video screens)
- Music
- Changed the default keybindings to be similar to modern FPS games.
- Volume sliders in the menu screen had an annoying 1sec delay before being modified. Removed it.
- Fixed some menu strings (for example, "exit to windows" became "exit to morphos")
- Made a new graphics options menu screen for setting resolution, mipmap on/off, 16/32bit textures, fullscreen/windowed.
(original game had just the option to set resolution)
- Some initial work to get "Classic Redux" high-res mod working. This makes the game look so much better but it eats a lot
of VRAM so I made a texture size limit and rescale option to get it running on my 32MB graphics card.
(I still need to expose this option to a menu, and fix a crash bug related to this mod - that crash exists on the PC version of Gold Edition as well)"

[http://morph.zone/modules/newbb_plus/viewtopic.php?topic_id=9614&forum=10](http://morph.zone/modules/newbb_plus/viewtopic.php?topic_id=9614&forum=10)

---

### Post by mastablasta on 2014-11-25
obviously it is not made for your version of Linux and since is not maintained it is up to the user to find the correct dependencies if at all possible. just like some windows 98 games or DOS games do not work in latest windows without 3rd party support.

---

### Post by mateo14 on 2014-12-01
I don't know if it will be an interesting information, but I contacted with the authors of AvP for Linux/MorphOS. You can see this topic on phoronix.com in the game section of the forum, and I think that still might be a chance to run an improved version of AVP on Linux in the future.

---

### Post by mateo14 on 2014-12-25
I just want to inform that a new version of Alien vs. Predator was released for Linux and OS X:


[http://icculus.org/avp/](http://icculus.org/avp/)

---

### Post by CitadelUniversal on 2014-12-26
What about the Linux Installers for linux games website it has an installer for Avp 1 here [http://www.liflg.org/?catid=7](http://www.liflg.org/?catid=7)  - I haven't tried it though since it's beta....

---

### Post by mateo14 on 2014-12-26
> **CitadelUniversal said:**
> What about the Linux Installers for linux games website it has an installer for Avp 1 here [http://www.liflg.org/?catid=7](http://www.liflg.org/?catid=7)  - I haven't tried it though since it's beta....

The installer from this website includes a very old version of AvP from 2009. I don't know if they will do a new installer for this new version of AvP which was published two days ago.

The new version of AvP can be compiled on Linux x86_64, and they added support for SDL 2. The author did not publish a changelog, so It is really hard to find specific changes.

---

### Post by Sasha_Aderolop on 2014-12-27
No problem with AvP and Wine.

---

### Post by mateo14 on 2015-02-14
[FONT=Helvetica Neue]Hi[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue]AnonymousHoser published a new version of Aliens vs Predator, and I think that experimental support for AvP Classic Redux is the most interesting feature in this version of AvP:[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue][https://www.youtube.com/watch?v=fNSvDj9rDTo#t=202](https://www.youtube.com/watch?v=fNSvDj9rDTo#t=202)[/FONT]
[FONT=Helvetica Neue]
[/FONT]
[FONT=Helvetica Neue][FONT=Helvetica]"Some work was done on the SDL2 support, namely the full screen support. There's still a lot more work required before it is stable though. Once that happens I plan on removing the SDL 1.2 support.[/FONT][/FONT]
[FONT=Helvetica]The OpenGL code has been changed to be compatible with OpenGL ES 1.0. The next release will require OpenGL 2.1 or OpenGL ES 2.0.[/FONT]
[FONT=Helvetica]AvP Classic Redux was briefly tested. One possible crash was fixed -- the original game was never intended to use such large assets, but there are likely other crashes out there."[/FONT]
[FONT=Helvetica]
[/FONT]
[FONT=Helvetica][http://community.ioquake.org/t/new-release-20150214/435](http://community.ioquake.org/t/new-release-20150214/435)[/FONT]

---

