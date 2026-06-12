---
title: "Second Life"
date: 2006-11-17
forum: Gaming &amp; Leisure
---

### Post by Darrious on 2006-11-17
Has anyone ever heard of Second Life, and how well it runs on Ubuntu.

---

### Post by Hemmer on 2006-11-17
Yeah I've heard of it, but as far as I can tell, there isn't a Linux client/port yet...

---

### Post by strawman on 2006-11-18
it works.  there is a beta linux version and i have it running on edgy.

---

### Post by MaximB on 2006-11-18
you there is a Linux port and it works on edgy !
here's how to install, don't mind the Portuguese, just follow the "english" terminal commands.
[http://www.ubuntugames.org/SecondLife](http://www.ubuntugames.org/SecondLife)
P.S
you must create an account in the official game site first in order to play : [http://www.secondlife.com](http://www.secondlife.com)

---

### Post by madmetal on 2006-11-18
i run second life on dapper for about 4 months and its getting better though it still has some bugs..
its easy to install and use.

---

### Post by Hemmer on 2006-11-18
i didnt know i had a client.

 *goes off to check it out*

---

### Post by mediax on 2006-11-20
I had Second Life installed when I was running Dapper and it ran perfectly. :D 

I've not tried it since I upgraded to Edgy - not enough hours in the day just at the moment. :rolleyes:

---

### Post by mutenewt on 2006-11-21
> **MAXDDARK said:**
> you there is a Linux port and it works on edgy !
here's how to install, don't mind the Portuguese, just follow the "english" terminal commands.
[http://www.ubuntugames.org/SecondLife](http://www.ubuntugames.org/SecondLife)
P.S
you must create an account in the official game site first in order to play : [http://www.secondlife.com](http://www.secondlife.com)

Max, I tried this on edgy but when I try to run secondlife I get a "Window creation error".  Any ideas?  Thx for the help.

---

### Post by MaximB on 2006-11-22
mmmmmmmmm......never heard of this error...is the installation went o.k ?
did you create an account first ?

---

### Post by hikaricore on 2006-11-22
> **mutenewt said:**
> Max, I tried this on edgy but when I try to run secondlife I get a "Window creation error".  Any ideas?  Thx for the help.

For me that comes from my 16bit colour setting, my card can't handle 24bit well enough to make it worth it so I don't get to play secondlife.  If you're running at 24bit you shouldn't get that error.  Check your xorg.conf file.

---

### Post by cwmccabe on 2006-11-23
> **mutenewt said:**
> Max, I tried this on edgy but when I try to run secondlife I get a "Window creation error".  Any ideas?  Thx for the help.

I tried on Dapper and got the same "Window creation error".  This happens whether I execute it from the command line or double click the *secondlife* icon.

---

### Post by Seine on 2006-11-23
I tried this last night. The Linux client works well but moving around the 'game' itself was an annoying experience. It seems to make no attempt to interpolate movement. Any character movements are enacted with the full force of network latency, making getting around staggered and difficult (like being drunk).

---

### Post by madmetal on 2006-11-23
you should have seen previous versions..:-k 
but its getting better ;)

---

### Post by Darrious on 2006-11-24
For me it is just that my graphics card is not compatible so the game runs VERY SLOW for me. It takes at least a minute just to render clothes on anyone.

---

### Post by xstaticxgpx on 2006-11-24
when i try to run second life i get 

> xsx@xsx-desktop:~/games/second-life$ ./secondlife
bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory


even though sudo apt-get install libuuid1 is already installed

---

### Post by Darrious on 2006-11-25
You could always try to look on the SL Linux Forums.

---

### Post by qrm on 2006-11-25
got it running pretty easily, no errors at all. But there are some really weird graphical artefacts nd it didnt look as fun as WoW

---

### Post by Darrious on 2006-11-25
I really do not think that it is that fun. SL is more of an exploration game. It does not really serve a purpose other than to have an open ended game that is based on life.

---

### Post by happy-and-lost on 2006-11-26
Does it require Composite Extensions?

---

### Post by patrick295767 on 2006-12-16
> **madmetal said:**
> i run second life on dapper for about 4 months and its getting better though it still has some bugs..
its easy to install and use.

it s not working for me; got thsi error 
window creation error
.x.2031221420
2006-12-16T13:18:41Z INFO: QUEUED THREAD STARTING
2006-12-16T13:18:41Z INFO: VFS: Using index file /home/homeuser/SecondLife_i686_      1_13_1_5/app_settings/static_index.db2 and data file /home/homeuser/SecondLife_i      686_1_13_1_5/app_settings/static_data.db2
2006-12-16T13:18:41Z INFO: Initializing window...
2006-12-16T13:18:41Z INFO: createContext, fullscreen=0 size=800x600
2006-12-16T13:18:41Z INFO: Compiled against SDL 1.2.5
2006-12-16T13:18:41Z INFO:  Running against SDL 1.2.9
2006-12-16T13:18:41Z INFO: createContext: creating window 800x600x32
2006-12-16T13:18:41Z WARNING: createContext: window creation failure. SDL: Could      n't find matching GLX visual
2006-12-16T13:18:41Z INFO: destroyContext begins
2006-12-16T13:18:41Z INFO: shutdownGL begins
2006-12-16T13:18:41Z INFO: SDL_QuitSS/VID begins
2006-12-16T13:18:41Z INFO: GTK Initialized.
2006-12-16T13:18:41Z INFO: - Compiled against GTK version 2.0.9
2006-12-16T13:18:41Z INFO: - Running against GTK version 2.8.20

(<unknown>:9130): Gtk-WARNING **: gtk_disable_setlocale() must be called before       gtk_init()
2006-12-16T13:18:41Z INFO: Creating a dialog because we're in windowed mode and       GTK is happy.
2006-12-16T13:18:47Z INFO: Skipping quitCursors: mWindow already gone.
2006-12-16T13:18:47Z INFO: destroyContext begins
2006-12-16T13:18:47Z INFO: shutdownGL begins
2006-12-16T13:18:47Z INFO: SDL_QuitSS/VID begins
2006-12-16T13:18:47Z WARNING: LLWindowManager::create() : Error creating window.
2006-12-16T13:18:47Z WARNING: Unable to create window, be sure screen is set at       32-bit color and your graphics driver is configured correctly.  See README-linux      .txt for further information.
2006-12-16T13:18:47Z INFO: remove_marker_file()

*********************************************************
This is an ALPHA release of the Second Life linux client.
Thank you for testing!
You can visit the Linux Client Alpha Testers forum at:
[http://forums.secondlife.com/forumdisplay.php?forumid=263](http://forums.secondlife.com/forumdisplay.php?forumid=263)
Please see README-linux.txt before reporting problems.

```

```



pitty,; that s my video that is too old
32 bits is too much for the video card r128
[http://www.die.net/doc/linux/man/man4/r128.4.html](http://www.die.net/doc/linux/man/man4/r128.4.html)

---

### Post by darkteckno on 2006-12-23
Any one got this working in edgy?

---

### Post by EdThaSlayer on 2006-12-23
I was just wondering. Do you need to pay a subscription fee to play this game?

---

### Post by Popoi on 2006-12-23
Anyone got this working in 64 bits?

---

### Post by hippyjim on 2006-12-30
> **EdThaSlayer said:**
> I was just wondering. Do you need to pay a subscription fee to play this game?

No - you can play for free, but to get any decent stuff you either need to work hard in game, or pay some real cash to buy in-game currency (called Linden Dollars). Typically it's about 1 USD to 280 Lindens, although the rate varies with the market.

If you sign up for an account and give them your paypal or credit card details, they give you L$250 to begin with (they do one $1 test billing, but it's refunded). If you pay the $9.95 subscription then you get L$1000 plus L$30 a week.

The best way to play is probably to use your innate linux scripty skills to build stuff in game and sell it. :) 

Now if only I could get my video card to work in linux, I'd be able to ditch the Windoze version and play it "pure" :)

---

### Post by eye208 on 2007-01-05
> **Darrious said:**
> For me it is just that my graphics card is not compatible so the game runs VERY SLOW for me. It takes at least a minute just to render clothes on anyone.

This is unrelated to graphics card performance. All the in-game content ("prim" geometry, textures, sounds) is streamed across the net on demand. That's why rendering takes some time when you enter a new area or encounter avatars with custom clothing and accessories.

I've been playing the game for a week now (Edgy + fglrx 8.28.8) and found the Linux client to be totally stable. No crashes yet. Sure, there may be some lag in crowded areas, but this affects the Windows client as well since it's a server-side issue. For SL, broadband internet is even more important than a good graphics card.

By the way, there is a SL modelling plug-in for Blender ([Prim.Blender](http://sourceforge.net/projects/primdotblender/)). It can be used to build complex SL models offline using the Blender UI, then import them into the game using a script.

The game itself can be described best as a mixture of The Sims, MySpace, and IRC. With the free account you cannot own land in SL, but other than that there are no restrictions. You can build and script your own stuff, store it in your inventory (even if it's as large as a house!), sell it to others or attach it to your avatar's body parts to customize its appearance. Freebies can be found in lots of places. SL's virtual world is vast and always changing since the residents keep building new stuff all the time. You can spend hours exploring the area with friends. Although SL doesn't have a goal in the traditional sense of gaming, it's a lot of fun and highly addictive, and the Linux client is very easy to install (just unpack and run).

---

### Post by alteo_gange on 2007-01-09
> **Popoi said:**
> Anyone got this working in 64 bits?
Hello Popoi!

"The Second Life client is a 32 bit application. Due to the nature how libraries work, you must provide 32 bit libraries for 32 bit applications and 64 bit libraries for 64 bit applications. On 64 bit linux systems you need to install the 32 bit compatibility versions of all the libraries Second Life needs."

```
$ cd /path_to_secondlife/lib
$ sudo wget http://romanoblog.free.fr/telechargements/libuuid.so.1
```

Tested on debian etch.
Good game!

---

### Post by NULL712 on 2007-06-16
This is probably a dumb question. But can some one tell how to uninstall second life, I have little hard drive space and i want to take most of it back.

Thanx

---

### Post by CheshireMac on 2007-08-21
Okay, so here's the kicker. I gave that same error to myself, trying to stop the client from constantly crashing on me. ~LOL~ Here's what happened:
I was constantly having the client run for a little while, only to crash my entire system, over and over again. So I outsourced after do all I could to fix the problem (to no avail). I asked someone in SL's Ubuntu area if they could help, and they told me to do this:
```
mac@mac1:~$ sudo mv /lib/modules/2.6.20-16-386/kernel/drivers/char/agp/intel-agp.ko /lib/modules/2.6.20-16-386/kernel/drivers/char/agp/intel-agp.ko-orig

```
So I did this just now, and I'm getting the Window Creation Error coming up when I try to launch the client. Is there any way to get SL to open again, without the constant crashing?

---

### Post by Hendrixski on 2007-08-22
has anybody tried this deb yet?  it's the 32 bit
[http://www.getdeb.net/release.php?id=1240](http://www.getdeb.net/release.php?id=1240)
I'm thinking of trying out SL at some point to see what all the buzz is about (I'm not a gamer, but I like how universities have online classrooms and stuff, and I don't want to spend any money on it)

---

### Post by Hendrixski on 2007-08-25
Wow, that getdeb package is easy to install and works like a charm.  In fact, works better than the windows version on the same computer.  :-)

It's fun, like the next generation of IRC.  Though, It's not quite there yet, it has a lot of promise and potential.  Very exciting new technology.

---

