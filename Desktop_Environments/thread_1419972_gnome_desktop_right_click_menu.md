---
title: "gnome desktop right click menu"
date: 2010-03-02
forum: Desktop Environments
---

### Post by Post Monkeh on 2010-03-02
i have nautilus actions installed and i've been wondering if there's any way to set it so that when i right click the desktop, i can have a menu in there similar or identical to the main applications menu?

i've read a few guides about using xautomation to initiate an alt & f1, but the problem is it just brings up the menu up at the panel.
i also read about a compiz menu, but i don't want to lose my default right click menu, just add to it.

---

### Post by pastalavista on 2010-03-02
You could try 'nautilus-actions'
```
sudo apt-get install nautilus-actions
```

It lets you add almost anything. It'll appear in the System|Preferences menu.

---

### Post by Post Monkeh on 2010-03-02
> **pastalavista said:**
> You could try 'nautilus-actions'
```
sudo apt-get install nautilus-actions
```

It lets you add almost anything. It'll appear in the System|Preferences menu.

read the first 5 words of my post ;)

---

### Post by pastalavista on 2010-03-02
> **Post Monkeh said:**
> read the first 5 words of my post ;)
Sorry about my short attention span. :P I can't get nautilus-actions to work at all on Lucid Lynx.

I bet you'd enjoy [CrunchBang Linux]("http://crunchbanglinux.org/wiki/about"). It's based on Ubuntu but uses the openbox window manager (which you could install on Ubuntu if you dare) and it has menus like you want.

---

### Post by Post Monkeh on 2010-03-02
> **pastalavista said:**
> Sorry about my short attention span. :P I can't get nautilus-actions to work at all on Lucid Lynx.

I bet you'd enjoy [CrunchBang Linux]("http://crunchbanglinux.org/wiki/about"). It's based on Ubuntu but uses the openbox window manager (which you could install on Ubuntu if you dare) and it has menus like you want.

i've tried it, and i like it except that for some reason apps like firefox and opera are reeeeaaaallllyyy slow to restore from being minimised if they have a few tabs open. i've installed it over ubuntu and on an external drive and it does the same thing on both.
i've considered seeing if there's any way i could use openbox to JUST provide a right click menu on the desktop and decorate my windows, then have nautilus take care of everything within its own windows, but i was just wondering if the nautilus-actions could provide some sort of access to my main menu.

---

### Post by urukrama on 2010-03-03
> **Post Monkeh said:**
> i've considered seeing if there's any way i could use openbox to JUST provide a right click menu on the desktop and decorate my windows, then have nautilus take care of everything within its own windows, but i was just wondering if the nautilus-actions could provide some sort of access to my main menu.

You can use Openbox in Gnome. If you install Openbox from the repositories (with Synaptic or through *aptitude install openbox*), select the Openbox-Gnome session in your login manager. You will then run Gnome with Openbox as the window manager, instead of Metacity.

If you search through the forums, you'll find a lot of threads on this topic. See [this post]("http://ubuntuforums.org/showpost.php?p=5136862&postcount=9") for some of them.

---

### Post by Post Monkeh on 2010-03-03
> **urukrama said:**
> You can use Openbox in Gnome. If you install Openbox from the repositories (with Synaptic or through *aptitude install openbox*), select the Openbox-Gnome session in your login manager. You will then run Gnome with Openbox as the window manager, instead of Metacity.

If you search through the forums, you'll find a lot of threads on this topic. See [this post]("http://ubuntuforums.org/showpost.php?p=5136862&postcount=9") for some of them.

i've tried openbox and while there are parts of it i like, it doesn't seem to like opera or firefox and restores their windows very slowly after they're minimised.

all of the threads i found described replacing the right click menu entirely, i just want to add functionality rather than replace what's already there.

i think i'll look into compiz-deskmenu, and initiate it with a keyboard shortcut rather than a desktop click

---

### Post by urukrama on 2010-03-03
> **Post Monkeh said:**
> all of the threads i found described replacing the right click menu entirely

Not all the one I linked to do. Some discuss how you can add options to the menu with nautilus-scripts. Perhaps that is what you are looking for?

---

### Post by hariks0 on 2010-03-23
If you want the main menu at the mouse cursor, remove the main menu/menu bar applet from the panel and press Alt+F1. If you bind a mouse click action [say, Ctrl+Right Click as I have done] the same could be done any where on the desktop. See the attachment.

Follow the link at my signature if you want to know how.:popcorn:

---

### Post by Clmmteverest on 2010-10-14
If you are still interested in using nautilus-actions the solution is to define a new scheme in the Advanced Conditions tab which has the name "x-nautilus-desktop". Select only the one you just created. I have both selection and location checked under the Actions tab, and the folder is set to "/". 

I set up a background switcher using that method and it works perfectly.

---

### Post by malspa on 2011-05-25
I got this to work in Lucid, using nautilus-actions. I was able to add an entry to the right-click menu on the desktop for an application. Still playing around with this since I don't know exactly what I'm doing, after installing nautilus-actions:

- Added a new action, gave it a name, checked the boxes for selection context menu and location context menu.

- Entered the path for the command on the Command tab.

- On the Advanced conditions tab, I added the scheme "x-nautilus-desktop." I think you have to make sure that's the only scheme checked.

- Then I logged out of GNOME and back in.

That's cool, but what I'd like to do is add an entry for the main menu, or for a submenu. Is that possible?

---

### Post by malspa on 2011-05-25
Well, in Lucid I added gnome-main-menu, and I added that in the Nautilus Actions Configuration Tool using the command /usr/lib/gnome-main-menu/application-browser. So that brings up the Application Browser. Closest I've been able to get to being able to bring up the main menu by right-clicking on the desktop.

My desktop's right-click menu looks like this at the moment (see attached thumbnail).

---

