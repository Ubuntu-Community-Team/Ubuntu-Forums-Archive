---
title: "A Note on Keyboard Shortcuts in Gutsy"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by Apreche on 2007-10-02
Just this past day or two I've thrown Gutsy on my laptop and my work desktop. I'm rocking the compiz pretty hard. I think I've found a nice balance between having more eye candy, but also making the computer easier to use. However, I have run into one huge problem. 

That problem is keyboard shortcuts. With the addiiton of compiz, keyboard shortcuts are now a nightmare. They are a nightmare in so many ways. It really is out of hand.

First of all, if a user is not clever enough to install compizconfig-settings-manager, and customize the keyboard shortcuts, they have no way to know they even exist. Setting desktop effect to the "normal" level enables a whole bunch of shortcuts that compiz has by default. There is no way for a user to know what these shortcuts are, or to change them, without being a power user. However, normal level of compiz is now default in ubuntu! 

Secondly, there are now too many keyboard shortcuts in too many places. You've got settings in Gnome. Settings in compiz. Settings in individual applications. In some ways, these different shortcuts mesh nicely. For example, the "show desktop" shortcut in gnome integrates nicely with compiz's show desktop. However, in other ways they do not work so nicely. ctrl+w to close window in compiz/gnome overrides the Firefox ctrl+w to close tab. 

Also, conflict detection. Compiz does a nice job of keeping its own shortcuts from conflicting. If I try to set one shortcut in compiz that is set elsewhere in compiz, it will ask me. However, if that shortcut is set in gnome, or an application, compiz has no idea. 

Another thing is the format for keyboard shortcut syntax. In Gnome and gconf-editor you'll see a shortcut like <Mod4>L, but in compiz, you'll see Mod4+L. There needs to be a standard way of representing shortcuts across the board to prevent confusion. It gets even worse when you have equivalent keys, for example if Super_L and Mod4 are the same key. Yeah, that's terrific. 

Here are some of my off-the-cuff ideas of how to make this situation better.

First, unify as many shortcut configurations as possible. At the very least, Gnome and Compiz configs should be unified into one place. 

Second, have the same rules for shortcuts across the board. How come I can use <Super>Tab as a shortcut in compiz, but the deskbar applet does not allow it? It makes no sense!

Three, the unified keyboard shortcut configurator should know about common shortcuts in popular applications. It should warn you if you try to use <Ctrl>T for launch terminal that that is the shortcut to open a new tab in Firefox. 

Lastly, by default the vast majority of keyboard shortcuts should be completely disabled. A shortcut conflict is one thing. A shortcut conflict with a function you don't know about and never use is even worse. It can also be bad if average users are typing on their keyboards and weird things start happening they don't understand without any explanation. Advanced users will be able to go through and set every keyboard shortcut they desire, and the rest will be disabled by default. Normal users, if they use shortcuts at all, will stick mostly to shortcuts for particular applications. 

There are other problems with keyboard shortcuts, but I don't want this to go on forever. Basically with the addition of compiz, which I approve of, the situation has gotten quite hairy. Something should be done to fix it before it gets worse.

---

### Post by Rupertronco on 2007-10-02
I really haven't had many problems with shortcuts, I guess it's because I only run a gnome session ~40% of the time. However, I agree that the shortcuts need to be cleaned up a bit. I spent quite a great deal of time eliminating the conflicts on my systems (I like stuff working without a hitch).  I'm really clueless as to why the ccsm (compiz-config-settings-manager) didn't come with the gutsy install. I'm just at a complete loss there, my only guess is some stability issue. 

My hopes are with the final release of gutsy the CCSM will be installed by default. I couldn't imagine using compiz without it.

---

### Post by Apreche on 2007-10-18
> **Rupertronco said:**
> I really haven't had many problems with shortcuts, I guess it's because I only run a gnome session ~40% of the time. However, I agree that the shortcuts need to be cleaned up a bit. I spent quite a great deal of time eliminating the conflicts on my systems (I like stuff working without a hitch).  I'm really clueless as to why the ccsm (compiz-config-settings-manager) didn't come with the gutsy install. I'm just at a complete loss there, my only guess is some stability issue. 

My hopes are with the final release of gutsy the CCSM will be installed by default. I couldn't imagine using compiz without it.While I still think there is a problem with keyboard shortcuts, I do not think the CCSM should be included in Ubuntu. It is too complicated and has poor UI. What we need is some UI for configuring compiz that allows more control than the appearance panel, but without the horrifying UI of the CCSM.

---

### Post by SunburnedCactus on 2007-10-18
As a genuine new user I've got to agree that a lot of it isn't even obvious, I've been poking about for a week and haven't found keyboard shortcuts anywhere yet. I've enabled most of the advanced settings but have no idea what they do in practice! :confused:

---

### Post by ArtInvent on 2007-10-19
Keyboard shortcuts are buried in the CCSM - one of the worst control panels ever created. I can now see kind of why this isn't loaded by default in Gutsy. However, the controls in Appearance are woefully basic. And why isn't there some very visible basic guide to the 10 or so keyboard and mouse controls that you'll be using pretty much all the time to control these things? I had to go through CCSM and blog posts and collect them and write them down on a postit.

You know, Compiz Fusion doesn't have to be so freaking complicated. There must be 10,000 permutations with all the options. And the naming of these options and explanations are not terribly descriptive. 

CCSM is a true mess and exhibits all the cliches people think of as Linux - too complicated and too much work, countered by the Linux geek's argument that it must be flexible and customizable. CCSM has been customizabled to death. Linux newbies should be able to fiddle with and customize this easily without being presented with the blueprints to the space shuttle.

---

### Post by dcstar on 2007-10-20
> **ArtInvent said:**
> 
.........
CCSM is a true mess and exhibits all the cliches people think of as Linux - too complicated and too much work, countered by the Linux geek's argument that it must be flexible and customizable. CCSM has been customizabled to death. Linux newbies should be able to fiddle with and customize this easily without being presented with the blueprints to the space shuttle.

Agreed, there really needs to be a simple set of effects "Templates" created so people can just pick and choose - like the way Desktop Themes are offered.

I've been using Unix/Linux for 15 years now, and I still haven't figured out where my "Super" key is yet since I installed Gutsy last week.....           :confused:

---

### Post by P_Squiddy on 2007-10-23
Well, the "Super" key on a PC is typically that "Windows" key that appeared a couple of years back.  Keep trying to find a nice Penguin icon to stick overtop, but it keeps rubbing off...

If you're on a Mac, sorry -- don't know which key is "Super" -- maybe the Apple key?

---

### Post by th3gh05t on 2007-10-25
What ARE the keyboard shortcuts for compiz? How do I get the cube to come up? Or the wall view?

---

### Post by logoodnix on 2007-11-05
[http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/]("http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/")

[http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/]("http://ulyssesonline.com/2007/10/25/compiz-fusion-keyboard-shortcuts/")

These are some basic ones.

---

### Post by cmavr8 on 2008-01-27
EDIT: SOLVED

Guys, I have made the mistake to assign <Control>T to some 3D plugin in CCSM, just to test.

Then I disabled the hotkey, and the plugin, but firefox would no longer use Ctrl+T to open a new tab!

I can't find any "hotkey" settings in firefox.. Help please..

SOLVED

---

