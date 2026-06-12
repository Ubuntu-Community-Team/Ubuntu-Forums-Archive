---
title: "Sound &amp; Video menu Renamed to Multimedia - How do I Change Menu Names back??"
date: 2009-04-01
forum: General Help
---

### Post by OzzyFrank on 2009-04-01
Hi. When I upgraded to Intrepid, **[COLOR="Indigo"]Sound & Video[/COLOR]** in the **Applications** menu got renamed to **[COLOR="#4b0082"]Multimedia[/COLOR]**, and **[COLOR="Blue"]Accessories[/COLOR]** got renamed to [COLOR="#0000ff"]**Utilities**[/COLOR]. Now, I suspect that this has something to do with me having KDE as well as Gnome, but I have had a mixed system since Edgy Eft 6.10, and this is the first time this has happened. Also, I have that thing someone developed to put all KDE/Kubuntu launchers into a **KDE** menu while in Gnome, and that is still fine. And no, the **Multimedia** and **Utilities** menus in the **KDE** sub-menu are still there with only KDE launchers, and those renamed menus only contain Gnome apps, not a mix of both.

So how do I go about renaming menu items? Tried to do it via editing the menu the normal way, but there is no option to rename items. Had a quick look in Gconf, but couldn't find the answer. I assume the answer is actually quite simple, but just need someone to point me to it. Thanks in advance. OzzyFrank

---

### Post by drs305 on 2009-04-01
In Jaunty, which is what I am on at the moment, they are still called Accessories and Sound & Video, so hold out hope.

Seriously, you can open the main menu for editing with "alacarte" in terminal. Click on Applications in the left pane, highlight the one you want to change on the right and select Properties, and name it anything you want.

---

### Post by OzzyFrank on 2009-04-01
Hi. I think Alacarte is what opens when you right-click the Applications menu and choose Edit. Yes, I was hoping the Properties button would do the trick, but while it appears active, it does nothing at all. This is true of the default menus and any I have created. I know I can basically recreate the 2 menus as they were named and drag all the launchers into them, but besides being a bit of a hassle, it won't give me any insight into now the menus work (and where one can rename entries).

An interesting note is when I helped a friend upgrade, this happened to him as well (since he has KDE and Gnome too) but after a reboot they were back to what they were originally called!

---

### Post by drs305 on 2009-04-01
Well, in that in Jaunty they retain the names you want and that I can edit them in the way I described, hopefully your system will return to normal soon. What you are experiencing is not normal nor an upgrade feature. You are correct that 'alacarte' gets you to the same editing method you tried.

---

### Post by OzzyFrank on 2009-04-04
So does anyone know which config file or whatever holds the menu entry names? There has to be something which stores all this info. I'm gathering at least one of you bright chappies knows the answer! Cheers

---

### Post by kyphi on 2009-04-04
In Gnome, System, Preferences, open Main Menu.  In the right screen, right click on Accessories and then go to Properties.  Change the name to whatever suits you.  Press Enter.  The change is reflected in the left screen as well.

---

### Post by OzzyFrank on 2009-04-04
Hi. As mentioned earlier, Alacarte (ie: "Main Menu") is not the answer, as while Properties works for entries inside the menus, it does nothing for the actual sub-menus (ie: no properties box appears).

Also, I tried editing **[COLOR="Indigo"]applications.menu[/COLOR]** in **/home/username/.config/menus** but it wasn't the answer either. When I replaced "Multimedia" with "Sound & Video", the Applications menu would not appear when pressed (actually, a blank menu about the size of a pixel or two appeared, but of course was useless). Might be a different story if I tried refreshing the menus or killing the gnome-panel (or just rebooting). I'll try that next.

---

### Post by OzzyFrank on 2009-04-04
OK, a reboot does nothing; deleting the modified **applications.menu** in /home/username/.config/menus instantly restores the Applications menu to a useable state. I have now also tried **sudo alacarte** via the terminal, and this is the output of what happens when I click on a menu like Multimedia then hit the *Properties* button:

[COLOR="DarkOliveGreen"][B]Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 325, in on_properties_button_clicked
    self.on_edit_properties_activate(None)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 373, in on_edit_properties_activate
    parser.write(open(file_path))
IOError: [Errno 2] No such file or directory: 'alacarte-made-1.directory'[/B][/COLOR]

What next?

---

### Post by kyphi on 2009-04-04
It works for me.  Let me explain it again:

In Gnome, System, Preferences, open Main Menu. The screen is divided into two parts.  In the left screen click on Applications.  In the right screen, right click on Multimedia and then go to Properties. Change the name in the drop-down box to Sounds & Video. Press Enter. The change will also appear in the left screen.

---

### Post by OzzyFrank on 2009-04-05
Hi. I fully understand the method, which I referred to as "the normal way" when I started this thread. My point is as I outlined below, that hitting the Properties button does absolutely nothing on sub-menu names, only the items within them. I understand it works for you; my point is that it doesn't work for me, and I need an alternative.

---

### Post by kyphi on 2009-04-05
My installation of Intrepid does not show any abnormal entries in the menus and the "conventional" way to change any names works very well.

As you said, it is most likely linked to having both Gnome and KDE running together as well as the "fixes" to separate the menu items.

I do not have an answer for you but you may like to look in /etc/xdg/menus.

---

### Post by OzzyFrank on 2009-06-22
Any ideas on this situation? There simply has to be some file or something that stores this info (unless it's magic?!). There must be someone who knows this, and also others who use both Gnome and KDE who have encountered this (if this isn't happening to you, I'm really happy for you, but please don't post that info as it is irrelevent).

---

