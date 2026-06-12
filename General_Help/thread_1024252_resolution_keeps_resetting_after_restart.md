---
title: "resolution keeps resetting after restart"
date: 2008-12-28
forum: General Help
---

### Post by methid122 on 2008-12-28
i have my pc hooked up to my 42" plasma. and the highest res is only 1024x768, so every time I restart my pc I have to plug in my monitor and set it back to my plasma's res.can anyone help me out real quick. im sure its just a simple text file i have to edit. thanks.  

:D ps.2 hours using ubuntu and i love it!!!

---

### Post by methid122 on 2008-12-28
bump

---

### Post by eBoxNet on 2008-12-28
first of all connect your tv screen and try to autoconfigure your x by typing : 

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

on a terminal window.after that restart x by hitting CTRL+ALT+BACKSPACE

---

### Post by methid122 on 2008-12-28
as i posted im still new with ubuntu, so how do i modify x? thanks

---

### Post by Seks on 2008-12-28
What are you using to change the resolution? I've found that the nvidia control panel doesn't make its changes permanent, and system>prefs>screen res does.

---

### Post by eBoxNet on 2008-12-28
> **methid122 said:**
> as i posted im still new with ubuntu, so how do i modify x? thanks

open up a terminal and type inside the command i posted.

---

### Post by methid122 on 2008-12-29
> **eBoxNet said:**
> open up a terminal and type inside the command i posted.

thanks alot, it starts up at my resolution.

---

### Post by eBoxNet on 2008-12-29
You are welcome ;)

Mark this as [SOLVED]

---

### Post by pwagner on 2009-01-30
Though the "sudo dpkg-reconfigure xserver-xorg -phigh" command was executed the maximum resolution that I am able to select is 800X600.  Previously, using 8.04 (now at 8.10) the resolution was able to be set to 1600X1200.  Even after copying the original xorg.conf (with the higher resolution options) and resetting the xserver (or rebooting the machine) the lower resolution prevails!!!

Any ideas on what to check/change next would be great!

---

