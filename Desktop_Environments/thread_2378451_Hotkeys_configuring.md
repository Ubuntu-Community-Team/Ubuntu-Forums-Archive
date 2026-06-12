---
title: "Hotkeys configuring"
date: 2017-11-23
forum: Desktop Environments
---

### Post by forneus2 on 2017-11-23
Trying to assign certain key combinations bit cannot find the menu options. I already have CTRL+ALT+T for launching terminal and I would like to have some hotkeys for launching File Browser/Home Folder and Firefox. Any ideas how to do that? Lubuntu 16.04

---

### Post by vasa1 on 2017-11-23
Look at the keybinds in *~/.config/openbox/lubuntu-rc.xml*.

---

### Post by kurt18947 on 2017-11-23
I'm using Ubuntu 17.10 right now, other 'flavors' will be different. I click the upper right corner -> tools -> settings -> Devices -> Keyboard -> custom shortcuts -> + key then specify key and associated command.

---

### Post by forneus2 on 2017-11-23
> **vasa1 said:**
> Look at the keybinds in *~/.config/openbox/lubuntu-rc.xml*.

That's what I was looking for. Thanks! Looks like CTRL+ALT+D gives me the file manager. Is it ok to edit this file to change it to CTRL+ALT+F or some other combo? Any other config files to edit along with this one?

---

### Post by vasa1 on 2017-11-23
> **kurt18947 said:**
> I'm using Ubuntu 17.10 right now, other 'flavors' will be different. I click the upper right corner -> tools -> settings -> Devices -> Keyboard -> custom shortcuts -> + key then specify key and associated command.
That never was an option in Lubuntu which is what the OP is using.

I've heard of a GUI for adding keyboard shortcuts for Lubuntu (or other LXDE-based systems) but somehow just got used to editing lubuntu-rc.xml (aka lxde-rc.xml and rc.xml) by hand. 

A couple of great links to using rc.xml in LXDE-based systems:  
[https://pclosmag.com/html/Issues/201011/page09.html](https://pclosmag.com/html/Issues/201011/page09.html)
[https://pclosmag.com/html/Issues/201107/page08.html](https://pclosmag.com/html/Issues/201107/page08.html)

---

### Post by vasa1 on 2017-11-27
> **forneus2 said:**
> That's what I was looking for. Thanks! Looks like CTRL+ALT+D gives me the file manager. Is it ok to edit this file to change it to CTRL+ALT+F or some other combo? Any other config files to edit along with this one?
Sorry but I missed your post!

Yoy can change anything to anything but you'll need to make sure you aren't using a keybind already assigned to something else or a keybind which could possibly conflict with other programs.

I like using the Super key plus something else. So, super+K would have pcmanfm open the des_k_top folder, super+N would open the dow_n_loads folder, super+F would launch _F_irefox and so on.

To register the changes and to ensure you haven't broken anything, run *openbox --reconfigure*. And always backup lubuntu-rc.xml *before* you edit it.

The two pclosmag links really helped me when I was using Openbox.

---

### Post by Dennis N on 2017-11-28
Although unavailable in Lubuntu 16.04, there is now an interactive GUI dialog in Lubuntu 17.10 to set up Hot Keys. Something to look forward to when you upgrade.

---

