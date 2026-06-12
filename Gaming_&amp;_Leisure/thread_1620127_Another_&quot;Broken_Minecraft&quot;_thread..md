---
title: "Another &quot;Broken Minecraft&quot; thread."
date: 2010-11-12
forum: Gaming &amp; Leisure
---

### Post by Tratz on 2010-11-12
Hey Guys,

I'm running Ubuntu 10.10 and installed the latest version of Sun Java (6.22). The game launches, updates and gets to the Mojang Specifications screen and then poofs. The Terminal shows this:

[FONT=monospace]tratz@tratz-Ubuntu:~/Documents$ java -jar Minecraft.jar
Username is 'Tratz'
28
Setting user: Tratz, XXXXXXX321222795520
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

Aborted
[/FONT]---------

Occasionally I get further than this...but I never really know why. One thing's for sure is I never actually get into the game past the start menu. Any suggestions?

---

### Post by Tratz on 2010-11-12
Just an update, I removed Sun Java and tried OpenJDK instead, same symptoms. The input errors...are they referring to my hardware? I've got a Radeon 5770 1GB card installed. I downloaded the additional drivers for it and for all intents and purposes (mind you, I haven't tried another *game*) my video/audio is working...

---

### Post by donkyhotay on 2010-11-13
Not certain, looks like it can't find an input device (keyboard, joystick, etc.) Not certain why that would happen though. I have just regular mouse/keyboard and don't have this issue with minecraft.

---

### Post by Tratz on 2010-11-13
I really don't know *what* it is. I installed Ubuntu 10.10 for a friend today and her laptop runs the java applet just fine o_o. The more I experiment with Ubuntu the more I realize - things just don't work. iTunes feel flat on its face in Wine, I know others are running it. Absolutely *none* of my steam games work no matter what front end I use to launch them. 

My computer hates me. It could be a motherboard/memory issue. Of course these things run fine in windows, as much as I don't *want* them to I'll just have to deal with it until I figure out exactly what the hell went sideways on me.

---

### Post by WienerWuerstel on 2010-11-13
> **Tratz said:**
> I really don't know *what* it is. I installed Ubuntu 10.10 for a friend today and her laptop runs the java applet just fine o_o. The more I experiment with Ubuntu the more I realize - things just don't work. iTunes feel flat on its face in Wine, I know others are running it. Absolutely *none* of my steam games work no matter what front end I use to launch them. 

My computer hates me. It could be a motherboard/memory issue. Of course these things run fine in windows, as much as I don't *want* them to I'll just have to deal with it until I figure out exactly what the hell went sideways on me.

Well, you can't blame Ubuntu when Windows Applications don't work like they do on Windows. Wine is an amazing App but some bloated Software like iTunes don't work that well and there are many *native* Alternatives (Rhythmbox, Banshee, Amarok...) that support the iPod/Phone just fine. And if you have a newer iPhone/Pod there is a PPA that installs the newest Version of ifuse, so that you can enjoy the great Apple Products on Linux. The Install Instructions are under this mess of a Text.

iPhone/Pod
```
sudo add-apt-repository ppa:pmcenery/ppa 
sudo apt-get update 
sudo apt-get upgrade
```

---

### Post by Tratz on 2010-11-13
I certainly don't blame Ubuntu for any of this. My assumption was that I was either doing something wrong or I have a hardware problem. Either way, since I've been able to prove Ubuntu out on another machine, I think there's more to my problem than just Java. I appreciate the tip though, I'll try that out anyhow :)

---

### Post by nosh276 on 2011-01-30
I have a similar problem.


I'm also having issue with Minecraft and Ubuntu.
I think it is related to Java.
I was running, very successfully, Minecraft on Ubuntu Netbook Remix.

I decided to try out Jolicloud--before I knew about its many imposed limitations (for example, it makes adding ppas a major pain in the ***).

It also makes installing Sun Java extremely difficult and I haven't managed a way around it yet. 

I have Open Java, but it didn't work as well as Sun, when running on UNR, and it crashes after about 30 seconds into gameplay. The longest I've made it is 3 minutes. 

My advice is to make sure that you completely remove all previous versions of Java and then install the latest from Sun. I can assure you that Minecraft does work, and well, on linux.

Good luck.

---

### Post by Refresh100 on 2011-01-30
Hmmm I run it just fine with me on a Radeon HD3200, is this a desktop or a laptop, or worse a netbook?

---

### Post by whowinsdares on 2011-01-30
Anyone know a good way to play counterstrike on Ubuntu please PM me

---

### Post by Refresh100 on 2011-01-30
> **whowinsdares said:**
> Anyone know a good way to play counterstrike on Ubuntu please PM me
What did that have to do with the topic?

---

### Post by Perfect Storm on 2011-01-30
> **whowinsdares said:**
> Anyone know a good way to play counterstrike on Ubuntu please PM me

[[img]http://s1.postimage.org/kdy3czole/Thread_Hijacker.jpg[/img]](http://www.postimage.org/)

---

### Post by Zenmij on 2011-01-30
What I found most annoying is that I was showing a friend various features of ubuntu today on this page :
[http://www.ubuntu.com/desktop/features](http://www.ubuntu.com/desktop/features)
 where it SPECIFICALLY says: Choose from hundreds of games! Supported software: Minecraft.

Now I thought with such a statement it would be in the Software centre, or it would have an established support. BUT not only is it not there, it barely works! as evidenced by a simple google search. Dissappointn :(

---

### Post by Refresh100 on 2011-01-30
> **Zenmij said:**
> What I found most annoying is that I was showing a friend various features of ubuntu today on this page :
[http://www.ubuntu.com/desktop/features](http://www.ubuntu.com/desktop/features)
 where it SPECIFICALLY says: Choose from hundreds of games! Supported software: Minecraft.

Now I thought with such a statement it would be in the Software centre, or it would have an established support. BUT not only is it not there, it barely works! as evidenced by a simple google search. Dissappointn :(
Now now, it can't be in the Software Center due to Notch's "one major rule," which is 
[QUOTE=Notch]
Do not distribute anything I've made. This includes the client and the server software for the game. This also includes modified versions of anything I've made.
In order to maintain control of the project, I need all game downloads to come from a single central source. I hope you understand.[/QUOTE]
Now, Ubuntu has Minecraft support, in fact, at least for me, great support. I play multiplayer on the Client all the time with no problems. What problems are you experiencing?

---

