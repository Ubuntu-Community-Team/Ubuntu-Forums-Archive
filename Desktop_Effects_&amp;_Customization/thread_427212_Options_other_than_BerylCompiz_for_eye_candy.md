---
title: "Options other than Beryl/Compiz for eye candy?"
date: 2007-04-29
forum: Desktop Effects &amp; Customization
---

### Post by trishacupra on 2007-04-29
I've discovered I have a crappy ATI graphics card in my laptop that is incompatible with Beryl. Oh, well. That's disappointing but I'll survive.

What other things can I do to add some eye candy to my desktop? I use ObjectDock in Windows - what can I use in Ubuntu that is similar? What about widgets/gadgets? Animated wallpaper and/or icons?

Thanks!

---

### Post by BaffledMollusc on 2007-04-29
> **trishacupra said:**
> I've discovered I have a crappy ATI graphics card in my laptop that is incompatible with Beryl. Oh, well. That's disappointing but I'll survive.

What other things can I do to add some eye candy to my desktop? I use ObjectDock in Windows - what can I use in Ubuntu that is similar? What about widgets/gadgets? Animated wallpaper and/or icons?

Thanks!

Are you saying that ATI cards are incompatible with Beryl? If so, that's not the case - you can make them work by using XGL and the Beryl package from the Beryl homepage rather than the version in the Ubuntu repositories. See [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy) for excellent step by step guide that got my card working.

Of course maybe there are ATI cards that are incompatible with Beryl  - all I know is that my X800 Pro works.

---

### Post by ericesque on 2007-04-29
There are a number of options for the OSX style dock.  This guide [http://www.taimila.com/osx-guide-2.php](http://www.taimila.com/osx-guide-2.php)
mentions a few.  The one I haven't tried, yet looks very promising, is the avant-window-manager.   The name doesn't say dock, but it seems to be pretty fully featured.  But other options are available and there are links in the guide.

Hope this helps.

---

### Post by luisromangz on 2007-04-29
My laptop's ATI X300 (which is really crappy) works fine with Beryl, installing the packages in Ubuntu's repositories, and then downgrading beryl-core to version 2.0 from Beryl-Project.

Good luck!

---

### Post by trishacupra on 2007-04-29
I'm currently trying the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy) just in case it gets it working.

---

### Post by BaffledMollusc on 2007-04-30
> **trishacupra said:**
> I'm currently trying the instructions at [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Eye_Candy) just in case it gets it working.
If it works, could you post back here and let us know what card you have? It'll be a useful data point in case other people search for Beryl and your card type.

---

### Post by trishacupra on 2007-04-30
BaffledMollusc, you're my hero!

I got Beryl working! This is fantastic!

I have an **ATI Radeon Xpress 200M**. I'm not sure I have all the effects working, but I definitely have the wobbly windows going on. And I have one of the Emerald theme things.

I thought after reading [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon) that I wouldn't have any luck, especially since clicking on System > Preferences > Desktop Effects did nothing, and enabling the restricted driver for my graphics card just gave me an error when trying to enable Desktop Effects that way. But following those directions and then installing the restricted driver (important - otherwise doesn't work properly) did the trick.

Now, how do I get rid of those notifications to upgrade Beryl, which will break it?

---

### Post by Rinzwind on 2007-04-30
Here do this to stop ubuntu updating it:

> # [http://ubuntuforums.org/showthread.php?t=418550](http://ubuntuforums.org/showthread.php?t=418550)
sudo -v
echo beryl hold | sudo dpkg --set-selections
echo beryl-core hold | sudo dpkg --set-selections
echo beryl-plugins hold | sudo dpkg --set-selections
echo beryl-plugins-data hold | sudo dpkg --set-selections
echo beryl-plugins-unsupported hold | sudo dpkg --set-selections
echo beryl-plugins-unsupported-data hold | sudo dpkg --set-selections
echo beryl-settings hold | sudo dpkg --set-selections
echo beryl-settings-bindings hold | sudo dpkg --set-selections
echo emerald hold | sudo dpkg --set-selections
echo libberyldecoration0 hold | sudo dpkg --set-selections
echo libberylsettings0 hold | sudo dpkg --set-selections
echo libemeraldengine0 hold  | sudo dpkg --set-selections
echo emerald-themes hold  | sudo dpkg --set-selections
echo beryl-manager hold | sudo dpkg --set-selections

Toss it in a text file make it executable and execute it :)

---

### Post by Nozem on 2007-04-30
Besides Beryl and Compiz, you could take a look at Enlightenment: a window manager that's slowly developing towards a desktop shell like Gnome and KDE. There are several versions: version 16 (E16) is the most stable, while version 17 (E17 or DR17) is the most advanced. I've heard some good stuff about it, though I haven't tried it myself. You can find quite a lot of info, inlcuding screenshots and videos on its main site: [http://www.enlightenment.org/](http://www.enlightenment.org/)

---

### Post by BaffledMollusc on 2007-04-30
> **trishacupra said:**
> BaffledMollusc, you're my hero!

I got Beryl working! This is fantastic!

Now I feel happy :)

---

### Post by trishacupra on 2007-04-30
> **BaffledMollusc said:**
> Now I feel happy :)

You and me, both. :)

---

### Post by trishacupra on 2007-04-30
> **Rinzwind said:**
> Here do this to stop ubuntu updating it:



Toss it in a text file make it executable and execute it :)

This disabled 7 out of 12 updates I have listed in the Update Manager. The other 5 still enabled are:

[B]beryl

beryl-core

beryl-plugins

beryl-plugins-data

beryl-settings[/B]

Do those need disabling too?

---

