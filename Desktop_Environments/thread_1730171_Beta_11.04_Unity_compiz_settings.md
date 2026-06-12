---
title: "Beta 11.04 Unity compiz settings"
date: 2011-04-15
forum: Desktop Environments
---

### Post by Maintech on 2011-04-15
I have been unable to find the settings to enable or adjust compiz in Unity. I am so used to Gnome that this is almost like starting over.

---

### Post by russ553 on 2011-04-15
Go to software center and download the Compiz Configuration Manager, ccsm.

There is a Unity button in the ccsm that will allow you to adjust Unity a little.  Not much you can change, though.

---

### Post by Maintech on 2011-04-15
> **russ553 said:**
> Go to software center and download the Compiz Configuration Manager, ccsm.

There is a Unity button in the ccsm that will allow you to adjust Unity a little.  Not much you can change, though.

It refuses to all me to install. Claims it would have to remove existing compiz and unity plus a lot of other dependencies.

---

### Post by Copper Bezel on 2011-04-15
What output do you get when you try to install it from the terminal? The package is ccsm. Post the output here.

---

### Post by Maintech on 2011-04-15
> **Copper Bezel said:**
> What output do you get when you try to install it from the terminal? The package is ccsm. Post the output here.

Here is a screen shot of my synaptic:

---

### Post by 3Miro on 2011-04-15
> **Maintech said:**
> Here is a screen shot of my synaptic:

No, don't remove anything!

Go to the menu (top left) and search for Synaptic Package Manager. Once in, you can search for CCSM, then use Synaptic to Install CCSM (mark for installation). Once installed, you can search the menu for CCSM and you will have all the settings. I think only the 3D cube doesn't work.

---

### Post by Copper Bezel on 2011-04-15
Before someone asks, I might have thought that would be a normal feedback for *removing* Compiz, but it's not; I just tried marking Compiz for removal, and I didn't get any of the items on that list as required changes. There actually might be something unusual going on.

Also, the Cube was fixed for this beta. = )

---

### Post by Maintech on 2011-04-15
> **3Miro said:**
> No, don't remove anything!

Go to the menu (top left) and search for Synaptic Package Manager. Once in, you can search for CCSM, then use Synaptic to Install CCSM (mark for installation). Once installed, you can search the menu for CCSM and you will have all the settings. I think only the 3D cube doesn't work.

ummmm....that doesn't make sense. You put a quote of me saying "this is a screenshot of my synaptic". I DID use the Synaptic Package Manager.....not apt-get install.......that should have been obvious from my screen shot.

---

### Post by Copper Bezel on 2011-04-15
You did indeed. = / Seriously, could you post your output from apt-get? I really do want to know so that we can figure out where this is failing.

It won't make an action with "reqired changes" without your confirmation, the same as Synaptic.

---

### Post by Maintech on 2011-04-16
> **Copper Bezel said:**
> You did indeed. = / Seriously, could you post your output from apt-get? I really do want to know so that we can figure out where this is failing.

It won't make an action with "reqired changes" without your confirmation, the same as Synaptic.

sudo apt-get install simple-ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages

Simple-ccsm is the ONLY ccsm listed.

---

### Post by Copper Bezel on 2011-04-16
Did you try installing it under the new package name listed there, "compizconfig-settings-manager"?

---

### Post by Maintech on 2011-04-16
> **Copper Bezel said:**
> Did you try installing it under the new package name listed there, "compizconfig-settings-manager"?

That did it. That was all that was needed. Thank you for pointing out what should have been obvious to me......but wasn't.

---

### Post by foxruns on 2011-05-04
installing under the new package name in synaptic worked for me as well

---

