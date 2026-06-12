---
title: "My keyboard does not let me write special characters anymore"
date: 2012-09-22
forum: Desktop Environments
---

### Post by toftenes on 2012-09-22
I'm not able to write the following characters anymore:
 ò ó ~ ô ö
and several others. Annoying as I need them when I write. 

All of these characters have in common that to write them I need to combine "Alt Gr" or shift-key with a second key followed with a letter. So three steps in total for the letters I struggle with. It did work just a week or two ago. 

It does still work in console (init 3) and in the guest account but not in init 5 on the account I use daily. 

The problem applies for all programs in the X environment(standard gnome).

What I've tried:
- System settings -> keyboard layout: Is set to Norwegian
- Switching to English and back did not help

---

### Post by StinkySQL on 2012-09-22
> **toftenes said:**
> It does still work in console (init 3) and in the guest account but not in init 5 on the account I use daily. 
The problem applies for all programs in the X environment(standard gnome).

Sounds like that specific account then, is there any way that the map was modified? I'm not an expert, just a guess.

---

### Post by toftenes on 2012-09-23
Yep, it is my specific account.  I'm sure I've not edited I've not edited the keyboard map on purpose.  Plus I don't know if there is any keymap-file in my home folder. It has to be some config file located in my home folder that is causing this. Right?

I just installed and configured urxvt, and unlike the gnome terminal, my keys work there, so for the moment I'll have to use "emacs -nw" in the terminal rather than the graphical one for writing.

---

### Post by toftenes on 2012-09-24
Ok, I bit the bullet, entered init 3, ran:

 mv -R ~/.* bak/ 

and copied back the config files I needed. I had to set up the desktop environment all over. Not that it was that much work.

It was not a pretty way to solve it but at least I can write normally again.

---

### Post by uzumakifahim on 2012-09-24
> **toftenes said:**
> Ok, I bit the bullet, entered init 3, ran:

 mv -R ~/.* bak/ 

and copied back the config files I needed. I had to set up the desktop environment all over. Not that it was that much work.

It was not a pretty way to solve it but at least I can write normally again.

I'm facing almost the same problem. I think I could solve my own problem with the same solution as you, but I can't understand your solution. Would you please describe your solution more clearly here.

Thanks in advance.

---

### Post by uzumakifahim on 2012-09-26
I've tried with this command in terminal

```
mv -R ~/.* bak/ 
```

but terminal showing that, this command is invalid. I don't understand what to do.

How can I solve this problem. Please anyone help me.

---

