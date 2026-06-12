---
title: "[SOLVED] Home Folder in Gutsy"
date: 2007-09-26
forum: Desktop Environments
---

### Post by chrismine on 2007-09-26
I do not know why but every time I restart my PC and upon boot up my home/profile folder is started automatically.

Is there a way to turn off this behavior?

I think it started to happen when I played around with WICD and Network _manger.

Thank you.

---

### Post by tbroderick on 2007-09-27
You mean the file manager opens your home folder after you login or are you talking about a /home partition? If it's the file manager, check System->Preferences->Sessions and see what is loading upon the start of GNOME.

---

### Post by chrismine on 2007-09-27
It is the home folder - i have checked startup sessions and all I can find is maybe User folders update - xdg-user-dirs-gtk-update or Visual - gnome-at-visual -s

Hope this means something.

I am not a total Linux n00b but I do not know what these entries do so I do not want ot disable it yet.

Thanks for any help.

---

### Post by chrismine on 2007-10-01
Anyone?

---

### Post by chrismine on 2007-10-05
Hello everybody

I still have the problem that my home folder open with Nautilus when I restart my computer. I have checked all the startup entries and disabled and re enabled them again after restarting. No joy.

Sometimes it opens maximized and sometimes minimized.

I also have the problem that my panel does not show when starting up - but clicking on the space where it should be brings it back.

Anyone have any ideas?

---

### Post by chrismine on 2007-10-06
I had to reinstall Gutsy last night after i switched to a bigger screen and cold not get thew resolution sorted out.

My home folder still opens on startup. 

Now I understand it less still.

Anyone?

---

### Post by jongkind on 2007-10-06
Can you post the contents of your /home/yourname/.config/autostart folder?

---

### Post by chrismine on 2007-10-06
The folder containts Power Manager and Volume Manager

---

### Post by jongkind on 2007-10-06
Hm, remarkable. I don't have a clue.

---

### Post by chrismine on 2007-10-06
Me too!

---

### Post by chrismine on 2007-10-06
As mentioned I have last night reloaded Gutsy from scratch, it must be some setting stored in my home partition.

---

### Post by chrismine on 2007-10-06
[SOLVED]

I changed the setting for nautilus under the Current Session tab in the Session GUI to normal from restart and apllied. Then rebooted.

The setting is back to restart but my Home folder does not open anymore.

---

### Post by JesseBeau on 2007-10-07
Thank you! My Home folder kept coming up at startup too! :)

---

### Post by greenstar on 2008-05-19
I had to remove ~/.gnome2/session before I got this to stop on my Dad's box.

---

