---
title: "editing Gnome main menu"
date: 2008-08-22
forum: Desktop Environments
---

### Post by Riffer on 2008-08-22
I would like to remove "Places" from the main menu.  How would I go about and do that?

---

### Post by swisscow on 2008-08-22
You can change the menu simply by right clicking on a blank part of the panel, choose add to panel and select main menu

This will get rid of all 3 "words" leaving you with just a button, in which the menus are organized.

I know this isn't quite what you asked for, but I don't know how to do that and this is pretty close.

Hope it helps

---

### Post by prshah on 2008-08-22
> **Riffer said:**
> I would like to remove "Places" from the main menu.  How would I go about and do that?

The closest I can suggest is to remove the menus entirely, then use a third party menu such as AWN's menu (it also has Cairo and Cairo classic menus).

You can even right click and add the "Main Menu" panel applet, but then "Places" is just shifted off the top panel and into the "Main menu" panel applet.

---

### Post by tuxxy on 2008-08-22
I love my places menu, are you crazy! :lolflag:

Yes as pointed out you can remove them all and have one menu but not sure about remoiving just the places menu.

---

### Post by bobus007 on 2008-08-22
> **swisscow said:**
> You can change the menu simply by right clicking on a blank part of the panel, choose add to panel and select main menu

This will get rid of all 3 "words" leaving you with just a button, in which the menus are organized.

I know this isn't quite what you asked for, but I don't know how to do that and this is pretty close.

Hope it helps

Been trying to do this for weeks. 

Thanks for the info

---

### Post by swisscow on 2008-08-22
> **bobus007 said:**
> Been trying to do this for weeks. 

Thanks for the info

Cool!

---

### Post by Riffer on 2008-08-22
Sorry for not being very clear.

I'm building a minimal version of Ubuntu for classroom use, and it needs to be locked down as much as possible.  I could just remove the menu and just have icons on the desktop, but if possible I would like to also have a menu.

I can edit Applications and System using the Main Menu editor, but it doesn't do anything for Places.  And as I'm trying to keep this version as light  weight as possible, I rather not install a third party program.

I'm wondering if I can/need to edit some config file or something.  Or is there some other way to remove Places from the main menu?

---

### Post by smu.23 on 2008-08-22
> **Riffer said:**
> Sorry for not being very clear.
I'm wondering if I can/need to edit some config file or something.  Or is there some other way to remove Places from the main menu?

Hello,

Maybe the following approach is also sufficient for you:
Open the gconf editor (you can install it with synaptic). Navigate to the key **/apps/panel/objects/**

Under that key you should see keys named **object_$N** (where $N is a number). Browse through these elements and look for one which has **object_type *menu_object***. This entry refers to the main menu (not the menu bar!). It is present when you use it in your panel. You can change the **menu_path** key to ***applications:/***. This way the Documents part of the menu will be hidden. Make sure you also select the **use_menu_path** key. You can also change the icon of the menu here.

I'm not sure if this _[link]("http://wiki.ubuntuusers.de/GNOME_Men%C3%BC")_ might help you since it is in german. At least the commands are similar.

hth

stefan

---

### Post by Ms_Angel_D on 2008-08-22
You may want to try Ubuntu System Panel it's a very customizable Menu replacement. Whenever I install Ubuntu USP is one of the first things I install, you can make it as advanced or as minimal as you like.

Check [here]("http://code.google.com/p/ubuntu-system-panel/w/list") and [here]("http://ubuntuforums.org/forumdisplay.php?f=156").

---

### Post by Riffer on 2008-08-22
> **MetalHellsAngel said:**
> You may want to try Ubuntu System Panel it's a very customizable Menu replacement. Whenever I install Ubuntu USP is one of the first things I install, you can make it as advanced or as minimal as you like.

Check [here]("http://code.google.com/p/ubuntu-system-panel/w/list") and [here]("http://ubuntuforums.org/forumdisplay.php?f=156").

I am considering it, but I can't find a .deb for it.

---

### Post by Ms_Angel_D on 2008-08-23
Check the first link I gave you and checkout the installation instructions under the wiki. It's a simple step by step walk through ;)

---

### Post by Adoring on 2008-08-23
Thank you

[COLOR="White"]http://www.al-mohd.com/[/COLOR]
[COLOR="White"]http://www.al-mohd.com/forum/[/COLOR]

---

### Post by 4leite on 2008-08-31
@Riffer - Any luck?


I need to do a similar task. I'm creating a menu for a kiosk type solution. Not particularly keen on writing a panel applet. I played with Gimmie and a few other alternatives, but they aren't what I'm after.

I really just want a Menu with the ubuntu icon that says Start (I know, but it's a target market thing) and has 6-10 applications listed.

I'll post again here if I come across anything...

---

