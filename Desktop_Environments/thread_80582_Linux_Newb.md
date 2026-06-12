---
title: "Linux Newb"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Donnut on 2005-10-22
I am a newb to linux, and when I installed Ubuntu, I just got a command promt.  How do I get to the desktop?  HELP!!!!!

---

### Post by GeneralZod on 2005-10-22
Oops - that shouldn't have happened :)

It sounds like Ubuntu doesn't like your graphics card - which graphics card do you have?

---

### Post by heimo on 2005-10-22
Did you do default install or expert install? You could try to install ubuntu-desktop using this command:
```
sudo apt-get install ubuntu-desktop
```

If you get any errors, there may have been problems during install. Post any warnings and errors.

Try to start gdm (graphical login manager):
```
sudo /etc/init.d/gdm start
```

---

### Post by Donnut on 2005-10-22
I have an ATI Radeon 9200.  Also, I loged in to the dos prompt, don't know if that helps any...

---

### Post by Donnut on 2005-10-22
I don't remember having a choice on expert install...

---

### Post by Donnut on 2005-10-22
now it says 99% working when i put in the ubuntu-desktop command, and hd is working....

---

### Post by Donnut on 2005-10-22
OK, is there anything else i have to setup besides desktop?

---

### Post by l0c0dantes on 2005-10-22
try typing "startx" 

That might help, not sure tho, im probally as new to this linux thing as you are

---

