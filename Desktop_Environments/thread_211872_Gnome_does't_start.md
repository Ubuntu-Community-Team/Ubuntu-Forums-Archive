---
title: "Gnome does't start"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Viper666 on 2006-07-09
I reinstalled ubuntu dapper after an unsuccesfull upgrade to edgy. After installing all i needed i updated dapper and now it doesn't start gnome.
It shows the login window and then it just give's me an empty desktop whith the default theme. No tasbar no icons..just the mouse. And i doesn't show that bar which shows that stuff is loading before u can actually use gnome.

I tryed dbus-launch gnome-session and it sais "Cannot open Display"

I also tryed deleting/reinstalling nvidia-glx (if deleted it just boots to the console).

when i try to edit /etc/x11/xorg.conf it sais something like "file not found" :shock: 

I really have no ideea of what to do next cause i don't wanna reinstall ubuntu. I must say i had NO problems since started using ubuntu.

What should i do???

---

### Post by Viper666 on 2006-07-09
no ideas? 

i think i'll just reinstall and NOT update for a few weeks :(

---

### Post by Zerocool10482 on 2006-07-09
I've had this happen before. Don't know how to fix it but type:

gdm

And this should work. It worked once.

---

### Post by Viper666 on 2006-07-09
when i typed GDm it started the login screen but there is still an empty desktop. I think i must reinstall :(

---

### Post by Zerocool10482 on 2006-07-18
Sorry thought that would help.

---

### Post by gosh on 2006-09-19
> **Viper666 said:**
> I reinstalled ubuntu dapper after an unsuccesfull upgrade to edgy. After installing all i needed i updated dapper and now it doesn't start gnome.
It shows the login window and then it just give's me an empty desktop whith the default theme. No tasbar no icons..just the mouse. And i doesn't show that bar which shows that stuff is loading before u can actually use gnome.

I tryed dbus-launch gnome-session and it sais "Cannot open Display"



I have the same problem. I cant start gnome nor xfce
When I start failsafe gnome it says it has trouble with dbus-launch and dbus-deamon.

---

### Post by nullmind on 2006-09-19
Could this be because of something to do with the setup of your display in your /etc/X11/xorg.conf file. Try posting that and maybe we can help.

What happens if you run gnome-panel or nautulis?

---

