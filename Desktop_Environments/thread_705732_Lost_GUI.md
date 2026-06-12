---
title: "Lost GUI"
date: 2008-02-23
forum: Desktop Environments
---

### Post by C.T.Anwar on 2008-02-23
Hi,
i have installed ubuntu 7.1 in my laptop. everything was working good except for my graphics. I have ATI Radeon xpress 200M in my laptop. i got the instruction from this forum on how to install the card while trying something went wrong and now i do not have any GUI anymore. What should i do. My processor is AMD sempron . Can anyone help me out here?:confused:

---

### Post by shad0w_walker on 2008-02-23
Can you provide a link to the guide you used? Knowing exactly what happened will help out alot with figuring out how to get things running again.

---

### Post by taurus on 2008-02-23
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by C.T.Anwar on 2008-02-24
> **shad0w_walker said:**
> Can you provide a link to the guide you used? Knowing exactly what happened will help out alot with figuring out how to get things running again.

Sorry cant seem to find it at the moment , i know it is somewhere in this forum . I searched with my graphics card name and found the instructions. while i was installing it something went wrong. now when i log into ubuntu it says cant load flgrx or something like that . i can write down the errors here if u want . 
let me know

---

### Post by C.T.Anwar on 2008-02-24
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

when i type the code it says need to be root. how do i go there ?

---

### Post by PmDematagoda on 2008-02-24
Append those commands with **sudo** to make them look like this:-
```
**sudo** dpkg-reconfigure -phigh xserver-xorg
**sudo** shutdown -r now
```
appending commands with **sudo** gives those commands root privileges which may be important at times to perform administrative tasks, but do not be too heavy-handed with **sudo** since it can harm your system when used improperly. So use **sudo** wisely.

---

### Post by C.T.Anwar on 2008-02-25
thanks guys , that helped . got back the GUI but new problem . whenever i try to log in , the desktop becomes blueish and then it automatically log me out. i am currently logged in with the failsafe gnome session . any suggestions ?

---

