---
title: "Beryl help - could be a simple problem"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by csaldan on 2007-04-25
I am having a problem with beryl. When i start it my windows have no title and i cannot move them around. Everything else in beryl seems to be working fine. I downloaded the beryl-manager and if i run beryl-manager and then beryl from the terminal it works fine. Is there any way to make it run from start-up instead of typing it into the terminal everytime i log in.

---

### Post by compmodder26 on 2007-04-25
I'm not sure I understand.  How are you starting beryl when the window borders don't work?

---

### Post by Lopsicle on 2007-04-25
System > preferences > sessions . add beryl-manager

---

### Post by csaldan on 2007-04-25
I put it in System -> Preferences ->session -> startup options

Ive added the command   beryl    over there so that it starts at start  up (I'm sorry im a newB)

Thanks for the quick reply

---

### Post by csaldan on 2007-04-25
if i jus add beryl-manager it doesnt start beryl , i have to go to a terminal and run beryl manually

---

### Post by djpinger on 2007-04-25
Try putting in

```
/usr/bin/beryl-manager
```

instead of just the executable in the session settings.

---

