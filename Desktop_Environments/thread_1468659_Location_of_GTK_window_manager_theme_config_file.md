---
title: "Location of GTK window manager theme config file"
date: 2010-05-01
forum: Desktop Environments
---

### Post by ryankask on 2010-05-01
Greetings all,

I was messing around in the Window Manager Theme settings area and changed the theme to another one and I was immediatley logged off and now I cannot log back in. It seems like X is having a hard time displaying whatever theme I chose.

I want to manually switch back to Albatross but I am unsure of where that setting is stored. Where is the configuration file for these themes stored?

I am using Xubuntu 10.4.

Cheers,
Ryan

---

### Post by kerry_s on 2010-05-01
/home/your-name/.config/xfce4

it's a hidden folder so in gui press "ctrl+h", on cli use "ls -a".

---

### Post by ryankask on 2010-05-01
Cheers, specifically it's in ~/.config/xfce4/xfconf/xfce-perchannel-xml. I believe there is a bug in the nVidia driver which caused X to crash and go back to the login screen when trying to use the theme "Wildbush."

Ryan

---

### Post by ryankask on 2010-05-01
Cheers, specifically it's in ~/.config/xfce4/xfconf/xfce-perchannel-xml. I believe there is a bug in the nVidia driver which caused X to crash and go back to the login screen when trying to use the theme "Wildbush."

Ryan

---

### Post by Salix0210 on 2010-05-02
Just a short note that I also had problems with Wildbush theme in Xubuntu 10.04. Renameing /home/zsofiandris/.config/xfce4/xfconf/xfce-perchannel-xml helped me to log in with XCFE again.

---

### Post by lucamanu on 2011-11-04
Confirmed: I just installed Xubuntu 10.04, including all updates. While browsing the various themes I was abruptly logged out.
I also renamed the whole directory ~/.config/xfce4/xfconf/xfce-perchannel-xml
(note for the noobs like me, while in terminal digit:
```
mv xfce-perchannel-xml xfce-perchannel-xml.old
```
then exit and just log back in).
That was an annoying one! :(
thanks terry and ryankask

---

