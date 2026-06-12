---
title: "Graphics problem: getting SDLMame cofigured and running properly"
date: 2008-11-30
forum: Gaming &amp; Leisure
---

### Post by jukingeo on 2008-11-30
Hello all, 

I have downloaded SDLMame from the Ubuntu Synaptic repository.  It is version 0.123.

I am intending to use WahCade as my front end as I been happy with the creator's MameWah front end when using Mame under Windows.  

However I was told to first get SDLMame running via the terminal before even attempting to run it with a front end.  So the first step was to find the proper directory and put some roms in it.  This itself proved to be a task in itself as I had to find out where the necessary folders and files are.  For some reason with SDLMame, nothing seems to be in the same place as with Mame emulators for Windows.

For one...the rom path.

It took me a day or so to find out that the rom path is:

/usr/local/share/games/sdlmame/roms

Then it took me another hour or so to find out that the configuration file for sdlmame is in yet another directory in a totally different location.

/etc/sdlmame/mame.ini

I made sure I had some roms in the previous directory and the latter directory was pointing to the previous directory I decided to give it a go.

So I launched the terminal and typed "mame pacman" and the program launched and ran!  However, the graphics are terrible and they seem to be set to the wrong resolution.  I am only seeing a part of the screen for the selected rom as well.  However, when punching in the controls, it does seem the game is operating.

All in all, I would like to know how to properly set up SDLMame so I can try to get it to work with my front end.

I would also like to know where all the necessary configuration files and directories are located since it does seem like SDLMame sprawls all the folders out all over the Ubuntu file system.

Versions:

Ubuntu Hardy (8.04)
SDLMame (0.123)

Thank You,

Geo

---

### Post by disturbedite on 2008-11-30
you could have answered all these questions yourself by doing two things:
1. looking at the installed files/paths in your package manager.
2. reading the sdlmame documentation that comes with sdlmame.
for more info, see the sdlmame forum:
[http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1](http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1)

---

### Post by jukingeo on 2008-11-30
> **disturbedite said:**
> you could have answered all these questions yourself by doing two things:
1. looking at the installed files/paths in your package manager.
2. reading the sdlmame documentation that comes with sdlmame.

Hmmm, that is easier said than done.  When I loaded up SDLMame, I was expecting a launch icon in the games section.  When I didn't get that, I found out later on that it was a command line launched program that is launched through the terminal and needed a front end.  Naturally by this state of the game, I couldn't even find the documentation to read it.

> for more info, see the sdlmame forum:
[http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1](http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=8&page=1)

Thanx, I will check it out.

Edit:

Dumb question:

Where is the search engine on that site?

Geo

---

### Post by jukingeo on 2008-11-30
Hello all,

Ok, I managed to find a solution to my problem.  Apparently SDLMame doesn't like the versions of the opengl driver that comes with Ubuntu, so this had to be changed.  In the mame.ini file under the graphics section, I changed the graphics from "opengl" to "soft" and that seems to have solved the problem and I can launch games now.

However, I will say that in comparison to the Windows version of Mame, Vector games such as Star Wars, Battle Zone, Lunar Lander, and Tempest look horrible.  The rendering is dark and blurry.  Anything that may improve the look of these games?

Other regular raster games such as Pac-man, Galaxian, etc are fine.

Geo

---

### Post by DoktorSeven on 2008-11-30
Play with the vector options in mame.ini (antialias, beam, flicker).

---

### Post by jukingeo on 2008-12-02
> **DoktorSeven said:**
> Play with the vector options in mame.ini (antialias, beam, flicker).


Hello Dok,

Yeah, I saw those files and did as you said, but I was just throwing arbitrary numbers in those spots and nothing seemed to improve the situation.  It got worse as I increased the numbers, but when I put them back to where they were, that seemed to be the best setting.  However, it is still pretty bad looking at those settings.

Setting the flicker to a higher number causes the screen to become brighter, but the vector renderings "flicker".  So I had to turn it back off.

I don't know if this is an SDL Mame issue or not considering it IS different from MAME32 (Under Windows).

Another thing I noticed is that the audio has a tendency to skip and stutter so often (and not only with vector games but raster games as well).   Most of the games I am playing are NOT memory intensive.  Just about all the games I play are from the early to mid 80's.  My machine is plenty powerful enough too.  I don't know if the SDLMame requirements are higher than for MAME32 though.

Thanx,
Geo

---

### Post by DoktorSeven on 2008-12-02
Yeah, it's not quite like plain MAME on Windows for some reason.  My config is to turn off flicker and antialias and turn the beam up to around 3 or so.  Some things (particularly the text) looks a little funny but the games are okay.

I'm sure your stuttering problems come from you using the soft driver, though; sdlmame is a lot slower when it has to use software rendering (I'm sure in Windows your MAME uses some form of hardware drawing).  Unless you don't have 3d drivers installed, not sure what the problem is there (and I hope it goes without saying that running games/emulators/etc in 3d while Compiz -- the 3d effects on your desktop -- is running is generally a bad idea).  I have no issues running sdlmame with an nvidia card running proper 3d drivers for it.

---

### Post by jukingeo on 2008-12-02
> **DoktorSeven said:**
> Yeah, it's not quite like plain MAME on Windows for some reason.  My config is to turn off flicker and antialias and turn the beam up to around 3 or so.  Some things (particularly the text) looks a little funny but the games are okay.

Using your settings as a guideline I played around with low numbers for both the antialias and the beam. I found that setting the antialias to 2 and the beam to 2.5 gave a decent balance between a clearer image with some brightness. It isn't perfect though, it is still not as clear or as bright as with Mame32 in Windows, BUT it is at least playable now.  Star Wars is still a bit blurry on the smaller letters.  Now Tempest, on the other hand improved dramatically with the 2, 2.5 setting.  It is ALMOST like that of Mame32.

> I'm sure your stuttering problems come from you using the soft driver, though; sdlmame is a lot slower when it has to use software rendering (I'm sure in Windows your MAME uses some form of hardware drawing). Unless you don't have 3d drivers installed, not sure what the problem is there (and I hope it goes without saying that running games/emulators/etc in 3d while Compiz -- the 3d effects on your desktop -- is running is generally a bad idea).  I have no issues running sdlmame with an nvidia card running proper 3d drivers for it.

I am running 3d accelerated drivers with my card...however, they are the drivers that are provided by Ubuntu and not ATI.  I have heard that the Linux drivers from ATI cause problems in Linux.  So I just enabled the 3D drivers that Ubuntu told me to use.  I just double checked just now and it IS enabled.

As for Compiz, I have no idea what that is, but I have heard of it many times here on-line.  In fact I have heard more bad things about it than good.  I think it is also a KDE thing, I have Gnome. So, I am pretty sure it is NOT on my machine.  As for the visual effects, I have turned those off a LONG time ago because they have caused many problems for me in Hardy.

I do admit that I did have better overall performance in Ubuntu when I had my Nvidia card installed. With the Nvidia card I was able to use the company's 3D drivers and I had very good performance.  However, the card was old and I needed to update it primarily for work (and games) that I still use in Windows XP.  However, there was an issue with power on my computer in that I don't have a huge power supply, so I couldn't go with one of those heavy duty video cards they have out today.  So I found a card by ATI that had twice the performance of my Nvidia card, but actually used LESS power.  But the ATI driver just doesn't work well in Ubuntu.

It could be my sound card too.  I am not using a Sound Blaster Live or built in audio, I have a professional sound card on my machine.  I don't have regular Ubuntu on my machine as I have Ubuntu Studio installed.  One of my reasons for moving to Linux was to see how it performs with audio creation and editing.  So I have a special multi-input/output card meant for audio recording work.  It could be that audio driver for that card may not like certain games.

Well, thanx for your help.  I guess I just have to live with it for now, unless something else comes up to improve my situation.

Geo

---

