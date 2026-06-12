---
title: "menu editor does not work"
date: 2008-10-06
forum: Desktop Environments
---

### Post by elitenoobboy on 2008-10-06
Has anyone else noticed that the editor used to edit the menus when you right click on the menu in the upper left and then select edit menus is completely broken and worthless. No matter what I do, it will not delete any entries from the menu at all. It will beep at me if I select something and then hit delete on my keyboard, and it will do absolutely nothing if I right click on a menu item and then select delete. Why is it doing this?

---

### Post by elitenoobboy on 2008-10-16
/b

---

### Post by denham2010 on 2008-10-16
Hi,

While I don't use gnome anymore, I seem to remember this has been a persistent problem, and I think it may have something to do with permissions.

Try either of the following approaches to see if you can edit the menus:

Press ALT+F2
and enter:
```
gksudo alacarte
```

or open a terminal and enter:
```
sudo alacarte
```

enter your root password and the menu editor will open up.

Cheers.

---

### Post by wmichaelb on 2008-10-17
I tried this to add an Applications category. If I don't use the sudo command, Alacarte lets me enter a new category, and I click on the "show" box to add it to the menu. But when I click on "Applications" on the Gnome menu bar, the new menu item isn't there. So I go back to Alacarte, and the box is unclicked! 

If I open Alacarte with the sudo command and my password, it won't show the added category in the list at all after I click on "new menu". If I go back to opening it without sudo, suddenly the new category is shown. But it simply won't show when I click on Applications. ????? 

Does anyone have any suggestions? How does this thing work? 
Thanks in advance.

---

### Post by elitenoobboy on 2009-01-24
So no one knows how to fix this POS app so that it will actually delete items? Launching it with sudo makes it show the menu entries for root, not the user, and at the same time it still wouldn't delete something when I tried.

---

### Post by Timpotten on 2009-01-30
I can use alacarte in another user account, and as superuser, but when I tried using alacarte as my usual 'tim' user, produces failure results below. I am not very Linux savvy (although I started computing a couple of decades ago with C/PM). Any help?

alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 56, in __loadMenus
    self.settings.dom = xml.dom.minidom.parse(self.settings.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 207, in parseFile
    parser.Parse(buffer, 0)
xml.parsers.expat.ExpatError: mismatched tag: line 15, column 4
tim@tim-desktop:~$

---

### Post by dylanrabbit on 2011-02-25
Ok, the Application menu settings are in:

~/.config/menus/applications.menu

Turns out the menu directory was owned by root and not readable to the user.  This looks a bit like security, though this could be from any of the distros I've used in the last 8 or so years.

Changing the owner of the tree to myself fixed alacarte and the right-click Edit Menus options, etc.  If *user* is your username and *group* is your primary group, then...

```
sudo chown -R *user:group* ~/.config/menus
```

Suggest that if it was worked when owned by root, then one should change it back when finished...

-DylanRabbit

---

### Post by ankspo71 on 2011-02-25
Hi,
I had that problem (sort of) a while back when I was testing Ubuntu Lucid aplha1. Reinstalling alacart didn't help my situation, but it just might help yours. I ended up having to download the source code for alacart and compile alacart myself. It worked great after that.

Here's the bug report I submitted:
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/499754](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/499754)

Since the download link in bug report has expired, here is a working link to Gnome's source code packages:
[http://ftp.gnome.org/pub/GNOME/desktop/](http://ftp.gnome.org/pub/GNOME/desktop/)

Try reinstalling alacart first though.
Hope this helps.

---

### Post by nestor_stura on 2011-02-28
Hi. I had the same problem and changing file owner it was solved.
I used Alt-F2, gksudo nautilus, looked for .config/menus folder and changed permissions.

Hope this helps

---

