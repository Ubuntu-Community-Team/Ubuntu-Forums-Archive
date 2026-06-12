---
title: "Compiz fusion not fully installed?"
date: 2009-02-11
forum: General Help
---

### Post by CaseLogic on 2009-02-11
I just installed ubuntu yesterday, and wanted to tweak compiz.

I wasn't aware that Compiz was already installed by default, so I followed these instructions

[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

I ran this:
sudo apt-get install compiz compizconfig-settings-manager

and I got an error.

"compiz --replace" works, but I don't have a settings manager to tweak anything.

How do I uninstall and reinstall so I can get all the options?

---

### Post by 73ckn797 on 2009-02-11
> **CaseLogic said:**
> 

How do I uninstall and reinstall so I can get all the options?

Go to System/Administration/Synaptic Package Manager. From there you can find Compiz and select to remove. Then you can try a re-install through Synaptics.

---

### Post by CaseLogic on 2009-02-11
I don't have my laptop on me atm so I can't test it, but I should be able to do it all through synaptics rather than doing anything from term?

---

### Post by ajgreeny on 2009-02-11
You certainly can.  It is probably worth using the "Completely remove (including configuration files)" in synaptic to make sure you get a clean start again with compiz.

---

### Post by CaseLogic on 2009-02-11
Do I just select "Compiz" or do I need to do a few of them?  There are a lot of compiz* packages :confused:

---

### Post by 73ckn797 on 2009-02-11
> **CaseLogic said:**
> Do I just select "Compiz" or do I need to do a few of them?  There are a lot of compiz* packages :confused:

The completely remove option will remove all associated stuff.

There is a main Compiz program and it will included necessary supporting things to make it work. Pay attention when you see a window that will tell you what is being installed or removed as the case may be.

---

### Post by CaseLogic on 2009-02-11
I uninstalled them all including config, and reinstalled every compiz* package available through synaptic (I updated the listings first).

I still don't have any options anywhere in System->Preferences or Administration to change any compiz settings.

What am I doing wrong?

I also still don't see a settings-manager package anywhere in synaptic

---

### Post by CaseLogic on 2009-02-12
Man I really wish I could get the settings manager somehow lol

---

### Post by CaseLogic on 2009-02-12
bump for great justice

---

### Post by rushmobius on 2009-02-12
The package to install is compizconfig-settings-manager.
It should be visible in the System -> Preferences then.

---

### Post by CaseLogic on 2009-02-12
> **rushmobius said:**
> The package to install is compizconfig-settings-manager.
It should be visible in the System -> Preferences then.
yes I know but the problem is that I've reloaded my packages like a billion times and that one is not on the list. what am I doing wrong?

---

### Post by solitaire on 2009-02-12
go to the command line and type in "compiz" (without quotes) and press the TAB key it should give you a list of commands that start with "compiz". What items are displayed?

---

### Post by CaseLogic on 2009-02-12
> **solitaire said:**
> go to the command line and type in "compiz" (without quotes) and press the TAB key it should give you a list of commands that start with "compiz". What items are displayed?
I'm not at home right now so I can't tell you immediately.

All I know for sure is that I typed compiz in synaptic and I installed all of them.  I do know that there was no 'settings manager' one though.  So I can turn it on and off via appearances->visual effects by setting 'normal' or 'extra', but that's it :(

---

### Post by solitaire on 2009-02-12
It might have been installed but, for some reason, did not create a menu entry. If you type in compiz and press the tab key (one or twice can't be sure i'm not at my linux pc at the moment) it should give you a list of all installed programs that start with compiz. so if the settings manager is there you should see it and run it manualy to test. you then can create a menu item at a later date. :D

---

### Post by CaseLogic on 2009-02-12
> **solitaire said:**
> It might have been installed but, for some reason, did not create a menu entry. If you type in compiz and press the tab key (one or twice can't be sure i'm not at my linux pc at the moment) it should give you a list of all installed programs that start with compiz. so if the settings manager is there you should see it and run it manualy to test. you then can create a menu item at a later date. :D
I've tried running it before and it didn't work.  The fact that it's not in synaptic kind of reassures that it's not installed.

I just don't know how to make it appear...

---

### Post by CaseLogic on 2009-02-12
Figured it out.. I had to select a different server to get the package list.  It's not "supported" so it wasn't listed under the main server.

---

### Post by 73ckn797 on 2009-02-12
> **CaseLogic said:**
> Figured it out.. I had to select a different server to get the package list.  It's not "supported" so it wasn't listed under the main server.


I was about to suggest that but then read your last posting.

---

### Post by dj722000 on 2009-02-14
Can you not also go to Applications-> Add/Remove, all open source application and find the manager in there? That's where I found it.

---

