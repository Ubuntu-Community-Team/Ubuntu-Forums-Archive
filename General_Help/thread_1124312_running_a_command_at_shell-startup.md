---
title: "running a command at shell-startup"
date: 2009-04-13
forum: General Help
---

### Post by Gorja on 2009-04-13
hey there!
now it's done! 8 weeks ago i deleted Windoze and enlarged my Hardy-partition. since that time i visited ubuntuforums.org nearly everyday to configure my Ubuntu to my own needs. I never had to sign up becaue every question i had was answered here.
but now, i couldn't find an answer according to my problem (this google thing didn't help either *rolleyes*)

my problem: when i start a shell i want a command to be executed. how to do that?
example: everytime i start a shell "mocp" should be executed

thx 4 your help :)

Gorja

---

### Post by kpkeerthi on 2009-04-13
Put the command in .bashrc in your $HOME folder

---

### Post by Gorja on 2009-04-13
simply in or at a special position?

solved... simply pasted it into the file...

thx 4 help kpkeerthi

---

### Post by Barriehie on 2009-04-13
> **Gorja said:**
> 
...my problem: when i start a shell i want a command to be executed. how to do that?
example: everytime i start a shell "mocp" should be executed

thx 4 your help :)

Gorja

Alternatively you could add a launcher to the desktop and the command would be:
```

gnome-terminal --command=mocp

```Barrie

---

### Post by Gorja on 2009-04-13
thought of this, too. but i addad alt+e as a shortcut for my shell... (trying to avoid clicking and using of mouse)
i am using moc and it should load everytime i press alt+e...

---

### Post by kpkeerthi on 2009-04-14
You could also bind alt + e to ```
gnome-terminal --command=mocp
``` and remove the command from .bashrc. This way mocp starts only when you press alt + e and not everytime you start your terminal.

---

