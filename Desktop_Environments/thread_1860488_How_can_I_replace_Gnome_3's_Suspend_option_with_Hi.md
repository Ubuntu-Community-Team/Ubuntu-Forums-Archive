---
title: "How can I replace Gnome 3's Suspend option with Hibernate?"
date: 2011-10-14
forum: Desktop Environments
---

### Post by BlacqWolf on 2011-10-14
In the power menu, there is the suspend option. However, just like the majority of computers, my computer isn't the best friend with suspending in Linux. However, I can hibernate just fine.

Is there a way to change the Suspend option in the power menu with Hibernate?

If I can't, can I at least disable sleep or remove it from the power menu so I don't accidentally hit it?

---

### Post by Kodeine on 2011-10-15
I too would like the option to Hibernate. Also a shut down option would be nice. You can actually get the shut down option bye holding 'alt' then clicking the top right hand corner menu. Instead of seeing standby you'll see shutdown (how would you have known to do that without having to search on the Internet?). 

There's no hibernation solution for Ubuntu although there does appear to be one for Fedora [http://mygeekopinions.blogspot.com/2011/06/how-to-add-shutdownhibernate-menus-in.html](http://mygeekopinions.blogspot.com/2011/06/how-to-add-shutdownhibernate-menus-in.html) I can't find such package in Synaptic though in Ubuntu 11.10. Anyone know how to do this?

---

### Post by Spr0k3t on 2011-10-15
Go have a look here, there's a few extensions that will show not only hibernate, but also shutdown.

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

---

### Post by Kodeine on 2011-10-15
> **Spr0k3t said:**
> Go have a look here, there's a few extensions that will show not only hibernate, but also shutdown.

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

I have to enable the 'user themes extension' but that option in the picture isn't there on my own computer? Only the 'install extension' selection is?

---

### Post by BlacqWolf on 2011-10-15
Thanks for the replies so far. It would be nice to replace that Suspend option with Hibernate, or at least to disable suspend and remove it from the menu. Now, I log out and hit the power button from there because I find myself occasionally hitting the Suspend option in attempt to shut down, either because I forget to hold down Alt or because I hit the wrong key. 

Considering most computers have problems with the suspend option in Linux (I wonder... after all this time, why haven't they fixed that?), why did the people at Gnome put it there in place of the Power Off option, which needs the Alt key to be held to reveal it? Yes, that's kinda nice if the Suspend option works on the majority of PCs, but it doesn't. There's only one PC ever that I've seen work with suspending in Linux.

These are my only complains about Gnome and Linux.

---

### Post by crdlb on 2011-10-15
I think "most" is an overstatement, but the problem will never be fixed if no one forces the issue (that is GNOME's logic). 

It would be pretty easy to edit the alternative status menu extension to remove the suspend entry (it's written in JS).

Change /usr/share/gnome-shell/extensions/alternative-.../extension.js ```

function updateSuspend(object, pspec, item) {
    item.actor.visible = object.get_can_suspend();
}
```
to ```
function updateSuspend(object, pspec, item) {
    item.actor.visible = false;
}
```

Or copy the whole alternative-... directory to ~/.local/share/gnome-shell/extensions/, then make the edit.

There may be a configuration key which would make 'get_can_suspend()' return false, but I don't know.

---

