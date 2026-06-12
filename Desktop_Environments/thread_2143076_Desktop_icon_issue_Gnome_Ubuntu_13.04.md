---
title: "Desktop icon issue Gnome Ubuntu 13.04"
date: 2013-05-07
forum: Desktop Environments
---

### Post by chazdg24 on 2013-05-07
[COLOR=#333333][FONT=Ubuntu Beta]I have been using Gnome Ubuntu 13.04. I updated to Gnome 3.8 and all is well. Not happy with Nautilus 3.6 in Unity or Gnome Ubuntu I try PCmanFM. My system begins to reboot at will, although PCmanFM is fast. I noticed that although Desktop icons are enabled in Gnome-tweak-tool, there are no desktop icons.
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]I try Thunar File Manager. Very fast like PcmanFM but still no Desktop icons. How do I fix this?[/FONT][/COLOR]

---

### Post by Archit88 on 2013-05-08
I think there is problem with your icon cache.
try to run this bash script using ```
sudo
```

```
for i in /usr/share/icons/*;do  gtk-update-icon-cache -f $i; done
```

---

### Post by mcduck on 2013-05-08
Also remember that desktop, including all the icons, is handled by the file manager. So by default the icons are handled by Nautilus, and if you stop Nautilus from starting on login and use some other file manager instead, you need to set that file amnager to handle the desktop. Both Thunar and PCMAnFM should have the option.

---

### Post by chazdg24 on 2013-05-08
I get the following error when running sudo for i in /usr/share/icons/*;do  gtk-update-icon-cache -f $i; done

bash: syntax error near unexpected token `do'

Thanks in advance for any help!

Edit:  I did it wrong.  I logged in as gnome root terminal and put in for "i in /usr/share/icons/*;do gtk-update-icon-cache -f $i; done"


gtk-update-icon-cache: No theme index file.
gtk-update-icon-cache: No theme index file.
gtk-update-icon-cache: No theme index file.
gtk-update-icon-cache: Cache file created successfully.
gtk-update-icon-cache: Cache file created successfully.
gtk-update-icon-cache: Cache file created successfully.
gtk-update-icon-cache: Cache file created successfully.
gtk-update-icon-cache: Cache file created successfully.
gtk-update-icon-cache: No theme index file.
gtk-update-icon-cache: No theme index file.
gtk-update-icon-cache: No theme index file.
gtk-update-icon-cache: Cache file created successfully.
gtk-update-icon-cache: No theme index file.

Unfortunately, it didn't work, still no Desktop icons.

---

### Post by chazdg24 on 2013-05-08
I decided to go with Nemo and made it default file manager.  The fix requires going into dconf under org-nemo-desktop,  There you can enable Home, Trash and Computer.

---

### Post by Bram_Andelhofs on 2013-08-13
Your answer is right here:

[http://www.youtube.com/watch?v=CoUqX9ZUijg](http://www.youtube.com/watch?v=CoUqX9ZUijg)

Good luck! ;)

---

