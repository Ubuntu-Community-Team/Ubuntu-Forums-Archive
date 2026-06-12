---
title: "About &quot;create USB-stick&quot;???"
date: 2009-01-26
forum: General Help
---

### Post by utnubuuser on 2009-01-26
Hello  --  A question towards someone "in the know" about the "create USB-startup" feature.

If I have a laptop (for example), that requires configuration of say the Video driver, and maybe sound, maybe some special function keys, and my xorg.conf file, etc, and I make those configuration changes, does the "create USB-startup" feature include those configuration changes, and incorporate them?
I'm not necessarily looking for that particular feature in that program, so much as I'm wondering if it's relatively possible to **create installation** ISOs on USB, DVD or CD that includes the configuration changes, or if those types of programs tend to make only "generic" installation/live CD/USB media.

I've read so many posts about configuring new laptops, desktops, or what-have-you, that it's made me curious to know if I can create, (and then make available), a fully configured .iso for a specific laptop/desktop model.

I realize that there are literally thousands of different models of laptops/desktops, but I'm also aware of the fact that when IBM, or Dell, or Toshiba produce a new model, they tend to do so in lots of thousands, hundreds of thousands, and sometimes millions.

Aside from the fact that Gnu/Linux supports the most hardware of any available OS, I realize that a 700meg iso cannot be expected to work "out of the box" on every system.  I also realize that whenever a Gnu/Linux user gets a new piece of equipment, be it laptop, desktop, or net-device, and spends several hours installing/enabling drivers, allocating key-functions, etc, (s)he is essentially creating a fully configured OS specific to that model of hardware, and that that iso could then be made available to anyone else looking to install on the same model.

Maybe I'm in the dark here and everyone's already making their customized ISOs available to the broader community.  But I sure seem to be also seeing a lot of posts/threads that read something like this: "Ok, I tried, but I'm switching back to XP," or: "Linux will never be ready for the mainstream desktop". etc.

And in most cases, when someone complains about a piece of equipment not functioning properly under Linux, I can almost always find threads/posts listing all the fixes, settings, etc, applicable to that piece of hardware.  Isn't that what Torrents are about? Sharing files?  

So, back to the original question: Is it possible to create a startup/installation CD/DVD/USB-stick specific for any given hardware model/configuration, and make it available to/for your neighbor?

---

### Post by krzysz00 on 2009-01-27
You can remaster the ISO
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
and apply all the configuration/app changes in the chroot.
You can then chose it as the CD image in the "Create USB Stick" app

---

