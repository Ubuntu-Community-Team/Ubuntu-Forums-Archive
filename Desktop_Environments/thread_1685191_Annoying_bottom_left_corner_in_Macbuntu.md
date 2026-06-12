---
title: "Annoying bottom left corner in Macbuntu"
date: 2011-02-10
forum: Desktop Environments
---

### Post by flee0308 on 2011-02-10
How do I disable the function which shows my desktop whenever I roll my mouse into the bottom left hand corner? I tried using compiz fusion, but now everything just gets minimised, instead of moving to the sides.

---

### Post by Krytarik on 2011-02-10
It seems that the "Scale" plugins now jumps into action instead.;-) Before it actually maybe was the "Expo" plugin. Then try disabling its edge binding also.

You can use "Simple CompizConfig Settings Manager" for that sort of task, package "simple-ccsm".

---

### Post by flee0308 on 2011-02-10
> **Krytarik said:**
> It seems that the "Scale" plugins now jumps into action instead.;-) Before it actually maybe was the "Expo" plugin. Then try disabling its edge binding also.

You can use "Simple CompizConfig Settings Manager" for that sort of task, package "simple-ccsm".

Sorry, but I am not good in linux yet. But from what I understand, I need to:

1) Turn off "Expo" and "edge binding" in CCSM right?

 But then, I cannot find "edge binding". Where can I find it?

2) Install "simple-ccsm". 

I went into synaptic package manager and searched for "simple-ccsm". I found the pacakge, version "0.8.2-0ubuntu1". Is that the one I am supposed to install?

---

### Post by Copper Bezel on 2011-02-10
You can actually just run the command

sudo apt-get install simple-ccsm

from a terminal window, no searching involved, but if the package that came up in Synaptic is called the Simple CompizConfig Settings Manager, then yes, it's the right one. I would actually suggest getting the full manager instead, though, just in case the Macbuntu tweak is tucked away somewhere in something obscure:

sudo apt-get install ccsm

It'll show up in your Preferences menu from the main menu (what Windows calls the "Start" menu.)

An "edge binding" just means how a particular plugin in Compiz can be set to activate when your cursor touches one of the screen edges. Previously, Macbuntu had the Show Desktop plugin activated with an edge binding for the lower left corner. The behavior you're describing now, where everything minimizes, is more like the Show Desktop widget from the Gnome Panel. I don't know how the Macbuntu settings are getting that behavior from a screen edge binding. You don't have to click anything for it to happen, do you?

In response to Krytarik, don't think you're describing the Scale plugin. The Scale plugin, by default if active, is bound to the upper-right corner, not the lower left, and it tiles all your windows on the screen to allow you to select them, looking like this:

[IMG]http://i146.photobucket.com/albums/r256/Kalimol/Screenshot-9.png[/IMG]

You don't need to disable Expo. It's an unrelated plugin for workspace switching.

If the plugin isn't Scale or Show Desktop, I'm not really certain what it might be. As I said, it sounds more like the Show Desktop panel applet, but there's no way to assign screen edge bindings to panel applets. I don't know if any of that helped, but I'll need more details before I can suggest anything further.

---

### Post by flee0308 on 2011-02-10
Well, nothing turns up with "sudo apt-get install ccsm". Anyway, I have installed the ccsm from Software Centre. I supposed that's the latest version.

Nope, I don't have to click anything to minimise.

Yeah, it isn't Show desktop, I disabled that. And it is not scale. I use scale alot, and scale is at the bottom right for Macbuntu.

And actually, I thought of a solution myself: Uninstall Macbuntu and install it again. I vaguely remember giving an option to let macbuntu minimize everything. If this method works, I will change the thread to "solved".

EDIT: How do I uninstall Macbuntu >.< I tried typing the code below, but Macbuntu didn't get uninstalled. I think I downloaded something else, in fact.

```
wget https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz -O /tmp/Macbuntu-10.10.tar.gz
tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp
cd /tmp/Macbuntu-10.10/
./uninstall.sh
```

---

### Post by Copper Bezel on 2011-02-10
Aha! I found it!

Go back to CompizConfig, go to General Options, select the Key Bindings tab, and - lo and behold - there is exactly one window action that can be set to a screen edge binding, and it's (yet another) Show Desktop, but one that operates by minimizing everything exactly as you described. Disable it. Done. = )

---

### Post by flee0308 on 2011-02-10
> **Copper Bezel said:**
> Aha! I found it!

Go back to CompizConfig, go to General Options, select the Key Bindings tab, and - lo and behold - there is exactly one window action that can be set to a screen edge binding, and it's (yet another) Show Desktop, but one that operates by minimizing everything exactly as you described. Disable it. Done. = )

Disabled, Thanks!

---

### Post by Krytarik on 2011-02-10
Well, that's the reason why I recommended Simple-CCSM, in order to not having to search for it. ;-)

---

