---
title: "Natty and Compiz Blur Plugin doesn't work"
date: 2011-05-02
forum: Desktop Environments
---

### Post by Nerotriple6 on 2011-05-02
So upgrade to Natty went well-ish.. Nevertheless I did a clean install and mounted my user folders/partitions back after removing everything else from the Home drive to ensure no incompatible leftovers from Maverick.

Now, I am dissapointed to see that I can't get blur on my transparent windows. This worked like a charm in Maverick and it looked brilliant but now it's often hard to tell windows apart if there are windows below the active one. So I had to turn down transparency... :(
I have D-bus enabled, proprietary drivers installed and I have been Google-searching like crazy to find a solution. None.. :(

Do any of you know the status of this plugin in Natty? Should it work, does it? Or not?

I have Focus blur activated and working, it helps but not enough.
My videocard is Radeon HD 4650 (AGP).

---

### Post by Nerotriple6 on 2011-05-02
**_Update:_**

When I got home I almost wanted to cry.. no blur. :(
So my (low) experience told me that this is a Unity issue and just now I logged out of my Unity session and into Gnome2.

My assumptions were right. I have blur and everything in Compiz works. I also noticed performance increase despite my transparency and blur settings which should decrease performance. Compiz do not like Unity. 

So I will use Gnome again. I have tried 3 times to get Gnome 3 working but errors and no fallback. I will wait until there is a stable repo for it. Allthough Unity was like a breath of fresh air. Even though I used it on my Eee that got hax0rd (in Windows :P:P).

_Nevertheless, any fix for this in Unity?_ Is it just immature or is there something I can do about it? If Compiz will work I think Unity can grow on me, there are some things I like about it, that I miss in Gnome.. :P

---

### Post by anishd on 2011-05-08
I was also searching for any solution. Probably loss of blur effect is a deliberate outcome of unity.

---

### Post by Nerotriple6 on 2011-05-08
Perhaps. It works in Gnome on the same install..

---

### Post by Krytarik on 2011-05-08
"Blur", too, doesn't work in my Lucid 10.04 with Gnome 2.

Greetings.

---

### Post by mia1dolfan on 2011-05-13
I had the same issue after upgrading to Ubuntu 11.04.  No blur on windows with GTK RGBa support, both using Unity and Classic sessions.

I resolved the issue on my system by launching ccsm --> Blur Windows, copy the regex window type context of "Focus blur windows" and paste into "Alpha blur windows".  You have to this separately inside of the Unity and Ubuntu Classic sessions respectively.

Once you have Compiz configured the way you like you may want to backup your config, especially if you enabled the Cube.  ccsm -> Preferences -> Export.  Again you have to do this separately for Unity and Ubuntu Classic.

:guitar:

---

