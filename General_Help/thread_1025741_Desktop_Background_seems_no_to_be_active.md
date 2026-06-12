---
title: "Desktop Background seems no to be active"
date: 2008-12-30
forum: General Help
---

### Post by arepaking on 2008-12-30
Hello!
Right after entering my password when Ubuntu starts, I can see my desktop background picture. 4 seconds later the picture disappear and I can only see a solid color as my background.

Does anyone knows how resolve this?

Thanks for your help.
AK

---

### Post by arepaking on 2008-12-31
Hi!
Any help?

---

### Post by namdung on 2008-12-31
In terminal 
```
gconf-editor
```

In *desktop-->gnome-->background*, select *draw_background*.

---

### Post by arepaking on 2008-12-31
> **namdung said:**
> In terminal 
```
gconf-editor
```

In *desktop-->gnome-->background*, select *draw_background*.

Hi, Thanks for your reply.

I tried to follow your steps but I got this message from the terminal:
```
arepaking@lx:~$ gconf -editor
bash: gconf: command not found

```

I also tried to do the desktop instruction but I couldn't find the desktop-->gnome-->background.

As a side note, I consider myself a noob with Ubuntu. The version that I'm running is 8.10 (Intrepid). I started to have this issue since I used Remote Desktop Viewer; I used to have the "Disable Wallpaper when connected" option enable. I unmarked this option but it did not work.

Thanks again for your help.
AK

---

### Post by chamber on 2008-12-31
Just to be clear its 

```
gconf-editor
```

and not 

```
gconf -editor

```

Theres no space between gconf and -editor

---

### Post by arepaking on 2008-12-31
> **chamber said:**
> Just to be clear its 

```
gconf-editor
```

and not 

```
gconf -editor

```

Theres no space between gconf and -editor

Thank you very much. This Fix the issue!

Cheers,
AK

---

### Post by arepaking on 2008-12-31
> **chamber said:**
> Just to be clear its 

```
gconf-editor
```

and not 

```
gconf -editor

```

Theres no space between gconf and -editor

Thanks Chamber!

---

