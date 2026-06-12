---
title: "Compiz: maximized windows out of control?"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by bela42 on 2007-06-25
Hi all,

when I maximize any window using compiz with gtk-window-decorator I cannot use the title bar controls anymore. Just the menu invoked either by <alt><space> or from the task bar. This is strange. Is there a fix for that available?

Thanks,

Bernd.

---

### Post by visik7 on 2007-06-25
sudo gedit /etc/drirc 
and paste
<option name=&#8221;allow_large_textures&#8221; value=&#8221;2&#8243; />
in it
should fix the problem

---

### Post by keesjelol on 2007-06-27
when i switch over to compiz or beryl in the beryl manager i lose my title bars, any suggestions?

---

### Post by superyounan1 on 2007-06-27
> **keesjelol said:**
> when i switch over to compiz or beryl in the beryl manager i lose my title bars, any suggestions?

try running ```
metacity --replace
``` or if you have emerald, ```
emerald replace
``` if one of those help, then change your command to start compiz to ```
compiz --replace -c emerald
``` or instead of emerald put metacity, depending on which worked well in the first step. the `-c` tells compiz to automatically load the preferred window decorator

---

### Post by Alp82 on 2008-05-07
I have another problem. I installed hardy and got a weird behaviour when windows are maximized: They automatically unmaximize and maximize when i am doing something in that windows (i.e. typing, but mostly when clicking). That's really annoying because i cant use maximized windows anymore... any suggestions?

Compiz and Emerald are enabled.

---

