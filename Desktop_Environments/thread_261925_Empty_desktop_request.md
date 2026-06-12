---
title: "Empty desktop request"
date: 2006-09-20
forum: Desktop Environments
---

### Post by Monstroxus on 2006-09-20
I like my desktop to be empty, of course this is easy to do, just get rid of all the icons on the desktop... but I have a double boot with XP and I like the fact that my XP drives are mounted, so I can access them easily. However because of this, I have 3 XP drive icons on my desktop. As far as I know I cannot get rid of them unless I unmount them.

Is there any method that will allow me to get an empty desktop (get rid of these icons), while in Nautilus I still will have mounted XP drives?

---

### Post by codejunkie on 2006-09-20
> **Monstroxus said:**
> I like my desktop to be empty, of course this is easy to do, just get rid of all the icons on the desktop... but I have a double boot with XP and I like the fact that my XP drives are mounted, so I can access them easily. However because of this, I have 3 XP drive icons on my desktop. As far as I know I cannot get rid of them unless I unmount them.

Is there any method that will allow me to get an empty desktop (get rid of these icons), while in Nautilus I still will have mounted XP drives?

open a terminal and enter ```
gconf-editor
```then click on apps/nautilus/desktop and uncheck the box that says volumes_visible and that should do it.

---

### Post by Monstroxus on 2006-09-20
Aha! Thanks, I will try that! Its really neat to have a totally clean desktop (at least in my opinion) so thanks again. I have one colleague who has her desktop completely full with shortcuts... arghhh. How can you work like that? Makes me nervous.

---

### Post by Jannes. on 2007-09-24
i've got a problem with my desktop. When i booted ubuntu yesterday my desktop was empty. And trough that i cant get a look at my windows files :s and now is my desktop empty and when i slide something to it it doesnt appear :s  
can someone help me?


Jannes

---

### Post by Wolki on 2007-09-24
> **Jannes. said:**
> i've got a problem with my desktop. When i booted ubuntu yesterday my desktop was empty. And trough that i cant get a look at my windows files :s and now is my desktop empty and when i slide something to it it doesnt appear :s  
can someone help me?

Do the following: Press alt-F2, enter "gconf-editor", Run. 
In the window that opens navigate to /apps/nautilus/preferences/ and look for a key called show_desktop. Is there a checkmark in the box next to it? if not, click it. You may now need to restart nautilus ("killall nautilus").

Does this fix your problem?

---

### Post by Jannes. on 2007-09-25
there is a checkmark

---

### Post by Wolki on 2007-09-25
> **Jannes. said:**
> there is a checkmark

OK, so it isn't the easy solution :-/

Can you try it with a different user account and see whether that user still gets a desktop?

---

### Post by Jannes. on 2007-10-10
there arent pictograms on the desktop too

---

