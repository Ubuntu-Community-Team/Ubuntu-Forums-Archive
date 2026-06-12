---
title: "Unity: Nautilus does not ctrl-d - no bookmark adding possible"
date: 2012-07-16
forum: Desktop Environments
---

### Post by lptr on 2012-07-16
Anyone found a solution that I can add bookmarks to Nautilus as I did this before when using GNOME?

Currently ctrl-d or directly selecting menu item does nothing.

Thanks.


Ubuntu 12.04 current patch state

---

### Post by lptr on 2012-07-17
nobody? 

Searched for this on the net. Could not even find something about on launchpad. Is this a new bug or feature in Unity?

---

### Post by lptr on 2012-07-17
Seems to be a feature. 

I tried things out on my old installation (Gnome2). See screenshots: First two showing Gnome2 Nautilus. This one has an entry line containing the full path. This one is missing in Unity's Nautilus (see third screenshot). 

As this address line is responsible for bookmarking (Ctrl-D) and seems to be empty (hidden or non existent whatever) no bookmarks can be added into sidebar.

Is there any way to get this address bar back into Nautilus for Unity? Is there any hidden switch or plugin that needs to get installed?

Any ideas?

---

### Post by Frogs Hair on 2012-07-17
I just added my Conky folder to bookmarks . I opened help and the instructions said to open the folder and select add bookmarks. I wasn't able to add the folder without opening it.

---

### Post by lptr on 2012-07-18
Thanks for reply. 

I have to revert. It adds a bookmark. I am safe it did not yesterday - strange. Anyways I expected to see this new entry *under* the entries not as the first entry. 

From your screenshot I see that bookmarks in English version of Nautilus is arranged differently. Did you rearrange this order, or is this just default?

Mine looks like this:

---

### Post by Frogs Hair on 2012-07-18
Nautilus is default with a different theme. I was logged in to the Gnome shell that is why the application menu appears in Nautilus. It would be on the top panel in Unity.

---

### Post by fercho15 on 2012-12-10
Yes, ctrl-d does not work as expected. You can also use the command line (Not difficult at all). Follow these instructions:

1. Open a terminal.
2. cd ~ ( to make sure you are in your home directory)
3. sudo gedit gtk-bookmarks 
4. You will find a list of folders like "file:///home/user/Documents" among others. Create your own links to the folders you want to add following the exact format.
5. Save you gtk-bookmarks file and close it.
6. type nautilus -q to exit your file explorer

Is done. Next time you start nautilus the folders must be there, of course if the paths you included are all right.

This was successfully tested in a Ubuntu 12.04 machine  running gnome3.

** In line 3, you can use your preferred editor gmacs, vi or vim, gedit is always available in the repository (sudo apt-get install gedit)

Enjoy it !

---

### Post by baillou2 on 2013-01-21
> **fercho15 said:**
> Yes, ctrl-d does not work as expected. You can also use the command line (Not difficult at all). Follow these instructions:

1. Open a terminal.
2. cd ~ ( to make sure you are in your home directory)
3. sudo gedit gtk-bookmarks 
4. You will find a list of folders like "file:///home/user/Documents" among others. Create your own links to the folders you want to add following the exact format.
5. Save you gtk-bookmarks file and close it.
6. type nautilus -q to exit your file explorer

Is done. Next time you start nautilus the folders must be there, of course if the paths you included are all right.

This was successfully tested in a Ubuntu 12.04 machine  running gnome3.

** In line 3, you can use your preferred editor gmacs, vi or vim, gedit is always available in the repository (sudo apt-get install gedit)

Enjoy it !

This did the trick. I also love knowing that that file exists in the first place. Never noticed it before.

Thanks a million.

But the bug still needs to be fixed. I mean, really, this is ridiculous.

---

