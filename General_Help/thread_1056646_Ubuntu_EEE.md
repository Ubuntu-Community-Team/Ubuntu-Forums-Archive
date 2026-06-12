---
title: "Ubuntu EEE"
date: 2009-02-01
forum: General Help
---

### Post by theQmaster on 2009-02-01
Hi,

I've seen the Ubuntu EEE on a netbook and thought it looked great. I especially liked the desktop and how it is organized.

My question: is it possible to make my desktop on Ubuntu 8.10 look closed to that ?

Thanks!
Q

---

### Post by dcstar on 2009-02-01
> **theQmaster said:**
> Hi,

I've seen the Ubuntu EEE on a netbook and thought it looked great. I especially liked the desktop and how it is organized.

My question: is it possible to make my desktop on Ubuntu 8.10 look closed to that ?

Thanks!
Q

Just install the same packages as the eee distro does (or install the eee distro).

---

### Post by theQmaster on 2009-02-01
I already have the 8.10 installed.

> **dcstar said:**
> Just install the same packages as the eee distro does (or install the eee distro).

---

### Post by MarblePanther on 2009-02-01
Read this first:


[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

> Ubuntu 8.10 (Intrepid) UNR Package Installation

The following instructions detail how to add UNR packages to an existing Intrepid based system:

   1.  Open the "Software Sources" dialog from the System->Administration menu
   2. Click on the "Ubuntu Software" tab and check the "Community-maintained..." box (or else libclutter will not be found).
   3. Click on the "Third Party Software" tab and the click "Add..." button
   4.In the newly opened dialog, paste the following line into the text entry box 
 ```
deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) intrepid main
```
   5. Click "Add source" button, then "Close". If the dialog asks you to reload the packages, select "yes".
   6. In Terminal (Applications,Accessories,Terminal), paste this and hit enter and wait for it to finish installing: ```
sudo apt-get update && sudo apt-get install go-home-applet human-netbook-theme maximus netbook-launcher window-picker-applet
``` 

Notes:

    * Neither the netbook-launcher or maximus automatically start, you will need to add them to your session through gnome-session-properties

^^^
Do this by opening System,Preferences,Sessions.  Add a line with the command: netbook-launcher          and one for:   maximus

    * "netbook-launcher" is the intrepid version of the launcher, based on clutter-0.8
    * The ppa will be updated shortly with metacity/desktop-switcher packages for intrepid. DO NOT USE the hardy versions of these packages with intrepid 

restart your computer and login


Note: I edited this a few times, please go over it again

---

