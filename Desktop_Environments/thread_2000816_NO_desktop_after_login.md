---
title: "NO desktop after login"
date: 2012-06-10
forum: Desktop Environments
---

### Post by kukuzry on 2012-06-10
HI, I  run purge nautilus,  and after that the computer cannot load the desktop.  It can only enter into the command line (like terminal). I run "sudo apt-get install Unbuntu-desktop" but no luck. 

Also I run "unity --reset", I can enter into the desktop but if I close the "X terminal", it will go back to command line window.

How can I restore to the previous desktop version?

---

### Post by codemaniac on 2012-06-10
What happens when you try to reinstall it ?

```
apt-get install nautilus
```

---

### Post by ajgreeny on 2012-06-10
> **kukuzry said:**
> HI, I  run purge nautilus,  and after that the computer cannot load the desktop.  It can only enter into the command line (like terminal). I run "sudo apt-get install [COLOR=Red]Unbuntu[/COLOR]-desktop" but no luck. 

Also I run "unity --reset", I can enter into the desktop but if I close the "X terminal", it will go back to command line window.

How can I restore to the previous desktop version?
Try ```
sudo apt-get install [COLOR=Red]ubuntu[/COLOR]-desktop
```Your command was incorrect, and don't forget linux is case-sensitive.

---

### Post by kukuzry on 2012-06-10
> **ajgreeny said:**
> Try ```
sudo apt-get install [COLOR=Red]ubuntu[/COLOR]-desktop
```Your command was incorrect, and don't forget linux is case-sensitive.

I used the correct one.

I run "sudo apt-get install ubuntu-desktop" and "sudo apt-get nautilus",

the system says it is already latest and there is 0 update.:-(

If I run "unity --reset", I can see my desktop, but there is an additional "X term" to open, if I close X-term, it will go back and there is GUI.

Thank you,

---

### Post by kukuzry on 2012-06-10
> **kukuzry said:**
> I used the correct one.

I run "sudo apt-get install ubuntu-desktop" and "sudo apt-get nautilus",

the system says it is already latest and there is 0 update.:-(

If I run "unity --reset", I can see my desktop, but there is an additional "X term" to open, if I close X-term, it will go back and there is GUI.

Thank you,

It is working now, I have to select different desktop in the login window.

I seem to install gnome, there are six or seven desktop option to select, such as gnome, gnome classic, ubuntu 2D....

Thanks,

---

