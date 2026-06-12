---
title: "Ctrl+Alt+F1..F6 doesnot work"
date: 2006-08-25
forum: Desktop Environments
---

### Post by sqadeer on 2006-08-25
I have installed Ubuntu 6.06 and the Ctrl+Alt+F1..F6 key combination to switch to console does not work. Have looked at the documentation, but tere is no metionof enabling or disabling this key combination. What can I do?

---

### Post by peabody on 2006-08-25
> **sqadeer said:**
> I have installed Ubuntu 6.06 and the Ctrl+Alt+F1..F6 key combination to switch to console does not work. Have looked at the documentation, but tere is no metionof enabling or disabling this key combination. What can I do?

Odd, works for me.  Do you have a custom .xmodmap?

---

### Post by sqadeer on 2006-08-25
No!

---

### Post by dmwit on 2006-08-25
Are you using XGL?  (I.e. compiz?)
~d

---

### Post by paddy1978 on 2006-08-25
I briefly had this problem for a while. It happened after I had been messing with my /etc/X11/xorg.conf file - I think the wrong keyboard type had got in the "InputDevice" section. Once I put the correct details in it seemed to work.

I think the "XkbModel" was the culprit - it was "pc104" but should have been "pc105". (That's a UK laptop though - I see your in Pakistan, so not sure what the layout code would be there).

Sorry this sounds a bit vague, but it was quite a while ago so I don't remember exactly what I did! Something for you to try though... :-)

---

### Post by sqadeer on 2006-08-25
No I am no using XGL, and I have checked with both pc104 and pc105 keyboards in my xorg.conf. No luck](*,) .

---

### Post by peabody on 2006-08-26
Do your Cntrl and Alt keys work in apps?  Both of them?

---

### Post by sqadeer on 2006-08-27
Yes both Ctrl and Alt work fine in Gnome terminal.

---

### Post by peabody on 2006-08-27
There may be a way to disable virtual terminal paging in the xorg.conf.  Maybe posting it will help.

---

### Post by funchords on 2006-08-27
I'm not sure what to do if the answer to this is 'no,' but do they show up when you do: **ps aux | grep getty**

---

### Post by sqadeer on 2006-08-27
YES they do show up!

---

### Post by funchords on 2006-08-27
Can you post your /etc/X11/xorg.conf here?

---

### Post by laibo on 2006-08-31
I have also problem with console.After instalation of nvidia driver i cant get to console.
If i press ctrl+alt+f..  i got black screen and nothing to do then a must switch to f6-graf mode. 
Before was everything all right. 
I have laptop ASUS A6vm with widescreen. I tried change keyboard in xorg.conf but dont help  and also i see terminals when i type ps -ax. Their state is Ss+.
Thx sory for my english

---

### Post by danderson3 on 2006-08-31
> **funchords said:**
> Can you post your /etc/X11/xorg.conf here?

see attached

---

### Post by enopepsoo on 2006-08-31
it seems fine to me, sorry I couldn't help more.:?:

---

### Post by christhemonkey on 2006-08-31
I used to have this problem with the propriety nvidia drivers (or maybe without them? i forget) back in flight 3 or something, 
To get round it, i just used the opposite nvidia driver to what i was using when it woudlnt work.

Its not really a solution im sorry.
I dont know why/how it happened, but since i'v been on 6.06(.1) it has been fine.

---

### Post by cwaldbieser on 2006-08-31
> **sqadeer said:**
> YES they do show up!

Can you change using the "chvt 1" command?

---

