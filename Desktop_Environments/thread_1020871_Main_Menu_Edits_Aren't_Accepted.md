---
title: "Main Menu Edits Aren't Accepted"
date: 2008-12-24
forum: Desktop Environments
---

### Post by infidel on 2008-12-24
Hello, all. Apologies beforehand if this has been covered elsewhere. It seems to be getting progressively harder to get relevant search results.

Under Intrepid, none of my new menu items are "taking". I go through the whole New Item process (via alacarte or System > Preferences > Main Menu or <right-click>Applications > Edit Menus/etc.) and end up with no usable results. New items appear in ~/.local/share/applications, but never in the menu editor nor the menus themselves. It's as though I'm clicking 'Cancel' instead of 'Ok'. 

I don't know how much more detailed I can be about it, though this is an in-place upgrade from Hardy if that matters. Never had any menu-editing problems under Hardy, so I'm really at a loss as to what the difficulty is. As far as I know, nothing I've installed has made any changes to the stock gnome-panel mechanism.

Any guidance would be greatly appreciated. Many thanks in advance.

**EDIT:** On a whim, I just enabled display of the 'Debian' menu and discovered that my new menu items are appearing there. The particular items that prompted this post were *supposed* to go in Applications > Games, not Applications > Debian > Games. I'm still at a loss as to why they're being sent to the wrong place, but at least I now know that they aren't being completely ignored. Still a problem, though.

---

### Post by ajaysutton on 2008-12-28
Hello,

I too am having a similar issue.  (Perhaps not really similar, but I've been searching for two days and haven't come across anything similar...)

On a new install of 8.10 (and also 8.4) when I go to launch alacart via System > Preferences > Main Menu, nothing happens at all.

I am able to go to a terminal and 'sudo alacarte' which makes the application open, but I when I try to move something it doesn't appear to go.

I want to say I've seen this once before some time ago, and I thought there was a fairly quick fix.  For some reason it sticks in my my that I had to chown something, but I can't for the life of me remember what it was.

Any help will be especially appreciated.

---

### Post by ajaysutton on 2008-12-28
Say, I just found another post by jellybaby here:

[http://ubuntuforums.org/showthread.php?p=6449107#post6449107](http://ubuntuforums.org/showthread.php?p=6449107#post6449107)

This is what I think I did before.  It seems to work for me now anyway.

I had to change ownership (chown) on the .config/menus folder and also the .local folder in my home directory.  I wish I knew why, but here are the commands he used:

```
sudo chown -R user .config/menu
sudo chown -R user .local
```

Hope this helps.

---

### Post by infidel on 2008-12-28
> **ajaysutton said:**
> I had to change ownership (chown) on the .config/menus folder and also the .local folder in my home directory.  I wish I knew why, but here are the commands he used:

```
sudo chown -R user .config/menu
sudo chown -R user .local
```

Hope this helps.
Thanks, ajay, but it didn't work for me.

However, I did discover that I can get things to show up where I want them by editing the Desktop Entries in ~/.local/share/applications by hand and specifying a Category. A little cumbersome, but better than nothing.

Thanks again!

---

### Post by Timpotten on 2009-01-30
Some clarification: menu_s_ not menu
for user 'tim' 
[email]tim@tim-desktop:~/.config[/email]$ sudo chown -R tim /home/tim/.config/menus
[email]tim@tim-desktop:~/.config[/email]$ sudo chown -R tim /home/tim/.local

I usually use the plain vanilla Gnome desktop, but prefer KDE Konsole (which runs in either desktop)  because it supports 'cut and paste' which I find is really helpful in avoiding errors (linux is case sensitive and I am a bit dyslexic I often get 'not found')  

alacarte (the menu editor) works for other users but on my usual account after above it still produces this error

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

Just in case, I also changed permission as well as ownership and re-booted but still the same. 
This page has a helpful 'tick in the box' guide to owner/group/other codes ([http://webtools.live2support.com/linux/chmod.php](http://webtools.live2support.com/linux/chmod.php))
chmod 700 /home/tim/.config/menus
chmod 700 /home/tim/.local
Any help?

---

