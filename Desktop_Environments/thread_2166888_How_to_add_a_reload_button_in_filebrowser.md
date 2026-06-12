---
title: "How to add a reload button in filebrowser"
date: 2013-08-11
forum: Desktop Environments
---

### Post by Azyx on 2013-08-11
If it is dark in the room, it can be hard to find F5 button, to reload nautilus. I wonder if i can get a reload button in nautilus and also if i can change the back and forward arrow the the left side WHITOUT compiling nautilus! Using 12.04LTS

/Cheers

Is this the only way????? [https://launchpad.net/nautiluspatchtogglelocationbar](https://launchpad.net/nautiluspatchtogglelocationbar)

---

### Post by Azyx on 2013-09-27
Now an upgrade removed  nautiluspatch_v3.4.2-0ubuntu8-1_amd64. This also happen when i compilde a nautilus package, to get back the navigation-arrows (As in 10.04LTS) from right to left side :(. Gonne get 'repetitive strain injuries' in my thumb :(

---

### Post by mc4man on 2013-09-27
> **Azyx said:**
> Now an upgrade removed  nautiluspatch_v3.4.2-0ubuntu8-1_amd64. This also happen when i compilde a nautilus package, to get back the navigation-arrows (As in 10.04LTS) from right to left side :(. Gonne get 'repetitive strain injuries' in my thumb :(
If you want to move the nav buttons to left that has to been done in source, specifically  in regards to the kirby33 patches in 
nautilus/src/nautilus-toolbar.c as below

```
@@ -127,7 +164,7 @@ nautilus_toolbar_constructed (GObject *o
 	item = gtk_tool_item_new ();
 	gtk_tool_item_set_expand (item, TRUE);
 	gtk_container_add (GTK_CONTAINER (item), hbox);
-	gtk_toolbar_insert (GTK_TOOLBAR (self->priv->toolbar), item, 0);
+	gtk_toolbar_insert (GTK_TOOLBAR (self->priv->toolbar), item, 3);
 	gtk_widget_show (GTK_WIDGET (item));
 
 	/* search bar */
```

The item number used (3 above) determines the number of 'icons' to the left of the location, placed in order listed in nautilus-navigation-action.h.
So 3 would put the nav. buttons to the left, the rest to the right

Is that what you had in mind?
(personally would build as a debian package set instead of the 'all-in-one' package as kirby 33 did. I could create a ppa with the kirby33 mods & nav to left in a few min or so if desired...

---

### Post by Azyx on 2013-09-27
It was an association I made in that booth 'tweaks' suddenly just disappear...The last one just after a day.

The deb-patch above give an extra tab, in Preferences for the File browser called Toolbar, there you can add other 'buttons' than back, forward and search in Nautilus. But it disappear after todays update :( Tried to reinstall, but it was dependency problem. Would bee nice if there was an ppa for this kind of patches...

It was a about a year ago, I downloaded the source-code and change it, but that also disappear after an update soon after. I think it bad that Ubuntu and Unity have so little possibility to change appearance and stuff. Soon as bad as Windows and OS-X...

---

### Post by mc4man on 2013-09-27
Ck this ppa in about 6 hrs for the kirby33 patched nautilus with the nav buttons on the left
( 6 hrs should be enough time for both i386 & amd64 packages to build, publish & let me ck. them out, don't try to upgrade before both archs are published if on an amd64 (64 bit) install 

[https://launchpad.net/~mc3man/+archive/naut-mods](https://launchpad.net/~mc3man/+archive/naut-mods)

before using get rid of any self built or kirby33 package, eg. get on the official precise version packages (if not already

Edit:7 hrs may be more likely

---

### Post by Azyx on 2013-09-27
Great!! :) I now uninstall nautilus-patch_v3.4.2-0ubuntu8-1_amd64 (Nautilus patch) and wait.

---

### Post by Azyx on 2013-09-27
By the way..
For approx a year ago I make an modification according to point [COLOR=#ff0000]**12**[/COLOR] on my other Computer.

[http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html](http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html)

But this suddenly stop working, after an upgrade I think. Do I need to get rid of this, or did the nautilus-mod disappear, when the arrows move over to the right-side?

---

### Post by Azyx on 2013-09-28
Worked Great!!! Thank you very much mc4man!!!  :)

---

