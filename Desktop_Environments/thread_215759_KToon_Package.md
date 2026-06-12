---
title: "KToon Package"
date: 2006-07-14
forum: Desktop Environments
---

### Post by shendric on 2006-07-14
Does anyone know if there is any plan to have an official Ubuntu package for KToon ([http://ktoon.toonka.com/](http://ktoon.toonka.com/))?  I tried to install the .deb package, but got too many dependencies, and I thought if there was an Ubuntu package that I could install by apt-get or Synaptic, that might be easier to deal with.

Alternatively, if anyone has gotten KToon to work under Dapper Drake, that'd be neat to hear about.

---

### Post by gThree on 2006-07-14
Just wanted to add another vote for an official package.  If this works, would love to see this in Kubuntu/Ubuntu.

---

### Post by monts on 2006-08-11
Yet another vote for this to make it as a package

---

### Post by dontunderstand on 2006-08-14
yes, i want it too.[-o<

---

### Post by lamego on 2006-08-14
I have created the .deb package for the current version.
Please let me know if it worked fine (it worked for me).
[ftp://ftp.sunsite.dk/projects/ptlink/ubuntu/debs/ktoon-0.8_0.8-1_i386.deb](ftp://ftp.sunsite.dk/projects/ptlink/ubuntu/debs/ktoon-0.8_0.8-1_i386.deb)

---

### Post by HanZo on 2006-08-22
thanks a lot! tried to compile the souces... but as usual without much luck... so I'm really happy about this .deb file!
the package installed without problems in dapper... just one dependency was not respected, libqt4-gui needs to be installed for ktoon to function as it needs the libqt svg library. not a big problem anyway.

---

### Post by HanZo on 2006-08-23
it's not really related to the deb package... but maybe it is... the app does not show any icons... but I think there should be some and I'm not able to use any drawing tools... 
and btw. what should I put in the "installation dir" box that I have to fill during the startup wizard procedure?

---

### Post by sciboy on 2006-08-26
Where the Ktoon data files are.
Run `dpkg -L | grep data`

But on my system, the path is /usr/share/ktoon/

---

### Post by shendric on 2006-08-28
Hey,

I got the package to install, and I got the libqt4-gui package installed.  However, when I start it and go through the installation wizard, when I try to browse for the installation directory, it freezes up on me.  I had tried to use dpkg -L to find the installation directory, but it tells me that ktoon isn't installed.  Any thoughts on what might be wrong?

---

### Post by xtingray on 2006-11-26
Hello to everyone,
I am working in the KToon project and i want to share some ideas with you:

- The application is still in beta state, so, try to do a package for it is not a good idea yet, but you can try it any way.

- If you want to test the version 0.8.0, i recommend you to use our live-cd, in that way you can test what the program can do in a quick and easy way. 
It can be downloaded from:
[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/KToon-Live-CD-16643.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/KToon-Live-CD-16643.shtml)

- If you want to make an Ubuntu package for KToon 0.8.0, you should to note that:
  1. You have to make the Qt 4.1.4 package for Ubuntu
  2. You have to make the ffmpeg package for Ubuntu, compiling it in shared mode. More info: [http://ktoon.toonka.com/documentation/index.php?title=Installing_FFMPEG_for_KToon](http://ktoon.toonka.com/documentation/index.php?title=Installing_FFMPEG_for_KToon)

I hope this ideas can help you a little.

---

### Post by cainmark on 2006-12-07
The KToon project needs some help, financial or otherwise.  they had posted about maybe letting theproject disappear.  I love their liveCD and anyone who thinks there should be a debian package of it for ubuntu ro use might want to help them out.  I don't have much, but I did send $25 because I've already gotten that much use of it, and it's worth it to me to see an open source animation package.  Moho (now Anime Studio) is an awesome program, but it is proprietary.

For ANY 2D animation software to be open source is well worth supporting it, in whatever little way you can.

---

### Post by kperkins on 2006-12-28
I would support it, if it actually _did_ something.
I can't get it to run on Ubuntu (crashes when opening--see several other threads about that), and the live CD doesn't work either. (The CD itself works fine, but ktoon doesn't, if you try drawing, nothing shows up--not very useful, and really quite disappointing, since it's supposedly running in an environment made for it.)

---

### Post by motin on 2007-01-06
> **sciboy said:**
> Where the Ktoon data files are.
Run `dpkg -L | grep data`

But on my system, the path is /usr/share/ktoon/

On mine, using the package above - it is the rather non-standard directory /data/

> **shendric said:**
> Hey,

I got the package to install, and I got the libqt4-gui package installed.  However, when I start it and go through the installation wizard, when I try to browse for the installation directory, it freezes up on me.  I had tried to use dpkg -L to find the installation directory, but it tells me that ktoon isn't installed.  Any thoughts on what might be wrong?

Same here. Use dpkg --contents Desktop/ktoon-0.8_0.8-1_i386.deb to see the contents on the package. The package will install the ktoon data files to plain simple /data/

Use /data as ktoon installation dir in the Wizard. 

It launches ok and shows clearly that it is a beta version, but looks slick anyway. 

Now I know. Since I am not interested in animation I really don't know what do with it though :) I only liked the fact that it should be able to export to .swf and thus I can recommend it to flash-creators that wants a good free animation studio.

---

### Post by muhkayoh on 2007-01-06
I've had no luck trying to run Ktoon.  I've had various problems that I couldn't solve when trying to install and run it so I tried the liveCD.  But that never loads as my Ubuntu Edgy ignores the CD and boots up Edgy every time. ](*,)

Matt

---

### Post by muhkayoh on 2007-01-06
Closest I've gotten yielded an immediate crash and this info:

```
[Initializing DApplication]
[Initializing DConfig]
[Initializing DConfigDocument]
*********Init configuration file : "/home/matt/.ktoon/ktoon.cfg"
ktoon is crashing with signal 11 :(
QPixmap::fromImage: Cannot convert a null image
QCoreApplication::exec: The event loop is already running

```

I don't know enough about what it says to be able to try to fix the problem.  For a brief second, though, I could see what might have been a nice splash page.  :D

Matt

---

### Post by shadarack on 2007-01-11
Help!

Not sure if I've done something wrong...I ran the .deb file, and now cannot find Ktoon to run it! Should it be in my program menu somewhere?

Does it make a difference if I'm using XFCE? I seem to recall hearing somewhere that some KDE programs will only run in KDE - is this one of them? /IS/ Ktoon a KDE program? The name suggests it is.

Despite a little experience, I'm still pretty much a Linux newb. Can someone tell me how to find Ktoon so I can run it, now that I've installed it?

---

### Post by cainmark on 2007-03-26
I didn't have any problems with the liveCD.  I think that it was so Qt  dependent made it difficult.
I was hoping they could get it into the ubuntu repositories, which is why I supported it..  I've only used it from the liveCD.

---

### Post by cainmark on 2007-03-26
the liveCd was the only way I could get it to run, but that was why I was asking for people to help them with the coding since i don't know how to do any of that.  But the liveCD interface works very well for me.

---

### Post by EnigMattic on 2007-03-28
> **muhkayoh said:**
> Closest I've gotten yielded an immediate crash and this info:

```
[Initializing DApplication]
[Initializing DConfig]
[Initializing DConfigDocument]
*********Init configuration file : "/home/matt/.ktoon/ktoon.cfg"
ktoon is crashing with signal 11 :(
QPixmap::fromImage: Cannot convert a null image
QCoreApplication::exec: The event loop is already running

```

I don't know enough about what it says to be able to try to fix the problem.  For a brief second, though, I could see what might have been a nice splash page.  :D

Matt

I'm having exactly the same problem... (except, curiously I don't get the final part of the error; 'QCoreApplication::exec: The event loop is already running') and my name is also Matt. What a world...
anyone got any ideas about this yet?

---

### Post by muhkayoh on 2007-04-04
Heh.

The Ktoon team recently [released a test version]("http://ktoon.toonka.com/") specifically aimed at Ubuntu and I downloaded it and got it running just now.  It's actually fairly impressive already as far as the feature set goes.  I'm officially excited about the project now (which is probably just the reaction they were aiming for with this Ubuntu test package).

Matt

---

### Post by shendric on 2007-04-04
> **muhkayoh said:**
> Heh.

The Ktoon team recently [released a test version]("http://ktoon.toonka.com/") specifically aimed at Ubuntu and I downloaded it and got it running just now.  It's actually fairly impressive already as far as the feature set goes.  I'm officially excited about the project now (which is probably just the reaction they were aiming for with this Ubuntu test package).

Matt

Yeah, I just downloaded it, as well.  It doesn't seem to do anything, though, just show you how it's all laid out.  Did you get it to allow you to draw anything?

Sean

---

### Post by muhkayoh on 2007-04-04
Yes, I've been able to draw lines and do fills, both with different colors chosen from the palette, so that much is working.  The line smoothing setting seems to be working as well.  I tried to import a background image, but that didn't seem to work.  Overall, though, it looks like they're headed in the right direction with the right bunch of features for more-or-less traditional 2D animation.  I hope they get a little infusion of development cash because of this.  I tossed 'em a few bucks, though I wish I could do more.  If this package winds up as good as it looks like it could, I'll probably use the heck out of it.

Matt

---

### Post by shendric on 2007-04-04
That's odd.  I just started it again, and this time, it worked.  Go fig.  It definitely has possibilities.  I'm pretty impressed with what they've got thus far.

Sean

---

### Post by shendric on 2007-04-04
> **muhkayoh said:**
> I tried to import a background image, but that didn't seem to work.

Just to let you know.  I tried the import image, as well, and what it did was add it to the library.  You have to add it to the stage from the library.  So, I was able to get one imported.  Were you able to do gradient fills?  When I tried it, all I got was a single color across the entire stage.

Sean

---

### Post by muhkayoh on 2007-04-04
> **shendric said:**
> Just to let you know.  I tried the import image, as well, and what it did was add it to the library.  You have to add it to the stage from the library.  So, I was able to get one imported.  Were you able to do gradient fills?  When I tried it, all I got was a single color across the entire stage.

Sean

Ah, okay.  That makes sense.  And I didn't try gradients yet.  Had to shut down, stop playing, and get back to work for now.  But I'll toy with it some more later.  I really hope these guys can keep going with the project, 'cause it really looks promising.

Matt

---

### Post by muhkayoh on 2007-04-04
Okay, I got to play with it some more and was able to import background images and get them onto a layer in the project.  What I'd love to see now is some good documentation so I can learn how some things are supposed to work.  (There isn't much documentation on the main site, at least not much in english.)  For instance, how does the whole key frame/tween concept work in Ktoon?  Is there (or will there be) a mechanism for, say, zooming backgrounds or any motion tweening?  (Maybe that Graphic Component editor module plays a roll in motion tweening, but I couldn't get it to do anything yet.)  Stuff like that.

I was able to output still images as well as video files, so you might actually be able to make movies with this already.  Here's a still that has an unfinished background image I imported from another project and a little stick figure hastily drawn over it in Ktoon:

[IMG]http://sketch.mattjordan.com/images/animation/20070404_frame_render_01.png[/IMG]

Still pretty exciting stuff for a wannabe animator like myself.

Matt

---

### Post by sanicki on 2007-07-19
Bump for KToon deb. Their [test binary]("http://ktoon.toonka.com/index.php?option=com_content&task=view&id=40&Itemid=36") works fine for me, I just can't figure out how to make a KMenu or desktop shortcut for it that works. Anybody know how?

[figured it out. has something to do with export KTOON_HOME=`pwd` in their ktoon script. correct path from command line, but shortcut produces path to user's home directory only. brute-force fixed it by adding 'cd <path to ktoon directory>' to the top of the script. anyone have a more elegant solution to share?]

---

### Post by yourpalal on 2008-05-16
using /usr/share/ktoon as my install dir i have no brushes, tools etc. I installed through adept (as i am using Kubuntu) please help thanks!:confused:

---

