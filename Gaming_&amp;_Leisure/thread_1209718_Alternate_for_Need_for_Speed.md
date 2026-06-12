---
title: "Alternate for Need for Speed"
date: 2009-07-10
forum: Gaming &amp; Leisure
---

### Post by Balvinder25 on 2009-07-10
Hi all,

I like to play Need for speed in windows but i've now completely shifted over to ubuntu , so whats the best alternate for this application .I have a 2 duo core processor with 2 gb ram and 160 hdd...Please advice

---

### Post by iheartubuntu on 2009-07-10
Frankly, Im not a fan of ANY of the car racing games available for Ubuntu.

The closest thing for racing fun IMO is Super Tux Kart. Its a bit childish though, similar to that Mario Kart game in Wii. But its still fun, especially if you have other people to play against. You can download it here... [http://www.getdeb.net/app/SuperTuxKart](http://www.getdeb.net/app/SuperTuxKart)

Right click onto the appropriate DEB file for your version of Ubuntu, download it and then click the deb file on your desktop to install it. Once installed, it should appear in your games section from the pulldown menu at the top left of your screen.

There are a few others in the Ubuntu repositories like Trigger and Torcs but I havent played them in a long time they sorta sucked. Im downloading them now and will let you know what I think of them.

---

### Post by Balvinder25 on 2009-07-10
thanks for the update..Will see how it works..

---

### Post by iheartubuntu on 2009-07-10
Trigger is like an off road style game and gets old quick. Torcs isnt bad, reminds me of the Porsche Need For Speed I used to have. You will need an nVidia graphics card to play it properly. At home I have ATI and it wont even play. Barely, there are strange shapes and boxes all around. With my nvidia here at work, the graphics are pretty good. Torcs doesnt seem to have any street racing though.

I might have to look further into Torcs... some screenshots dont look too bad and people create their own cars and tracks... check these links out...


Tracks...
[http://sites.google.com/site/torcscreations/tracks](http://sites.google.com/site/torcscreations/tracks)

Cars...
[http://sites.google.com/site/torcscreations/cars/supercars](http://sites.google.com/site/torcscreations/cars/supercars)

Looks like a lot of stuff and links all around the main torcs website..

[http://torcs.sourceforge.net/](http://torcs.sourceforge.net/)

---

### Post by iheartubuntu on 2009-07-10
Screenshots of the newest TORCS version...

[http://torcs.sourceforge.net/index.php?name=News&file=article&sid=66](http://torcs.sourceforge.net/index.php?name=News&file=article&sid=66)

---

### Post by Balvinder25 on 2009-07-10
they all look cool , but i think they wont work on my system as i have ATI aswell..but will test the tux games that you mentioned about..thanks aton ..

---

### Post by Col-1023 on 2009-07-11
Is TORCS specifically optimised for Nvidia cards, or is the ATI drivers that is the problem.

Once the open source Radeon drivers fully support 3D, will ATI cards work with TORCS?

---

### Post by iheartubuntu on 2009-07-11
> **Col-1023 said:**
> Is TORCS specifically optimised for Nvidia cards, or is the ATI drivers that is the problem.

Once the open source Radeon drivers fully support 3D, will ATI cards work with TORCS?

Not sure. I just tried Torcs here at home with my ATI vid card and it does work. Im running Jaunty so I dont have a lot of luck anymore with ATI cards. With 8.10 all my 3Dgames like Regnum and Torcs work great using "Envy NG" (google it) to install the ati drivers. Envy doesnt work with Jaunty I guess, so games like Regnum dont work at all. Im surprised Torcs works fine in Jaunty using my ATI card. Thats why I just ordered an nVidia card this morning :)

---

### Post by iheartubuntu on 2009-07-13
I just finished installing vDrift using an auto-package file. You can download the package file from here:

[http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=VDrift-2007-03-23-full-2.package&use_mirror=transact](http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=VDrift-2007-03-23-full-2.package&use_mirror=transact)

and to install it, use these instructions (pretty simple)...

[http://autopackage.org/docs/howto-install/?PHPSESSID=14446d06e10bcb25bd547de703774890](http://autopackage.org/docs/howto-install/?PHPSESSID=14446d06e10bcb25bd547de703774890)

Notice though, the game file is from 2007 and they have more current updates on the main vdrift website, although I cant figure out how to compile the newest vDrift source files.

The game is pretty cool for a free racing game I must say... Im curious how much nicer the newest version is compared to the 2007 autopackage version.

--------------------------------

Another pretty good racing game... similar to vDrift but even better physics and graphics would be the Live For Speed. There is no linux version, but the Windows version works great for me using Wine....

[http://www.lfs.net/](http://www.lfs.net/)

Its a game you have to pay for to unlock all the cars and tracks, but you are given a couple tracks and a couple cars to play around with for free. Check it out.

---

### Post by Ozor Mox on 2009-07-15
> **shirteesdotnet said:**
> I just finished installing vDrift using an auto-package file. You can download the package file from here:

[http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=VDrift-2007-03-23-full-2.package&use_mirror=transact](http://sourceforge.net/project/downloading.php?groupname=vdrift&filename=VDrift-2007-03-23-full-2.package&use_mirror=transact)

and to install it, use these instructions (pretty simple)...

[http://autopackage.org/docs/howto-install/?PHPSESSID=14446d06e10bcb25bd547de703774890](http://autopackage.org/docs/howto-install/?PHPSESSID=14446d06e10bcb25bd547de703774890)

Notice though, the game file is from 2007 and they have more current updates on the main vdrift website, although I cant figure out how to compile the newest vDrift source files.

The game is pretty cool for a free racing game I must say... Im curious how much nicer the newest version is compared to the 2007 autopackage version.

Yesterday I installed the newest version of VDrift (2009-06-15) and it is excellent. It now has vehicle collisions, more tracks and cars, and a very challenging AI.

It is dead easy to compile, have a look [here](http://wiki.vdrift.net/Compiling). Basically, you need to download the source, run the massive apt-get install command, untar the source, cd into the directory, then run:

```
scons
```

```
sudo scons install
```

That's it! Just run vdrift from a terminal, or create an application launcher.

---

### Post by iheartubuntu on 2009-07-16
> **Ozor Mox said:**
> Yesterday I installed the newest version of VDrift (2009-06-15) and it is excellent. It now has vehicle collisions, more tracks and cars, and a very challenging AI.

It is dead easy to compile, have a look [here](http://wiki.vdrift.net/Compiling). Basically, you need to download the source, run the massive apt-get install command, untar the source, cd into the directory, then run:

```
scons
```

```
sudo scons install
```

That's it! Just run vdrift from a terminal, or create an application launcher.

Thanks so much for the info... I will give it a try!

Im also having A LOT of fun with a game called "Live For Speed", but I'm running it under Wine. Works great though. Free demo with a few cars and couple of tracks.

[http://www.lfs.net/](http://www.lfs.net/)

You can unlock all cars and all tracks for a fee. It has multiplayer, excellent graphics (incredible),an awesome online forum where you can download free skins (artworks) for your car, etc. It also has real world physics, damage, tire temps, and the ability to fine tune your car before the race.

---

### Post by iheartubuntu on 2009-07-16
Thanks for the info on how to install VDrift. It worked!

I must admit, it is very similar to Live For Speed. Even the file types, folder structures within the game directory are all similar to LFS. I would give LFS a 9 out of 10 rating and VDrift, 6 out of 10. VDrift is FREE, while LFS is not (but has a free demo). 

I see quite a lot of similarities between the two... I dont know which game came first, I think VDrift did, but LFS must have more programmers (and paid ones) as the graphics are a couple notches better. Plus in LFS, when you get hit, your car shows damage, which I didnt see in VD. Theres just a lot more options to do in LFS.

I will keep playing both games and hope to contribute bug reports, and sign up to the forum on VDrift to hopefully better improve the game. It could be as good if not better than LFS if more people played and gave input. Thats one reason I play Regnum Online (free) instead of WoW. Regnum has come a LONG way in terms of graphics and playability.

---

### Post by Ozor Mox on 2009-07-16
Yeah, VDrift certainly still has a way to go, and they don't hide this fact on their website:

> This game is in the early stages of development but is already very playable.

Still though, it's nice to have another playable racing game on Ubuntu. I might give this Live For Speed game a go actually...

---

### Post by DigitalWolf333 on 2009-07-16
play need for speed on wine?

you might not be able to have all the graphics settings on that you used to have, but it should run fine 

i recently downloaded trackmainia using wine and it runs great, the only problem is that with the pc3 shader the car's culling seems to be reversed O_o...so i have a mostly invisible car with shadows :D. anyway i just play on pc2, can't have motion blur on pc2 though :(

i also had to follow a tutorial to get the sound working correctly, fortunately people test common games with wine and post tutorials on fixing problems :)


so you could give it a shot

---

### Post by iheartubuntu on 2009-07-16
Wolf, the game Im talking about is Live For Speed... its different than Need For Speed. I never could get my NFS games to work in Ubuntu... but LFS looks and works great if you have an nVidia card. I'm hooked!

Heck, now I'm using Blender to create beautiful renderings of my cars with my own skins! Looks nice!!!

Here is the Blender rendering HOWTO...

[http://www.lfsforum.net/showthread.php?t=34770](http://www.lfsforum.net/showthread.php?t=34770)

Here is an example of a rendering...

[IMG]http://img161.imageshack.us/img161/4066/lfsreadytorenderkitrendlf6.png[/IMG]


> **DigitalWolf333 said:**
> play need for speed on wine?

you might not be able to have all the graphics settings on that you used to have, but it should run fine 

i recently downloaded trackmainia using wine and it runs great, the only problem is that with the pc3 shader the car's culling seems to be reversed O_o...so i have a mostly invisible car with shadows :D. anyway i just play on pc2, can't have motion blur on pc2 though :(

i also had to follow a tutorial to get the sound working correctly, fortunately people test common games with wine and post tutorials on fixing problems :)


so you could give it a shot

---

### Post by iheartubuntu on 2009-07-16
Download the game from the LFS website [http://www.lfs.net/](http://www.lfs.net/) and make sure you have Wine already installed. An nVidia graphics card is probably a must have for this too. Run the install EXE file you downloaded and it will unpack everything onto your desktop (at least thats what it did for me). I put all of it in its own LFS folder. Then go into the folder and use Wine to run the LFS.exe file and it should load right up!

Check the LFS forums for free skins, how to install them, etc.

If any of you do get Live For Speed going, here is a video showing some gameplay and also how to do a pit stop...

[http://vimeo.com/2498762](http://vimeo.com/2498762)

---

### Post by DigitalWolf333 on 2009-07-16
pretty sweet, i could totally do better render set up though ;)

been using blender for years
------------------------------------
i don't see why nfs wouldn't work, 

[http://www.youtube.com/watch?v=VopBgQpjkYU](http://www.youtube.com/watch?v=VopBgQpjkYU)

that dude got it workin, 

its worth a shot atleast...

---

### Post by iheartubuntu on 2009-07-16
> **DigitalWolf333 said:**
> pretty sweet, i could totally do better render though ;)

been using blender for years
------------------------------------
i don't see why nfs wouldn't work, 

[http://www.youtube.com/watch?v=VopBgQpjkYU](http://www.youtube.com/watch?v=VopBgQpjkYU)

that dude got it workin, 

its worth a shot atleast...

HEY!Would you happen to know of any good Blender how-to or tutorial websites or blogs? I'd really like to learn it!

---

### Post by DigitalWolf333 on 2009-07-16
i'll pm you

---

### Post by iheartubuntu on 2009-07-16
> **DigitalWolf333 said:**
> i'll pm you

thanks so much!

---

### Post by DigitalWolf333 on 2009-07-16
np, nice screen savers btw, i especially like the cracked windows one :P

make a 3d one sometime :)

---

### Post by Samhain13 on 2009-07-20
> **shirteesdotnet said:**
> Blender how-to or tutorial websites or blogs? I'd really like to learn it!

I recommend:
[Blender Noob-To-Pro](http://en.wikibooks.org/wiki/Blender_3D:_Noob_to_Pro)
[Blender 3D Design Course](http://www.gryllus.net/Blender/3D.html)

 :D

---

### Post by Arthur_D on 2009-07-20
I've only seen 2 fun racers available for Linux, and that's SuperTuxKart (use the latest, 0.6.1a) and [Tile Racer.]("http://tileracer.model-view.com/tl/index.php/information.html")
Tile Racer is a quite mature freeware racer with an in-built editor and ghost driver. And it's good looking too! :D

---

### Post by Col-1023 on 2009-07-26
Tile Racer isn't in the repositories, is there a reason for that?

 I checked the website and the graphics look good for a game developed by just a few people.

---

### Post by Arthur_D on 2009-07-26
> **Col-1023 said:**
> Tile Racer isn't in the repositories, is there a reason for that?
AFAIK it's just a freeware game, and as such it might be under a non-permissive license. Haven't checked that much though.

---

### Post by Col-1023 on 2009-07-27
I checked the forum on their website and the developers have decided to keep the game CLOSED SOURCE for now, so I assume that's the reason for it not be included in the repos.

They are also using the physx SDK, so I don't know how this affect whether they can open the source.

---

