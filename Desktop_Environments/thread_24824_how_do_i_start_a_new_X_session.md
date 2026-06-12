---
title: "how do i start a new X session ?"
date: 2005-04-08
forum: Desktop Environments
---

### Post by maddox on 2005-04-08
lets say i´m working in gnome and want to start a new X session in vt8.... with gdm asking for user/pass etc etc again.........how do i do this??  


any help would be greattly apreciatted

---

### Post by dusu on 2005-04-08
just clicking on the log out button does not work ?

---

### Post by lao_V on 2005-04-08
It's in one of the menu's I think - "Start new session"?

---

### Post by tomchuk on 2005-04-08
Applications -> System Tools - > New Login will start gdm on the next available VT.

---

### Post by rosslaird on 2005-04-08
You can also just type ctl-alt-f1, which will give you a new console login. You can do anything you want from there (though if you want another x-session you need to specify it correctly on the command line using DISPLAY options).

You can go back and forth with ctl-alt-f1 and ctl-alt-f7 (back to where you started). In fact, I think you can setup sessions going all the way to ctl-alt-f12.

---

### Post by Scorpios on 2005-04-15
any one knows how to start another X session automaticly when the computer starts ? I couldn't find how to do it.

---

### Post by lao_V on 2005-04-15
[QUOTE=Scorpios]any one knows how to start another X session automaticly when the computer starts ? I couldn't find how to do it.[/QUOTE]

why would you want to start another automatically when one is running?

---

### Post by Scorpios on 2005-04-16
The computer has serveral users who'd like to keep their sessions running at the same time, along with the ability to easly switch between them (ctrl + alt + F??). I know this is possible since I've done so at warty by modifying the xdm.conf file but I cant find the way to do so using hoary.

---

