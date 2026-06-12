---
title: "(L)ubuntu and advanced visual effects (compiz) howto"
date: 2012-05-25
forum: Desktop Environments
---

### Post by uflieven on 2012-05-25
[FONT="Courier New"]This howto describes the steps needed to get compiz running.

If you're new to linux, you may follow this howto but be aware
that you can face some difficulties (in that case other forum
members (or even me) should be able to help out)

This howto applies to Lubuntu, and to all Ubuntu-based
distro's in general (this includes Linux Mint, etc.)

Note that by adding compiz, Lubuntu will become somewhat heavier
on system resources (it will use about 130 MB's of RAM just after
startup instead of 100), if you don't want that, don't use this howto.

If however, you want to use appealing visual effects in Lubuntu,
and don't mind it becoming a little heavier, then read on.

All blue code lines have to be entered in a terminal window.
You don't have to execute all the blue ones, only the ones that
apply.

All words in green have to be replaced. For example, if you see
<name of the theme> in green, that means you don't have to type
<name of the theme>. You should replace it with the name of the
theme, e.g. Nodoka.

**Step 1**
------

On a fresh (L)ubuntu install, enter the following commands in a terminal:
The first one, on the next line is very important, don't forget it, or you
will experience problems.

```
[COLOR="Blue"]sudo apt-get update[/COLOR]
```

**Note to users of Lubuntu versions prior to 12.04:** Compiz seems to
work better with lightdm than it does with lxdm. When logging out,
you may not be able to login again, unless you choose to reboot.
So, if possible, replace lxdm with lightdm by opening a terminal
and entering the following command (Maybe something should be done
about that default magenta background of lightdm, I don't like it,
personally)

```
[COLOR="Blue"]sudo apt-get install lightdm lightdm-gtk-greeter[/COLOR]
```

**If you have an Intel GPU:**

```
[COLOR="blue"]sudo apt-get purge -y xserver-xorg-core
sudo apt-get install -y xorg xserver-xorg-video-intel intel-gpu-tools libdrm-intel1 libva1 libva-x11-1 mesa-utils[/COLOR]
```

I found out which packages where needed by reading Leo Cardinaals' blog. Thanks, Leo!

Now continue under step 2.

**Otherwise (if you have an AMD/ATI or Nvidia GPU):**

You should install the additional hardware drivers using jockey 
(in Lubuntu, the addditonal hardware drivers can be found in the
main menu under preferences)

**Step 2**
------

Enter the following commands in a terminal:

```
[COLOR="Blue"]sudo apt-get install -y compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default compiz-plugins-extra compiz-plugins-main compiz-plugins-main-default compizconfig-settings-manager
sudo apt-get install -y gconf-editor metacity[/COLOR]
```

Then, reboot your system.

After rebooting, download the script compiz-check, as follows (in terminal):

```
[COLOR="blue"]wget [http://blogage.de/files/70708/download](http://blogage.de/files/70708/download) -O compiz-check[/COLOR]

```
Make it executable: 

```
[COLOR="blue"]sudo chmod +x compiz-check[/COLOR]
```

Execute it:

```
[COLOR="blue"]./compiz-check[/COLOR]
```

If the scipt ended with no errors, you will be able to use compiz.
Otherwise you probably won't (sounds logical).

In that case, it is not recommended to continue this howto.
Still, you can search for the error(s) on the internet and
you may be able to solve them.

**Step 3**
------

Then you should install at least 1 metacity theme.

There are two options:

1) install the package metacity-themes and use one of the supplied themes
In terminal: ```
[COLOR="blue"]sudo apt-get install metacity-themes[/COLOR]
```
Then you should continue under step 4.

2) search a theme on the internet and use that (takes a bit longer,
but it maybe worth it, I like the themes better)

Go to [www.gnome-look.org](www.gnome-look.org)

In the left column, choose Metacity.

Click on the tab 'Highest Rated' and choose a theme to download
(e.g. Ordinary Metacity)

After downloading, the new theme will appear in /home/<username>/Downloads
Extract the theme using a terminal:

If it is a tar.gz archive issue the following command: ```
[COLOR="blue"]tar xzvf [COLOR="Green"]<name of the theme>[/COLOR][/COLOR]
```
If it is a tar.bz archive issue the following command: ```
[COLOR="Blue"]tar xjvf [COLOR="Green"]<name of the theme>[/COLOR][/COLOR]
```

One or more new folders will be created, copy them to /usr/share/themes:
```
[COLOR="Blue"]sudo cp -R [COLOR="Green"]<name of folder 1> <name of folder 2> <name of folder n>[/COLOR] /usr/share/themes[/COLOR]
```

Note: if the theme name contains spaces, you should add a backslash before each space
e.g. Ordinary\ Colors

**Step 4**
------

In the applications menu, point to system, configuration-editor.

In the configuration-editor, go to /apps/metacity/general/theme and
change the value in the name of the theme (mind the spelling and capital letters)

Then close the configuation editor.

In the applications menu, point to preferences, compizconfig settings manager.

You should enable at least window decorations, move window, desktop cube,
rotate cube and viewport switcher.

Under viewport switcher, click the third tab (desktop based viewport switching).
At the line 'move next', enable button 4.
At the line 'move previous' enable button 5.
At the line 'initiate plugin action' enable button 2.

Under general settings, click the last tab (desktop size) and change the values
to 4, 1 and 4 respectively.
Almost done, continue to step 5.

**Step 5**
------

**If you are using Lubuntu:**

In a terminal window, enter the following command:

```
[COLOR="blue"]sudo nano /etc/xdg/lxsession/Lubuntu/autostart[/COLOR]
```
At the bottom, enter the following: ```
[COLOR="blue"]@compiz --replace ccp[/COLOR]
```
Then save the file and exit (using Ctrl+x)

This will autostart compiz when you log in.

Continue to step 6.

**If you're NOT using Lubuntu:**

You should add the following line to the end of some autostart file 
(usually somewhere under /etc/xdg):

```
[COLOR="Blue"]@compiz --replace ccp[/COLOR]
```

**Step 6**
------

Log out and log back in.

That's it! 

Now you can rotate desktops using the mouse wheel.
Of course you can enable other plugins (like wobbly windows)
if you want to.

Note:
When you rotate desktops, the pager plugin of lxpanel 
may not change accordingly.[/FONT]

---

