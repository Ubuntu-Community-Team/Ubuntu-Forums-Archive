---
title: "Help me switch to ubuntu for good!"
date: 2009-06-17
forum: General Help
---

### Post by captainstarbucs on 2009-06-17
Hi. I am a long time windows user, and I want to switch to Linux for GOOD.

The Problem
I have quite a few windows specific programs that i use on a daily basis, but I hear WINE is out of beta and can run most of these programs. Below, i will list all of my programs that i need, and i would kindly like replies on an alternative program, or how i can run them otherwise.

The Programs

[High Priority]

1. Dual Monitor Support via Nvidia.

- This is the biggest problem I've had with switching to linux. I have two monitors that i can't live without. I've messed around with a Wubi installation of Ubuntu to find that the linux Nvidia drivers can support a dual monitor setup, but only in two ways. The first way is just a "span", kind of like one big monitor. But what i absolutely need is the video card driver to recognize both of my monitors separately, much like a windows native dual monitor support. It seemed that in that wubi installation, that there was sort of an option like that but it would not let me save the configuration. The error said something along the lines of "xscreen.conf cannot be found." (I will revise that once i go back into my wubi installation and find out what it really says, verbatim.) If there is a solution to this, will i be able to use two task bars without 3rd party software?

2. Audio Card Configuration

- This is also a very huge issue. I have a high def Realtek soundcard that works very well with configuration. In windows, i ***absolutely must*** configure my soundcard to the "Rock" settings as it makes ALL music sound much more crisp. Without this setting, music (and all sounds) sound as if it had a low setting on treble. I only know the drivers for windows, but there must be some kind of fix for this in linux. I think it's mostly a glorified equalizer. Big issue here.

3. Zune Software

- All i need is to get media on and off my zune, with the easiest route possible. Any linux solutions? If not, can virtualbox pick up my zune via USB?

3 1/2. Blackberry media manager

- I need to get stuff off and on to my Blackberry. Any linux specific software for this?

[Medium Priority]

4. World of Warcraft

- I've actually seen this run on linux before in youtube videos. But how well does it actually run? Any WoW Linux players?

5. Ventrilo

- A definite must. I am an admin of a ventrilo server. I've gotten it to run on ubuntu BUT the push to talk key won't work if the window is not focused on the ventrilo.exe. Is there a fix for this? If there isn't, can I run this program in virtualbox on a windows XP installation with my push to talk key still intact while I'm focused in on my linux desktop? (I've seen Mac's parallels do this before, I'm wondering if it's possible for virtualbox.)

6. Steam / Various Steam Games

- There must be tons of people who know how to do this. Biggest games are Left 4 Dead, Team Fortress 2 and Audio Surf. Is this possible on a linux native desktop? Virtual box? Any video lag occur?

7. Photoshop / Dreamweaver CS4

- Self explanatory, really. Will it run? Any good alternatives? I know of GIMP.

8. VirtualBox

- Say I save a text file on a virtual installation of windows xp using virtualbox. Is it possible to get that text file from virtual box to my main linux desktop with ease? (I'll try to think of more questions later.)

[Low Priority]

9. Logitech Stuff

- I have a nice G15 Keyboard from logitech, with an LCD screen. Is there anything that will make that LCD screen of use in linux? I also have a G9 mouse, and a logitech webcam. I need a recommendation for a web cam program for linux at least.

10. Winamp

- Probably just gonna use Amarok. Good idea?

---

### Post by snakeman21 on 2009-06-17
Well, I don't have all of your answers, but I'll give you the ones I do have:

Zune software:  Currently, there is no way to sync a Zune with Linux.  This is because Microsoft added a step in the detection process that looks for a valid Windows install.  There may be a way to do it from VirtualBox, but I don't believe so.

Photoshop:  Gimp is an excellent alternative.

Virtualbox: Yes.  You can set a shared folder.  Then from windows inside virtualbox, you will find the folder in My Network Places.  Very simple.

Winamp:  The list goes on and on.  Amarok is great, and there are several others to choose from.

Webcam:  There are several webcam programs such as Cheese.

Hope this is helpful!  Sorry about the Zune... I sold mine and got an iPod.  There are several linux programs that sync iPods without a problem.

Edit:  I forgot to mention:  Numerous Windows applications can run under Wine, a Windows compatibility layer for Linux.  Download it from the repos, and use it to run Windows programs.  It won't work for ALL windows programs, but it will work with a lot of them, and the list keeps growing.

---

### Post by snakeman21 on 2009-06-17
Check out Wine [HERE]("http://www.winehq.org/")

---

### Post by cph05a on 2009-06-17
1. You can download the drivers from [nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us"). I have a GeoForce GTX 180 and it duel screen works just fine.

2. I have no experience with sound card stuff, so someone else will need to answer that one. 

3. Look into [Songbird]("http://getsongbird.com/"). I believe it ether supports the zune or has a plugin for the zune you can get.

3.5 no idea, someone with a blackberry should answer this.

4. Wow runs in [Crossover Games]("http://www.codeweavers.com/compatibility/browse/name?app_id=1185")

5. I don't know 

6. again [Crossover Games]("http://www.codeweavers.com/compatibility/browse"), just keep in mind that some games may not work, so read over the compatibility list

7. I have dream weaver 8 and flash MX running on my Ubuntu laptop right now, again using crossover. I believe photoshop is also on the supported list.

8. Yes, you can do this. [http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12]("http://maketecheasier.com/share-files-in-virtualbox-between-vista-guest-ubuntu-host/2008/11/12")

9. sorry, I don't have any logitech stuff. Just see if it works from the live CD. 

10. There are plenty of alternatives to WinAmp around. Again, I use songbird. 



There is plenty of information around to help get you going in linux. Try booting from the live CD as well to get a good feel for which hardware components work "out of the box" and which ones might need some work. 

Also, there are a lot of cross platform alternatives to windows software. Try them out and see what you like.

---

### Post by hermitcrabred on 2009-06-29
Please excuse my ignorance, I`m new to Computers. How can I get Wine?...I have a few programs I would love to be able to run in Ubuntu, such as YouTube Downloader and FPSC Creator. I need some help. Thank you!

---

### Post by t4thfavor on 2009-06-29
WINE is in the add/remove programs dialog on the applications menu.

as for the youtube downloader there is a firefox plugin that will do that for youtube, and a bunch more youtuube like sites. So no wine required for that.

What is an FPSC Creator, there must be a linux alternative.

---

### Post by snakeman21 on 2009-06-29
you can also open a terminal and type:

```
sudo apt-get install wine
```

It will ask for your password.  Type it (it will not show up) and hit enter.

---

### Post by albinootje on 2009-06-29
> **captainstarbucs said:**
> 
8. VirtualBox
- Say I save a text file on a virtual installation of windows xp using virtualbox. Is it possible to get that text file from virtual box to my main linux desktop with ease? (I'll try to think of more questions later.)

VirtualBox has "shared folders", you can access those as a "network drive" inside the xp guest VM.

Here's a howto :
[http://bloggy.kuneri.net/2008/05/16/how-to-share-files-with-virtualbox-between-mac-and-windows/](http://bloggy.kuneri.net/2008/05/16/how-to-share-files-with-virtualbox-between-mac-and-windows/)

---

### Post by cptrohn on 2009-06-29
IN regards to the Zune, I beleive that the Songbird plug-in only works if you have Windows...

I had a Zune when I first migrated from Windows as well, and I ended up putting it up on Ebay and getting a Cowon D2+... It took some researching but if you want a PMP that is truly on the higher end and has awesome codec support for both audio and video this is the one to get imho..
[http://www.cowonglobal.com/](http://www.cowonglobal.com/)   The S9 blows both the Ipod and the Zune out of the water... and the D2's are awesome little players as well, that also support  a 32 GB SDHC card for added memory too... AND the Cowons are flash based as well...

---

### Post by kostkon on 2009-06-29
> **captainstarbucs said:**
> 9. Logitech Stuff

- I have a nice G15 Keyboard from logitech, with an LCD screen. Is there anything that will make that LCD screen of use in linux?
Yes, using *G15Tools*. Search for *g15* in Synaptic (using the full search not the quick-search) and install any package you will find appropriate. You'll want to install the [*g15daemon*]("http://packages.ubuntu.com/jaunty/g15daemon") and [*g15stats*]("http://packages.ubuntu.com/jaunty/g15stats") packages.

---

### Post by Simian Man on 2009-06-29
Honestly you have so many dependencies on proprietary software and hardware, I wouldn't bother switching to Linux for good.  Many of your problems have only incomplete or hackish solutions that will leave you butting your head against your desk.

Leave Windows on as a dual-boot or just run Linux inside a VM - unless you are just a masochist, which is OK too :).

---

### Post by 3rdalbum on 2009-06-29
> **Simian Man said:**
> Honestly you have so many dependencies on proprietary software and hardware, I wouldn't bother switching to Linux for good.  Many of your problems have only incomplete or hackish solutions that will leave you butting your head against your desk.

Leave Windows on as a dual-boot or just run Linux inside a VM - unless you are just a masochist, which is OK too :).

One of the few times I'd say this, but I agree - you locked yourself pretty tightly into Windows. You require an equaliser setting from Realtek's Windows audio drivers in order to get decent sound? I'd be taking that card back, or changing my speakers. In any case, you're locked-into their drivers.

Your Zune is like a brick without Windows - you might have already guessed that. Microsoft implemented DRM that prevents the Zune from syncing with anything other than Windows. Before being too hard on Microsoft, we should remember that Apple tried doing it too - but Microsoft can code better.

Ventrilo doesn't have a Linux version, so you locked yourself in that way. I don't know if you can set Wine to be able to listen to keystrokes that aren't explicitly directed to its window, but I wouldn't be surprised if you can't seeing as all malicious keyloggers run on Windows.

Proprietary games: You're mostly locked to Windows. Wine can run some of them, Crossover Games can run some of them. But most won't.

My best advice to you would be to start reducing your dependency on Windows-only stuff before trying to switch. Sell the Zune, get something cross-platform. I don't really know much about Ventrilo, but I'm sure there's a cross-platform solution there too. Get a decent sound card with native Linux drivers (something out-of-the-box). Get an Xbox or PS3 or dual-boot for the games.

---

### Post by mixmaster on 2009-06-29
Currently I boot my primary machine into windows and do most of my productive work under linux in virtualbox.  This is to avoid hastle with a few graphics intensive games and similar software.  WinXP runs perfectly happily in virtualbox but the emulated graphics are not up to running the more demanding games.  I'm hoping shortly to get a more powerful system and see if the 3D acceleration available in the virtualbox 3.0 beta changes that situation.

Given that you have to work quite hard to get a system without some form of Windoze on it you might as well take advantage of it.  The strategy I've outlined works quite well and is more convenient than dual booting.

PS: Look at bibble as an alternative to lightroom.

---

