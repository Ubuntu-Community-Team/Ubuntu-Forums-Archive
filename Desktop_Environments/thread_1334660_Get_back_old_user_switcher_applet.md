---
title: "Get back old user switcher applet?"
date: 2009-11-22
forum: Desktop Environments
---

### Post by josephellengar on 2009-11-22
I don't like the new one.  I liked the menu that I could drop down and select restart/shutdown/log out without moving my mouse very far, but the new one can only log out and change user.  Can I get back the old one?  I don't like the shut down button, where there is the pop up in the middle of the screen.  Any suggestions?

---

### Post by randysilverwolf on 2009-11-28
yes i very much agree, i hate this user switcher, this was the same one in fedora that i hated so much, please free us and give ur a patch or something so we can get back the user switcher the old gnome/ubuntu jaunty/intripid

---

### Post by Doughy on 2009-11-29
I recently registered a blueprint about this issue:

[https://blueprints.launchpad.net/ubuntu/+spec/fast-user-switcher](https://blueprints.launchpad.net/ubuntu/+spec/fast-user-switcher)

---

### Post by josephellengar on 2009-11-29
> **Doughy said:**
> I recently registered a blueprint about this issue:

[https://blueprints.launchpad.net/ubuntu/+spec/fast-user-switcher](https://blueprints.launchpad.net/ubuntu/+spec/fast-user-switcher)

Thank you.  Although personally, I preferred the fast-user-switcher applet not for the fast user switching but more because it gave the dropdown menu that had  restart, log out, and shutdown on it, so I didn't have to move my mouse to the middle of the screen.  That was much better.

---

### Post by mazz0 on 2009-11-29
Sorry, I know this sounds obvious, but doesn't indicator-applet-session do exactly what you want?  Unless you do actually need the quick user switch ability mentioned above, that is...

---

### Post by josephellengar on 2009-11-29
> **mazz0 said:**
> Sorry, I know this sounds obvious, but doesn't indicator-applet-session do exactly what you want?  Unless you do actually need the quick user switch ability mentioned above, that is...
Um, yes.  It does.  Thanks!  That applet should be installed by default.  EDIT: except that this one doesn't give you the option to turn off the "shut down in x seconds" dialog, which is also extremely annoying.

---

### Post by teseglet on 2009-11-29
You can shut off the 60 second shutdown delay in the gconf-editor under apps/indicator applet session and check the box.  What bothers me is I can't change or remove my username next to the "quit" button in the panel.

---

### Post by josephellengar on 2009-11-29
> **teseglet said:**
> You can shut off the 60 second shutdown delay in the gconf-editor under apps/indicator applet session and check the box.  What bothers me is I can't change or remove my username next to the "quit" button in the panel.

Ugh- I hate how gnome is transitioning to the gconf-editor.  The registry is one of the things that everybody hates about Windows.  This should all be in a nice simple .txt file.

---

