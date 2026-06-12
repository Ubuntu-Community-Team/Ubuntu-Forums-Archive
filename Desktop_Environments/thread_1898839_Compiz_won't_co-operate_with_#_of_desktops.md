---
title: "Compiz won't co-operate with # of desktops"
date: 2011-12-22
forum: Desktop Environments
---

### Post by meanmrmustard on 2011-12-22
I'm not sure what might have been changed in regard to this problem but I cannot get more than 1 desktop unless I switch desktop managers to metacity.
With Compiz enabled even with the general settings set to allow 6 desktops I can only get one.

I'm thinking there must be some other setting in Compiz that is conflicting but so far experimenting has produced no results.

Anyone have an idea what may be causing this?
thanks

---

### Post by emmomalick on 2011-12-22
Do you see Desktop Switcher at the right corner of the bottom panel? How many desktops are shown there?

---

### Post by meanmrmustard on 2011-12-22
> **emmomalick said:**
> Do you see Desktop Switcher at the right corner of the bottom panel? How many desktops are shown there?

Just one.

---

### Post by emmomalick on 2011-12-22
> **meanmrmustard said:**
> Just one.
Right Click on the Desktop Switcher e.g (your current active work-space)from the right bottom panel, Click on Preferences, Increase the number of workspaces as required by you. 

Now try what you are trying to do. Do inform me if it works.

---

### Post by meanmrmustard on 2011-12-22
> **emmomalick said:**
> Right Click on the Desktop Switcher e.g (your current active work-space)from the right bottom panel, Click on Preferences, Increase the number of workspaces as required by you. 

Now try what you are trying to do. Do inform me if it works.

The right click on the panel has "properties" no preferences. Properties only allows changing orientation and size along with expand, autohide and show hide buttons checkboxes on the general tab. The background tab lets me choose color, transparency and a background image.
There is no way in this dialog to increase the number of desktops.
Maybe in Metacity, but not with Compiz running.

---

### Post by emmomalick on 2011-12-22
I think you're going in the panel properties, that not what I told you. Do right click on the DESKTOP SWITCHER, (as it the only one shown at the right bottom corner of the panel) here you see PREFERENCES from there you can change the number of workspaces.

---

### Post by emmomalick on 2011-12-22
Check here. 

[http://www.addictivetips.com/ubuntu-linux-tips/add-switch-and-change-workspace-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/add-switch-and-change-workspace-in-ubuntu-linux/)

---

### Post by meanmrmustard on 2011-12-22
> **emmomalick said:**
> I think you're going in the panel properties, that not what I told you. Do right click on the DESKTOP SWITCHER, (as it the only one shown at the right bottom corner of the panel) here you see PREFERENCES from there you can change the number of workspaces.

Ok... I found preferences but it only shows columns and rows - no tabs - and the Help and Close buttons.
I see the help says "Use the Number of workspaces spin box to specify the number of workspaces that you require." but there is no spinbox.
I wonder if compiz has some setting that is inhibiting this.
There is a setting in Compiz to increase the # of workspaces but it does nothing... even after a re-boot, there is still just one workspace.
edit:
Compiz settings does have a box to  check that is supposed to "keep Compiz compatible with the Gnome desktop environment." it is checked and greyed out. I guess I need to start the manager as root to change this.

another edit:
So I ran sudo ccsm and unchecked the "Gnome compatibility" box - then I open ccsm as regular user and see the box is still checked.

---

### Post by sikander3786 on 2011-12-22
Hi.

Which version of Ubuntu is this?

First of all, we should make sure that your machine is capable of running Compiz. Do you get those animation effects when you switch your manager to Compiz? From a Terminal, please post the output of this command:

```
lshw -c video
```

> I guess I need to start the manager as root to change this.

No, it should run as the normal user thats you.

As an attempt, you can try to restore the default settings of Compiz and see if that helps.

```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
```

---

### Post by meanmrmustard on 2011-12-22
> **sikander3786 said:**
> Hi.

Which version of Ubuntu is this?

First of all, we should make sure that your machine is capable of running Compiz.

I'm sure it's capable. It's been running Compiz since the install (Natty) and worked fine until recently.

> 

No, it should run as the normal user thats you.

It runs as normal user but the option to change the "Gnome Desktop integration" setting is greyed out until it's run as root.

I found another setting in Compiz under preferences and unchecked the "Enable integration into the desktop environment" and also clicked to reset to defaults the profile information.
One or the other did the trick.
Now the columns box in desktop switcher changes the number of desktops when I increase it. (side note: What is this "workspace spinbox" mentioned in the help file? No such thing exists in my preferences dialog)
When I go back to ccsm general settings under desktop size, the number of desktops is set to 1. I change it to six and immediately have a single desktop again (in the switcher). I returned it to 1 and all six are showing again.
Maybe I've found a bug?

Still though in the General category (ccsm settings manager), the Gnome Compatibility box and the OpenGL box - both checked - are greyed out and cannot be changed.
As I said in the last post, running ccsm as root allows me to uncheck the boxes but after closing it and opening ccsm as regular user the box is still checked and greyed out.

yet another edit:
I've just discovered that, as normal user, I am unable to check or uncheck any of the boxes in ccsm manager, they are all greyed out.

---

### Post by sikander3786 on 2011-12-22
Did you try resetting the Compiz settings as mentioned in the above post?

It might also be helpful to purge Compiz completely from Synaptic and then re-install it. Probably you used CCSM as root for once and then lost the normal user's access. However, this is weird.

---

### Post by meanmrmustard on 2011-12-23
> **sikander3786 said:**
> Did you try resetting the Compiz settings as mentioned in the above post?

It might also be helpful to purge Compiz completely from Synaptic and then re-install it. Probably you used CCSM as root for once and then lost the normal user's access. However, this is weird.

I did do that after getting the # of desktops fixed.
The "~/.compiz-1/session/*" command didn't find a file, the next one exited quietly.

Do I then need to re-boot to re-create the ~/.compiz... file? - not quite ready to do that.
I'm still unable to add or remove components in ccsm as user.
Maybe purging Compiz is the best idea.

---

### Post by sikander3786 on 2011-12-23
Nopes you don't need to create the missing file. These commands are intended for different versions of Ubuntu, some come with one file and some with the other.

Yeah, the last hope is probably purging and re-install Compiz.

---

### Post by LewisTM on 2011-12-23
As far as I know Compiz manages the number of desktops differently than other window managers.

In ccsm/General/Desktop size, you should set it to *one* desktop and as many *virtual* horizontal and vertical desktops as you want (e.g. 6 horizontal). 

Those Virtual desktops are also called *Viewports* and that is what is managed by the Switcher. You can have several actual desktops each with its own set of viewports but I don't see why anyone would do that.

---

### Post by meanmrmustard on 2011-12-23
I will purge and re-install Compiz once I have other issues taken care of, then come back and tell how it fixed everything!
Thanks to all for your input.

---

### Post by lolpenguin on 2011-12-25
Can't believe everyone missed this: virtual desktops are called **workspaces**.

---

### Post by LewisTM on 2011-12-25
> **lolpenguin said:**
> Can't believe everyone missed this: virtual desktops are called **workspaces**.
Not when Compiz is concerned.
See [http://wiki.compiz.org/GeneralOptions](http://wiki.compiz.org/GeneralOptions)
When switching workspaces in KDE, GNOME or XFCE, you actually ask Compiz to switch viewport. So you have to set the virtual size to >1. For instance to have a cube, you need to set the horizontal size to 4.

---

