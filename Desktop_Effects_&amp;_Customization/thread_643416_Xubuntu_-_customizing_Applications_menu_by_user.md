---
title: "Xubuntu - customizing Applications menu by user"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by darkbladepdx on 2007-12-17
Hi, folks-

I have seen threads about this general topic elsewhere, so if this has been asked and answered, I apologize, just point me at the right thread.

I´m running Gutsy and xfce4, all kept updated. I´m trying to customize the Applications Menu by individual users, i.e. have user A have tetris in his games sub-menu but not user B, and have user B have AbiWord but not user C or D, and so on.

The information I have gotten  from other threads/forums say that I need to go to /usr/share/applications and grab a copy of the <n>.desktop file for the given application that I wish to suppress in for a user,  move that copy to /home/<username>/.local/share/applications, edit it and add the line NoDisplay=true somewhere into the file, following which the given application entry in the menu will be suppressed for the given user. 

I tried this to no avail. I also got online in #xubuntu a night or two ago with a nice person nicked soldats who went through it with me, testing on his own system. We both got very odd results, with him getting menu items that had previously been universally suppressed (e.g., NoDisplay in /usr/share/applications/<n>.desktop no longer working after having worked for a significant period).

Folks, I´m at a loss. If I´m missing something blindingly obvious, as I said before, I apologize, point me at the thread and I will skulk there abjectly. :)

Thanks very much in advance for any assistance you can give!

Nate Lee  (new to ubuntu, but liking it quite a bit)

---

### Post by mali2297 on 2007-12-22
Why don't you use the menu editor?

Create a new menu, remove the Systems entry and add your own entries. If you open Xfce's application finder side by side with the menu editor, you can drag and drop the applications that you want to add. When finished, save your new menu.

The menu is saved in an xml file which is located in the directory /home/yourloginname/.config/xfce4/desktop/. Copy that xml file to /home/userA/.config/xfce4/desktop/, /home/userB/.config/xfce4/desktop/ or whatever. Make certain that the file's owner is correctly set.

---

### Post by darkbladepdx on 2007-12-23
> **mali2297 said:**
> Why don't you use the menu editor?

Create a new menu, remove the Systems entry and add your own entries. If you open Xfce's application finder side by side with the menu editor, you can drag and drop the applications that you want to add. When finished, save your new menu.

The menu is saved in an xml file which is located in the directory /home/yourloginname/.config/xfce4/desktop/. Copy that xml file to /home/userA/.config/xfce4/desktop/, /home/userB/.config/xfce4/desktop/ or whatever. Make certain that the file's owner is correctly set.

Hmmm. This seems a bit less than user-friendly.

So, is this to indicate that the earlier info (tailoring by editing local copies of the app's <n>.desktop file is erroneous or superseded? If so, I'd hope that there's  a better way than either editing xml in the raw or digging all over the system for apps and making sure that launcher syntaxes are correct and so on, because if Ubuntu wants to be new-LINUX-user-friendly, it'll need to take into account that users with families will want to easily tailor age(or even individual)-appropriate environments.

Not to be too snarky here, but I'm trying to use a UNIX/LINUX-style solution (tailor the existing master's behavior for individual circumstances) rather than a MicroBloat-style solution (build an entirely _new_ three-handed paintbrush to make blue marks instead of red ones).

Thank you, mali, but to paraphrase the inimmitable Ben Stein - "Anyone else?.... Anyone?.... Anyone?"

---

### Post by mali2297 on 2007-12-23
> **darkbladepdx said:**
> 
So, is this to indicate that the earlier info (tailoring by editing local copies of the app's <n>.desktop file is erroneous or superseded?

The drawback of my method is that the menus will not be automatically updated when new applications are installed, otherwise I would say it is preferable.

> 
 If so, I'd hope that there's  a better way than either editing xml in the raw or digging all over the system for apps and making sure that launcher syntaxes are correct and so on, because if Ubuntu wants to be new-LINUX-user-friendly, it'll need to take into account that users with families will want to easily tailor age(or even individual)-appropriate environments.

As I said, you can drag and drop applications from the app finder to the menu editor. There is no need to manually edit the xml file. If you don't want to copy the files, you can login as the different users and repeat the procedure for each.

---

### Post by mali2297 on 2007-12-23
An alternative to adding entries from the app finder is to start with the automatically generated menu and remove entries that you do not want.

From [Xfce's wiki]("http://wiki.xfce.org/faq"):
> 
How to edit the auto generated menu with the menu editor?

cp ~/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml
cd ~/.config/xfce4/desktop/
cat menu.xml > menu3.xml
cat menu2.xml >> menu3.xml
mv menu.xml menu.orig.xml
mv menu3.xml menu.xml

Now, you already have a menu with all the categories in the main tree with some duplicates, but you must first edit menu.xml with your favorite editor and remove the 4 following lines in the middle of the file, otherwise the menu editor will complain about a wrong format:

</xfdesktop-menu>
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE xfdesktop-menu>

<xfdesktop-menu>

That's all. Now you can run the menu editor, remove the few duplicates and edit all as you like.

Settings > Desktop > Menu > Menu Editor

Notes: by removing the “system” line, you will remove all the duplicates menu entries from the auto generated file. So, if it is changed in this auto generated file, they don't appear anymore, but you will get rid of most of the duplicates.

To restore the original menu, just do in a terminal:

mv menu.xml menu3.xml; mv menu.orig.xml menu.xml


---

### Post by darkbladepdx on 2007-12-23
Again, I´m tryig to avoid lots of xml editing and dup files that have to kept track of. Is the <n>.desktop file method not correct, superseded or otherwise not right? What happened there? If that was a way that worked, and it does not now, is it a bug now, was it a bug then or what? If it _has_ been superseded, is it by anything other than heaps of duplicate, maintenence-requiring xml?

---

### Post by dizee on 2007-12-24
What you could do is move the desktop file from /usr/share/applications to /home/user/.local/share/applications instead of copying it. This way you would have the application in your menu but no other user would, unless you manually added it to their home folder in the same way. It's a bit cumbersome but it should work.

---

### Post by darkbladepdx on 2007-12-24
Thanks. But - I´m trying really hard to avoid ¨cumbersome, but it should work¨, whether that´s a separate xml menu that requires continual maintenance or duplicating lots of entries to _add_ things to an empty menu. As I said before, way back in the beginning, I´ve seen mention of the method of adding <N>.desktop files with ¨NoDisplay=true¨ added to them to a given users directory to trim said file from the master menu which is (largely) automatically maintained. Again, is this method A) an error (i.e. it was never the case), B) superseded by something new, or C) gone because of a bug (If this, is it coming back soon?)? I ask this particularly because I don´t seem to be the only person who thinks that this method exist(s/ed) and work(s/ed), and if it did/does, I´d like to use it, since it seems that A) this is the method designed into ubuntu, and B) it is an efficient method if it works.

Any info on this question?  THanks again...

---

### Post by mali2297 on 2007-12-25
Can you say whether the problem is that the local .desktop files are not read or that the *NoDisplay=true* option does not work?

To find out, you could copy one of the .desktop files to your local folder ~/.local/share/applications. Edit the file so that *Name=* is set to something else. Then restart X. Does your custom entry name appear in the menu?

If it does appear, continue with adding the line
```

NoDisplay=true

```
to the .desktop file. Restart X. Has your custom entry vanished?

---

### Post by darkbladepdx on 2007-12-26
OK, thanks. I will do and let you know!

---

### Post by darkbladepdx on 2007-12-29
OK-

I already had a test file in place (/home/<user>/.local/share/applications/tetravex.desktop, owner <user>, permissions rw-r-r-). It had NoDisplay=true. I explicitly set NoDisplay=false and set Name=ThisIsATest. No change in <users>´s Applications menu, but now the .desktop file shows in thunar as ThisIsATest. It was always visible as Tetravex, so visibility in Thunar did not change, but the display name has changed.

To force a re-read of menu-building files, I restarted the machine (which I presume restarted X).

So - No custom entry showed up in the menu. The filename changed as displayed in Thunar.

It looks like we´re back at the question - bug (to be reported?), bad original info (which seems unlikely, given the mechanisms that _seem_ to be in place), or superseded method (so what&#347; the new method?)

Thanks again,

Nate Lee

---

### Post by mali2297 on 2007-12-29
See what happens if you rename the file from tetravex.desktop to (say) test.desktop. It might be that you cannot have a system wide .desktop file with the same name.

---

### Post by darkbladepdx on 2007-12-30
Hmm- 

well, apparently Thunar is a somewhat less than trustworthy application. The  _actual_ filename (according to ¨sudo ls <directory>¨) is gnotravex.desktop, which Thunar has _never_ displayed. This is _not_ _good_. This borders on a Windoze level of deceit. Hey! Ubuntu coders! TELL ME THE TRUE STATE OF MY FILESYSTEM AT ALL TIMES NO MATTER WHAT METHOD I USE TO VIEW IT! Thunar should show that same thing an ls does. 

Well, apparently the _actual_ filename is irrelevant, and apparently the system doesn´t give a rap about what it&#347; supposed to do. So, I´m still stuck back at square one. How do I get the attention of an appropriate Ubuntu system coder on this one? My initial question still stands, workarounds are not going to cut it as far as I´m concerned, and this is less-than-acceptable for a release number like 7. For 2, yes, but 7? No. Mali, thanks for your attempts at help, here, but how do I get this to the system folks? I now have two major complaints here, and I really want definitive, authoritative answers. Those answers may very well determine whether I stick with Ubuntu at all. :(

thanks in advance...

---

### Post by mali2297 on 2007-12-31
> **darkbladepdx said:**
> How do I get the attention of an appropriate Ubuntu system coder on this one? 

Since your problem concerns XFCE, you should probably address the XFCE developers:
[https://launchpad.net/xfce](https://launchpad.net/xfce)

If you simply don't like XFCE, you might want to try Gnome (regular Ubuntu) or KDE (Kubuntu).

---

### Post by darkbladepdx on 2007-12-31
OK, will do. As to Ububntu or Kubuntu, I´m running on a p-2 266Mhz and 128 MB RAM here. From what I can see, those other environments are too big for this little machine. But I will point the XFCE folks at this and see if I can get a response. If not, are there any other front ends you´d recommend for an old system like this?

---

