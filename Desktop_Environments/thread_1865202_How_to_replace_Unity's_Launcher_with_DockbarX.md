---
title: "How to replace Unity's Launcher with DockbarX"
date: 2011-10-19
forum: Desktop Environments
---

### Post by Emblem Parade on 2011-10-19
**Why?**

Like many people, I love a lot of things about Unity but am badly burned with the inability to customize some aspects of it.

In this guide I'll try to be constructive and show you how in a few minutes you can get a good-if-not-better Unity experience than the one offered out of the box! The point is to retain as much of Unity's functionality as possible while still allowing you to customize it.

At the end of the guide, I also include instructions for how to very easily undo these changes.

(The particular pain point for me is that the Launcher and Dash are locked to the leftmost monitor, which in my setup is a secondary monitor located to the left of me main desk. Using Unity there would quickly lead to neck injuries! If you have the same problem try adding your two cents to this ignored Launchpad bug: [https://bugs.launchpad.net/unity/+bug/668415](https://bugs.launchpad.net/unity/+bug/668415), though note that Mark Shuttleworth marked it "won't fix" and it is being ignored by the Unity team. It's really disheartening that the Unity team has so poorly engaged the community on this issue.)

This guide has been tested with Ubuntu 11.10 (Oneiric Ocelot) but should also work with previous Unity versions.

**What We're Going to Do**

We're going to do four things:

1. Replace the Unity Launcher with DockbarX -- it supports Unity indicators and quicklists, but is far more customizable than the Unity launcher
2. Replace the Unity Dash with Synapse -- lightning fast, full support for Zeitgeist, but unfortunately no support for Unity Lenses and Scopes
3. Replace the Unity Panel with the the Unity 2D Panel -- identical to the 3D panel, with full support for the global menu and indicators
4. Replace Unity's Application Switcher with the Compiz Application Switcher

Explanation for #3: because Unity 3D is one integrated package, we can't just replace the Launcher and Dash while leaving the Panel intact. Luckily, Unity 2D is more modular, and we can run the Unity 2D Panel just fine in Compiz! Seriously, it looks 100% the same. It's too bad Unity 3D isn't as modular.

Explanation for #4: the default application switcher in Unity is handled by Unity itself. Luckily, Compiz comes with a few good options to replace it.

I am also including a nice Unity-lookalike theme for DockbarX made by BigRZA.

**Step 1: Installation**

Open a terminal and run these commands:

```
sudo add-apt-repository ppa:synapse-core/ppa
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install synapse dockbarx dockbarx-themes-extra compizconfig-settings-manager
cd ~
wget http://www.deviantart.com/download/197980167/unite_11_04_theme_by_bigrza-d39veh3.zip
unzip unite_11_04_theme_by_bigrza-d39veh3.zip -d .dockbarx/themes/
rm unite_11_04_theme_by_bigrza-d39veh3.zip
```

**Step 2: Setting up Synapse and DockbarX**

Use the Dash to run Synapse. Go to its preferences and set it to "Startup on login". You can use CTRL+SPACE to pop it up later.

To run DockbarX as a standalone launcher, use CTRL+F2 and run "dockx". Go to appearance and switch your theme to "unity_v11.04" and click the reload button to the right of the theme selection combobox.

Have fun with its many, many configuration options! (In such stark contrast to Unity's Launcher...) 

**Step 3: Startup Applications**

To make DockbarX startup automatically, we need to do some manual work. Open Dash and run "Startup Applications". Add an entry called "DockbarX" with the command "/usr/bin/dockx".

While we're there, let's add another entry called "Unity 2D Panel" with the command "/usr/bin/unity-2d-panel". This will make sure the Panel starts up automatically, too.

**Step 4: Compiz Settings**

Use Dash to run "CompizConfig Settings Manager" (aka CCSM). Now, go the "Ubuntu Unity Plugin" and disable it. Woosh!

Now, enable "Application Switcher". (Note that you can also enable "Ring Switcher" or "Shift Switcher" instead.)

**Step 5: Return of the Panel**

To get the panel back, press CTRL+SPACE to get Synapse up (we no longer have the Dash running) and run "unity-2d-panel".

**Enjoy!**

Next time you log in using the "Unity" session, you should get the same desktop.

**How to Undo This**

Super easy:

1. Open "Startup Applications" and disable "DockbarX" and "Unity 2D Panel".
2. Open Synapse's preferences and disable "Startup on login".
2. Open "CompizConfig Settings Manager" and re-enable "Ubuntu Unity Plugin", while also disabling "Application Switcher".

That's it, no harm done.

**Further Options**

1. I happen to like Synapse, but you can also use GNOME Do, GNOME Pie, Kupfer or Launchy.
2. You can also run DockbarX as an applet inside Avant Window Manager (AWN) if you want a more full-featured dock. I personally prefer the minimalism of DockbarX on its own in tandem with the Unity Panel.

**Known Issues**

1. The Unity 2D Panel has some rendering bugs with multiple monitors which have different resolutions. Still, it's functional.
2. Synapse does not support Unity Lenses. Perhaps someone can write a plugin?
3. Cannot set the SUPER key on its own to pop up Synapse. (Though you can set it to SUPER+SPACE)

---

### Post by Emblem Parade on 2011-11-02
As another addition to the guide:

The problem of using Synapse or the other keyboard launchers is that you can't get a complete look of all applications installed, the same way you could do with Dash.

So, consider adding [Classic Menu Indicator]("http://www.florian-diesch.de/software/classicmenu-indicator/"), which will give you access to the classic GNOME2-style application menu.

```
sudo apt-add-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator
```

You'll need to launch it explicitly the first time, but it will add itself to your startup application and be available next time you login.

---

### Post by Emblem Parade on 2011-11-23
Sigh. The Unity 2D panel app has its own set of issues. Likely it will be buggy for you if your monitors are of different sizes.

If this is the case for you, I suggest the following amendment to the above:

1) Disable unity-2d-panel from your "Startup Applications". You won't be using it anymore.

2) Open CompizConfig Settings Manager. Disable "Application Switcher". Now, re-enable "Unity", and edit its settings as follows:

a) In the "behavior" tab, set "Reveal Mode" to "None"
b) Set "Hide Launcher" to "Dodge Windows". This way, if you have any window there, it won't take up space.
c) Disable the key shortcuts for "show the launcher", "put keyboard-focus on launcher" and "execute a command". You do want to key for "open the first panel menu".

This pretty much does away with the Dash entirely! Unfortunately, there is no way to truly disable the Launcher, only to make it as unobtrusive and invisible as possible. You still might see it come and go as notifications happen... unfortunately there's nothing we can about that.

---

