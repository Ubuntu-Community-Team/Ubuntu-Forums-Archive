---
title: "iPod"
date: 2005-12-13
forum: Desktop Environments
---

### Post by manofsteel on 2005-12-13
Hi I'm getting an iPod for chriistmas, and would really love to use it with Ubuntu, so here are my questions. 

1.How or what program do I use to get Ubuntu to see the iPod?

2.Do I need a different program to move music to it? 

3.Is there any program that lets me subscribe to Podcasts?

---

### Post by teaker1s on 2005-12-13
'gtkpod'
'ipod'
from repositories and installed with synaptic will allow you to manage your ipod
'iPodder'is a GUI-driven podcast receiver, allowing users to download
and listen to Internet audio programs.

---

### Post by JoshHendo on 2005-12-13
Thanks to Apple and the way they have designed their ipods, you probably won't be able to use it with ubuntu. You will require itunes, that you MAY be able to run via wine, though I don't think you will be able to. Unlike most mp3 players (Creative for example. I have a creative player and it works like a charm with ubuntu :)), you need a program to use ipods. Apple want you to use their OS. Get a mac if you are getting a ipod. Your best bet is with Wine and itunes, though knowing apple, it probably won't work =p

-edit-

Looks like someone posted some programs before me :). Hope that works. Just 1 tip, don't put any linux folders with the linux file system on the ipod. if it just for music, it should be fine :) (I killed my mp3 player doing that once, luckely it had a recovery mode which enabled me to sort out this problem).

---

### Post by Night on 2005-12-13
teaker1s is correct, works like a charm except for unmounting. Which leads me off to my tread jacking (its related), How do I unmount my iPod properly I keep getting a error message about how it cant unmount correctly.

---

### Post by arpunk on 2005-12-13
[QUOTE=JoshHendo]Thanks to Apple and the way they have designed their ipods, you probably won't be able to use it with ubuntu. You will require itunes, that you MAY be able to run via wine, though I don't think you will be able to. Unlike most mp3 players (Creative for example. I have a creative player and it works like a charm with ubuntu :)), you need a program to use ipods. Apple want you to use their OS. Get a mac if you are getting a ipod. Your best bet is with Wine and itunes, though knowing apple, it probably won't work =p

-edit-

Looks like someone posted some programs before me :). Hope that works. Just 1 tip, don't put any linux folders with the linux file system on the ipod. if it just for music, it should be fine :) (I killed my mp3 player doing that once, luckely it had a recovery mode which enabled me to sort out this problem).[/QUOTE]
There are linux programs that work very well with ipods... ive read that *banshee* has a nice ipod support.

---

### Post by manofsteel on 2005-12-13
Thanks for the reply guys, and yes how do we unmount the iPod correctly?

---

### Post by teaker1s on 2005-12-13
not sure about unmounting I have a mp3 player that is seen as a mass storage device and I can remove it without errors by unmounting or turning off.

I also have a creative DAP
(old as the ark but for a conservatory size isn't an issue) this uses gnomad.
 I'd suggest closing gtkpod and turning off when the player is idle if the new ones will, disconnecting when you are sure it's idle or contact gtkpod developers website for further help

---

### Post by teaker1s on 2005-12-13
[http://www.gtkpod.org/about.html](http://www.gtkpod.org/about.html)

good luck and welcome to the forums:KS

---

### Post by RAOF on 2005-12-13
You should be able to eject the ipod, in the same way as you eject a cd.  From a terminal, try "eject ipod" (or whatever your ipod gets called), and it should work.

---

### Post by manofsteel on 2005-12-13
thanks guys.

---

### Post by ossi on 2005-12-13
I use an ipod with video and Ubuntu. My ipod has never been used with itunes or os x and works without problems.

Currently there are severeal programs in backport who offer ipod support - more or less reliable. A candidate for good usability sure is Amarok - though it will use common libraries in version 1.4 set to release early 2006.

So what to do now? I can recomment gtkpod, which works for creating filestructures and transferring music absolutely fine and reliable. What I do currently (due to I am not to consistent with naming files) is gathering together the files in my music application (Amarok) and then drag the files in gtkpod. Even that works, though Amarok is basically a KDE application.

For podcasts there is Amarok. But there is a list for applications here:

[http://wiki.podcast.de/Podcatcher]("http://wiki.podcast.de/Podcatcher")

Gtkpod is working on art support currently. There has been a new version out (0.99) on Dec.12.
Look here:

[http://www.gtkpod.org/news.html]("http://www.gtkpod.org/news.html")

There is a support for Evolution and the ipod's calendar. But you can also simply copy the calender which is a hack - but very simple and it works like documented here:

[http://ubuntuforums.org/showthread.php?t=87414&highlight=ipod+evolution]("http://ubuntuforums.org/showthread.php?t=87414&highlight=ipod+evolution")


Alright, so finally video. There is something running on gtkpod. But this is not yet included in the program. You can find informations here:

[http://www.hermann-uwe.de/blog/initial-linux-support-for-the-5g-video-ipod-video-sync-using-gtkpod-libgpod]("http://www.hermann-uwe.de/blog/initial-linux-support-for-the-5g-video-ipod-video-sync-using-gtkpod-libgpod")

From what I know it is set to be included in the next release. As long as you're going for the "classic" ipod and just want to listen to music you will NOT face any problems. I do have experiences with an ipod shuffle. It worked too with gtkpod, but sometimes had slow transfer speeds - especially when transferring many files. 

So finally it is also reported that ipod nano is supported - I guess mini should not be a problem??? Anyone got experiences?

And there is also another application which I guess is quite cool called banshee. It is also meant to be a music-player software:

[http://patches.ximian.com/Main_Page]("http://patches.ximian.com/Main_Page")

Unmounting the ipod sometimes is a bit a problem. Just open the console and become root. Then type:

eject /dev/sd?

That works perfect for me, though I never had any problems when I unmounted the ipod through gnome desktop and then just pulled out the cable. But that's just not the way to do it. 
So that's it from me but there are sure other users who made experiences. greets

---

### Post by Night on 2005-12-13
```
eject: unable to eject, last error: Invalid argument
```

---

### Post by RAOF on 2005-12-13
If gnome comes up with an icon for your ipod on the desktop, you should be able to just right-click on it, and select "eject".  Or possibly "unmount".  That was certainly my Breezy experience (when ejecting my iPod would cause a kernel panic.  Now fixed in Dapper, and only seems to affect some AMD64-firewire users.  You're probably safe :))

---

### Post by WanderingStar on 2005-12-13
Well when I can actually get my iPod to mount (its 50/50) I can usually remove it by right clicking on the icon in "Computer" and choosing unmount.  If you get a pmount error it can usually be cleared by doing a 'sudo /etc/init.d/hotplug restart' in the terminal.  I think pmount gets out of sync with hotplug - but I have not really looked into it.

---

### Post by landotter on 2005-12-13
If it's not been bought yet, why get an iPod in the first place? Design wise--sure it's nice enough, but personally I wouldn't buy an digital player that didn't just mount as mass storage. Same goes for cameras. The fact that other players support more formats than the overy-hyped iPod is icing on the cake.

I'm not saying that iPods are bad, but there are better choices that interface with Ubuntu better--for less money.

---

### Post by RAOF on 2005-12-13
[QUOTE=landotter]If it's not been bought yet, why get an iPod in the first place? Design wise--sure it's nice enough, but personally I wouldn't buy an digital player that didn't just mount as mass storage. Same goes for cameras. The fact that other players support more formats than the overy-hyped iPod is icing on the cake.

I'm not saying that iPods are bad, but there are better choices that interface with Ubuntu better--for less money.[/QUOTE]
iPods **do** mount as removable storage.  You need the programs to mess with the db that the iPod uses to manage the music, nothing else.

One of the better reasons to buy an iPod for linux use is that everyone else has one.  Specifically, all the developers of the media-library type software have them, and not anything else.  So things like amarok, banshee, rhythmbox - they all support iPods, and have a much worse support for everything else (as far as I can tell - I don't **have** anything else ;))

Plus, iPods are really nicely designed.  You don't get ogg playback, which is a pity, but apart from that they work really well.

---

### Post by KermitJr on 2005-12-13
I don't have an ipod, but AmaroK has an ipod section, so I assume it works well with it.

KJ

---

### Post by ossi on 2005-12-18
I can't underline the last statement but Amarok has stated that it will use the same library as gtkpod for ipod suppot in 1.4. 
So far Amarok and ipod has not worked good for me. Eject works for me without any problems. Just do it throught terminal if it doesn't work with desktop.

---

### Post by urusaiyatsu on 2005-12-18
**sudo** eject ipod

You can also create a custom launcher with this command and add it to your panel. I find if you check the 'run in terminal' command it always works. Sometimes it doesn't work for me it if the ipod is connected by usb rather than firewire.

---

### Post by aysiu on 2005-12-18
[QUOTE=RAOF]iPods **do** mount as removable storage.  You need the programs to mess with the db that the iPod uses to manage the music, nothing else.[/QUOTE] I think that's what landotter meant. Most MP3 players mount as removable storage where you can drag-and-drop songs in to the file browser of the player, and the songs will play.

To the OP, don't get an iPod. It's true there are a lot of Linux programs built around iPods, but usually *new* iPods have issues with Linux support--mounting, unmounting, reading the database, etc. Sure, you can wait until the devs for various projects catch up with the latest version of iPod, but if you're buying something new, why not get a player that works?

---

### Post by Integralmannen on 2005-12-19
[QUOTE=WanderingStar]Well when I can actually get my iPod to mount (its 50/50) I can usually remove it by right clicking on the icon in "Computer" and choosing unmount.  If you get a pmount error it can usually be cleared by doing a 'sudo /etc/init.d/hotplug restart' in the terminal.  I think pmount gets out of sync with hotplug - but I have not really looked into it.[/QUOTE]

Thanks alot!
I've been having this problem with my ipod not being recognized. Only noticed briefly... not recognized as a device at least.
Restarting hotplug did the trick for me! (sometimes I have to unplug/plug it for it to automount.
(For unmounting I use "sudo eject media/ipod")

---

### Post by Cath0de on 2005-12-19
Hi, yeah, is there a way I can take the music from my iPod and move it onto my HD? Because I recently switched from windows and need some way of transferring all my music over, and that would be really convenient if I could just move it from iPod to HD.

I've tinkered around with gtkpod, but can't find anything that would do what I want.

---

