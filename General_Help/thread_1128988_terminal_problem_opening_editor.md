---
title: "terminal problem opening editor"
date: 2009-04-18
forum: General Help
---

### Post by name123 on 2009-04-18
Hi, i just installed ubuntu 8.1o. I use it for programing, so I work with editors from the terminal. The problem is that the terminal is like "paused" when I open an editor, nedit, gedit. paused means that I am not able to run any other command until I close the editor. How can I configure my terminal to still be operating after open an editor window?

thanks :)

---

### Post by chriskin on 2009-04-18
if i am correct, you have to write a "&" after your command if you want the terminal to go on working. not sure though, going to check out now :)


hm even though i was almost sure, it isn't working for me. 
was it another symbol then? :S try it too, it might be a problem of my computer

---

### Post by Denestria on 2009-04-18
```
gedit file.txt **&**
```

If you use a terminal based editor like nano *ctrl-z* will suspend it to the background and *fg* will bring it back.

---

### Post by chriskin on 2009-04-18
so it IS the & symbol..
hm..then why is it no longer working for me? never mind, i never used it either way :)

---

### Post by name123 on 2009-04-18
> **chriskin said:**
> if i am correct, you have to write a "&" after your command if you want the terminal to go on working. not sure though, going to check out now :)


hm even though i was almost sure, it isn't working for me. 
was it another symbol then? :S try it too, it might be a problem of my computer

is working, but it still feels unconfortable to put it after each command.

---

### Post by chriskin on 2009-04-18
> **name123 said:**
> is working, but it still feels uncomfortable to put it after each command.

you can always open a second , third or Nth tab if you want, i've never heard of a terminal that keeps on working without the user asking it to.

---

### Post by name123 on 2009-04-18
> **chriskin said:**
> so it IS the & symbol..
hm..then why is it no longer working for me? never mind, i never used it either way :)

The bothering thing in this question is that in ubuntu 8.04 that option was like on by default settings. My termial was still enable after opening editor.

---

### Post by chriskin on 2009-04-18
> **name123 said:**
> The bothering thing in this question is that in ubuntu 8.04 that option was like on by default settings. My termial was still enable after opening editor.


without you fiddling with something? cause mine on 8.04 wasn't :O

---

### Post by name123 on 2009-04-18
> **chriskin said:**
> without you fiddling with something? cause mine on 8.04 wasn't :O

nothing just editor command and the name of the file. I think there might be something to edit the .bashrc (in my case) to set this option. I don't know.

---

