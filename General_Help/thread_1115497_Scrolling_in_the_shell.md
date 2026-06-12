---
title: "Scrolling in the shell?"
date: 2009-04-03
forum: General Help
---

### Post by dodle on 2009-04-03
I have been using Ubuntu for a good while now, but I still have not learned how to scroll when I boot with no gui.  

For example:
   I boot up in text mode and enter the command```
help
```
   A list of usable commands prints out on the screen, but is cut off at the top so that I cannot see the first section of the printout.

How do I scroll up to be able to see this?

---

### Post by ShaunG on 2009-04-03
You can try piping your command to less or more.

Example:

```
ls -l | more
```

or 

```
ls -l | less
```

If you pipe to less you should be able to use up/down nav keys to navigate up and down through the text.

Hope this helps

---

### Post by 3Miro on 2009-04-03
You cannot scroll in pure shell.

Use commands like:
```

some_command | more
some_command | less

```

You will pipe the command to less or more commands. Those will handle the "scrolling" for you (use the up/down keys and space to move a screen at a time).

---

### Post by iaculallad on 2009-04-03
While on the terminal window:

Ctrl+Shift+Page UP -> Scroll Upwards
Ctrl+Shift+Page Down - > Scroll Down

EDIT: Aaaahhhh... you're in pure shell? That won't work.

---

### Post by oobe-feisty on 2009-04-03
yes but Shift+Page UP and Shift+Page Down so your suggestion is still valid


> **iaculallad said:**
> While on the terminal window:

Ctrl+Shift+Page UP -> Scroll Upwards
Ctrl+Shift+Page Down - > Scroll Down

EDIT: Aaaahhhh... you're in pure shell? That won't work.

---

### Post by dodle on 2009-04-03
Okay, but after piping a can't get back to the command input line.  It says "End" at the bottom but I can't Ctrl+C out of it.  Hitting *Enter* and *Escape* doesn't do anything either.

---

### Post by ShaunG on 2009-04-03
Press q for quit :)

EDIT: Type 

```
man less
 man more
```

 etc for the man pages on those commands, loads more info on them in there

---

### Post by dodle on 2009-04-03
> **ShaunG said:**
> Press q for quit :)

Too simple. Thanks.

---

### Post by ShaunG on 2009-04-03
Not a problem :)

---

### Post by iaculallad on 2009-04-03
> **oobe-feisty said:**
> yes but Shift+Page UP and Shift+Page Down so your suggestion is still valid

Yes, valid when you're booted on desktop environment.

---

