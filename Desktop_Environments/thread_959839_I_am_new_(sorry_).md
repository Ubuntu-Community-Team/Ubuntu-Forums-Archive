---
title: "I am new (sorry )"
date: 2008-10-26
forum: Desktop Environments
---

### Post by dsjoes on 2008-10-26
how do you get and install the dock that goes with the mac theme.

how do you change the splash screen.

when i go onto hotmail.com and login it tells me i need to upgrade my browser. i am using firefox 3.0.3.

i am using ubuntu 8.4.

Thanks:)

---

### Post by ad_267 on 2008-10-26
Nothing to be sorry about, everyone's new once.

how do you get and install the dock that goes with the mac theme.
- There are a few different docks but the most popular is AWN. Instructions to install a more recent version than that available from the normal 8.04 repositories can be found here: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

how do you change the splash screen.
- I'm not sure what you mean by "splash screen," because there isn't a splash screen by default. You can set one if you install gnome-splashscreen-manager I think. You can change the login screen in System - Administration - Login Window.

when i go onto hotmail.com and login it tells me i need to upgrade my browser. i am using firefox 3.0.3.
- Yeah just ignore that, hotmail is stupid, it wouldn't say that if you had firefox 2.

---

### Post by dsjoes on 2008-10-26
thanks

i have installed compiz effects but it does not show up in system-preference but when i installed it and double clicked the finished install bit the screen opened but it said install at the top of its screen and would not let me install it.

---

### Post by ad_267 on 2008-10-26
I'm not sure what you mean sorry. You shouldn't have to install anything, compiz is already installed by default. You can go to System - Preferences - Appearance - Desktop Effects and set them to normal or extra to enable compiz. If you can't enable that because your video card is not supported then you can enable compositing in Metacity, the default window manager. I'll explain that if you need to.

---

### Post by dsjoes on 2008-10-27
it is enabled but it does not appear in the menu

---

### Post by freqhack on 2008-10-27
Try installing Fusion-Icon

```
sudo apt-get install fusion-icon
```

It'll appear in you applications menu under System Tools. Or you can run it from the command line by just typing fusion-icon

It will put a little blue icon up on your panel next to the clock. Right-click on it and 'Settings Manager' will be the first item there if you have the Compiz Settings Manager installed.

---

### Post by dsjoes on 2008-10-27
i have installed it and it has got compiz options and select window manager that has got compiz in it

---

### Post by issih on 2008-10-27
Provided your graphics drivers are up to scratch (i.e. hardware acceleration is working) compiz is enabled by default, however there are no menu items to really see, or settings to tweak.

Essentially, by default, ubuntu gives you three different visual profiles..Open up System->Preferences->Apearance

On the Visual Effects tab of that dialog you can choose from None, Normal or Extra.

"None", does not use compiz, it uses gnome's default window manager metacity.

"Normal" uses compiz and provides a few visual effects to make things look prettier, but not too many.

"Extra" has lots of visual bells and whistles.

In all cases however, you are stuck with the choices that the ubuntu dev's have made as to what visual effects you are going to see.

The fusion icon linked above allows you to easily switch between window managers (e.g. compiz and metacity, and also switch between different window decorators, e.g. emerald)

If what you really want is the ability to tweak what plugins compiz is using, and change the visual effects to your own custom profile you need to install ccsm (compiz onfig settngs manager)

Just search for it in synaptic, or use the following command in a terminal:

```
sudo apt-get install compizconfig-settings-manager
```

That will add a new application to your Preferences menu, that will allow you to change the settings compiz is using.

Hope that helps.

---

### Post by dsjoes on 2008-10-27
thanks that has given me advanced desktop effects settings

---

