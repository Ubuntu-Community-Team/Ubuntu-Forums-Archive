---
title: "How to run compiz setting manager in ubuntu 7.10"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2007-10-19
Hi,

I have ubuntu 7.04 and manually installed compiz+beryl. It works. 
Yestereday, I upgraded it to ubuntu 7.10 via software manager. 

But i cant run the compiz setting manager via menu item.
i even try that in command line, and this is the error i get:

$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

Can someone please help me with my problem?
Thank you.

---

### Post by flx2000 on 2007-10-19
Have you tried installing the compizconfig-settings-manager package by Synaptic?

---

### Post by yinglcs2 on 2007-10-19
I have searched 'compizconfig-settings-manager' in synaptic , it said no package found.

And I have tried apt-get, it said it is already installed.

$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by klikko on 2007-10-19
I had the same starting point, and now I'm suffering from the exact same problem. I also had * Compiz Fusion Icon* installed for easy access from my taskbar, and it also cannot open the settings manager. It seems that everything that tries to launch it (including Settings > Preferences > Appearance) is hitting the same errors you got earlier. I got them as well when running *ccsm* from the terminal.

I knew it was foolish to install 7.10 before people had time to figure out what sorts of bugs would be around in the final release...

EDIT: Check out this thread: [http://ubuntuforums.org/showthread.php?p=3553573]("http://ubuntuforums.org/showthread.php?p=3553573"). I haven't had a chance to try anything yet, but he had the exact same problem and got a bunch of responses.

---

### Post by Crimble on 2007-10-20
Add me to the list, all is working fine, I just can not access the manager via anything.

---

### Post by yinglcs2 on 2007-10-20
I finally solve it by go to  synatic package manager:
1. uninstall compiz setting manager
2. install compiz setting manager

My guess is I have a version of compiz setting manager (manually installed compiz on ubuntu 7.04) which is incompatible with compiz in ubuntu 7.10.

---

### Post by Crimble on 2007-10-20
yes, this was the fix for me as well.

---

### Post by speckman on 2007-10-20
i want to know why this wasn't installed for me when i upgraded to 7.10.  It's a little disappointing to have to search google, then synaptic to add the ability to control the most interesting settings on my desktop.

---

### Post by themusicwave on 2007-10-20
Any other ideas  I tried the uninstall reinstall thing and no luck.

I also totaly removed all of compiz and reinstalled it and still no luck.  Still that same error...

---

### Post by Crimble on 2007-10-21
"i want to know why this wasn't installed for me when i upgraded to 7.10"

I'm gonna go with:

BECAUSE THE PEOPLE WHO ARE MAKING A FREE OS FOR YOU DIDN'T DO IT. NO COMPLAINING ABOUT SOMETHING THAT COMES FOR FREE.

---

### Post by legalizemeth on 2007-10-21
> **yinglcs2 said:**
> I finally solve it by go to  synatic package manager:
1. uninstall compiz setting manager
2. install compiz setting manager

My guess is I have a version of compiz setting manager (manually installed compiz on ubuntu 7.04) which is incompatible with compiz in ubuntu 7.10.
This worked for me, too.  Thanks!

---

### Post by Perpetual on 2007-10-21
> **speckman said:**
> i want to know why this wasn't installed for me when i upgraded to 7.10.  It's a little disappointing to have to search google, then synaptic to add the ability to control the most interesting settings on my desktop.

I would say it wasn't installed as to stick to the keeping things simple for new users goal.  If you select Custom under Visual Effects, there is a default set of effects enabled.  For a beginning user, this should be sufficient until they progress their knowledge.

Once they understand Ubuntu/Linux and are not apt to destroy their OS, they can simply install Compiz Config Manager and play with all of the other settings.

Yeah, I was like 'what the hell' when I installed Gutsy.  But really, it makes sense and it's easiest enough to install if you need/want it.

---

### Post by zachthejones on 2007-10-21
hey guys, I installed the settings manager, but I have no idea how to access it. I can't find it on any of my menus and when I run "compizconfig-settings-manager" I get nothing...  Any help would be greatly appreciated!

Um, never mind, finally found it under system->Preferences->Advanced Desktop Effects Settings

yeah, that latter option is a mouthful...

---

### Post by Perpetual on 2007-10-21
System > Preferences > Advanced Desktop Effects Settings

Or...

System > Preferences > Appearance > Visual Effects there should now be a Preferences button next to Custom.

---

### Post by svanhulle on 2007-10-26
I found this post with a fix that worked for me.
[http://forum.compiz-fusion.org/showthread.php?t=4927](http://forum.compiz-fusion.org/showthread.php?t=4927)

My problem was I added Trevino's repo to install kiba-dock.  So some wrong components for Compiz were getting installed from there instead of the Ubuntu repos.

I had to completely remove Compiz restart, remove Trevino's repo and re-install it.

---

### Post by High_Yield on 2007-12-19
I am a linux/Ubuntu noobie and was VERY unhappy with the video until this.
OMG - I cannot tell you how much a difference it makes.  It looks just the the IPhone ads on TV - I kid you not.

Go to system Synaptic to download the package.  then follow his instructions to the letter.
"The solution: go to General Options in the CompizConfig Settings Manager. Under the Display Settings tab, uncheck “Detect refresh rate”, set the “Refresh rate” slider as far as it will go (to 200), and check “Sync to VBlank”."

Took me a bit to actually "SET" my new settings as I customized then but the radio button was not checked. However once I clicked the "Custom" button - bammo - best video EVER.:popcorn:

---

