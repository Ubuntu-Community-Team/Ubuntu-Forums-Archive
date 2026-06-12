---
title: "Minecraft crashes, requires force-shutdown"
date: 2014-08-18
forum: Gaming &amp; Leisure
---

### Post by ka2012 on 2014-08-18
Hi everyone. I have had minecraft installed for a while, and its been working fine up until now.  Now I open it, and the launcher comes up fine. I hit play, and it shows me the screen that says mojang, then my screen gets a greyish-black checkerboard pattern over the entire thing, like so. [ATTACH=CONFIG]255608[/ATTACH]   I have tried bringing up a terminal, ctrl-alt-arrowing to another screen, pressing escape, but it doesn't do anything, so I have resorted to holding down the power button and restarting. I am using Java runtime 7 (I tried switching to 6, also reinstalling 7). My video card is  [AMD/ATI] Wrestler [Radeon HD 6310]. I have tried searching for a solution, but the complete lack of error messages or feedback is making it a bit difficult, so any help would be appreciated. Thanks.

---

### Post by lah7 on 2014-08-25
Are you using any proprietary drivers? (Located under Software Sources &#8594; Additional Drivers) Try installing AMD's own driver to see if that helps.
Alternatively, if you are using AMD's own driver, try the open source one to see if it still happens.

I will assume you're using the IcedTea OpenJDK runtime (provided in the repositories)
Mojang suggest using Oracle's Java runtime which isn't in the repository as it is partially closed source. [You can install it a search away]("https://www.google.co.uk/#q=install+oracle+java+ubuntu+14.04").

---

### Post by bizhat on 2014-08-26
I have MineCraft, works fine on my HD 5670 512 MB GPU. I use Open Source driver and java

```

$ java -version
java version "1.8.0_20"
Java(TM) SE Runtime Environment (build 1.8.0_20-b26)
Java HotSpot(TM) 64-Bit Server VM (build 25.20-b23, mixed mode)
$ 

```

Installed java from webupd8 PPA

[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

---

### Post by nsync on 2014-08-26
Try Checking if you got any mods installed , also if im not mistaken, i think minecraft doesn't support J7 , also if it causes a complete shutdown. you might have some hardware problems or  there are some drivers missing.

---

### Post by ka2012 on 2014-08-29
Hi, thanks for the help everyone. I did manage to fix it by uninstalling and reinstalling minecraft. I figured out that it only did that when it was full screen, so when I reinstalled it, I didn't select that option and now its running fine. I am still using OpenJDk Java runtime 7, and its working fine as long as I don't full screen it. It just confused me how fullscreen was fine one day and then did this the next (I didn't change anything). I will try using the other drivers and/or Oracle's runtime and see if that fixes. Until then, Ill just play it maximized instead of fullscreen.

---

### Post by ka2012 on 2014-08-29
And nsync, It don't its causing a complete shutdown. It just completely messes up the graphics, and the only way to get it back to normal or do anything is to restart the computer, and the only way I could figure out how to do that was just to hold the power button to turn it off. Thanks for the help!

---

