---
title: "Can I enlarge text size in Applications Menu?"
date: 2009-03-02
forum: Desktop Environments
---

### Post by Bearly Able on 2009-03-02
I suspect the answer to this is "no", but I'll ask anyway.  Is there a way to enlarge the text size - or even just the line height - in the Xubuntu Applications Menu?

An elderly friend with arthritis is finding it hard to control fine movements with the mouse to navigate the menu (she's also new to computers and to using a mouse at all).  If I could enlarge the target area for her, it would make a big difference, but she doesn't need text enlarged generally, as her eyesight is better than mine.

Can anyone help, or suggest other ways to overcome her problem?

Thanks.

Lesley

---

### Post by appier on 2009-03-02
You should have some control over the font size using Applications --> Settings --> Settings Manager --> User Interface.  The default font will be to the right.  Having said that, sometimes when I have applied those changes, they do not all apply correctly until I log out of the desktop and log back in.

The XFCE desktop is quite customizable so if this does not do the trick, probably someone can tell you how to edit a configuration file and make it do what you would like.

Regards,

Mark

---

### Post by Bearly Able on 2009-03-03
Thanks, Mark.  I'd had a look around, but couldn't see anything that would let me change just the menu text size.  I'll go back and have another try.

---

### Post by Bearly Able on 2009-03-08
Couldn't get to play with the system until today, as it's not my computer.  I've had another look around, but can still only find how to change the font size for the system as a whole (desktop, panels, settings manager, etc), which isn't what I need or want.

Anybody have any other suggestions that might help?

---

### Post by morgengenuss on 2009-03-08
well, theoretically there should be a way to achieve that by modifying the gtk-theme's gtkrc. but tbh i'm not that kind of a themer to actually know how it could be done. it's just a thought/hint...

---

### Post by Bearly Able on 2009-03-10
Well, I'm reassured someone else feels, as I do, that it should be possible.  Unfortunately, I don't have any idea how to do this myself, so can anyone help, please?

---

### Post by Bearly Able on 2009-03-11
Is there anyone out there who can help?  I'm sure my friend isn't the only Xubuntu user with arthritis or other problems who would welcome improved accessibility.

---

### Post by appier on 2009-03-22
It does look like one can set just the panel font and the menu fonts.  I haven't actually had a chance to try this--so attempt at your own risk.  Please refer to the following link:

 [http://ubuntuforums.org/archive/index.php/t-275090.html](http://ubuntuforums.org/archive/index.php/t-275090.html)

There is also a link embedded in that page as well with more detail on what to do with the xorg.conf file.

---

### Post by Bearly Able on 2009-03-23
Thanks for that, appier - I was beginning to lose hope.  I'm not sure when I'll get a chance to play about with it - it's not my machine - but I'll post back and let you know how I get on.

---

### Post by rolandrock on 2009-03-23
Hi Lesley,

To clarify...

Q. Can I modify the font size of panel-menu-item-labels (e.g. System->Preferences->Appearance) without affecting fonts on other menu-labels (e.g. Nautilus File menu).
A. No (not without some SERIOUS re-engineering of your gnome installation - as far as I know)

Q. Can I modify the panel-menu-items container so that it displays larger buttons without affecting other menus (I think your original query requested this).
A. Yes (I think!).

Gtk widgets' properties are inherited through a heirarchy and are then modified by the display manager.  While I don't pretend to understand this process, I have had some success hacking it.  Note, this method is not best practice.  Unfortunately I don't know what best practice is in this case (I am willing to learn if someone would like to advise).  Anyhoo, let's get hacking.

First, you need to find out which 'controls' theme is being used.  You should be able find this by going to System->Preferences->Appearence, click on 'customise' and make a note of the selected 'controls' theme (we'll call it <MY_THEME>).

If this theme is a standard one (installed in /usr/share/themes) then you need to be very careful.  As root, you can modify the file /usr/share/themes/<MY_THEME>/gtk-2.0/gtkrc but make sure you back it up somewhere safe and be aware that your modification will be overwritten by theme updates.

Hopefully, the theme being used will be a user theme and the relevant gtkrc file will be:
~/.themes/<MY_THEME>/gtk-2.0/gtkrc

Whichever gtkrc file you edit, you need to see if there exists a line that defines a value called "gtk-icon-sizes".  This value will probably not exist in the file.  That is ok.  If you need to add the line, add it near the top (by convention, under the initial #comments).  You must assign a string to "gtk-icon-sizes" that incorporates your modifications.  Here is the value in my customised gtkrc file that I modified to make the panel menu items _smaller_ rather than larger (note this is all on one line):

> gtk-icon-sizes = "panel-menu=16,16:panel=16,16:gtk-button=16,16:gtk-large-toolbar=16,16:gtk-small-toolbar=16,16"

For your purposes, start your experiments with something like:

> gtk-icon-sizes = "panel-menu=32,32:panel=32,32"

Always keep backups of your gtkrc files so you can revert if things go wrong.  Also, keep a copy of your successfully modified file so you can reapply your changes if the theme is updated and your changes overridden.

Remember that each time you modify your gtkrc file, you must restart X to force the changes to be recognised.  Either re-boot computer or bounce X using <CTRL><ALT><BCKSPC>.

The numbers 32,32 identify the icon size as 32 by 32 pixels.  Typical values include 16,16 22,22 24,24 32,32 48,48.

If you detect no changes after making radical updates to the gtkrc file then either the values are being overridden (in gtk heirarchy or by display manager) or you are editing the wrong gtkrc.  In either case, you will have to start experimenting.

Always backup important data as playing with these settings can (in theory) render your system pretty much unusable requiring a reinstall.

I know that after a lot of messing around, I did manage to shrink the menu items to an aesthetically pleasing size.  However, it is quite an assumption on my part that reversing the process will result in larger panel menu items.  But that's me.  I am very assumptive.

I hope this helps.  Good luck.

Kind Regards
Paul

---

