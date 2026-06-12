---
title: "XFCE customization"
date: 2011-11-28
forum: Desktop Environments
---

### Post by bug67 on 2011-11-28
Recently switched from Linux Mint 10 (based on Ubuntu 10.10) to Xubuntu 11.10.  I did so in order to have an up to date system with a still supported DE *that I can live with*

Anyhow, I have some questions:

1. Customized cursors Seem to be hit or miss with any version of *buntu.  Custom cursors worked fine for me in Mint 10.  They don't work at all in 11.10 unless I'm hovering over an open browser or email window.  As soon as I navigate off the open browser/email window, the curser reverts back to the default cursor.  I first noticed this issue with Ubuntu 10.04 LTS.  I have read several "fixes" but none of them ever worked. Does anyone know of a sure fire way for me to have my custom cursors?

2.  Is there a setting to turn off select by double clicking on the mouse pad? Very annoying. I couldn't find a setting for this with XFCE. I'd rather just use the buttons on the touch pad to select not the pad itself. 

3. Is there a plugin for the xfce window browser (Thunar) like gksu nautilus for adding the "open as root" contextual menu item?

4. Can I install Compiz in Xubuntu?  I'm sure there is a terminal command but I'm a point and click, copy/paste kinda guy

I think that'll get me by for now. I'm sure as I work with XFCE, I'll come up with some other stuff. Thanks in advance!

---

### Post by LewisTM on 2011-11-28
1. Same here, no idea how to fix it but I'm not into funky looking pointers.

2. gpointing-device-settings is what you want to install. There is a box you can uncheck to disable tapping.

3. In Thunar's Edit/Configure custom actions menu, add an action called 'Open as superuser' with command 'gksudo exo-open %f', set it to appear on file pattern '*' and check all selections. This will add a contextual menu item that will open directories with Thunar as root and open files with their default application also as root.

4. The simplest way is to install fusion-icon and add an autostart entry with 'fusion-icon --force-compiz'. Also verify that compiz-gnome is installed since it provides the window decorator.

Cheers!

---

### Post by 3Miro on 2011-11-28
In Ubuntu, it is compiz that causes issues with the custom cursors, I have not seen trouble with XFCE and custom cursors. You can use compiz under XFCE, however, you may have some issues with the windows decorations. Unless you are using Emerald, you will need a bunch of Gnome-dependencies as well Gnome-control-center to be able to select the decoration theme.

---

### Post by LewisTM on 2011-11-28
There is a [very recent tutorial]("http://it-diary.com/tutorials/install-compiz-emerald-xubuntu-11-10") on how to install both compiz and emerald on Xubuntu. Worth a look.
I still prefer to autostart fusion-icon and set the command 'emerald --replace' in Compiz-Config-Settings-Manager's window decorations dialog.

---

### Post by bug67 on 2011-11-28
> **3Miro said:**
> In Ubuntu, it is compiz that causes issues with the custom cursors, I have not seen trouble with XFCE and custom cursors.

Mine aren't working. I installed comix cursors via Synaptic package manager, logged out/in, wonky cursor behavior. Had the same result when I ran Mint 12.

---

### Post by jimrew111 on 2011-11-28
yes you can get compiz in xfce but its really not that great = you cant change the window theme.

---

### Post by bug67 on 2011-11-28
> **jimrew111 said:**
> yes you can get compiz in xfce but its really not that great = you cant change the window theme.

I guess the only real reasons I want Compiz are for custom window placement settings and user space switching. I could care less about the eye candy...except for my cursors. If I could figure out that without Compiz, fine.

---

### Post by neu5eeCh on 2011-11-28
> **bug67 said:**
>  2.  Is there a setting to turn off select by double clicking on the mouse pad? Very annoying. I couldn't find a setting for this with XFCE. I'd rather just use the buttons on the touch pad to select not the pad itself. 

You can create a script with the following in it (to be run at start up):

> 
# Turn off touchpad tap
/usr/bin/synclient MaxTapTime=0


Or, at terminal, type:

> synclient MaxTapTime=0

You know, the -buntu's all need to fix this. They either need to get the touchpad to work the way it should (as in windows) or turn it off by default. This is just stupid. 

> **bug67 said:**
> 3. Is there a plugin for the xfce window browser (Thunar) like gksu nautilus for adding the "open as root" contextual menu item?

You can create a keyboard shortcut to accomplish this. Keyboard --> Application Shortcuts. Mine is Ctrl-Shift-N.

> **bug67 said:**
> 4. Can I install Compiz in Xubuntu?  I'm sure there is a terminal command but I'm a point and click, copy/paste kinda guy

Yes, but you'll break a sweat. Another member wrote a guide for this here at the forum. Search for it and I will too.

---

### Post by neu5eeCh on 2011-11-28
> **bug67 said:**
> I guess the only real reasons I want Compiz are for custom window placement settings and user space switching. I could care less about the eye candy...except for my cursors. If I could figure out that without Compiz, fine.

By user space switching, do you mean switching between applications and desktops? If so, there's a better solution than compiz - at least for me.

---

### Post by bug67 on 2011-11-28
> **VTPoet said:**
> By user space switching, do you mean switching between applications and desktops? If so, there's a better solution than compiz - at least for me.

Switching between virtual desktops. As of now, I have to physically click on which desktop/work space I want to work in by selecting its icon in the top panel. When I was running a system with Compiz, I could use my mouse's scroll wheel or the touch pad's 2 finger scroll to switch work spaces. I also had the added benefit of the cube effect but, that's not what's important to me.  Care to elaborate on your solutions?

---

### Post by beesthorpe on 2011-11-28
you can use the scroll wheel in xfce - go to "window manager tweaks" in the settings manager and it's under "workspaces" tab

---

### Post by neu5eeCh on 2011-11-28
Sure, I'm not Linux savvy enough to come up with this by myself - so I'm just passing it on. You need to bind the "window list" menu to your mouse. Here's what you do:

The Xubuntu Window List Menu is called:

xfdesktop --windowlist

And in order to bind it to the mouse:

1. Install xbindkeys:

> sudo apt-get install xbindkeys

2. Create initial config file:

> xbindkeys --defaults > $HOME/.xbindkeysrc

3. Edit ~/.xbindkeysrc and add to the end of the file:

> "xfdesktop --windowlist"
b:2

4. Re-read the configuration file:
Code:

> killall -HUP xbindkeys

(But it should reconfigure as soon as the config file is changed.)

5. b:2 is the middle mouse button (the scroll button on my mouse). Press it anywhere to bring up that menu. If you want this to work on every login, add xbindkeys to your autostart.

---

### Post by neu5eeCh on 2011-11-28
> **beesthorpe said:**
> you can use the scroll wheel in xfce - go to "window manager tweaks" in the settings manager and it's under "workspaces" tab

Yes, but that won't let you also switch between individual apps, I don't think. The solution above, for me, is killer. The window list menu allows you to switch between apps and/or workspaces.

---

### Post by beesthorpe on 2011-11-28
is that different from the "show window list on desktop middle click" option in the settings manager > desktop >Menus?

---

### Post by neu5eeCh on 2011-11-28
> **beesthorpe said:**
> is that different from the "show window list on desktop middle click" option in the settings manager > desktop >Menus?

No, it's the same thing. The difference is that by using xbindkeys you can middle click **anywhere**. You don't have to be on the desktop. You can middle click on an open app (meaning you don't have to close it first). It behaves like a very modest version of Compiz scale.

---

### Post by bug67 on 2011-11-28
> **beesthorpe said:**
> you can use the scroll wheel in xfce - go to "window manager tweaks" in the settings manager and it's under "workspaces" tab

Oh, yeah!  How'd I miss that?  :P

---

### Post by beesthorpe on 2011-11-28
> **VTPoet said:**
> No, it's the same thing. The difference is that by using xbindkeys you can middle click **anywhere**. You don't have to be on the desktop. You can middle click on an open app (meaning you don't have to close it first). It behaves like a very modest version of Compiz scale.

oh I see - that  does sound pretty nifty, provided you don’t use middle click pasting a lot.

---

### Post by cottfcfan on 2011-11-29
Any custom cursor works in Xubuntu but you need to edit the file:
```
sudo leafpad /usr/share/icons/default/index.theme
```
Then change the line Inherits= to the name of your cursor theme.
Mine for eg. is Inherits=Ecliz (case sensitive)
Save & close, then log out/in.
Your cursor theme should now be constant instead of flitting between DMZ & your own cursor.

---

### Post by LewisTM on 2011-11-29
You can also bring up the window list with the Window Menu Xfce panel applet, if yo don't want to sacrifice the middle button. I use it a lot to close tabs in browsers and to trigger alternate actions in Cairo-dock.

Another way to use the wheel is to enable 'Switch workspaces with the mouse wheel' in the Workspace Switcher properties. That way you switch workspace when hovering above the pager/switcher.

---

### Post by Vakkotaur on 2011-12-03
(If this is in the wrong place, or already answered, kindly point me to thr right place/answer, thank you.)

I recently moved from Xubuntu 10.04 LTS (wiping out / but not /home) to Xubuntu 11.10.  Did "middle mouse button emulation" change default from ON to OFF?  I seem to have lost tha ability to paste selections without resorting to the keyboard, which is rather annoying as the (near) simultaneous clicks produce a undesired behaviors.

I use a trackall without any middle button, so I need to emulate it.  (Logitech Marble Mouse).  Googling around, I saw something of using xinput to change settings but kept getting told I needed to provide setting that I haven't a clue about.

How do I get middle button emulation back?  Thank you.

---

### Post by beesthorpe on 2011-12-03
For middle mouse button emulation you could try installing "gpointing-device-settings" - it's available in Synaptic.

It doesn't seem to show up in the Application Menu but it can be started  by entering "gpointing-device-settings"in a terminal. It seems to work as expected.

---

### Post by Vakkotaur on 2011-12-03
Thank you, beesthorpe. That was the easy enough sort of solution I was hoping for.  I'll be cussing (more than ) a bit less now.

---

