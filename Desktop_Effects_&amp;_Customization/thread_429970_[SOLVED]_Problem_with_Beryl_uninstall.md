---
title: "[SOLVED] Problem with Beryl uninstall"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-05-01
I installed Ubuntu last night adn checked out Compiz and it worked great. Then I put on Beryl using the Add/Remove and that worked too.
 
Today i read something abt emerald themes in beryl. So i first did
 
```

sudo aptitude remove beryl

```
 
and then installed beryl beryl-manager and emerald-themes like so 
```
 
sudo apt-get install beryl beryl-manager emerald-themes

```
 
Now my problem is thatBeryl doesnt load up. I even removed all three packages but now even my Compiz doesnt start up. I have Cube Enabled in the Desktop Effects and wobbly windows...but neither work !
 
Also, only one of my desktops have both the taskbars. Once i switch desktops...i cant do anything i just see a brown ubuntu wallpaper !
 
Help !!

---

### Post by Belyel on 2007-05-01
I had very odd problems when trying to uninstall/reinstall beryl.  The only thing that finally worked for me was to purge beryl using "apt-get remove --purge beryl beryl-* emerald emerald-* libberyl* libemerald*", remove the settings folders .beryl and .emerald in my home directory, then reinstall from scratch.  All your settings will be lost, but it worked for me.  Also, there was no need to uninstall beryl before installing the themes.  All you needed to do was apt-get install emerald-themes.

---

### Post by starcraft.man on 2007-05-01
Ummm, well I'm a bit confused why you removed beryl to install emerald. They are independent, at least in the sense that you don't need to have emerald to run beryl, I don't think the reverse is true.

As for beryl doesn't load up, did you manually readd it to the session list? 

```
System > Preferences > Sessions
```

its right in the first tab just add these three terminal commands to make sure it works.

```
beryl
beryl-manager
emerald --replace
```

(sometimes when theres an error, beryl doesn't load just from picking beryl-manager, this might fix your problem.) 

I don't understand your second question, what do you mean switch desktops? Rotate the cube? Please be specific.

Hope that fixes your first problem. :)

---

### Post by Inxsible on 2007-05-01
i mean i cant have a cube at all. Although i have 4 workspaces...when i switch between them there is no cube effect. also once i switch there are no taskbars on the other workspaces so i have to do a ctrl+alt+backspace to restart X

---

