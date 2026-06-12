---
title: "A couple easy questions.."
date: 2009-04-07
forum: General Help
---

### Post by letmekilluplz on 2009-04-07
Go to post #11 (page 2) to see new questions

---

### Post by lisati on 2009-04-07
> **letmekilluplz said:**
> 1. What is the gnome splash screen?

2. Where do I go to access installed themes and install new ones.

3. Where are the compiz settings?

4. How can I change the login screen?

5. Is there a way I dont have to authenticate everytime I want to do something admin?

Sorry about the wave of questions and thanks in advance!

1. It depends on what you mean by "splash screen". The *desktop background* on 8.10 is an ibex
4. Have a look at the System->administration menu for an option "Login Window"
5. It depends: most regular applications (e.g. Open Office) don't normally need authentication,

---

### Post by Pacopag on 2009-04-07
you can download themes and gdmthemes (login screens) at gnome-look (just google "gnome look".  To add a theme, go to system, preferences appearance, then drag and drop the file (without unzipping it) into the space where the other themes are.

To change login screen, go to system, administration, login window, then click the local tab, then add, then find the file (again, don't have to unzip it).

That's all I know.

Just a note.  I actually temporarily broke my system by trying to use a bad login window.

---

### Post by RedSingularity on 2009-04-07
1)  What do you mean by "splash screen"?  The ubuntu loading screen when you start the computer?

2) You can get new themes [HERE](www.gnome-look.org) and the instructions to install them are there as well.

3) You have to install compiz settings manager......type "sudo apt-get install compizconfig-settings-manager" into a terminal.

4) Change the login screen in System>Administration>Login window.

5)  Yes there is and it is quite easy to do but i cannot remember it.

---

### Post by Therion on 2009-04-07
> **letmekilluplz said:**
> 1. What is the gnome splash screen?
I think you are referring to the **usplash**.  Do you want to change it, or what?

> **letmekilluplz said:**
> 2. Where do I go to access installed themes and install new ones. 
System/Preferences/Appearance "Themes" tab.

> **letmekilluplz said:**
> 3. Where are the compiz settings?
System/Preferences/Appearance "Visual Effects" tab.
You can install CCSM (CompizConfig Settings Manager) for much, much finer control from Synaptic or Add/Remove however.
The tab allows for "None", "Normal" and "Extra" settings.

> **letmekilluplz said:**
> 4. How can I change the login screen?
System>Administration>Login Window "Local" tab.

> **letmekilluplz said:**
> 5. Is there a way I dont have to authenticate everytime I want to do something admin?
Yes, but I'm not going to tell you how to do it.

---

### Post by Pacopag on 2009-04-07
compiz settings should be under system, preferences, appearance, then click the visual effects tab.  To get really sweet effects, you have to install compiz-fusion.  There is a sticky thread that tells you how.

And Therion, I like the goat head.  Really sharp.  Can you hook me up with a higher-resolution graphic of it?

---

### Post by Pacopag on 2009-04-07
Check out the Sticky thread in the "Desktop Environments" forum for compiz-fusion.

---

### Post by Therion on 2009-04-07
> **Pacopag said:**
> compiz settings should be under system, preferences, appearance, then click the visual effects tab.  To get really sweet effects, you have to install compiz-fusion.  There is a sticky thread that tells you how.
CompizFusion comes installed by default but, for whatever reason, CCSM does not.  And you need CCSM to *access* the full range of effects.

---

### Post by maheshasolkar on 2009-04-07
> **letmekilluplz said:**
> 1. What is the gnome splash screen?

From what I understand, Gnome Splash Screen is the graphic that shows progress when Gnome is loading. If I am not too wrong, Ubuntu has it disabled by default.

> **letmekilluplz said:**
> 2. Where do I go to access installed themes and install new ones.

I think this has been answered, you can access installed themes at System -> Preferences -> Appearance. You can find new themes on websites like [http://www.gnome-look.org/](http://www.gnome-look.org/)

> **letmekilluplz said:**
> 3. Where are the compiz settings?

You can install compiz config setting manager like so:

```
sudo apt-get install compizconfig-settings-manager
```

After installing, the compiz config setting manager will appear in System -> Preferences.

> **letmekilluplz said:**
> 5. Is there a way I dont have to authenticate everytime I want to do something admin?

I am sure there is, but I don't think that is a good idea.

---

### Post by mb_webguy on 2009-04-07
> **letmekilluplz said:**
> 1. What is the gnome splash screen?
It's the screen you see while the OS is loading, with the little statusbar.

> 2. Where do I go to access installed themes and install new ones.System->Preferences->Appearance.  Gnome-look.org is a great place to find new themes.

> 3. Where are the compiz settings?
If it's not already installed, install the compizconfig-settings-manager package.  You'll now have System->Preferences->Advanced Desktop Effects Settings.

> 4. How can I change the login screen?
System->Administration->Login Window, the Local tab.

> 5. Is there a way I dont have to authenticate everytime I want to do something admin?
Yes, but you really, really, really, really shouldn't.  This is an important part of the Ubuntu security model, and part of the reason Ubuntu (and Linux) is a more secure OS than Windows.  In fact, it's such a bad idea that it would be a violation of forum policy to tell you.

---

### Post by letmekilluplz on 2009-04-07
Ok new questions~

1 - How do you install Usplash themes? Ive tried startup manager it wont work.

2- the desktop cube. How to you get it to zoom out and be a big cube instead of being inside it?

---

### Post by Therion on 2009-04-08
> **letmekilluplz said:**
> Ok new questions~

1 - How do you install Usplash themes? Ive tried startup manager it wont work.
See this tutorial:  [http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html](http://www.debianadmin.com/configure-grub-and-usplash-settings-using-simple-gui-interface-in-ubuntu.html)

or this tutorial:  [http://geekybits.blogspot.com/2007/11/installing-new-usplash-themes-in-ubuntu.html](http://geekybits.blogspot.com/2007/11/installing-new-usplash-themes-in-ubuntu.html)

Both use Startupmanager and Startupmanager DOES work, I use it myself.


> **letmekilluplz said:**
> 2 - the desktop cube. How to you get it to zoom out and be a big cube instead of being inside it?
See this tutorial:  [http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

---

