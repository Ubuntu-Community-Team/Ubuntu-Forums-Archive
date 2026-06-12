---
title: "[How-To] Getting the most out of Avant Window Navigator as an alternative &quot;shell&quot;"
date: 2011-03-24
forum: Desktop Environments
---

### Post by Copper Bezel on 2011-03-24
There are a lot of tutorials online for getting at individual features in AWN (or DockBarX), and I understand that not every feature I'm making use of here is necessarily going to be useful to every user - this is an interface tailored to *my* workflow. Still, if you're new to AWN, here's a quick tutorial on some of the features you'll want to know about to be able to take full advantage of it. The goal here is to configure AWN as an alternative shell to Unity that retains all the same basic features (and a few extra.)

In this tutorial, despite the default settings on everything else, I'm using the (very trendy, I know) Orta theme and Faenza icons. I don't think it's without reason that these are becoming Gnome's Aqua. They're very readable and clean, and they both include a lot of special features (like Orta's extensive appearance configuration options and Faenza's inclusion of special notification tray icons for common apps like Dropbox and Tomboy.)

Although I know there are perfectly good reasons for both options, I'm going to be assuming in this tutorial that you're using a theme with the window buttons on the *left*, as this is needed for the Unity-style workflow presented. If you don't know how to change this feature, I'll explain it when I mention gconf-editor below. 

Ingredients:

We'll need to add two PPAs to your system - one for AWN and one for DockBarX. 

```
sudo add-apt-repository ppa:awn-testing/ppa

sudo add-apt-repository ppa:dockbar-main/ppa
```

After that, we'll update the package lists, then install these packages.

```
sudo apt-get update

sudo apt-get install avant-window-navigator-trunk dockbarx awn-applet-dockbarx xfce4-utils ccsm gconf-editor
```

The packages you're installing:

avant-window-navigator-trunk - The new panel itself
dockbarx - A better task manager that plays nicely with AWN
awn-applet-dockbarx - The wrapper that connects the two
xfce4-utils - A utility package from XFCE that includes a replacement Run Dialog (explanation later)
ccsm - Compiz Config Settings Manager, which allows you to configure desktop effects and keyboard shortcuts, including the Run Dialog
gconf-editor - Gnome Configuration Editor, which will allow us to replace Gnome Panel completely with AWN.

We'll start at the defaults. Log into a default Gnome 2 environment (by selecting it under Session at the Login screen) and, once you're all logged in, run Avant Window Navigator. 

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/001.png[/img]

You can remove the bottom Gnome Panel by editing its settings, but there's no way to remove the last panel while the panel application is running. Instead, we'll just make AWN the new default panel application. hit Alt+F2 and run gconf-editor and change this key from gnome-panel to avant-window-navigator . 

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/002.png[/img]

Log out and log back in for the change to take effect.

If you have your window control buttons on the right, you can shift them to the left in gconf-editor, too, so do that while you're here. Select Apps -> Metacity -> General and look for the Button Layout key. Note that this won't work if you're using an Emerald window frame.

Now we have a very bare desktop. You'll notice that Alt+F2 has stopped working, and there's no system tray. We'll get these features back in a moment. 

For right now, let's begin by making the AWN launcher a little more presentable. By right-clicking the panel, you can access its settings. We'll make the icon size a bit smaller and move it to the left. Set the behavior to Intellihide and the hide style below this to Transparency. This is one feature AWN has over Unity: the dock will be visible at all times, but if it overlaps a window or a window is maximized, it will fade into an overlay that can be clicked through and only reactivate when you touch the left border of the screen. This means that the dock doesn't take up any pixel space but is always visible and immediately accessible.

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/003.png[/img]

The applets you see here are the Cairo Menu (which offers a nice quick-access Places menu) and the Task Manager with a Separator in between. If you plan on using DockBarX, don't worry about adding launchers to the taskbar yet.

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/004.png[/img]

Go back to the preferences tab and click Add Dock. This one will be our system tray. Set it to Top, with a behavior of Always Visible, and drag the Position slider to the far right. Set the Icon Size to about the thickness of your titlebar (about sixteen or eighteen pixels.)

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/005.png[/img]

Now, remove the existing applets and add a Notification Area and an Indicator Applet from the Applets tab. You'll notice that the icons are stacked weirdly and a little ugly: right click the border of the Notification Area, set Number of Icon Rows to 1, and turn off the background. To get the same effect in the Indicator Applet, right Click anywhere in the applet itself, select Preferences, and check the box for Enable Applet Icon Mode. You can also add a Quit/Logout applet or  a Digital Clock to the dock at this time.  Notice that the Indicator Applet can be run in more than one place at a time and each can be configured separately, so that you could, say, separate out your Me Menu or Sound Control as its own dock applet.

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/006.png[/img]

AWN's default offset from the screen edge is 10. I'd suggest a much smaller setting for a layout like this one (because the system tray has to fit into the window titlebar and because the left-hand Launcher is set to Transparency, so we want the buttons to be clickable when the cursor is at the far edge of the screen.) Find this setting under the Advanced tab and set it for each dock.

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/007.png[/img]

We're most of the way to a functional-looking desktop, but there's still no Run Dialog when you press Alt+F2, because this is actually a dialog provided by Gnome Panel. Instead, we'll use the one provided by xfce-utils. From the Main Menu at the left, go to Preferences -> Compiz Config Settings Manager (ccsm), then click the Commands tile. Enter "xfrun4" as Command 0, then click the keybindings tab. Enter whatever keystroke you like, although you might want to make it something other than Alt+F2 to avoid possible conflicts. 

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/008.png[/img]

You could use something like Synapse instead of xfrun4, although xfrun4 will allow you to run more complex commands. Either one will appear when you select Launch from the Main Menu.

This gets us most of the way to a functional desktop, but I'd recommend using DockBarX over the default taskbar, as I'll explain in the following post.

---

### Post by Copper Bezel on 2011-03-24
Here's what we have so far:

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/009.png[/img]

Now we'll deal with the taskbar, which we'll want to replace with DockBarX, which comes with a few extra features not available in AWN's taskbar. You can't remove the AWN taskbar and keep the Intellihide behavior, but by removing the last launcher and setting it to Display Only Launchers, you can make it invisible.

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/010.png[/img]

If DockBarX is properly installed, you can simply add it to the dock as an applet. Now, you can add launchers to DockBarX by simply dragging and dropping them from the Main Menu. It's already much prettier than AWN's taskbar, but it isn't consistent with the rest of the theme. Go to Accessories - > DockBarX Preferences. 

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/011.png[/img]

For the Faenza icons, I prefer the Minimalistic 2 theme, which keeps the spacing and size of the icons consistent. Whatever theme you select, be sure to hit the Refresh button next to the menu to apply it. I'm also selecting the option here to keep the GTK-style menus, which offer quicker access to Recent Documents and match the system theme. 

Another appearance tweak you might want to enable is under Window Item, which is to enable Window Previews and the Close Button, giving you Windows-7-style  previews of open windows when you hover their icons that can be quickly minimized or closed.

And here's the bit that DockBarX really has over AWN's taskbar. There are a vast number of tweaks and settings for the behavior of taskbar items. One really nice feature that made its way into Unity as well is this Compiz Scale setting, which will fan out all the windows currently running in an application if its icon is clicked.

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/012.png[/img]

DockBarX's Plugins are also a perk. Enable "Helpers" for recent documents, Rhythmbox controls right in the window preview, etc. Similarly, in the Advanced features tab, you can choose the behavior you want for OpenOffice windows. These features go just a bit farther than the equivalents in AWN's taskbar. 

Going back to AWN's settings, we'll make some final tweaks for that last bit of polish. AWN uses the system colors by default, but they're not always laid out in a way that matches the theme itself, and you might not want a perfect match, anyway. Select the Themes tab and go straight to the Customize button - all the theme settings can be controlled from here, including the curve radius and all colors, all of which include alpha transparency. 

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/013.png[/img]

So here we are - you have a Unity-style interface (with all of the features and a couple extra) that can still be tweaked and configured to your liking and workflow. Happy customizing!

[img]http://dl.dropbox.com/u/17749392/AWNtut/Revised%20Screenshots/014.png[/img]

---

### Post by Lucradia on 2011-03-24
Just so I don't lose it here, I'll post a thank you reply.

Two birds, one stone.

---

### Post by Rasa1111 on 2011-03-24
]Thanks mate!

Just got this dockbarx thing installed earlier, and theres a couple things Ive been wondering.. 
 Ill fully read through this and come back with any questions.

Im going for a something a lil more like this~
[IMG]http://lh6.googleusercontent.com/_1QSDkzYY2vc/TU6yZbzaHHI/AAAAAAAAC24/52Waj_6vVgU/s500/dockbarx-rhythmbox.png[/IMG]

 almost there, *almost*...
Subscribed! lol :)

many thanks

---

### Post by Copper Bezel on 2011-03-25
Sweet, and y'welcome both of you. = )

> Im going for a something a lil more like this~

Let's see, DockBarX has Preview turned on under Window List and Close Button turned on under Window Item, and the Rhythmbox controls are turned on under Advanced. The preview size is set to ~250, larger than the default.

For AWN itself, the style is Lucido, and under the Theme tab and under Customize, the theme's Highlight Colors are set to 0% opacity and the Thickness is set to 0. There's a separator on either side of DockBarX in Applets. But I know you know how to do all of that, because I've seen your screenshots, and you're the one who told me about the geometry tweaks in Theme -> Customize. = )

Edit: Made a correction above: The package that includes xfrun4 is xfce4-utils, not xfce-utils.

---

### Post by Rasa1111 on 2011-03-25
Thanks mate. :)

Ok, here is my dilemma...

 The only way I can see the 'preview' when hovering over an icon,
is when the window/app itself is open.

Seems rather pointless. :confused:

Let me show you..

 If chromium is minimized,
and i hover my cursor over it in AWN, the 'preview' window pops up,
but shows me nothing but the chromium icon >[ATTACH]187017[/ATTACH]

Same for anything else...[ATTACH]187019[/ATTACH]
>  

But, if the window/app itself is open/maximized, and i hover over the icon.. the preview/contents shows up in the dockbarx preview. 
[ATTACH]187018[/ATTACH]
[ATTACH]187020[/ATTACH]

Is this a 'bug' on my end? or am i just missing some setting somewhere?  lol

got AWN for my top panel now though. thanks. :)

---

### Post by Copper Bezel on 2011-03-25
Cool. = )

> Is this a 'bug' on my end? or am i just missing some setting somewhere?

Unfortunately, it's an inherent problem in the way Compiz draws windows (DockBarX is heavily Compiz-dependent, and a lot of the cooler features use Compiz plugins, including the Window Preview.) 

If a window is minimized, it isn't mapped at all. That's why it doesn't appear in Scale and only displays as an icon in the Ring and Shift Switchers, for instance. The perk is that it doesn't consume resources being rendered; the drawback is that it can't be previewed through any of these plugins, which are all taking their visuals from Compiz's compositor itself, because the window is simply not being drawn *anywhere*.

The Preview can still be useful for windows on other workspaces or hidden behind maximized ones, but no, I don't know of any way to force it to map the window for minimized ones. There was talk at one time of Compiz keeping these windows mapped without displaying them, but I don't know what became of it, and it'd be a fairly complex (and slow) workaround for DockBarX to fix the problem within the present Compiz framework.

One thing I've found useful is to go to the Window Item tab and uncheck "Close window list" by Select. It doesn't solve your problem directly, but if you have this setting switched off, then clicking the icon to bring up a minimized window won't close the preview, so you can just click it again to minimize it back and get back to what you were doing.

---

### Post by Rasa1111 on 2011-03-25
damn!

 Thanks man. :)

 I wonder how he did it then?
[IMG]http://lh6.googleusercontent.com/_1QSDkzYY2vc/TU6yZbzaHHI/AAAAAAAAC24/52Waj_6vVgU/s500/dockbarx-rhythmbox.png[/IMG]

 I guess..
If I can't get this to act "proper"..
I might as well remove it.  lol

 If that doesnt work,
 I guess I don't see the point of it. 

That was the main reason i installed it to..
to achieve the effect in above screenshot. lol  d'oh!

I appreciate your time, my friend. 
 Thanks. 
and nice work! :) <3

---

### Post by Copper Bezel on 2011-03-25
Thanks. = ) Yeah, I don't know what's going on in that screenshot. I guess it's on another workspace?

[img]http://dl.dropbox.com/u/17749392/Screenshots/nopreview.png[/img]

---

### Post by M7S on 2011-03-25
In compiz 0.9.2 and newer there's an option to show previews for minimized windows. Sadly there's also a bug in newer versions of compiz that makes previews show up behind popup instead of above it. So you need to make the popup background almost transparent to see it.

---

### Post by Copper Bezel on 2011-03-25
Huh. And that wouldn't help at all for DockBarX, where the preview background can't be configured at all, although I wonder if it would be composited differently than in the ordinary Compiz window previews. That might explain the screenshot Rasa saw. Worth trying when I have time, I guess. = ) Thanks for the tip!

---

### Post by M7S on 2011-03-31
Sorry, I didn't see your answer before now (note to self, always subscribe to threads where you give  DockbarX support).

You can change the color and transparency of DockbarX popup from DockbarX preference, that's what I meant. I'm the developer of DockbarX, of course I'm talking about DockbarX and nothing else. ;)

That screenshot is from webupd8:s webpage and the window is probably on a part of the screen that isn't in the screenshot.

---

### Post by Rasa1111 on 2011-03-31
still kind of annoyed I couldnt get that to work how I wanted/expected. lol :/

---

### Post by M7S on 2011-03-31
With compiz 0.92 or later it almost works that way if you turn down the transparency of the dockbarx popup and enable previews for minimized windows from compiz settings.

To get compiz 0.92, install Natty or compile from source (at least I don't think there's a maverick ppa for compiz 0.92, but I'm not sure).

---

### Post by Copper Bezel on 2011-03-31
> I'm the developer of DockbarX, of course I'm talking about DockbarX and nothing else.

Oh! That makes sense then. And yeah, I'd somehow missed the Window List Background setting.

Also, thank you, because you've simplified my life.

---

### Post by hewbert on 2011-04-25
Any clues on how to do this with Natty?  I'm assuming the issue with removing the gnome-panel has to do with the transition to gsettings, as changing the 'panel' in gconf doesn't work.

I dig this setup on my netbook and enjoy the added benefits of having the gnome stuff loaded up.

Edit:  Looks like copying /usr/share/gnome-session/sessions/classic-gnome.session to something like 'awn.session' and editing it accordingly works for now.

---

