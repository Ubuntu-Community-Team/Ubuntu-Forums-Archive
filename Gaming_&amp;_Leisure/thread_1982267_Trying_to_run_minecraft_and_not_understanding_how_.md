---
title: "Trying to run minecraft and not understanding how Ubuntu works..."
date: 2012-05-18
forum: Gaming &amp; Leisure
---

### Post by J3WD4Z on 2012-05-18
Okay, so i've searched around on the ofrums a little bit and i know why minecraft wont work i keep getting this error message when i boot MC



      Minecraft has crashed!      
      ----------------------      

Minecraft has stopped running because it encountered a problem.




--- BEGIN ERROR REPORT 7cf3a456 --------
Generated 5/18/12 3:38 AM

Minecraft: Minecraft 1.2.5
OS: Linux (i386) version 2.6.38-10-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Client VM (mixed mode, sharing), Sun Microsystems Inc.
LWJGL: 2.7.1
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Could not init GLX
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.initDefaultPeerInfo(Native Method)
    at org.lwjgl.opengl.LinuxDisplayPeerInfo.<init>(LinuxDisplayPeerInfo.java:52)
    at org.lwjgl.opengl.LinuxDisplay.createPeerInfo(LinuxDisplay.java:717)
    at org.lwjgl.opengl.Display.create(Display.java:855)
    at org.lwjgl.opengl.Display.create(Display.java:785)
    at org.lwjgl.opengl.Display.create(Display.java:766)
    at net.minecraft.client.Minecraft.a(SourceFile:236)
    at net.minecraft.client.Minecraft.run(SourceFile:657)
    at java.lang.Thread.run(Thread.java:662)
--- END ERROR REPORT 955e85fd ----------


Now i am aware of what this means, i tried and installer i found on the minecraft.net forum that a VERY avid ubuntu user designed and installed it (i got this error before i used the installer) and its still here. 

I did more research on the thread and found out this is a VIDEO CARD issue... now I have researched on how to install new drivers and I'm so lost... I did however find a command that managed to help me figure out my video card AND chip set which is good because i figured that would be the FIRST THING you guys would want me to obtain... 

I try too just Google my chip set and ubuntu installer and I get a long list of commands and steps that I don't fully understand, installing ubuntu was a last desperate attempt to save what was left of my laptop when my ex best friend (lots of emphasis on the ex best friend i cant ask him to change it) installed BLACKBUNTU which is apparently a platform of ubuntu for penetration of security?

 I don't know i don't care I just use it as an OS and have hardly any idea on how to use it... 

All i want is to be able to run minecraft and for someone to be able to break it down and give me direct commands and a clear and concise step by step way to fix this video drivier problem. 

And if aftewards i still get this error then clearly my video card is incompatible with minecraft on ubuntu (i used it back when i had windows but my windows got pwned due to my ignorance of proper computer safety precautions that i know now i must take in order for things like this to happen).

 But that doesn't help me now that im using ubuntu NOT KNOWING how to use ubuntu...  I cannot ask my ex friend to uninstall blackbuntu even if i wanted to as we haven't spoken in 6 months and I REALLY need some help with this...  I'm not a moron when it comes to computers... I'm just not a programmer I'm an animator...  

I'm apologise for my super long post, but some help on understanding ubuntu and how to run everything would be really helpful.

 And for some stupid reason I can't open the ubuntu software centre and I have some hardware issues but I that is another thread for another day for another forum and those hardware issues will not effect my video card in any way shape or form...  Please help I would appreciate it a whole hell of a lot...

---

### Post by thatguruguy on 2012-05-18
> **J3WD4Z said:**
> 
Now i am aware of what this means, i tried and installer i found on the minecraft.net forum that a VERY avid ubuntu user designed and installed it (i got this error before i used the installer) and its still here i did more research on the thread and found out this is a VIDEO CARD issue... now I have researched on how to install new drivers and I'm so lost... I did however find a command that managed to help me figure out my video card AND chip set which is good because i figured that would be the FIRST THING you guys would want me to obtain... I try too just Google my chip set and ubuntu installer and I get a long list of commands and steps that I don't fully understand, installing ubuntu was a last desperate attempt to save what was left of my laptop when my ex best friend (lots of emphasis on the ex best friend i cant ask him to change it) installed BLACKBUNTU which is apparently a platform of ubuntu for penetration of security? I don't know i don't care I just use it as an OS and have hardly any idea on how to use it... all i want is to be able to run minecraft and for someone to be able to break it down and give me direct commands and a clear and concise step by step way to fix this video drivier problem and if aftewards i still get this error then clearly my video card is incompatible with minecraft on ubuntu (i used it back when i had windows but my windows got pwned due to my ignorance of proper computer safety precautions that i know now i must take in order for things like this to happen) but that doesn't help me now that im using ubuntu NOT KNOWING how to use ubuntu...  I cannot ask my ex friend to uninstall blackbuntu even if i wanted to as we haven't spoken in 6 months and I REALLY need some help with this...  I'm not a moron when it comes to computers... I'm just not a programmer I'm an animator...  I'm apologise for my super long post, but some help on understanding ubuntu and how to run everything would be really helpful, and for some stupid reason I can't open the ubuntu software centre and I have some hardware issues but I that is another thread for another day for another forum and those hardware issues will not effect my video card in any way shape or form...  Please help I would appreciate it a whole hell of a lot...

Could this be broken down into logical units? I'd love to try to help you, but I really can't figure out what you're asking.

---

### Post by fallenshadow on 2012-05-18
Just realized my post was irrelevant as it looks like a video card issue. You need to install a working driver for that graphics card!

---

### Post by nothingspecial on 2012-05-18
> **thatguruguy said:**
> Could this be broken down into logical units? I'd love to try to help you, but I really can't figure out what you're asking.

Done.

---

### Post by thatguruguy on 2012-05-18
Thanks, nothingspecial.

To the OP: Are you asking how to figure out the video card you have?  Open a terminal, and type the following:
```
lspci | grep VGA
```
Do you happen to know which version of Blackbuntu you're running? You should be able to find out by typing the following in a terminal:
```
lsb_release -a
```
Posting the information about your hardware and OS would be a good way to start.

---

### Post by J3WD4Z on 2012-05-19
> **thatguruguy said:**
> Thanks, nothingspecial.

To the OP: Are you asking how to figure out the video card you have?  Open a terminal, and type the following:
```
lspci | grep VGA
```Do you happen to know which version of  Blackbuntu you're running? You should be able to find out by typing the  following in a terminal:
```
lsb_release -a
```Posting the information about your hardware and OS would be a good way to start.



ok i typed in that command and it says distributor ID: Ubuntu
Description Ubuntu 11.04
release 11.04
codename natty i really just need a straightforward download for a driver and a straight forward way to install it...

Edit: sorry i feel kinda stupid i honestly thought i punched in my video card and chipset into my first post but i didnt epic fail on my end when i punch in the second command it says, 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f], now how do i find a driver for ubuntu with this? do i literally just google it and install a random driver and hope to god it works?

Edit 2: is it a super ridiculously complicated answer if i ask this question, based on what i do know about computers, if your video card works improperly because of a driver issue then your vidoe stays inactive and uses a chunk of your RAM as a temporary video card that creates very strange and unusual colors and patterns on the desktop making it near impossible to use your compter because all your ram is being sucked into video and it runs super slow?  but i can go on youtube and watch videos for hours and i played minecraft when i had windows vista... i dont understand why i'm having this problem at all...  and if it's a super complicated answer that's impossible to explain without having an exstensive knowledge of programming just say "complicated answer"

---

### Post by thatguruguy on 2012-05-19
> **J3WD4Z said:**
> says, 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f], now how do i find a driver for ubuntu with this? do i literally just google it and install a random driver and hope to god it works?

You have a driver for it. Otherwise, your screen would be blank.

The only driver available for your graphics card is the open source fglrx, which is what you have. AMD no longer supports that graphics card, so no proprietary drivers are available.

You have 2 options if you want to play Minecraft in Linux:

[LIST=1]
[*]Buy a better graphics card, preferably one from Nvidia.
[*]Follow the suggestions given [here]("http://www.minecraftforum.net/topic/158692-howto-optimize-minecraft-for-linux/"), and see if you have any luck.
[/LIST]

---

### Post by Lynceus on 2012-05-19
Hope i don't have any problems when  installing minecraft, my computer specs are not that good...

---

### Post by mode7 on 2012-05-20
fglrx would probably work better than whatever proprietary driver out there (That still worked with a recent distro) could offer.

I recall visiting family and trying to get my sister's desktop to run Minecraft (About the closest thing to an FPS she'll play), and had almost no luck. The desktop had only an AGP slot, so the only thing I had that worked was a Radeon 9500 Pro...
Anyways, only the fglrx driver allowed MC to even *start*, and it ran at approximately 2-4 FPS at the lowest settings. Optifine never worked, either.
MC has been a hit or miss for me. It is much worse on laptops, which I assume you have (judging by the card), when you can't upgrade the video card. I agree with thatguruguy, get an Nvidia card if possible when making your next PC purchase(s). I haven't had issues with the newer Intel graphic chipsets either.

Now for not opening Ubuntu Software Center, can you open a terminal, type "sudo apt-get install synaptic", and then open Synaptic Package Manager? That will allow you to install packages through a GUI (And I prefer Synaptic over the Software Center anyways)

Also, you cannot (usually?) uninstall an operating system ;) You generally just write over the partition it is installed to.

---

