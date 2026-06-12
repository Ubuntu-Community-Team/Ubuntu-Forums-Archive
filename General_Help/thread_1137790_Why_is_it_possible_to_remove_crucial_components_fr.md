---
title: "Why is it possible to remove crucial components from the toolbars?"
date: 2009-04-25
forum: General Help
---

### Post by chaeussinger on 2009-04-25
I'm trying to move things around, but I accidentally clicked on "remove" instead of the "lock" checkbox and the "move" button. I somehow managed to do that to the portion of the toolbar that has the menus "applications", "places", and "system".

I know how to find the terminal, but what command do I have to use to restore the toolbars to the default configuration?

Also, can someone tell me the Ubuntu equivalent to "program files" in Windows?

---

### Post by mb_webguy on 2009-04-25
Just right-click the panel, select "Add to panel", and select "Menu Bar".

What you consider to be "crucial" may be considered irrelevant to someone else.  For example, some people prefer to use the Main Menu applet (which is more like the Windows Start menu, and uses less space on the panel) rather than the Menu Bar applet.  Some people don't want to use either of these, and prefer to use launchers to access all of their software.  And the panels themselves are removable, so it you only want a top panel, or only a bottom panel, or want to use panels on the left and/or right instead, then you can do that.  Nothing in the Gnome desktop is considered "crucual", and everything can be customized.

---

### Post by chaeussinger on 2009-04-25
Well it's crucial for me :P Thanks for the tip. I'll try it once I get back into Ubuntu.

---

### Post by Dr_Willis on 2009-04-25
Right click the panel - add to panel -> select 'Menu Bar'

There is no one directory thats the 'program files' directory. Programs install the parts they use in the proper locations around the filesystem.

ie: libraries go to /lib or /usr/lib or /usr/local/lib  and thers a logic to the whole system. (and a long history)  binaries can be most anywhere, and are normally in one of the directories  listed in your PATH variable.

see output of 

# echo $PATH  

to see what all is included.


If you wanted to reset ALL of gnome to the original defaults you could delete the various .gnome*  and  perhaps the .gconf* directories and log back in, the defaults will get recreated. (this is a little extreme) 

As for the answer to your 'title' -  the components are not crucial  and they are easy to add back to the panel.  You can use gnome without the panel or any of those  components if you wanted to. :P

---

### Post by loell on 2009-04-25
i use **pessulus** lockdown editor, so the users at the office won't bother me about accdental removals of the preset icons and what not in the toolbar.

you should try it. :)

---

### Post by mb_webguy on 2009-04-25
If you want to lock the panels once you get them configured, press Alt+F2 and enter the command gconf-editor.  Now go to apps->panel->global and check the box next to locked_down.

---

