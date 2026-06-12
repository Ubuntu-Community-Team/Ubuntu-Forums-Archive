---
title: "Mouse gestures with Unity Workspace Switcher"
date: 2011-04-30
forum: Desktop Environments
---

### Post by JGSD on 2011-04-30
I'm trying to keep an open mind and give Unity/11.04 a fair chance because it seems that Ubuntu are serious about it and see it as the future.

However, I'm having a terrible time trying to make it work for me in a productive way.

One thing that I think would make a big difference would be the ability to set a mouse gesture whereby I could move the mouse pointer to different corners of the screen to activate things such as activating the Workspace Switcher or even just shrink down all of the currently open windows so that I could see everything that I had open at a glance. I can do this on OSX on my MacBook and it'd be great to be able to do it in Ubuntu, too.

I've tried installing Brightside but it only has "Toggle showing desktop" and then a bunch of power-related options for the screen corner-based mouse gestures. There's a "custom action" option but I've searched around and I can't seem to find a command line option for activating the Workspace Switcher nor the other feature I mentioned above.

I know that I can do Super+S to activate the Workspace switcher, but I find that flicking the mouse over into the corner of the screen is just so much more efficient.

In the new "System Settings" menu, clicking on "Launcher & Menus" gives a ridiculously low number of configuration options so I'm really not sure what to do!

---

### Post by Bonster on 2011-04-30
You can configure scale feature and others but u gotta install compizconfig-settings-manager look for it in the software center/synaptic

or

> sudo apt-get install compizconfig-settings-manager

---

### Post by nigeldodd on 2011-04-30
I agree about the paucity of ways to invoke the workspace switcher. I think this perhaps follows from the heritage of Unity being for small machines. My desktop machine is as untidy/rich as my study desktop with lots of parallel tasks on display and I need a way of switching between them easily.

With the previous Ubuntu I had 6 workspaces linearly arranged and could glide though them with the mouse, click on their icons, rotate the 'cube' etc,. Very rich environment in comparison to what I have so far discovered with Unity.

Unity seems restrictive by comparison and lacking in configuration possibilities.

---

### Post by JGSD on 2011-04-30
> **Bonster said:**
> You can configure scale feature and others but u gotta install compizconfig-settings-manager look for it in the software center/synaptic

Hi Bonster, thanks for your reply.

It looks like compizconfig-settings-manager was already installed but I didn't know that the feature I was talking about was called "scale".

Anyway, the function I was looking for is called "Initiate Window Picker" and I have now set it to activate as soon as I move the mouse to the top left corner of the screen which is excatly what I wanted to do :-)

So, thanks again :-)

---

### Post by foxy123 on 2011-05-10
Has anyone figured it out? I tried to edit settings in teh Viewport Switcher and Desktop Wall plugins but it does not work for me :(

---

### Post by FuManShu on 2011-05-22
To set the mouse gesture to be similar to OS X,  you need to install compizconfig-settings-manager, open said application, click on "Expo" in the "Desktop" section and change the setting for "Expo Edge". It will allow you to choose the edge to slide your mouse to.

---

### Post by JGSD on 2011-05-29
> **FuManShu said:**
> To set the mouse gesture to be similar to OS X,  you need to install compizconfig-settings-manager, open said application, click on "Expo" in the "Desktop" section and change the setting for "Expo Edge". It will allow you to choose the edge to slide your mouse to.

Hi FuManShu. Thanks for answering my original question! Expo activates the workspace switcher. Double-clicking on a workspace zooms into it. 

Scale, on the other hand, does the thing where all of the windows in the existing workspace are scaled down to fit on the screen at the same time. A single-click on one window de-scales all of the windows and brings the one you clicked to the foreground. Scale is the more OSX-like one of these two, but it's great to have both of them available with mouse gestures now :-)

Is it just me, or is the Compbiz settings thing horrifically difficult to figure our at a glance? There's an obvious effort to categorize the different effects but I can't help but think that there must be a more intuitive way of presenting all of these different options. That's twice now that I've known exactly what I wanted but after spending ages flicking through all of these vaguely-named effects, not being able to find what I wanted.

---

### Post by wildmanne39 on 2011-05-29
> **JGSD said:**
> Hi FuManShu. Thanks for answering my original question! Expo activates the workspace switcher. Double-clicking on a workspace zooms into it. 

Scale, on the other hand, does the thing where all of the windows in the existing workspace are scaled down to fit on the screen at the same time. A single-click on one window de-scales all of the windows and brings the one you clicked to the foreground. Scale is the more OSX-like one of these two, but it's great to have both of them available with mouse gestures now :-)

Is it just me, or is the Compbiz settings thing horrifically difficult to figure our at a glance? There's an obvious effort to categorize the different effects but I can't help but think that there must be a more intuitive way of presenting all of these different options. That's twice now that I've known exactly what I wanted but after spending ages flicking through all of these vaguely-named effects, not being able to find what I wanted.
Hi, it is a little more complicated then it use to be, but I have the cube and many effects working perfectly in natty now by following to guides, I will give links to them. [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)
  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by brel on 2011-06-24
I'm with JGSD, the compizconfig-.. is very difficult to work with!! The only way I could find what I wanted was by using the advanced search (on the lower left). I typed 'initiate' because I saw it as the start of the option name in a post further up.

There is a 'scale' icon but I didn't find it until it was too late. I got stuck in the 'scale addons' section for a while though.

Ugh. I'm not convinced by the vocabulary. Expo is a rip off of 'exposé' which is the osx equivalent of scale. After expo, I thought 'desktop zoom' since that seems like the right idea (zoom out I suppose). I would never have thought of 'scale'. Fortunately it was also in a post above.

Anyway, I've got what I wanted but it could have been a lot easier.

Thanks.

---

