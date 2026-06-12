---
title: "How-To: Change Panel Color Xfce4 - Xubuntu 9.1"
date: 2010-04-20
forum: Desktop Environments
---

### Post by drreed on 2010-04-20
This how-to is written for Xfce users who would like to change the panel color in a theme. The method is tested and works for me with Xubuntu i386 9.10 Karmic w/ Xfce 4. The file names given here were created by sysinstall or subsequent apt-get's, without interference from me. It may work for any Linux distribution with Xfce 4, but I don't know.

```

Make sure you have some themes installed:

$sudo ls -l /usr/share/themes

To get several nice ones quickly:

$sudo apt-get install xfwm4-themes xfce4-theme-brushedchrome

$ls -l /usr/share/themes

If you don't have a color-palette application that's handy, try this one:

$sudo apt-get install gcolor2


```If you haven't already done so, it might help to choose a background, or several that have similar color schemes.

Arrange your open windows such that you get an idea how the desktop will look with any theme. You want to a couple windows open to compare themes.

From the desktop menu choose <settings><appearance>.

Using your mouse, click through the list of themes, choosing one that looks the way you want, but you still need to change the panel color.

When you find one remember the chosen themes name, it's case sensitive.

Create a directory for a new theme. It will be just like the theme you liked, but provide you the file to modify for different colors. You can keep the installed theme, and have your "customized" themes too. In our example, I'll call my new theme Exploit1, and I liked the "Albatross" theme.

```

$sudo mkdir /usr/share/themes/Exploit1

make the copy

$sudo cp -R /usr/share/themes/Albatross /usr/share/themes/Exploit1

that also created /usr/share/themes/Exploit1**/gtk-2.0/gtkrc**.

This the file where we'll find things we can modify with the theme.

$sudo mousepad /usr/share/themes/Exploit1/gtk-2.0/gtkrc


```Near the top of that ascii file, you should see some familiar html color codes for things like "bg" (background), etc. 

If you search for the word "panel", you may find a structure that sets your panel attributes. I did, but I haven't checked every theme - only Albatross.

Here: I changed the attibute "bg[NORMAL] to the color I selected.

```

style "panel" = "dark" {
## Default style
    bg[NORMAL] = "#186224"
## Style 2 : darker active tab and light orange prelight tab
    fg[PRELIGHT] = shade(1.3, @selected_bg_color)
    fg[ACTIVE] = "#fff"
    bg[ACTIVE] = "#1A1A1D"
    bg[PRELIGHT] = "#444"
}

```
Open your bcolor2 color app that you installed, (it's in your graphics submenu on your desktop, or just run bcolor2 from the command line.

Choose the color you need and edit the gtkrc file with the resulting html code.

Notice there are other attributes for ACTIVE and PRELIGHT. When you figure out more things that can be done with your panel, come back here and share it.

Save your work.

Force an update by clicking to another theme, then back to your new one. If you haven't noticed, that copy command also put your new theme into the list on <settings><appearance>. And you can choose it like any other.

Check permissions of your theme files, and set them to look like the other themes.

There are many things you can customize in that file. If you want some nifty screenlets
install:

```


$sudo apt-get install screenlets


```If you want to change the transparency effects of your windows, from your desktop menu open <settings><Window Manager Tweaks> and choose the "Compositor" Tab.
I have mine set so that by clicking on the top of my window, my window becomes transparent. I can work in a terminal, and see through it to double-check commands from a tutorial or how-to.

Hope this helps.

---

### Post by Glutanimate on 2013-03-20
I know that this thread is quite old, but I would just like to thank you for writing this fantastic tutorial. It allowed me to fix a theming issue with the system tray I had when defining a custom color for the panel.

---

### Post by howefield on 2013-03-20
Old thread closed.

---

