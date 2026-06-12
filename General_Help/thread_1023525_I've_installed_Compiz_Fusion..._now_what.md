---
title: "I've installed Compiz Fusion... now what?"
date: 2008-12-28
forum: General Help
---

### Post by charleskw on 2008-12-28
So I wanted to install beryl on my Ubuntu without using Terminal, so I was told to download Compiz Fusion. So I downloaded and installed it from Synaptic. Now what? How do I get beryl features?

---

### Post by omskates on 2008-12-28
Applications --> Terminal

sudo apt-get install emerald

when it asks for a y/n, type y to continue.

Go to System -> Preferences -> Compiz Config Manager
Enable window decorator




Download beryl themes from Gnome-Look & save to desktop

Click on import and point to the downloaded theme package from within the Theme Manager 

Go to System -> Preferences -> Emerald Theme Manager
Click on "import" and point to the downloaded theme package from within the Theme Manager
It will install the theme for you

---

### Post by stderr on 2008-12-28
To configure it, you'll want to install CCSM.

```
sudo apt-get install compizconfig-settings-manager
```

If you *really* wanted to, you could install it through synaptic...

You can then switch to Compiz by System -> Preferences -> Appearance, Visual Effects, and changing to 'Normal' or 'Extra'. Compiz itself can then be configured by running the CCSM, which should also be under System -> Preferences. 

Others will probably advise you better here, but you'll probably want to do things like enable 4 workspaces, enable the desktop cube and rotate cube, etc... but basically when you've got compiz loaded and CCSM up, you can play with everything 'till your heart's content.

The Emerald window manager can also be enabled in CCSM. You'll probably need to run 

```
sudo apt-get install emerald
```

before you can access the Emerald Theme Manager to customise it.

---

### Post by Ratscallion on 2008-12-28
Seeing as you don't want to use the Terminal, my suggestion is installing the CCSM from either Synaptic Package Manager or Add/Remove Programs. Once that's done you should have Advanced Desktop Settings in System->Preferences.

The beryl project was fused with Compiz a while back, now all of the beryl and compiz plugins are in one window, the Compiz Config Settings Manager. Or CCSM for short. 

To be able to use the different plug-ins and see them working, you'll need to have Desktop Effects enabled. Go to System->Preferences->Appearance, in Visual Effects, make sure Extra or Custom are checked.

---

### Post by steveneddy on 2008-12-28
> **charleskw said:**
> So I wanted to install beryl on my Ubuntu without using Terminal, so I was told to download Compiz Fusion. So I downloaded and installed it from Synaptic. Now what? How do I get beryl features?

What Beryl features are you looking for?

---

