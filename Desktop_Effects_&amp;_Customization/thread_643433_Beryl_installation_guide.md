---
title: "Beryl installation guide"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by Sordelka on 2007-12-17
Can anyone point out a good Beryl installation guide for Ubuntu Gutsy 7.10?

Thank you!

---

### Post by spiderbatdad on 2007-12-17
have you seen this one? [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by JillSwift on 2007-12-17
I suggest going with Compiz-fusion. Beryl's a dead project and not supported, and Compiz-fusion does everything Beryl could do, including the Emerald window decorator.

---

### Post by Sordelka on 2007-12-17
Um where do I get it and is there a guide for Ubuntu 7.10?

---

### Post by spiderbatdad on 2007-12-17
it comes installed with 7.10 to enable, though you need the settings manager found in synaptic```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Joeb454 on 2007-12-17
> **spiderbatdad said:**
> it comes installed with 7.10 to enable, though you need the settings manager found in synaptic```
sudo apt-get install compizconfig-settings-manager
```

If you install that you'll get all the options to enable the cube etc. You'll need to do some fiddling, but just post back if you have more problems :)

---

### Post by Sordelka on 2007-12-17
I have installed it. It works perfectly. Except one thing: How do I make it turn and twist like in all those youtube videos. 

Example:

[http://www.youtube.com/watch?v=ZRP8fPcaSzI](http://www.youtube.com/watch?v=ZRP8fPcaSzI)

When it shows like the cube in a space environment and you see all the desktops. Not in line but as a cube. 

I cannot find that option...

---

### Post by spiderbatdad on 2007-12-17
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by spiderbatdad on 2007-12-17
i think the middle mouse button is the defualt setup for that. if you dont have a middle mouse try both buttons. There are nearly endless settings as you play with it and learn to use it, for example you can change the distance the screen zooms out on the cube as it rotates.
First. in the settings manager you will have to select "cube" and "rotate cube" as options. they are not selected by default

---

### Post by Joeb454 on 2007-12-17
to move the cube, I think the default setting is Ctrl+Alt+Left Mouse button, you have to click and hold the button

Also Ctrl+Alt+Left or Right works too :) That just switches workspace though...but you can do it REALLY fast :p

---

### Post by atlya02 on 2008-02-17
> **spiderbatdad said:**
> it comes installed with 7.10 to enable, though you need the settings manager found in synaptic```
sudo apt-get install compizconfig-settings-manager
```

Hay everyone.  New Newbie.  I know I have to enter the above qoute into the terminal... Can someone break it down key by key?

---

### Post by oldos2er on 2008-02-17
atlya02, start with the commands "man sudo" and "man apt-get." You can also plug the whole command "sudo apt-get install compizconfig-settings-manager" into Google.

---

### Post by atlya02 on 2008-02-18
thx much!
I will give it a try.:)

---

### Post by theRightNee on 2008-02-18
question: i have been trying to get my Quadro 2 Pro card to work with compiz for a long time now, and I am just curious...does it even work under compiz? I read under one of the forum topics that legacy cards do not work well...=[

---

### Post by Tatty on 2008-02-18
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29")

and if that doesnt work...

[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by theRightNee on 2008-02-18
o well...i was planning on getting a newer card sooner or later...
btw...i couldn't seem to find a list of cards...could you tell me the name of the link? thanks!

---

### Post by Tatty on 2008-02-18
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html")

Your card is mentioned near the end, but i dont really understand wether that means ubuntu can install the drivers for it or not.

I had a look over on the nvidia site and the legacy driver there does support your card, so you could try installing that as per the second link in my last post.

---

### Post by FuturePilot on 2008-02-19
The nvidia-glx-legacy (71xx) driver does not have support for compositing.

---

