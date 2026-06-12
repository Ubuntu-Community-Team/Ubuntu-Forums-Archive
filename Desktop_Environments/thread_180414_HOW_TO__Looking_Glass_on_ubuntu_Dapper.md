---
title: "HOW TO : Looking Glass on ubuntu Dapper"
date: 2006-05-22
forum: Desktop Environments
---

### Post by wakady on 2006-05-22
Here is a little how to add looking glass to ur ubuntu desktop

**NOTE **I tested it on my ATI 9600XT with latest driver for nVidia u must have at driver 1.0-8756 or higher,
if u get any trouble look here
[https://lg3d.dev.java.net/nvidia-driver-install-tips.html]("https://lg3d.dev.java.net/nvidia-driver-install-tips.html")
and here
[https://lg3d.dev.java.net/lg3d-getting-started.html#Platform_Requirements]("https://lg3d.dev.java.net/lg3d-getting-started.html#Platform_Requirements")

**Here we start**

First must install JDK 6 directly from here
[http://www.java.net/download/jdk6/binaries/jdk-6-beta2-bin-b84-linux-i586-11_may_2006.bin]("http://www.java.net/download/jdk6/binaries/jdk-6-beta2-bin-b84-linux-i586-11_may_2006.bin")

or choose from here
[http://download.java.net/jdk6/binaries/]("http://download.java.net/jdk6/binaries/")

Then install LG3D packages from here

1- Ubuntu Lg3d package 
[https://lg3d-core.dev.java.net/files/documents/1834/34717/lg3d-core_0.8.0_rel_i686.deb]("https://lg3d-core.dev.java.net/files/documents/1834/34717/lg3d-core_0.8.0_rel_i686.deb")

2- Ubuntu lg3d-jdk package 
[https://lg3d-core.dev.java.net/files/documents/1834/34718/lg3d_jdk1.6.0_i686.deb]("https://lg3d-core.dev.java.net/files/documents/1834/34718/lg3d_jdk1.6.0_i686.deb")

3- Ubuntu lg3d-java3d package 
[https://lg3d-core.dev.java.net/files/documents/1834/34719/lg3d_java3d_1.4.0_i686.deb]("https://lg3d-core.dev.java.net/files/documents/1834/34719/lg3d_java3d_1.4.0_i686.deb")

u can run it from here 
```
/usr/share/lg3d/bin/
```

ATI users can only run 
```
./lg3d-app
```
which starts in application mode 
It can run in full screen & as a Desktop like Gnome & KDE but it didn't work on my ATI :confused: i think it can on Nvidia

So help ur self with the rest u can start from here
[https://lg3d.dev.java.net/lg3d-getting-started.html]("https://lg3d.dev.java.net/lg3d-getting-started.html")

**For LiveCD ca be found here**
[https://lg3d-livecd.dev.java.net/]("https://lg3d-livecd.dev.java.net/")

**For Full Review go here**
[http://www.tuxmachines.org/node/3171]("http://www.tuxmachines.org/node/3171")

**Some Images too...**

[IMG]http://www.tuxmachines.org/gallery/albums/lg3d/blackgoat.sized.jpg[/IMG]

[IMG]http://www.tuxmachines.org/gallery/albums/lg3d/gaim3.sized.jpg[/IMG]

[IMG]http://www.tuxmachines.org/gallery/albums/lg3d/cosmosch2.sized.jpg[/IMG]

[IMG]http://www.tuxmachines.org/gallery/albums/lg3d/browser.sized.jpg[/IMG]

[IMG]http://www.tuxmachines.org/gallery/albums/lg3d/fmclk2.sized.jpg[/IMG]

---

### Post by wakady on 2006-05-22
Here is a Great clip that can explain what words can't do

[http://www.sun.com/software/looking_glass/demo.xml]("http://www.sun.com/software/looking_glass/demo.xml")

---

### Post by lithorus on 2006-05-22
[QUOTE=wakady]Here is a Great clip that can explain what words can't do
[http://webcast-east.sun.com/archives/GSN-1312/GSN-1312_forjds.mov]("http://webcast-east.sun.com/archives/GSN-1312/GSN-1312_forjds.mov")[/QUOTE]
404

---

### Post by rado_london on 2006-05-22
Does it work with Intel GMA900 graphics. I also have pentium m 1.7 ghz and 512 MB ram. Is it ok for running it and is it usefull for day to day work.

---

### Post by ssalman on 2006-05-22
[quote=wakady]Here is a Great clip that can explain what words can't do
[http://webcast-east.sun.com/archives/GSN-1312/GSN-1312_forjds.mov]("http://webcast-east.sun.com/archives/GSN-1312/GSN-1312_forjds.mov")[/quote]

web page : 
**[FONT=Arial,Helvetica,Geneva][SIZE=-1] Not Found[/SIZE][/FONT]**

 !!!

---

### Post by wakady on 2006-05-22
Link updated above & here too
[http://www.sun.com/software/looking_glass/demo.xml]("http://www.sun.com/software/looking_glass/demo.xml")
if still didn't work google for the Looking Glass clips or videos

---

### Post by cykematica on 2006-05-22
ok two things.  does this work with compiz?  and what applets are you using to get that panel and where/how can i get it?

---

### Post by rado_london on 2006-05-22
HI
I installed that thing but when i try to start it from CLI I get the grid wallpaper and the X mouse cursor and then everything goes white. Nothing happens. How do I repair this. I am ready to give out any error messages.

---

### Post by RaptorRaider on 2006-05-22
1. You should mention these .deb's should be installed from a terminal. GDebi gets stuck while installing because of licenses (severe bug IMO).
2. This doesn't seem to work with Xgl. Edit: It does when you run ./lg3d-dev instead.

---

### Post by it.henrik on 2006-05-22
great pice of soft .. when the videos isnt even playable in linux .. all I could get was sound from the high-res clip .. not good enough for a eye candy demo ;)

---

### Post by wakady on 2006-05-22
rado_london 
tell me what u did then if i can help u i'll but u have to tell me what is ur system specs & what error did u get..

for the videos i got it from the link i posted 2 days ago i donno what happened but they are AMAZING :D

Forgot its a complete new environment nothing to do with compiz....

---

### Post by rado_london on 2006-05-22
Well I did what was shown in the first post. I isntalled it then killed X and started it. My specs are:
Pentium M 1.7GHz
512 RAM
80 GB HDD
Inel GMA900 graphics card.

Can you tell me exaclty which error mesage to show and how to record it?

---

### Post by obey43 on 2006-05-23
would it be possible to create a session to run this, as one creates a session to run xgl/compiz?

---

### Post by wakady on 2006-05-23
First i donno if it can run on intel graphics card or not i can't confirm coz i didn't use any, u didn't tell me what command did u use to run it !!

First
```
cd /usr/share/lg3d/bin/
```

Then
```
./lg3d-app
```

and it worked for me this way 

about adding it to sessions sure u can i did it and it's now included when i choose what session to log with but i don't remember the exact command, i'm at office now but i'll let u know when i go home,
its some where in 
```
/usr/share/lg3d/bin
```

something like > ./lg3d-session-add
not sure although check it ur self till i go home & tell u

---

### Post by Lord Illidan on 2006-05-23
So how does it feel like? Is it slow? Is it easy to remove?

---

### Post by wakady on 2006-05-23
To add looking glass to gdm 
type
> ./add-lg-to-gdm
in
> /usr/share/lg3d/bin/

---

### Post by rado_london on 2006-05-23
[QUOTE=wakady]First i donno if it can run on intel graphics card or not i can't confirm coz i didn't use any, u didn't tell me what command did u use to run it !!

First
```
cd /usr/share/lg3d/bin/
```

Then
```
./lg3d-app
```

and it worked for me this way 

about adding it to sessions sure u can i did it and it's now included when i choose what session to log with but i don't remember the exact command, i'm at office now but i'll let u know when i go home,
its some where in 
```
/usr/share/lg3d/bin
```

something like 
not sure although check it ur self till i go home & tell u[/QUOTE]
By doing this I end up with empty window and sun java splash screen. Nothing seems to happen. I cant close the window so I have to close the terminal in order to remove it. However I just want to know is LG3d really usable and useful or it is just sunny toy to play with.

---

### Post by NobodySpecial on 2006-05-23
The video is all very playable.

Go to the link video Opera, choose the high bandwidth Real Media file, and Opera will (if you have it configured right) open the file in the Real Media player.

---

### Post by Video Toaster on 2006-05-23
[QUOTE=NobodySpecial]The video is all very playable.

Go to the link video Opera, choose the high bandwidth Real Media file, and Opera will (if you have it configured right) open the file in the Real Media player.[/QUOTE]
It is if you exclude the QuickTime file.  ;)

---

### Post by NobodySpecial on 2006-05-23
By "configured right" I meant this:

Under Opera 9.00 Preview 2 with Realplayer 10 Gold:
Tools -> Pref -> Advanced -> Downloads -> Handlers for saved files -> Add ->
File type: rm
Program: realplay

Now Real Media files will be properly launched in the Realplayer.

I love Firefox and use it for 99% of all my needs (actually use Swiftfox :) ).  But only Opera can correctly handle external players such as Realplayer, Beep Media Player, etc.  This is something I hope the Firefox devs take a look at.

---

### Post by srt4play on 2006-05-23
Firefox on my Breezy computer works just fine at launching realplayer as well as other helper apps and always has. 

Impressive video.

---

### Post by wakady on 2006-05-23
i donno but if u r running it under XGL or AiGLX try to run it under normal env.
also.. if u think XGL is useful then looking glass is useful too
got my point ;)

---

### Post by dabear on 2006-05-25
wakady; where am I supposed to install jdk1.6.0? Running the install file from my desktop (as root through cli) only makes a new directory called jdk1.6.0 on my desktop.

---

### Post by dabear on 2006-05-25
Ok, so I read the project page. Running this command should make it work, but I only get a java splash screen:
```

JAVA_HOME=/home/bjorninge/Desktop/jdk1.6.0/ /usr/share/lg3d/bin/lg3d-app

```

I also tried killing X and running this command from the terminal:
```

JAVA_HOME=/home/bjorninge/Desktop/jdk1.6.0/ /usr/share/lg3d/bin/lg3d-session

```
but the only thing I get is a java 3d error complaining about not having OpenGl1.3 (1.2 is found).

 Any idea? I woul really like to try this..

---

### Post by nalmeth on 2006-05-26
Can anyone offer a review of Looking Glass? 

Unfortunately the [LG3D LiveCD]("http://distrowatch.com/table.php?distribution=lg3d") doesn't work on my intel i915GL graphics card (i810 driver).
I had the *previous* release going at work, and on my dad's PC.

It's quite nice, but I thought looked a little unrefined.

The panoramic viewing was really cool. You just pick out one of the many included wallpaper's (icon on the bottom right), and you push the sides of the screen to look around. Beautiful.
The 3D window flipping was really seamless, and fun of course. 

The window's looked kinda funny though, blocky and kind of un-vibrant color's.. Naturally work in progress. Also, I couldn't get a terminal, firefox, or gaim to open. Some of the games and toy's worked though. 

All in all it was great beyond being a little raw.

What is this release like? 

BTW wakady you might want to post the liveCD link, people might want a liveCD to try first.
HowTo look's good, will try it out when I get my new (used) NVidia card running :)

---

### Post by strikeforce on 2006-05-31
I tried it using my nvidia 6800GT and it works a treat.  Its very different and my resolution is 1280x1024 so its tiny in parts but yeah looks so cool.

I will hopefully find some time to have a big play around with it and see what can be done.  It runs smooth as well.  P4 3.2 Ghz so I'm hoping it will run smooth.

---

### Post by panurge77 on 2006-06-02
[https://wiki.ubuntu.com/JavaPackageBuildNewVersions](https://wiki.ubuntu.com/JavaPackageBuildNewVersions)

This should do the trick of getting jdk installed right. I'll try it now.:-k

Edit: no, it did not work for me

---

### Post by panurge77 on 2006-06-02
del

---

### Post by H.E. Pennypacker on 2006-07-03
Wow...Looking Glass appears to be amazing.  I have Compiz/AIGLX currently installed, so I am not going to be trying Looking Glass.  When it becomes very stable and popular, I'll try it.

---

### Post by jgcamp99 on 2006-07-03
"if u think XGL is useful, then looking glass is useful too"

My sentiments exactly, when I posted a thread about it earlier. I downloaded the 137 MB megabundle, installed it, but it appears to be a demo that opens up a window within my current gnome session in a separate window. By installing the debs, Is this a stand alone desktop thing that would integrate with what I've already set up with Ubuntu thus far ? I prefer this to the xGL/Compiz show. The cube is interesting, but 3d, PLG is more what I expected. The cube, somehow reminds me of WYSIWYG 3d spreadsheets in Lotus 1-2-3 from the early 1990's (if any of you remember those), before MS Office/Excel took the lead for spreadsheets. This looks to be like a stylexp 3d desktop version of what Vista will have. I'd like to have the flexibility to keep the 3d desktop more conservatively traditional from a standpoint of the mouse pointer, the window appearances and so on, not like the coughdrop stylexp colors and weird shapes for a mouse icon. Keep the theme relatively tame, but incorporate the 3d aspects. Is that an option here with PLG (Project Looking Glass) ?

[IMG]http://www.microsoft.com/library/media/1033/windowsvista/images/features/feat_UX_09.jpg[/IMG]

This is something that I could ergonomically work on all day long, PLG is too much eye candy for my eyes in terms of shock value of the theme.

---

### Post by Treviño on 2006-07-18
Using XGL + Compiz it shouldn't work... Btw, what about launching lg3d in a different display (:0, or :93... I mean standard xorg...)?

---

### Post by mguerrac on 2006-09-18
hola ah todos me gustaria saber como instalo el xgl en dapper

---

### Post by DoorGunner on 2006-09-19
Hi.... I mangaged to get it installed..

I am running an AMD 3400 machine with a nVidia 6600GT.  I am hoping to find some further instructions....IE how to get some icons going etc and how to access program files. I cant wait to try it on my next uber machine  Everything works although it does seem a little laggy.

When i Check glxinfo | grep rendering i get direct rendering no . According to the card list my 6600gt should be able to direct render. Has anyone come accross a good set of instructions to fix this? or know how?

:biggrin:

---

