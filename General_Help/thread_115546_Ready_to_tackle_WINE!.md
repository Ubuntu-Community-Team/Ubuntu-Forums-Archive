---
title: "Ready to tackle WINE!"
date: 2006-01-10
forum: General Help
---

### Post by Optiker on 2006-01-10
I'm ready to try my next in trying to transition to Linux...learn to use WINE.

On my installation, in ADEPT, there are a number of items for WINE. The item named "wine" was installed - don't recall if it installed by default or if in a moment of great courge I installed it. Later, as I read a little more, it seemed that what I needed was what was called "winesetuptk" so I c ould get it properly setup, and "xwine" because that is a graphical interface which appealed to me more than a command line tool. In addition, I figured I might as well install "wine-doc" so the documentation is there if I need it.

When I selected these to install, it uninstalled "wine". I didn't understand taht, but decided that I might as well go for it and see what I learn. So, now the three packages above aare installed, and I don't know what to do with them.

I found /usr/bin/winesetup and doubleclicked to run it, and it opened a GUI that is a setup wizard. The first dialog asks for location of the Wine configuration file, but offers a default, which I accepted, and then accepted the defaults throughout.

Now what? Can aanybody walk me through setting up some Win app in Wine as an example?

Thanks!
Optiker

---

### Post by mustang on 2006-01-10
Hmm I'm not sure wine is something you dive into for fun. It's more of a last resort thing. 

I suppose you could try any app you used on windows and see if it works or not. Sometimes there are dll problems in which you gotta find the right dll and drop it into the windows/system on the wine fake drive.

Good luck

---

### Post by onesojourner on 2006-01-10
I think you need wine installed along side xwine. I might be wrong on that though. once you have it working type xwine in the command line then start clicking away. start with the launch button in the start menu.

---

### Post by Optiker on 2006-01-10
mustang...thanks for replying, but I guess I'll hold on for something more constructive.

Optiker

---

### Post by Optiker on 2006-01-10
one...thanks for the reply. Yeah...I saw wine as installed, but when I installed xwine, it uninstalled wine - didn't allow them to coexist. Also, how do I get apps to show up in that list? I thought I'd eard something about installing apps under wine - I know nothing about that.

Still looking for more help, please.

---

### Post by JuanFerS on 2006-01-10
To install and app with wine you need to do the following:

/where the installation file is$ wine setup.exe (or whatever the name of the installation executable is).

I have used wine in suse and then switched to Crossover Office, never tried it in kubuntu, but if recall correctly that's how you install something.

---

### Post by hscottyh on 2006-01-10
First of all use WINE from wineHq not the one in the ubuntu repository.

Add this to your sources.list:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Then install wine.

I would also recomend installing IE6 and Windows Media player with the Sidenet Configuration Utility, which can be found at:

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

It will give you a good start at getting a correctly setup fake windows directory.

---

### Post by Optiker on 2006-01-10
Juan and Scotty...thanks to both of you for replies. Looks like I'll try Scotty's suggestion first, then to Juan's. Looks like I'll need to uninstall what I have on there, then install the wineHQ list. Thanks for that...was wondering what to do and went with the Wine site suggestion to use the backport source.

Out of time tonight....will try tomorrow night.

Thanks again!
Optiker

---

### Post by Billquinn1 on 2006-01-11
Just one more thing. Scotty is right on the money. Before you start though, you should use adept to uninstall any wine stuff you have already installed and remove the .wine folder and the "c" folder from your home/yourname directory. (If you got that far the first try) Another thing is don't let your system "upgrade " wine. It will break it.

Have fun!

---

### Post by ace2005 on 2006-01-11
Well i this is what i did and it worked very well

First of all like Scotty said add this to your sources.list

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Then install wine and winetools

Run wine tools, it will guide you through installing software like IE and Media Player as well as codecs, start with base setup and work down the list, this will install everything you need.

:)

---

### Post by Optiker on 2006-01-11
Bill...thanks for the confirmation that Scotty's suggestions were the right way to go. Looking forward to trying it tonight.

Question: "...don't let your system 'upgrade' wine. It will break it."

How do I keep it from upgrading wine, and what is the "it" that will break - wine, my Kubuntu installation?

Thanks!
Optiker

---

### Post by Billquinn1 on 2006-01-12
The wine devs are always tweaking. Those tweaks are not always forward. It will just make apps in wine quit working.
Once you have it all installed like you want it, look for wine in synaptic. It will be there as the version you installed. Then just click on it once and click "package" on the tool bar and click "lock version". I'm not sure how to do it from another package manager but this way works.

---

### Post by Optiker on 2006-01-13
Scotty, Bill...I've uninstalled the three Wine packages that I'd previously installed and added the source to my list.

Question: Now that there is more than one entry in the sources list that include Wine, how do I assure that I'm installing from the one you gave me? In Adept, I don't see anything that shows the source, and the list looks pretty much the same as before I added the source you gave.

Thanks!
Optiker

---

### Post by Optiker on 2006-01-13
Got it! I installed and ran winetools, and although there were some errors, I was able to at least install some of the stuff supported in winetools, including IrfanView. However, installation of WinAmp failed. Not a problem...at least for now. That's a start.

Question...how do I install an app that isn't listed in the installation menu in winetools? Or is this biting off far more than a Linux noob should?  :)

Thanks!
Optiker

---

### Post by Cliff76 on 2006-01-13
I'm trying the same path installing wine. I used the official winehq repo and installed wine 0.9.5. I then tried using winetools to install IE6 and it kept telling me after it downloaded ie6setup.exe that the file was corrupt. So then I tried the wine-config-sidenet utility and when I use that to auto-install ie6 it just hangs. I then tried the manual install method which asks a few more questions and backs up everything it installed the first time and the windows update window comes up again. When I start the windows update install it hangs once again. At first I thought it was a problem with our dumb proxy but then I realized that wasn't the problem or else how would it have downloaded IE to start? Is there something I'm doing wrong? Do I have the wrong version of wine? the sidenet tool says it was tested with wine 0.9. Where do I go from here?

---

### Post by eddyvlad on 2006-01-13
Hmm... the last time I tried to run Adobe using wine, my ubuntu won't start. Stuck at the login screen. I'm not going to play around with that anymore... :mad:

---

### Post by hscottyh on 2006-01-14
[QUOTE=ace2005]Well i this is what i did and it worked very well

First of all like Scotty said add this to your sources.list

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

Then install wine and winetools

Run wine tools, it will guide you through installing software like IE and Media Player as well as codecs, start with base setup and work down the list, this will install everything you need.

:)[/QUOTE]

winetools is the way to go... I just tried it and it is better than sidenet by far!!! I thought sidenet was nice, but winetools lets you get _a lot_ more installed!!!

Thansk for the tip. Maybe I'm dreaming it, but if I recall winetools used to uninstall wine. But that's probably before I knew to use winehq's version.

---

### Post by Optiker on 2006-01-14
Winetools didn't work for everything. Tried Winamp for example, and failed.

How do Install apps that aren't listed in winetools? I kow  you can  because folks in the City of Heroes forums run it on wine.

So far, my only "other" program that ahs succeeded is IrfanView.

Thanks!

Optiker

---

### Post by ace2005 on 2006-01-14
Simple, just go to the winamp site and download the .exe and double click on it

:)

Edit: i mean in double click it in konqueror

---

### Post by ace2005 on 2006-01-14
A Tip for Winamp

Go into winetools, then go into "Modify the Wine Configuration" then go into Audio and select Alsa as sound output, and in graphics enable the "Emulate a virtual desktop", this will stop winamp being on top of all apps and all desktops, which sucks so will allow you to minimize the entire desktop and minimize winamp with it.

You must get the Enhancer plugin for winamp, it makes the sound a lot better, thats why i like to use it on some songs instead of juk but try telling people that

[http://www.winamp.com/plugins/details.php?id=81361](http://www.winamp.com/plugins/details.php?id=81361)

---

### Post by Riggs on 2006-01-27
I see you guys are saying to install Winetools.

> james@ubuntu:~$ sudo apt-get install winetools
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetools
Not sure what's going on here... HELP :)

---

### Post by Jengu on 2006-01-27
First off, there's no good reason to run winamp under wine. XMMS is a straight clone of it if you really want that interface, and on Kubuntu you can get amaroK which is an **awesome** player.

Second, don't install winesetuptk. Wine now comes with a utility, winecfg, that lets you graphically configure it, making winesetuptk unnecessary. winesetuptk will try to write configuration files that newer versions of wine no longer use. Only try winetools if wine by itself doesn't work -- many apps will run simply by typing "wine whatever.exe".

Winamp may just not work currently under wine -- you aren't necessarily doing something wrong. The normal way to install an app once you have wine installed is simply to run wine on the installer like you would any other exe. If I remember right Kubuntu is smart and associates .exe files so they open in wine when you click them once wine is installed.

---

### Post by Garyu on 2006-01-28
[QUOTE=Jengu]Second, don't install winesetuptk. Wine now comes with a utility, winecfg, that lets you graphically configure it, making winesetuptk unnecessary. winesetuptk will try to write configuration files that newer versions of wine no longer use. Only try winetools if wine by itself doesn't work -- many apps will run simply by typing "wine whatever.exe".[/QUOTE]

But WHY? I was just about to try it, and now I don't know what to do. What is the exact reason as to why I should avoid winesetuptk? 

And also, how come everyone refers to "winetools" if it is really called "winesetuptk"???

---

