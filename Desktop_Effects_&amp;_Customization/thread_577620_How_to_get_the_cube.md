---
title: "How to get the cube"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by Dapman01 on 2007-10-16
I enabled the effects under system and get the wobble, but I don't know how to get the cube.  I have it check marked, but don't know how to get it running

---

### Post by LowSky on 2007-10-16
are you using beryl or compiz or compiz fusion? and what edtion of ubuntu?

---

### Post by jr.gotti on 2007-10-16
In the general options, change your desktop horizontal size to 4. Also make sure Desktop Cube is enabled.

I'm assuming you have ccsm installed. If not, click

[apt:compizconfig-settings-manager](apt:compizconfig-settings-manager)

Oh, and to rotate the cube, its Ctrl+Alt+Directional Arrow, or Ctrl+Alt Left click drag.

---

### Post by Dapman01 on 2007-10-16
> **LowSky said:**
> are you using beryl or compiz or compiz fusion? and what edtion of ubuntu?

I'm just using whatever ubuntu comes with
I have feisty 7.04

---

### Post by argie on 2007-10-16
> **Dapman01 said:**
> I'm just using whatever ubuntu comes with
I have feisty 7.04

In *Desktop Effects*, enable "*Workspaces on a cube*". Then to use the cube, Press Ctrl  + Alt + &#8594; and Ctrl + Alt + &#8592;

---

### Post by Dapman01 on 2007-10-16
> **argie said:**
> In *Desktop Effects*, enable "*Workspaces on a cube*". Then to use the cube, Press Ctrl  + Alt + &#8594; and Ctrl + Alt + &#8592;

That's what I did and when I press ctrl+alt+ right or left, nothing happens.  Now when I do ctrl+alt+ up or down, the windows become seprated

---

### Post by jryprt on 2007-10-16
Try Ctrl+Alt Left click drag the mouse

---

### Post by Dapman01 on 2007-10-16
> **jr.gotti said:**
> In the general options, change your desktop horizontal size to 4. Also make sure Desktop Cube is enabled.

I'm assuming you have ccsm installed. If not, click

[apt:compizconfig-settings-manager](apt:compizconfig-settings-manager)

Oh, and to rotate the cube, its Ctrl+Alt+Directional Arrow, or Ctrl+Alt Left click drag.

when I clicked it said that firefox cannot open because I don't have the right program installed

---

### Post by bsalt on 2007-10-16
I know that in Gutsy you have to install the Compiz settings manager:

```
sudo apt-get install compizconfig-settings-manager
```

From then on, whenever you open up System -> Preferences -> Appearance, the option is there for Custom settings and to open up the config utility, as well as directly in System -> Preferences -> Appearance -> Advanced Desktop Effects Settings


Hope this helps.

---

### Post by Dapman01 on 2007-10-16
> **jryprt said:**
> Try Ctrl+Alt Left click drag the mouse
nothin

---

### Post by linuxlizard on 2007-10-16
Key combinations? I just hold down my middle mouse button and there it is.:)

---

### Post by Dapman01 on 2007-10-16
> **bsalt said:**
> I know that in Gutsy you have to install the Compiz settings manager:

```
sudo apt-get install compizconfig-settings-manager
```

From then on, whenever you open up System -> Preferences -> Appearance, the option is there for Custom settings and to open up the config utility, as well as directly in System -> Preferences -> Appearance -> Advanced Desktop Effects Settings


Hope this helps.

when I did that this came up

patrick@patrick-desktop:~$ sudo apt-get install compizconfig-settings-manager
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager
patrick@patrick-desktop:~$ 

and this is exacly what firefox said

Firefox doen't know how to open this address, because the protocol (apt) isn't associated with any program

By the way, thanks a bunch everyone who is helping me.  I'm loving the ubuntu community

---

### Post by jryprt on 2007-10-16
Read this it is a very good guide [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

that is what i used
Jerry

---

### Post by Dapman01 on 2007-10-16
if the flexible windows thing is working, shouldn't the cube work also?

---

### Post by bsalt on 2007-10-16
By default, the Cube doesn't work. Install compizconfig-settings-manager, and disable the Desktop Wall and enable Desktop Cube, and Rotating Cube.


```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by Dapman01 on 2007-10-16
> **bsalt said:**
> By default, the Cube doesn't work. Install compizconfig-settings-manager, and disable the Desktop Wall and enable Desktop Cube, and Rotating Cube.


```
sudo apt-get install compizconfig-settings-manager
```

How do I disable the desktip wall and enabe desktop cube

---

### Post by bsalt on 2007-10-16
Go to System --> Preferences --> Advanced Desktop Effects Settings, look or search for Cube, enable those, and it will ask if you want to disable the wall. It's pretty straightforward if you open the app and look at it.

---

### Post by Dapman01 on 2007-10-16
> **bsalt said:**
> Go to System --> Preferences --> Advanced Desktop Effects Settings, look or search for Cube, enable those, and it will ask if you want to disable the wall. It's pretty straightforward if you open the app and look at it.

thanks, I think I am going to keep ubuntu, I am currently loving the community.

I will try this after class and post if it works

---

### Post by Dapman01 on 2007-10-16
I don't have the advanced desktop thing under preferences

---

### Post by Dapman01 on 2007-10-16
does anyone know how I get advanced desktop settings in preferences

---

### Post by jr.gotti on 2007-10-16
Alrighty!

Open a terminal.

Enter this: 

```
sudo gedit /etc/apt/sources.list
```Add this to the bottom.

```

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 

```Save that, and run

```

sudo apt-get update

```now, run

```

sudo apt-get install compizconfig-settings-manager

```Now, enter

```

ccsm

```There, you'll be able to edit all the plugins.

Make sure that in General Options, Desktop Horizontal Size is set to four, and the Cube plugin is activated.

Hope this helps!!

-Jason

EDIT: Oh, and the firefox link didn't work because thats a new feature in Gutsy ;) I wasn't aware you were running fiesty.

---

### Post by Dapman01 on 2007-10-16
where am I suppose to put ccsm

---

### Post by jr.gotti on 2007-10-16
Either hit Alt+F2 and put it there, or put it in a terminal.

Alternatively, it should be somewhere in the menu. I think system>preferences.

---

### Post by Dapman01 on 2007-10-16
> **jr.gotti said:**
> Either hit Alt+F2 and put it there, or put it in a terminal.

Alternatively, it should be somewhere in the menu. I think system>preferences.

from sudo apt-get update on down I used run
all goes well until I hit when I have to run ccsm and then it says Could not open location 'file:///ccsm'

---

### Post by Dapman01 on 2007-10-16
bump

---

### Post by Rupertronco on 2007-10-16
> **Dapman01 said:**
> from sudo apt-get update on down I used run
all goes well until I hit when I have to run ccsm and then it says Could not open location 'file:///ccsm'
Why did you use run?

Enter those commands in a terminal. They're not for the run box.

---

### Post by Dapman01 on 2007-10-17
Man, this is starting to get frustrating
So I have CompizConfig Settings Manager.  Set up up perfictly like you guys said and all I get is this little dinky application selector that says desk1 and desk 2.  Is it not going to work with my copy of ubuntu maybe.  Am I missing an apply button someware

---

### Post by Dapman01 on 2007-10-17
oh, and the buttons I'm pressing are ctrl+alt+up (down left right)

---

### Post by jr.gotti on 2007-10-17
In the settings manager I need you to check a couple things for me.

In general options, under Desktop Size, what is your Horizontal Virtual Size Set to?

Are Desktop Cube and Cub Rotate enabled?

---

### Post by bsalt on 2007-10-17
Ok. Well, maybe you should upgrade your system to Ubuntu Gutsy. It will take an hour or two on basic Cable, but it provides a better settings manager for compiz. But also, you might want to turn off compiz temporarily and then right click on the workspace switcher on the botttom bar, and enable 4 workspaces. You could have the cube enabled, but only with 2 workspaces, so really, it's just a two sided plane. If you choose to upgrade, here is the command you should run:

```
sudo update-manager -d
```

---

### Post by Rupertronco on 2007-10-17
> **bsalt said:**
> Ok. Well, maybe you should upgrade your system to Ubuntu Gutsy. It will take an hour or two on basic Cable, but it provides a better settings manager for compiz. But also, you might want to turn off compiz temporarily and then right click on the workspace switcher on the botttom bar, and enable 4 workspaces. You could have the cube enabled, but only with 2 workspaces, so really, it's just a two sided plane. If you choose to upgrade, here is the command you should run:

```
sudo update-manager -d
```

I wouldn't recommend upgrading to Gutsy until its final release candidate is out, and a fresh install is preferred to an upgrade.

Upgrading the os to fix an eye candy problem will be a solution in only incredibly rare circumstances and I think might be a bit too much to just get a pretty desktop.

---

### Post by bsalt on 2007-10-17
Well. From my personal experience, I upgraded to Gutsy Beta couple weeks ago on my laptop with no problems, and it releases tomorrow, and I have already downloaded and installed the Gutsy release candidate on 2 other computers and had no problems. But as far as what I have experienced, Gutsy is *far* better than Feisty. As the newer versions of Ubuntu have always been. This one is more stable, supports more hardware, has built-in compiz fusion with better support, has Pidgin IM now, and so on. I'm sending this message from Gutsy AMD64 on my desktop, and the 64-bit really works excellently as well. I'm just saying that I think upgrading to Gutsy is the least risk than any of the other previous versions.

But, you're right, it can cause some problems, and the best thing to do has been to reinstall, but I think they really got the upgrade worked out now, so a reinstall should only be used if upgrading does not work out. It will even remove the apps that are no longer supported and install the ones that replace them. 

lol but I'm off my soapbox now.

---

### Post by Rupertronco on 2007-10-17
> **bsalt said:**
> Well. From my personal experience, I upgraded to Gutsy Beta couple weeks ago on my laptop with no problems, and it releases tomorrow, and I have already downloaded and installed the Gutsy release candidate on 2 other computers and had no problems. But as far as what I have experienced, Gutsy is *far* better than Feisty. As the newer versions of Ubuntu have always been. This one is more stable, supports more hardware, has built-in compiz fusion with better support, has Pidgin IM now, and so on. I'm sending this message from Gutsy AMD64 on my desktop, and the 64-bit really works excellently as well. I'm just saying that I think upgrading to Gutsy is the least risk than any of the other previous versions.

But, you're right, it can cause some problems, and the best thing to do has been to reinstall, but I think they really got the upgrade worked out now, so a reinstall should only be used if upgrading does not work out. It will even remove the apps that are no longer supported and install the ones that replace them. 

lol but I'm off my soapbox now.

Oh I totally agree his best bet is to upgrade to the newest Gutsy, I just find it easier to say "get the release version as it's supposed to be stable" just because there might be a small problem rectified by the latest install.  Also it's a pain trying to support each beta/early version of gutsy when for all we know problems might be solved by just installing the real release.

---

### Post by octotom on 2007-10-17
Maybe this will help you get the cube effect.

With desktop effects enabled, disable the cube only.  Then increase the workspaces to four.  Then go back to desktop effects and re-enable the cube.  Hopefully it will work.  It did for me!

Shalom,
Tom

---

### Post by Dapman01 on 2007-10-17
Thanks guys for all your help I got it working.  
I reinstalled ubuntu and got and installed the drivers and it worked without any modifications
Now, what cool things can I do with the cube

---

### Post by jr.gotti on 2007-10-17
> **Dapman01 said:**
> Thanks guys for all your help I got it working.  
I reinstalled ubuntu and got and installed the drivers and it worked without any modifications
Now, what cool things can I do with the cube

...rotate it. Left, and Right. ... OHH!! And sometimes up and down! :P

---

### Post by Scroobytec on 2007-10-17
> **Dapman01 said:**
> Thanks guys for all your help I got it working.  
I reinstalled ubuntu and got and installed the drivers and it worked without any modifications
Now, what cool things can I do with the cube

Try and see how many faces you can rotate round on your desktop. :lolflag:

But seriously the cube helps when you have plenty of windows open and have to move between them - place different windows on different faces then you do not have to min and max all the time, just clicking on the tab in the bottom bar will flip the cube to the desired face.

You can pretty things up with a sky dome, cube caps, transparency of the cube and if you get tired of it looking like you are turning around the cube switch to inside cube view and it will look like you are at the centre of the rotating cube.

I still want to see if I can get specific apps to open on specific faces, the same face every time.

Enjoy the toy, but it can serve a purpose.

---

