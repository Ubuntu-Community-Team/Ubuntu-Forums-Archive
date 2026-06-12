---
title: "Unity Bar Does Not Hide"
date: 2011-08-16
forum: Desktop Environments
---

### Post by asad.bukhari on 2011-08-16
After clicking something in the unity bar, it does not auto hide as it usually does. It stays in front of windows (even if they are maximized). This happens occasionally. It's an issue b/c it blocks a part of my desktop from view. For example, in an instance when the unity bar does not auto hide, I cannot hit the back button on my web browser and must minimize the firefox window to do so....

How can I fix this?

---

### Post by Frogs Hair on 2011-08-16
Open the Compiz CCSM if installed and check your settings in the Unity plugin settings.

If it is set to auto-hide , open the terminal and try this command .
```
unity --reset
```

---

### Post by Frogs Hair on 2011-08-16
> **Frogs Hair said:**
> Open the Compiz CCSM if installed and check your settings in the Unity plugin settings.

If it is set to auto-hide , open the terminal and try this command .
```
unity --reset
```
After reseting Unity you will need to enable auto-hide again .

---

### Post by asad.bukhari on 2011-08-16
I installed compiz ccsm and fixed the issue through there as you described.

I have another basic question:
Compiz ccsm seems better than the default app installed to configure settings. Now that I've installed it, I can get rid of the default app without any problems, yes?

---

### Post by Frogs Hair on 2011-08-16
I have never bothered  removed the basic Compiz settings after installing the CCSM , so I don't the answer .

---

### Post by asad.bukhari on 2011-08-16
No worries. Thanks for the help :)

---

### Post by WanderingAlbatross on 2011-10-17
The same thing did not work for me.  I wonder if it is because I am using unity-2d.  When I type:

> unity --reset

It says 
> The program 'unity' is currently not installed.  You can install it by typing:
sudo apt-get install unity


---

### Post by WanderingAlbatross on 2011-10-19
I eventually found the answer [here]("http://ubuntuforums.org/showthread.php?t=1863532").

---

