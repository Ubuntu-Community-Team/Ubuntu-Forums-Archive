---
title: "customizing the gnome right-click desktop menu"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by vwaj on 2007-07-22
anyone know how to customize the menu that appears when you right-click on the gnome desktop?  i'd like to be able to access the terminal (and perhaps other programs as well) from this menu.  i also would prefer if it appeared on the main section of the menu, not on a submenu.

i believe it is possible to do this by replacing metacity with the openbox window manager...but i'm already using beryl.  and as far as i can tell there's no way to make beryl alter the contents of the menu.

any help is much appreciated.

---

### Post by Brian96 on 2007-07-22
Not to hijack, but I've similarly been interested in getting a main menu with a desktop mouse click.

---

### Post by urukrama on 2007-07-23
It is possible, and it has been discussed on here before. Let's see if I can find a similar thread on this.

EDIT: See [here]("http://ubuntuforums.org/showthread.php?t=228371") for instructions. Other threads on this or similar issues can be found [here]("http://ubuntuforums.org/showthread.php?p=2705574#post2705574") and [here]("http://ubuntuforums.org/showthread.php?p=2813187#post2813187")

---

### Post by mcduck on 2007-07-23
> **vwaj said:**
> anyone know how to customize the menu that appears when you right-click on the gnome desktop?  i'd like to be able to access the terminal.
That, at least, is very easy. 'sudo apt-get install nautilus-open-terminal', or install the package with your tool of choice. Then log out and back again and you have 'Open in Terminal' in your right-click menu.
> **vwaj said:**
> 
i believe it is possible to do this by replacing metacity with the openbox window manager...but i'm already using beryl.  and as far as i can tell there's no way to make beryl alter the contents of the menu.

any help is much appreciated.
Replacing Metacity would not help, as it's just a window manager and the right-click menu in Gnome is handled by Nautilus, the file manager..

---

### Post by Brian96 on 2007-07-23
So the desktop mouse-click menus are controlled by the file manager? 

If so, then if I replaced Nautilus with Thunar I should be able to get to the right-click main menu on the desktop?

I am trying to balance what I like in Gnome with what I like in Xfce (and other DEs). For example, I really like the simplicity with which menus can be edited in Gnome. However, I like the simplicity with which I can obtain a main menu from the desktop with Xfce. I'd also like to do all of this without any panels.

---

### Post by hyperair on 2007-07-23
Go to Synaptic Package Manager and install nautilus-actions, nautilus-gksu, nautilus-open-terminal, and nautilus-image-converter. When you're done, you'll be able to resize and rotate images in Nautilus, open a terminal from any folder, and access any file/folder as administrator through the rightclick menu. Also, you can customize extra options by going to System->Preferences->Nautilus Actions Configuration.

---

### Post by urukrama on 2007-07-23
> **Brian96 said:**
>  If so, then if I replaced Nautilus with Thunar I should be able to get to the right-click main menu on the desktop?

No, this won't work, as Nautilus is more than a file manager and also draws the desktop. Thunar doesn't, and though there is a [script]("http://psychocats.net/ubuntu/nonautilusplease") around that allows you to change your default file manager to Thunar, it does not affect desktop items, for this reason.

You can disable Nautilus from drawing the destkop, and then use a right-click desktop menu if you use openbox, fluxbox, etc. as window manager, but that is not what you are after. I don't think there is another option aside from editing the Nautilus menus as suggested earlier (unless there is something hidden deep in gconf, but I doubt it).

---

### Post by Brian96 on 2007-07-25
I installed the recommended applications (I REALLY like the image converter--I have been looking for something like this for Linux after using a similar tool in M$). The "open terminal" option appeared on the desktop menu, but I am still not sure how to add custom items to the menu. This is probably because I am still struggling with how to actually use the Nautilus Actions Configuration utility. Any suggestions?

---

### Post by hyperair on 2007-07-26
I reckon I could help you with it, if you post what you intend to do.. Otherwise, probably not.

---

### Post by CowzRule on 2007-07-26
Here are some scripts that will add the following to your right click menu

gedit-here
root-gedit-here
root-nautilus-here
root-terminal-here
terminal-here

Place these simple scripts in

/home/YOURUSERNAME/.gnome/nautilus-scripts

replace YOURUSERNAME with your user name.
the folder .gnome2 is a hidden folder. You'll need to hit Ctrl+h to see it.

I know these are displayed in a sub-menu but it shows what you can do.

---

### Post by Brian96 on 2007-07-26
> **hyperair said:**
> I reckon I could help you with it, if you post what you intend to do.. Otherwise, probably not.

What I really want is to be able to get a main menu when I right click on the desktop. If there is a way to add the main menu to the existing Nautilus desktop menu, that would be fine. If that is not possible, I would at least like to add launchers to the right-click menu for certain applications (firefox, thunderbird, etc.).

I know that other WMs and DEs already offer the option to change the right-click menu. However there are things I like about Gnome and Nautilus that I'd like to keep if I could only get past this issue. So I'd like to find a way to do this in Gnome/Nautilus without having to substitute the WM.

Thanks for your help.

---

### Post by hyperair on 2007-07-26
I'll go through Firefox:
1. In Nautilus Actions, click Add.
2. Label: Firefox, Icon: path to some firefox icon, Path: /usr/bin/firefox
3. Under the Conditions tab, change the "Appears if selection contains" to "both"
4. Under Advanced Cinditions check everything.

---

### Post by Brian96 on 2007-07-26
> **hyperair said:**
> I'll go through Firefox:
1. In Nautilus Actions, click Add.
2. Label: Firefox, Icon: path to some firefox icon, Path: /usr/bin/firefox
3. Under the Conditions tab, change the "Appears if selection contains" to "both"
4. Under Advanced Cinditions check everything.

Thanks, I'll try that!

---

