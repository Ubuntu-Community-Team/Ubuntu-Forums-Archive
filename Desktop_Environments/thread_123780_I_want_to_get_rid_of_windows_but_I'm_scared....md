---
title: "I want to get rid of windows but I'm scared..."
date: 2006-01-30
forum: Desktop Environments
---

### Post by catalytic on 2006-01-30
Windows is pretty much unrepairable, and I'm not going to buy a copy to re install myself. So I am running Ubuntu, but there are some things that it just can't do, or I'm not sure how to do.

It's been a month now, and I'm only slightly better at using this new OS.
I have not been able to successfully run any of my pre installed windows games, even after searching FAQ's and copying the file to my Ubuntu partition.

I notice that there is a lot of open source games, yet most of them you still need the install CD! Where do you buy Linux games???
I have tried installing, Doom, Quake, Enemy Territory, WoW none of them will work.
Enemy Territory will load, but lags so much that it is not playable, I can't even set it up to play a game.

Everything seems slower, programs take a long time to start, if they start at all.

I'm happy to go and buy games such as Neverwinter Nights but where in Australia can I get such games?
I thought that all Ubuntu programs were free? I know there are shareware versions of Doom, but all the ones I have installed won't work.

I download and extract the tar files, I click on the game icon and nothing, I try running it through terminal, nothing. Doom is in my applications menu, the start page comes up and then goes away, the game just wont run.

Please someone give me some advice on what I can do here :( 

Until I can at least play Doom or Quake online, and actually get Ubuntu to run faster without to many errors, I don't want to delete windows.

Also on start up I notice that mounting hardrives fails. I can access these NFTS files fine as long as I am in root. Infact I deleted my user account and now do everything in root. Is this ok?

I would like to just put everything on the one files system so I can read write, but not sure how to go about this. There isn't much on here that I'm worried about loosing everything is backed up apart from Windows.

So what should I do?

Would I just run the Ubuntu installation cd over the top of the whole hard drive?

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=catalytic]Windows is pretty much unrepairable, and I'm not going to buy a copy to re install myself. So I am running Ubuntu, but there are some things that it just can't do, or I'm not sure how to do.

It's been a month now, and I'm only slightly better at using this new OS.
I have not been able to successfully run any of my pre installed windows games, even after searching FAQ's and copying the file to my Ubuntu partition.

I notice that there is a lot of open source games, yet most of them you still need the install CD! Where do you buy Linux games???
I have tried installing, Doom, Quake, Enemy Territory, WoW none of them will work.
Enemy Territory will load, but lags so much that it is not playable, I can't even set it up to play a game.

Everything seems slower, programs take a long time to start, if they start at all.

I'm happy to go and buy games such as Neverwinter Nights but where in Australia can I get such games?
I thought that all Ubuntu programs were free? I know there are shareware versions of Doom, but all the ones I have installed won't work.

I download and extract the tar files, I click on the game icon and nothing, I try running it through terminal, nothing. Doom is in my applications menu, the start page comes up and then goes away, the game just wont run.

Please someone give me some advice on what I can do here :( 

Until I can at least play Doom or Quake online, and actually get Ubuntu to run faster without to many errors, I don't want to delete windows.

Also on start up I notice that mounting hardrives fails. I can access these NFTS files fine as long as I am in root. Infact I deleted my user account and now do everything in root. Is this ok?

I would like to just put everything on the one files system so I can read write, but not sure how to go about this. There isn't much on here that I'm worried about loosing everything is backed up apart from Windows.

So what should I do?

Would I just run the Ubuntu installation cd over the top of the whole hard drive?[/QUOTE]
Well, there is an Ubuntu gaming sub-forum that can help you out with respect to games.  Basically, for anything 3D, you are going to want to make sure you get your hardware acceleration working.  That will depend on your video card.  There are lots of other free games you can get just by opening up the synaptic package manager and filtering on the "Games and Amusement" section in the left pane.

I also like to go to [http://www.happypenguin.org/]("http://www.happypenguin.org/") as this is a great spot to find out about new games for Linux.  Lots of times, the games will be in one of the repositories so you can just use synaptic to get them.  Other times, the author's home page will provide a binary you can just download and run or a .deb for Ubuntu you can install with dpkg.

Sometimes, you have to install from source.  Since a lot of games use SDL these days, that has become a lot easier.  Ubuntu comes with SDL (Simple Direct Media Layer) installed, but you probably need to get the matching "libsdl*-dev" package from synaptic in order to compile.  You will also need the "build-essential" package.  Here is a good link on how to install all sorts of software:
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

The folks in the gaming forum can probably help you out with questions about specific games.

---

### Post by catalytic on 2006-01-31
This is what I get when I try to run quake2

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
using /root/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx

How do I fix this? I have also downloaded the source code but I don't understand how to get it to work.

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=catalytic]This is what I get when I try to run quake2

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
using /root/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx

How do I fix this? I have also downloaded the source code but I don't understand how to get it to work.[/QUOTE]

Not really sure-- looks like you have some issue with the sound device (/dev/dsp).  Also, I don't think you should be running the game as root.  You normally shouldn't have to be root to play a game.

If you like FPS games, I'd recommend Nexuiz [http://www.nexuiz.com/index.php?module=info]("http://www.nexuiz.com/index.php?module=info")
It is pretty decent, and they supply a pre-compiled binary that you can just untar and play.

---

