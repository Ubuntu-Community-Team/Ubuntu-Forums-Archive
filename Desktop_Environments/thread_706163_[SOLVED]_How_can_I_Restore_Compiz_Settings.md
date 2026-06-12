---
title: "[SOLVED] How can I Restore Compiz Settings"
date: 2008-02-24
forum: Desktop Environments
---

### Post by Protek on 2008-02-24
Hi there,

I've recently uninstalled the restricted driver for my ATI and reinstalled it.  I have re-enabled Compiz Advanced Desktop Effects again, but all my settings have reverted to defaults.  I took a backup of my home directory and a few others, but don't know where the Compiz settings are found, so I can restore them.

Can somebody point me in the right direction please?

Thanks,

---

### Post by alan34 on 2008-02-24
Here

alan@alan-desktop:cd ~/.config/compiz/compizconfig/

File is Default.ini

---

### Post by Protek on 2008-02-24
Hi Alan,

Thanks for your quick reply.  I have located the compizconfig directory in my backup, but there is only one file in there called "config" which contains the following details:

[gnome_session]
profile = 
plugin_list_autosort = true

This doesn't restore my comiz settings (i.e. rotating cube and wobbly windows) when i copy it over my existing file.

Any ideas?  

Thanks.

---

### Post by alan34 on 2008-02-24
My guess is that you have never saved/altered  the settings so will not have that file there.

Well at least you can enjoy puting everything back to how it was :-)

---

### Post by imoatama on 2008-02-24
If you were using Gconf to record your setting rather than a flat-file, there wont be a settings file in the compiz directory. Check in ~/.gconf/apps/compiz in your backup - i dont know much about gconf but it's possible that copying that from you backup to your .gconf/apps directory will restore compiz settings

---

### Post by Protek on 2008-02-24
Thanks imoatama!

That did the trick perfectly.  All settings restored.

Just a quick note: I had to logout and back in again (or restart X), but once I did everything was sweet.

Thanks again.

---

