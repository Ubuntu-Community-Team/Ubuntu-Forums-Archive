---
title: "Can't Restart X"
date: 2005-08-10
forum: Desktop Environments
---

### Post by NMUrugbysteve on 2005-08-10
I've been tinkering with enlightened gnome recently, and now when I ctrl+alt+backspace I'm brought to a command line login. I login as my username and then I can't get back into GDM. Also, when I do logout, restart, it takes me to the CLI login and i have to login and give command reboot.

---

### Post by roland on 2005-08-10
[QUOTE=NMUrugbysteve]I've been tinkering with enlightened gnome recently, and now when I ctrl+alt+backspace I'm brought to a command line login. I login as my username and then I can't get back into GDM. Also, when I do logout, restart, it takes me to the CLI login and i have to login and give command reboot.[/QUOTE]

Try "startx" after logging in. Gnome should start now.

---

### Post by NMUrugbysteve on 2005-08-10
[QUOTE=roland]Try "startx" after logging in. Gnome should start now.[/QUOTE]
 Yeah, I've been doing that for a while. It works fine, but anyone have any clue as to what I could have broken here? I shouldn't have to type any commands just to restart my computer.

---

### Post by roland on 2005-08-10
[QUOTE=NMUrugbysteve]Yeah, I've been doing that for a while. It works fine, but anyone have any clue as to what I could have broken here? I shouldn't have to type any commands just to restart my computer.[/QUOTE]

In Ubuntu you shouldn't have, indeed. It could be the runlevel, there are 6 of them, and maybe there has been configured that the wrong one has to be default. Please check the [font=courier]/etc/inittab[/font] file with a text editor, as the root user. So for example [font=courier]$ sudo gedit /etc/inittab[/font].

Now check the following lines:
```

# The default runlevel.
id:2:initdefault:

```

Check the number between the semicolons, it should be 2. **Backup the file first**, then edit it, and restart your computer. And see what happens...

---

