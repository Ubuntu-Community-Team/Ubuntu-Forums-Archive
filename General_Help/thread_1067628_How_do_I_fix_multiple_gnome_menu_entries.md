---
title: "How do I fix multiple gnome menu entries??"
date: 2009-02-12
forum: General Help
---

### Post by inspired on 2009-02-12
Hi folks,
I've been putting up with this for a while now. But as I add more apps this issue is starting to become annoying. I'd appreciate some help in sorting it out, if possible.

What happens is that multiple menu entries are often created for applications installed. For instance, there are five entries for Brasero Disc Burning. I have have to deactivate four of them (using gnome menu editor) and leave one activated to end up with one entry showing up in the menus.

Numerous apps have two entries. 
Looking at it, it's possible these are apps I have reinstalled (for instance, most of the audio apps have 2 to 5 entries, perhaps from when I was struggling to get audio apps to work properly). It might also be caused when an application is updated. Not sure.

Another issue... when I want to rearrange the menus (using the menu editor) the following happens: I want to move a menu entry to a new folder. I can drag it there and it creates a copy. I now have an entry in the old location and in the new location. There seems to be no way to cut and paste the menu entries. Just copy and paste. Is this normal?

I'd love to sort this out, as I am rapidly going into menu chaos, and I tend towards being anal retentive when it comes to organising my menus on an OS :)

Jonathan

---

### Post by cb951303 on 2009-02-12
That bugs me too. Instead of deactivating I delete the entries though. That seems to prevent future double entries sometimes.

---

### Post by prshah on 2009-02-12
> **inspired said:**
> I want to move a menu entry to a new folder. I can drag it there and it creates a copy. I now have an entry in the old location and in the new location. There seems to be no way to cut and paste the menu entries. Just copy and paste.

If you hold down shift while dragging menu items in the Menu Editor, it will _move_ the menu item; without the shift modifier, it will copy the item as a standard behavior.

Don't know why you are facing a problem with duplicates though; I've never had this problem even though I've been upgrading from 7.04 onwards though till 8.10 currently.

---

### Post by cb951303 on 2009-02-12
Even after a fresh install, before changing/installing literally *anything* there is always couple of double menu entries.
I'm experiencing this since ubuntu 7.x

---

### Post by zika on 2009-02-12
+1
-1(see the post below)
___
0 :)

---

### Post by geirha on 2009-02-12
Never experienced this either. I've been upgrading from edgy to hardy. I can give you a short rundown of how the menu system works though, might give you a clue on figuring out why this happens.

Menu-entries installed by packages from the repositories are installed in /usr/share/applications/ as .desktop-files. .desktop-files are text files with a fairly simple format. You can open open one in a text-editor and have a look.

It will also look in /usr/local/share/applications/, which is where things get put by default if you build the application yourself.

Now, if you delete a menu-entry from your menu, the corresponding .desktop-file is copied from /usr/share/applications to ~/.local/share/applications and a line "Hidden=True" is added to it. Any .desktop file in ~/.local/share/applications take precedence over /usr/share/applications. If you delete the desktop-file inside .local/share/applications/, the one in /usr/share/applications/ will be used again, and thus it will reappear.

I'm wondering though, what happens if you move away your current .local/share/applications? ```
mv ~/.local/share/applications ~/.local/share/applications.old
```

Do you get double entries immediately afterwards?

---

### Post by zika on 2009-02-12
I've never "played" with those multiple entries up to right now. I've counted 10 identical Okular entries and I've deleted 9 of them. I've counted 5 Brasero entries but, after closer look, I've found that all of them have different start-up options so they survived. so, Okular (which came with 8.10, I guess) was the reason I marked my +1. nevertheless thank You for insight to menu system, ...
yes, once I went to directory You gave, I found those (marker) files and after deleting them, I've got them back in menu that arranges "Main menu". but, even though they seemed same in menu that arranges the "Main menu" and their command lines were the same,they were not just the same (once I've looked at them closer) so they are back (all 10) in the menu (unchecked)... ;)
thank You again, good insight!

---

### Post by inspired on 2009-02-12
> **prshah said:**
> If you hold down shift while dragging menu items in the Menu Editor, it will _move_ the menu item; without the shift modifier, it will copy the item as a standard behavior.

Don't know why you are facing a problem with duplicates though; I've never had this problem even though I've been upgrading from 7.04 onwards though till 8.10 currently.
Thanks. I did try the shift modifier, but then it won't complete the drag and drop. The item I am dragging visually slides back to where I dragged it from. So that doesn't work for some reason either.

Jonathan

---

### Post by inspired on 2009-02-12
> **cb951303 said:**
> That bugs me too. Instead of deactivating I delete the entries though. That seems to prevent future double entries sometimes.
If the double entry was one I created by copying and pasting the entry to the location where I prefer it (I can't CUT and paste, nor drag and drop with SHIFT modifier, see above on that)... and I then delete the original... then the new one is delete also most of the time. So I end up having to have a deactivated one in the original location.

Cheers,
Jonathan

---

### Post by inspired on 2009-02-12
> **geirha said:**
> 

I'm wondering though, what happens if you move away your current .local/share/applications? ```
mv ~/.local/share/applications ~/.local/share/applications.old
```

Do you get double entries immediately afterwards?
Thanks for all the info. I'll read it a few times in order to get my head around it.

I moved that folder as suggested and now I have lost all the entries in custom folders I had created. The folders are there but are empty. Not good. I shall restore that folder now.

Any idea why that happened?

UPDATE: Bummer. I have did mv ~/.local/share/applications.old ~/.local/share/applications thinking that would restore what I had, and now all my custom folders are gone too. Any way to get them back? I've spent hours fiddling with menus to get them the way I want.

**UPDATE 2. Okay. Now the folders have reappeared. But not the entries I had in them. Would really like to get that back. Must be at least 30 changes to redo.**

Cheers,

Jonathan

---

### Post by geirha on 2009-02-12
.local/share/applications/ most likely recreated itself with a default config. so when you did "mv ~/.local/share/applications.old ~/.local/share/applications/" it moved it into that new folder (as ~/.local/share/applications/applications.old)

Try:
```

# Move it back out of applications/
mv ~/.local/share/applications/applications.old ~/.local/share/
# Rename the new applications folder to applications.bad, then immediately afterwards, move the applications.old back into place
mv ~/.local/share/applications ~/.local/share/applications.bad ; mv ~/.local/share/applications.old ~/.local/share/applications
```

---

### Post by inspired on 2009-02-12
> **geirha said:**
> .local/share/applications/ most likely recreated itself with a default config. so when you did "mv ~/.local/share/applications.old ~/.local/share/applications/" it moved it into that new folder (as ~/.local/share/applications/applications.old)

Try:
...
Thanks. Got it back.
I see there are many duplicate file names in that applications folder. The files are often not identical though, as their byte size is different.

---

### Post by inspired on 2009-02-28
Hi folks...
Thanks for all the help on this.
I took a rest from trying to sort this out... as it seems I spend way too much time trying to tweak Ubuntu/Linux into behaving the way I would like. Just spend half a day getting MTP and MSC connections to an mp3 device to work properly.

Anyway... this issue is still bugging the heck out of me. The more apps I install the more it bugs me... all these multiple entires... not being able to ust drag and drop an entry from where ever the app install put it to where I want it, etc.

Here's the two main things I'd like to solve. Based on the great help received so far, I've not managed to figure these two things out.
1) I can't move (drag and drop with shift modifier) menu entries from one location to another. I have to copy them. Using the shift modifier they just visually shoot back to where they were. Without the shift modifier they are copied, I then end up with two copies.
It would be nice to fix that. Failing that... #2 would be good to solve

2) Once I have copied the entry to the new folder, if I delete the original entry, the copied one is also deleted. Both vanish.
If I don't delete the original I of course have the option to disable/hide it, but then I end up with a huge list of disabled entries... and that is a pain.
How can I move an entry without creating two instances? Put another way, how can I delete the original without deleting the copy?

I'd love to sort this out. I have a lot of apps I use and fiddle with, and I am fast getting into a messy menu madness! :confused:

Thanks...
Jonathan

---

