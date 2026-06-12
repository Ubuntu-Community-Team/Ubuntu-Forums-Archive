---
title: "Right Click Menu on Desktop missing"
date: 2010-11-07
forum: Desktop Environments
---

### Post by Detonate on 2010-11-07
Using Maverick.  I installed the Unity Netbook Edition on my Desktop just to check it out.  It's cute, but it is of course not ready for the desktop yet.  So I'm back in Gnome now, my favorite Desktop.  The problem is, Unity seemed to make some changes to my system.  I now no longer have a right click menu on the desktop in Gnome.  How can I get this back?  The menu must be activated by some entry in a conf file somewhere but I can't find it.  Where is it?  

TIA.

---

### Post by Brandon Williams on 2010-11-07
I don't use Gnome any more, but I may remember enough about this to point you in the right direction. Hopefully, my incomplete response will push someone else to give you a more complete answer.

When you're running with the standard UNE interface, Nautilus is not running to manage the desktop. It's Nautilus that provides the right click menu on the desktop, icons, etc. If I recall correctly, you need to list nautilus as a required component, and you can do this with gconf-editor. After launching the program, navigate to /desktop/gnome/session/required_components. Make sure that filemanager is one of the required components and that its value is nautilus.

As I say, this might not be 100% correct, but hopefully it will at least help you search out a more thorough/complete answer.

---

### Post by Detonate on 2010-11-07
Sounds like that might be it.  As soon as I get back to that computer I will try it and post results.  Thanks.

---

### Post by Detonate on 2010-11-07
Sorry Brandon, but It already has "filemanager   nautilus"  as a key.  So that did not work.  Any other ideas short of reinstalling the Gnome Desktop?  Thanks.

---

### Post by Brandon Williams on 2010-11-08
To refresh my memory, I went back and looked at [an old bug](https://bugs.launchpad.net/ubuntu/jaunty/+source/desktop-switcher/+bug/349519) that is somewhat related. I think that the required_components settings will in fact always be there. There also used to be a required_components_list that could be accessed like so:```
gconftool-2 --get /desktop/gnome/session/required_components_list
```
For regular desktop mode, the list should be:```
[windowmanager,panel,filemanager]
```
If it doesn't look like that, then run:```
gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel","filemanager"]
```
If the current values of both required_components_list and required_components are correct, then there's something completely different going on and hopefully someone who still runs gnome will be better able to help.

---

### Post by Detonate on 2010-11-08
It already reads [windowmanager,panel,filemanager]so that's not it:(

Thanks for trying, Brandon.  Hope someone else comes in on this thread soon.  Its not really a big deal.  I can always just reinstall the gnome-desktop.  Just don't want to go through all the setup again. But maybe a reinstall will keep all my current settings.

---

