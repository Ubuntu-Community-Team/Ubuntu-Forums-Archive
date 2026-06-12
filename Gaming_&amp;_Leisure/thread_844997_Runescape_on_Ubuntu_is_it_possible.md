---
title: "Runescape on Ubuntu is it possible?"
date: 2008-06-30
forum: Gaming &amp; Leisure
---

### Post by Vigh on 2008-06-30
Hi is it possible to play runescape on Ubuntu, preferabbly using SwiftKit, if not just in the browser. I have wine and crossover. I would really love to get runescape going in ubuntu. Cheers Anthony

---

### Post by eragon100 on 2008-06-30
The browser version runs on adobe flash and thus on linux. (Native, no wine or crossover required). You have to play on low graphics quality tough, high doesn't work. I tested it out for someone else on the forum once.

Since I don't play runescape, I have never heard of the client you mentioned, but just take a look in the wine appdb to see if it works with wine: [http://appdb.winehq.org/]("http://appdb.winehq.org/")

Have fun! :)

---

### Post by Phenax on 2008-06-30
> **eragon100 said:**
> The browser version runs on adobe flash and thus on linux. (Native, no wine or crossover required). You have to play on low graphics quality tough, high doesn't work. I tested it out for someone else on the forum once.

Since I don't play runescape, I have never heard of the client you mentioned, but just take a look in the wine appdb to see if it works with wine: [http://appdb.winehq.org/](http://appdb.winehq.org/)

Have fun! :)

It uses Java, and should work fine. I think you may have to use an unsigned applet though -- it's been a while.

---

### Post by lockerhaxor on 2008-06-30
It's a browser game, thus there should be no problem running it on Linux. As long as you have the latest version of Adobe Flash (Which has an Ubuntu version) you should be good to go.

I wasn't aware there were programs you could use to play this game, but your best bet would be to try Wine to run it. However make sure it's not choppy. Some programs, like Safari, run super choppy through Wine, and you'd be better of staying in a browser.

Hope this helps,
Lockerhaxor

---

### Post by starcannon on 2008-06-30
Works fine here, be sure to go into:
 System-->Administration->Synaptic Package Manager
and install Sun-Java

---

### Post by snaggapuss on 2008-07-02
Hi, I'm a linux newbie and I got runescape up and running in the new HD version. I use firefox v3 and the latest sun java version 6 i think. I had to delete java and reinstall it.  Then used the "patch" RS give in there technical advise to get it to run full screen but its running awesome.  Swiftkit doesnt work in ubuntu or any linux for that matter, so you would have to use wine if you wanted to use it. There was another programme similiar to swift kit but I lost the link and can't even remember the name, but its out there somewhere

---

### Post by geezerone on 2008-07-31
Installed the three plugins and more but can't play runescape here :confused:

---

### Post by doorknob60 on 2008-07-31
My guide to set up Sun Java (needed for Runescape) in Ubuntu, both in 64 bit (AMD64) and 32 bit (i386). If you don't know whether you have, go to a terminal (Applications > Accesories > Terminal) and type this:
```
uname -m
```
If it says x86_64, you have 64 bit, if it says i686 or x86 then you have 32 bit.

**32 Bit (i386):**

In terminal (Applications > Accessories > Terminal):
```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```
And you should be good to go :)

**64 Bit (AMD64):**
Thanks to Sun, it's slightly more complicated...although when the final Java 7 is released it should be as easy as it is in 32 bit :)

Run each line one at a time in a terminal (Applications > Accessories > Terminal):
```
sudo apt-get install ia32-libs
wget http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//firefox/releases/3.0.1/linux-i686/en-US/firefox-3.0.1.tar.bz2
tar -xf firefox-3.0.1.tar.bz2
sudo mv firefox /opt/firefox32
sudo apt-get install ia32-sun-java6-bin
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox32/plugins/
sudo ln -s /opt/firefox32/firefox /usr/local/bin/firefox32
```

Now run the command 'firefox32' to start the 32 bit Firefox, complete with a Runescape compatible Java :) **Make sure you close *all* instances of Firefox before you do this or it won't work!**

----

**Full screen Runescape HD problems?** No problem! (Both 32 bit and 64 bit)
> 22. RuneScape HD will not go full screen in my version on Linux. Is there a way to get it to go full screen?  
On some recent versions of Linux, a system modification is required to enable correct functioning of the full-screen mode.
Note that this change could have adverse effects if you are running two monitors but you can reverse it once you finish playing RuneScape HD.
To enable the modification:
Open a linux terminal window.
Type the following commands:
cd /usr/bin/X11
sudo cp Xorg Xorg-backup
sudo sed -i s/XINERAMA/ZINERAMA/g Xorg
Then reboot your linux machine.
To disable the modification:
Open a linux terminal window.
Type the following commands:
cd /usr/bin/X11
sudo sed -i s/ZINERAMA/XINERAMA/g Xorg
 Then reboot your linux machine 
Note also that we are expecting the next update of Java to fix this issue after which you will no longer need the modification.

Hope my guide-in-a-thread helped :-)

---

### Post by FAttyBones on 2009-06-08
I had to turn off Advanced Desktop Effects to get the "guide in a thread" to work.  IDK if it was a performance issue, I have a new, but pretty low-end computer.

---

### Post by Matt_Johnson on 2009-06-08
I believe it is run on java and should be playable in firefox without wine ect.

---

### Post by FAttyBones on 2009-06-09
more info.  I was using 64 bit, so installed 32 bit firefox and java as per "guide in a thread".  After turning off compiz (Advanced Desktop Effects), it works, but you can't open a tab on top or minimize without making runescape go blank.  Once it's blank, it's still logged in, but you can't see or play.  Also, had to disable the default plugin, so it wouldn't try to install Flash, which blanks runescape also.  Installing flash is a bad idea, it crashes firefox32.  Runecape works though.  Thanks for the guide, Doorknob.

---

### Post by Pressondude on 2009-06-20
"Guide in a thread" did not work on my Jaunty install

---

### Post by Kingz747 on 2009-07-25
Hey Guys your all being so dum here

If you really want to get Runescape to work on Ubuntu/Linux or any operating server download 

IE (Internet Explorer)'s for linux 

[http://linux.softpedia.com/get/Internet/HTTP-WWW-/IEs-for-Linux-11281.shtml](http://linux.softpedia.com/get/Internet/HTTP-WWW-/IEs-for-Linux-11281.shtml)

Download IE 5 when it appears on your desktop Double click then wait you wont see anything saying loading like with firefox as it is not ment to be there..

---

### Post by Liolikas on 2009-07-26
For me it works on HD on 32bit system Firefox 3.0.x and java-plugin-1.6.0_14 (you can check this in tools->add-ons->plugins).
Do not forget to install java-plugin trough synaptic!

---

### Post by stevefed5291 on 2009-07-30
tried doorknob's guide but it didn't work for me, that being said I am running Mint 7 x64, not normal jaunty. Thanks for guide anyway though. Quick note though, doorknob's guide specifies [http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//firefox/releases/3.0.1/linux-i686/en-US/firefox-3.0.1.tar.bz2](http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//firefox/releases/3.0.1/linux-i686/en-US/firefox-3.0.1.tar.bz2), as the path to the bz2 when it should be:

[http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//firefox/releases/3.0.10/linux-i686/en-US/firefox-3.0.10.tar.bz2](http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//firefox/releases/3.0.10/linux-i686/en-US/firefox-3.0.10.tar.bz2)

just replace the path (really just two added "0"'s after the 1's in "3.0.1"

---

### Post by Triggerhapp on 2009-08-22
Jaunty has some problems with HD... but standard detail should work fine.

"sudo apt-get install sun-java6-plugin" in a terminal

then load it in firefox, and it should ask you to allow it to run.

After that, you're away!

no need for dirty hacks with wine/IE at all.

---

### Post by wolfyking2 on 2009-08-22
Really?  I'm using Ubuntu 8.04, and I have a GeForce MX 420 (I know, really old.  Way better than my intel one, tho :P) and I can run runescape in HD at like 40 fps.  :popcorn:

---

### Post by geezerone on 2009-08-28
Hardy Heron here but no HD and always slow :sad:

---

### Post by FunPika on 2009-08-28
I also can't get HD to work in RuneScape. When I try Java crashes/the applet goes gray. When that happens an error file like the one I attached shows up in my home directory.

---

### Post by MyTer on 2009-10-20
> **doorknob60 said:**
> My guide to set up Sun Java (needed for Runescape) in Ubuntu, both in 64 bit (AMD64) and 32 bit (i386). If you don't know whether you have, go to a terminal (Applications > Accesories 

Hope my guide-in-a-thread helped :-)

this worked GREAT!!!
Thank You!
[http://ubuntuforums.org/images/icons/icon10.gif](http://ubuntuforums.org/images/icons/icon10.gif)

---

### Post by freackout on 2009-10-25
> **eragon100 said:**
> The browser version runs on adobe flash and thus on linux. (Native, no wine or crossover required). You have to play on low graphics quality tough, high doesn't work. I tested it out for someone else on the forum once.

Since I don't play runescape, I have never heard of the client you mentioned, but just take a look in the wine appdb to see if it works with wine: [http://appdb.winehq.org/]("http://appdb.winehq.org/")

Have fun! :)you dont need wine to run runescape its a browser dependent programme, ie its run by java, all 3d and HD works well remove openjava-jdk, you can install the full sun-java packages (synaptic) or simly install the extra firefox runescape plugins zybez & the runeHQ browser bar they will install the correct java stuff, widescreen is sorted by 

1. Open a linux terminal window.
2. Type the following commands:
* cd /usr/bin/X11
* sudo cp Xorg Xorg-backup
* sudo sed -i s/XINERAMA/ZINERAMA/g Xorg
3. Then reboot your linux machine.
ALL the compiz stuff still works too no need to disable or change desktop settings (rightclicking change the desktop settings) the desktop visual effects non as mentioned you can leave them on full normal extra or custom) ie if you got compiz working just add the above stuff keeping all compiz HD and widescreen browser working great at same time. thanks guys....

---

### Post by doorknob60 on 2009-10-25
Hmm, people are still reading my guide-in-a-thread? Well, I've updated it many times since I posted that, here's my updated version: [http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu](http://doorknob60.is-a-geek.org/wiki/index.php/How_to_install_32_bit_Java_and_Firefox_in_Ubuntu)

---

### Post by nexx892 on 2009-10-25
All of you are dumb.


Runescape uses java.

It can run just as good if not better than on windows because java is native. (Java runs a VM on any OS so if your on windows your running the same JVM environment as if you were on linux.

It even runs full screen.

Also RSBOT even works.


You just don't have java installed.

---

### Post by doorknob60 on 2009-10-25
nexx892: Yeah, except that Java is buggy on Linux and you sometimes need weird workarounds, and to complicate things further, you need to use a different version of Java that what comes with Ubuntu, so no, it's not always that simple.

---

### Post by Jaynano on 2009-12-28
Thanks doorknob60.  That worked like a charm.  Both Firefox and Chrome are able to run Runescape now.

---

### Post by blazemore on 2010-04-17
I have 32 bit Ubuntu and I can only get safe mode.
Why is this?

---

### Post by Sharft 6 on 2010-04-29
Oh i just installed "ubuntu restricted extras" in the ubuntu software center and it seems to work good.

running ubuntu 10.04 x64

---

### Post by blazemore on 2010-04-30
> **nexx892 said:**
> All of you are dumb.


Runescape uses java.

It can run just as good if not better than on windows because java is native. (Java runs a VM on any OS so if your on windows your running the same JVM environment as if you were on linux.

It even runs full screen.

Also RSBOT even works.


You just don't have java installed.

You're the dumb one. have you actually tried to run Runescape? We know the theory but in practice only Safe Mode works, and even that is slow and buggy.

---

### Post by blazemore on 2010-04-30
> **Sharft 6 said:**
> Oh i just installed "ubuntu restricted extras" in the ubuntu software center and it seems to work good.

running ubuntu 10.04 x64

Does it work in High Detail? What graphics card are you using?

---

### Post by Sharft 6 on 2010-04-30
> **blazemore said:**
> Does it work in High Detail? What graphics card are you using?

radeon 4850 512MB

yes it works in high detail but not standard detail lol. high detail didn't work till i downloaded the drivers from the ati website and just followed through with default/automatic install. (sudo sh ./ati-blahblahblah, next ,next, next)

**the bad**
sound doesn't work but the sound sucks on that game anyway. 
Tabbed browsing doesn't work but you can open another web browser.
The custom mouse cursor thing doesn't look right.
In high detail the applet flickers sometimes for some reason. Muck like quadrapassel
Sometimes the applet doesn't load

**the good**
It runs very smooth in high detail compared to safe mode and even compared to windows i think.

---

### Post by blazemore on 2010-05-01
> **Sharft 6 said:**
>  high detail didn't work till i downloaded the drivers from the ati website and just followed through with default/automatic install. (sudo sh ./ati-blahblahblah, next ,next, next)


Before I do this I'd like to know a few things:
[LIST=1]
[*]What driver were you using before you installed from ATI's website? The default, open-source one? Or the packaged one from the Hardware Drivers utility?
[*]What version of Ubuntu are you using, and did you upgrade to this version or fresh install?
[*]Are you 32 bit or 64 bit?
[*]What Java are you using? OpenJDK or Sun Java?
[*]What browser are you using?
[/LIST]

Thanks a lot

---

### Post by Sharft 6 on 2010-05-01
> **blazemore said:**
> Before I do this I'd like to know a few things:
[LIST=1]
[*]What driver were you using before you installed from ATI's website? The default, open-source one? Or the packaged one from the Hardware Drivers utility?
[*]What version of Ubuntu are you using, and did you upgrade to this version or fresh install?
[*]Are you 32 bit or 64 bit?
[*]What Java are you using? OpenJDK or Sun Java?
[*]What browser are you using?
[/LIST]

Thanks a lot

I'm brand new to ubuntu so I don't know much

1. I think i was using the default display driver. I didn't go out of my way to install any others except the one on ati's website.

2.  fresh install ubuntu 10.04 LTS desktop x64

3. 64bit

4. I think I'm using OpenJDK. I did try to install OpenJDK using the ubuntu software center but the runescape website couldn't detect java on my system. So I uninstalled OpenJDK and installed ubuntu restricted extras. Looking at my installed software with ubuntu software center it would appear that either OpenJDK didn't uninstall or ubuntu restricted extras reinstalled it because OpenJDK is still on the list.

5. I'm using the preinstalled firefox browser. v3.6.3 x86_64

I'm guessing you wouldn't need to download the ati driver from the website. I just got it from there because I didn't know which one to download in ubuntu software manager. Infact now I think of it I might not have even had to install the drivers at all. I only tried to use high detail once and the screen went white or gray so i decided high detail is out of the question for the current configuration.

---

### Post by joenewtzie on 2010-05-02
> **doorknob60 said:**
> My guide to set up Sun Java (needed for Runescape) in Ubuntu, both in 64 bit (AMD64) and 32 bit (i386). If you don't know whether you have, go to a terminal (Applications > Accesories > Terminal) and type this:
```
uname -m
```
If it says x86_64, you have 64 bit, if it says i686 or x86 then you have 32 bit.

**32 Bit (i386):**

In terminal (Applications > Accessories > Terminal):
```
sudo apt-get install sun-java6-plugin ; sudo update-java-alternatives -s java-6-sun
```
And you should be good to go :)

**64 Bit (AMD64):**
Thanks to Sun, it's slightly more complicated...although when the final Java 7 is released it should be as easy as it is in 32 bit :)

Run each line one at a time in a terminal (Applications > Accessories > Terminal):
```
sudo apt-get install ia32-libs
wget http://mozilla.mtk.nao.ac.jp/pub/mozilla.org//firefox/releases/3.0.1/linux-i686/en-US/firefox-3.0.1.tar.bz2
tar -xf firefox-3.0.1.tar.bz2
sudo mv firefox /opt/firefox32
sudo apt-get install ia32-sun-java6-bin
sudo ln -s /usr/lib/jvm/ia32-java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox32/plugins/
sudo ln -s /opt/firefox32/firefox /usr/local/bin/firefox32
```

Now run the command 'firefox32' to start the 32 bit Firefox, complete with a Runescape compatible Java :) **Make sure you close *all* instances of Firefox before you do this or it won't work!**

----

**Full screen Runescape HD problems?** No problem! (Both 32 bit and 64 bit)


Hope my guide-in-a-thread helped :-)




Everything from that helped me get runescape to work on my 32 bit but now i'm getting this in command:

"(firefox-bin:13692): Gdk-WARNING **: XID collision, trouble ahead"

not sure if thats bad or not...it seems bad. haha.

---

### Post by zakshdw on 2010-05-26
thanks doorknob60 that worked for me :D

---

### Post by ginin on 2010-05-27
I couldn't make it work with doorknob's solution. Firefox just wouldn't see the new plugin (about:plugins)

I found that this worked well though:
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

:)

---

### Post by 13k on 2010-05-28
> **Sharft 6 said:**
> I'm brand new to ubuntu so I don't know much

1. I think i was using the default display driver. I didn't go out of my way to install any others except the one on ati's website.

2.  fresh install ubuntu 10.04 LTS desktop x64

3. 64bit

4. I think I'm using OpenJDK. I did try to install OpenJDK using the ubuntu software center but the runescape website couldn't detect java on my system. So I uninstalled OpenJDK and installed ubuntu restricted extras. Looking at my installed software with ubuntu software center it would appear that either OpenJDK didn't uninstall or ubuntu restricted extras reinstalled it because OpenJDK is still on the list.

5. I'm using the preinstalled firefox browser. v3.6.3 x86_64

I'm guessing you wouldn't need to download the ati driver from the website. I just got it from there because I didn't know which one to download in ubuntu software manager. Infact now I think of it I might not have even had to install the drivers at all. I only tried to use high detail once and the screen went white or gray so i decided high detail is out of the question for the current configuration.

I don't really know how to answer your question, but all i know is that jdk includes jre(java run time) which makes runescape run.

---

### Post by datacrusher on 2010-08-06
Iv tryed all this suggestions, but i cant run runescape the whole browser, and lacks the hd or bigger than the low quality configurations.

i can run glxgears, and my ati driver is installed ok... any other clues?

---

### Post by 13k on 2010-08-12
> **datacrusher said:**
> Iv tryed all this suggestions, but i cant run runescape the whole browser, and lacks the hd or bigger than the low quality configurations.

i can run glxgears, and my ati driver is installed ok... any other clues?

 if you're trying to run hd, i don't think it's possible yet, or i haven't looked hard enough.

---

### Post by CPL2010 on 2010-08-13
Just run the restricted essentials from the software center.  It'll have you up and running in no time.

---

### Post by geezerone on 2010-08-13
I have 8.04 and although the Runescape web page loads, as soon as I click 'play' the browser closes in Firefox.

---

### Post by Oxwivi on 2010-08-21
RuneScape audio doesn't work for me, although any other audio sources from the browser like Flash works. Didn't try any other Java app for sound though.

---

### Post by doorknob60 on 2010-08-21
I did this and it seems to fix Java sound problems: [http://ubuntuforums.org/showpost.php?p=9494340&postcount=10](http://ubuntuforums.org/showpost.php?p=9494340&postcount=10)

---

### Post by FattyOwl on 2010-08-22
I can run runescape without any troubles on highest quality after installing the OpenJDK Java package. I'm using Ubuntu 10.04 64-bit and Google Chrome to play it.

---

### Post by Oxwivi on 2010-08-23
Ah, I reformatted for some reason and now the audio works fine. Guess the reason will remain a mystery.

**EDIT** I didn't run any MP3 files yet, so I'll try that fix anyway. Thanks. ):P

---

### Post by 10snoopy1 on 2010-08-23
> **Sharft 6 said:**
> Oh i just installed "ubuntu restricted extras" in the ubuntu software center and it seems to work good.

running ubuntu 10.04 x64

That package is useful for playing runescape and other online games. 

Good thing they keep it up-to-date!
:)

---

