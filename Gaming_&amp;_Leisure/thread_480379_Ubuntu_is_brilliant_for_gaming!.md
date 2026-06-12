---
title: "Ubuntu is brilliant for gaming!"
date: 2007-06-21
forum: Gaming &amp; Leisure
---

### Post by janipewter on 2007-06-21
Being a Linux distro after all, I never believed Ubuntu would be any good for running Windows games. However, I couldn't have been more wrong.

A few friends and I decided to play Counter-Strike 1.6 in college today. Obviously as it is designed for Windows it installed fine on the XP machines, but I felt like a challenge - so I made a bet that I could install it on my Ubuntu machine and play with the rest of the group. 

Having never tried getting CS1.6 to work on Ubuntu before, that was quite a stupid decision. Needless to say it was incredibly easy - it installed under Wine seamlessly, and the only extra work I had to do to get it to run properly was install a truetype font which it required.

Within literally minutes I was in the server and playing with the rest of the group. Funnily enough, the game actually ran BETTER on the machine than it did on the Vista machines (my 50fps+ compared to the 20fps on the Vista box).

I never thought running games under Linux would be so easy. Good work guys, Ubuntu continues to be my favourite distro!

---

### Post by tgm4883 on 2007-06-21
While you thanks is appreciated, you may want to throw some of it over to the guys at [www.winehq.org](www.winehq.org).  They are the reason that you were able to do that so easily.  They rock.

---

### Post by a12ctic on 2007-06-21
HL is built on opengl and an iD engine, as well is HL2. Its not a suprize they work next to flawlessly in linux.

---

### Post by ubuntu27 on 2007-06-21
**janipewter** Good thing you were able to install CounterS on Ubuntu (i've never tried to use Wine).

How about giving a NATIVE Linux games a shot? ;)

There are some cool First Person Shooter games that are in the repository, those are:

- [Tremulous]("http://tremulous.net/"):  Found in Multiverse Repository

 - [OpenArena]("http://openarena.ws/"): Found in Universe repository 

- [Nexuiz:]("http://alientrap.org/nexuiz/") Found in Universe Repository 

- [AssaultCube]("http://assault.cubers.net/"): NOT found in the repository, it can be installed from source or from [GetDeb.com]("http://www.getdeb.net/app.php?name=AssaultCube")

---

### Post by tolstoybikeboy on 2007-06-21
Nexuiz...i can't install it...i find it in the repository list..however..when i select install..i get the error that the manager can't find the files...they can't be downloaded....is there an updated apt list for this?

---

### Post by charlieg on 2007-06-21
Probably a more topical game for this thread is [True Combat: Elite]("http://www.truecombatelite.net/"), a mod of  [Enemy Territory](http://enemy-territory.4players.de:1041/), both of which are available natively on Linux.

---

### Post by ubuntu27 on 2007-06-21
> **tolstoybikeboy said:**
> Nexuiz...i can't install it...i find it in the repository list..however..when i select install..i get the error that the manager can't find the files...they can't be downloaded....is there an updated apt list for this?

What happens if you try to install using the terminal?

Open the Terminal (Applications/Accessories/Terminal) 

and type the following

```
sudo aptitude update
```  press Enter in your keyboard, and type your password.

```
sudo aptitude install nexuiz
```

Copy and Paste the Output of the terminal here.

---

### Post by Thomas Jensen on 2007-06-21
I recommend everyone to try [Sauerbraten]("http://sauerbraten.org/") (it says "game engine" on the front page but it's actually a complete game). It features **very** fast FPS gameplay and still manages to run smoothly on low-end machines.

Also it has this interesting multiplayer game mode called "coop-edit" where every player can edit the map while they are playing on it together. It's great if you like to collaborate with other people on making stuff.

---

### Post by Mizarus on 2007-06-22
that thread for some reason made me remind of my old voodoo 3, iam still waiting for the opengl coming back form the ashes

---

### Post by lordhebe on 2007-06-22
> **a12ctic said:**
> HL is built on opengl and an iD engine, as well is HL2. Its not a suprize they work next to flawlessly in linux.

I know HL is based on OpenGL, but I though HL2 was based on DX

---

### Post by adityakavoor on 2007-06-22
i have installed CS 1.6 though wine .. how can I run the game ??

---

### Post by Silenus on 2007-06-22
Could  you post directions on what you did to get it working under wine, I was a big steam fan on windows, but have failed to get 1.6 to work under any linux distro.

---

### Post by adityakavoor on 2007-06-22
Installing was not a problem

installing wine 
```
sudo apt-get install wine
```

installing CSS
```
wine /media/cdrom0/csssetup.exe
```


dunno what to do next to get the game running :(

---

### Post by cisforcojo on 2007-06-24
Sometimes WINE adds applications to Applications-> Wine -> Programs -> ...

but if you can't find it there,

cd /home/username/.wine/drive_c/Program\ Files/

then 'cd' to where you installed it (assuming you installed it to this path). you should be able to find the executable and then

wine ./*****.exe


NOTE:

I noticed you haven't yet run winecfg

I strongly recommend typing 'winecfg' in a terminal and configuring wine first. Just a suggestion.

---

### Post by Enverex on 2007-06-24
> **cisforcojo said:**
> Sometimes WINE adds applications to Applications-> Wine -> Programs -> ...

but if you can't find it there,

cd /home/username/.wine/drive_c/Program\ Files/

then 'cd' to where you installed it (assuming you installed it to this path). you should be able to find the executable and then

wine ./*****.exe


NOTE:

I noticed you haven't yet run winecfg

I strongly recommend typing 'winecfg' in a terminal and configuring wine first. Just a suggestion.

If it doesn't make a menu shortcut try running "wineboot" in the terminal. Also, don't run things with ./ using Wine, just "wine Blah.exe" should be used.

> **a12ctic said:**
> HL is built on opengl and an iD engine, as well is HL2. Its not a suprize they work next to flawlessly in linux.

> **lordhebe said:**
> I know HL is based on OpenGL, but I though HL2 was based on DX

What Hebe said, NEITHER of the games are based on ID engines. Half-Life one did have an OpenGL engine but it works fine in Direct3D mode or OpenGL mode. Half-Life 2 is a lot more complicated however due to using lots of advanced DirectX 9 features.

---

### Post by noerrorsfound on 2007-06-24
> **Enverex said:**
> What Hebe said, NEITHER of the games are based on ID engines. Half-Life one did have an OpenGL engine but it works fine in Direct3D mode or OpenGL mode. Half-Life 2 is a lot more complicated however due to using lots of advanced DirectX 9 features.
Half-Life 1 is powered by the GoldSrc engine which is a modified Quake 1 engine.
[http://en.wikipedia.org/wiki/Half-Life](http://en.wikipedia.org/wiki/Half-Life)
[http://en.wikipedia.org/wiki/GoldSrc](http://en.wikipedia.org/wiki/GoldSrc)

---

### Post by Enverex on 2007-06-24
Half-Life one I can imagine but not an unmodified engine as you pointed out (it did allow for Direct3D, Software and OpenGL renderers). Half-Life 2 on the other hand was alot more restrictive, i.e. one renderer.

---

### Post by wana10 on 2007-06-24
for me, both css and cs1.6 were easy to get running, no problems for either.
first of course you have to get wine. then go find tahoma.ttf and place it in /home/*username*/.wine/drive_c/windows/fonts/. now gow get the steam install package from steams website, which comes in .msi form. cd to the directory where you downloaded the msi and run 'msiexec /i steam.msi'. if i remember correctly i had an error returned here because of a missing package but a quick apt0get will take care of that. once steam is installed wine should place an icon for it on your desktop and in the wine programs folder in your applications menu. now run steam, log-in, and go to the my games tab. as i had run these programs in windows before they were greyed out under the not-installed header. double click the program you want, in my case css and cs1.6, and then wait while they install themselves. after installing they should appear in white under the installed header. double click to run and enjoy. 
using the steps above i can play both games with no graphical hang-ups or glitches and full sound.

---

### Post by adityakavoor on 2007-06-24
> **wana10 said:**
> for me, both css and cs1.6 were easy to get running, no problems for either.
first of course you have to get wine. then go find tahoma.ttf and place it in /home/*username*/.wine/drive_c/windows/fonts/. now gow get the steam install package from steams website, which comes in .msi form. cd to the directory where you downloaded the msi and run 'msiexec /i steam.msi'. if i remember correctly i had an error returned here because of a missing package but a quick apt0get will take care of that. once steam is installed wine should place an icon for it on your desktop and in the wine programs folder in your applications menu. now run steam, log-in, and go to the my games tab. as i had run these programs in windows before they were greyed out under the not-installed header. double click the program you want, in my case css and cs1.6, and then wait while they install themselves. after installing they should appear in white under the installed header. double click to run and enjoy. 
using the steps above i can play both games with no graphical hang-ups or glitches and full sound.

I can find Counter Strike under the Installed tab (in white) . When I double click to run it ... it takes me to the store .. Cant get the game running :( :(

---

### Post by Motoxrdude on 2007-06-25
> **adityakavoor said:**
> I can find Counter Strike under the Installed tab (in white) . When I double click to run it ... it takes me to the store .. Cant get the game running :( :(

Have you actually bought the game?

---

### Post by barmazal on 2007-06-25
> **janipewter said:**
> 

Within literally minutes I was in the server and playing with the rest of the group. Funnily enough, the game actually ran BETTER on the machine than it did on the Vista machines (my 50fps+ compared to the 20fps on the Vista box).

I never thought running games under Linux would be so easy. Good work guys, Ubuntu continues to be my favourite distro!


try to run other games, 80% of them won't work 

as for Vista, it's written on plain English what system requirements are if you have low FPS then you not met with requirements

---

### Post by adityakavoor on 2007-06-26
> **Motoxrdude said:**
> Have you actually bought the game?

Yes I have

---

### Post by Sockerdrickan on 2007-06-27
HL2 is not OpenGL it's DirectX

---

