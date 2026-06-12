---
title: "Nautilus Menu configuration.."
date: 2009-07-10
forum: Desktop Environments
---

### Post by slgilley on 2009-07-10
Some background info on me.  I'm a Unix/Linux systems admin.  Been doing this for 20 years or so.  I've been using Fedora for my desktop at work, but have gotten frustrated at how few user apps are either supported or relatively easy to install.  My officemate uses Ubuntu and really likes it, and gave me enough reasons that I decided to give it a try.

We have a bunch of machines that I regularly log in to.  Under Fedora, to get a window manager I liked, I finally settled on Enlightenment.  (It's not perfect, but my favorite, WindowMaker, didn't seem to work.)  Anyway, while I didn't like the method, at least editing menus by hand was at least reasonably easy.  Still not to the ease of WindowMaker, by any means, but okay.

So now we come to Ubuntu.  I've managed to get pretty much everything working the way I want it to work. (Can I get rid of the bar with the MS Windows like stuff?  The one that normally shows up on the bottom of the screen?  Don't need it, don't want it.)

Except for menus.

The default right-click on root background menu is completely useless to me.  I want to change that entire menu to something useful.  Okay, so I found and installed nautilus-config.  For one or two items, its fine.  I have thirty or forty.  So I went digging to try to figure out what the file(s) were that controlled that so I could edit them by hand and add what I wanted.

Sigh.  XML.  Everybody seems to love XML these days.

So, my point is that the way the XML files are set up is relatively complex, and makes it a real pain to try to hand edit the files.  Further, modifying the right click menu is also frustrating -- I have to download and use a special program to do it?  And even when I do that, I still don't see ways to completely replace the menu rather than just adding to it, and even adding to it is a pain for more than a very few entries.

Maybe I'm missing something.  Is there some way to easily add a bunch of apps into the menu?  Is there something where I can erase and recreate the menu quickly and easily, adding just what I need?

I like Ubuntu, but I wish that the backend stuff was less complex.

<rant>
Why do you need a big tree of directories with XML files to create a menu?  Really, a menu can be done with simple parsing on a single file that is easily hand editable.  I've seen it done before -- I think I've done it myself, though I don't recall when.  It's not that I don't like XML, I just don't think it's needed in this case.  Why is these layer of complexity added?  Is there a real reason, that is, a real need that can't be satisfied just as easily with a single file?  What's a menu?  A label, in this case an optional tool tip, and a command string.

Sigh.
</rant>

Sean.

---

### Post by Zimmer on 2009-07-10
> **slgilley said:**
> 

 (Can I get rid of the bar with the MS Windows like stuff?  The one that normally shows up on the bottom of the screen?  Don't need it, don't want it.)



Sean.

Right click on it and 'Delete this panel.
I use the panel at the top! Add disk Mounter to this panel, comes in very useful (install gnome-applets for this).

---

