---
title: "'Shut down' dialog box"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by Perpetual on 2007-11-01
Hi all.  Posting in customization because I want to customize the Ubuntu Shutdown (Restart, Hibernate, Logout, etc.) Dialog.  I am wanting something simpler, such as what Mandriva 2008 and Fedora FC8 are using.  I tried to find an example but couldn't.  I am assuming it's a basic Gnome Shutdown Dialog?  Is there a way to change it?  Not particularly fond of it's appearance, especially if you use a different Icon Set as it changes the buttons to an even lesser attractive set.

---

### Post by Forlong on 2007-11-01
Don't know which one Mandriva and Fedora are using but here's how you can get the usual GNOME shut down dialog:

1. Run
```
gconf-editor
```
2. Enable **/apps/panel/global/upstream_session**

3. Restart the panel:
```
pkill gnome-panel
```

---

### Post by Perpetual on 2007-11-01
Thanks Forlong.  I looked in gconf-editor and did not see anything.  Guess I was looking for something more obvious :)

Edit: I will mark this solved as soon as I try it.  Can not at the moment but will ASAP.

---

### Post by Perpetual on 2007-12-15
Sorry to open an old thread but was just getting back to messing with this and could not figure it out.  This is what I would like...

[IMG]http://farm3.static.flickr.com/2162/2114471838_1601696a7a_o.png[/IMG]

Rather than the default.  I can't seem to figure out how to change it or if it's possible to change.

**edit: nevermind, you were right forlong.  I must have done something wrong before.  Thanks again.**

---

