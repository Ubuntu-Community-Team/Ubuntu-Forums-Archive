---
title: "K-Menu using the Windows key on the keyboard"
date: 2006-04-13
forum: Desktop Environments
---

### Post by pranav on 2006-04-13
I am new to linux, i am loving it. I am encouraging my friends to use it as well. Thank you everyone.

I need a little help, all my friends(all are new to linux) want to know how to get the K-menu using the windows key on the keyboard.

We found a way to assign short cuts to every program in the menu using the "menu editor", but we still do not know how to get the K-menu using the windows key.

Please help.:)

---

### Post by aysiu on 2006-04-13
Maybe [this](http://docs.kde.org/stable/en/kdebase/faq/panel.html#id2552351) might help.

---

### Post by jlhughes on 2006-04-13
[QUOTE=aysiu]Maybe [this](http://docs.kde.org/stable/en/kdebase/faq/panel.html#id2552351) might help.[/QUOTE]

I'm trying to do the 5.7. How do I use the Windows® key to open the K menu?

I have created win-key.sh

#!/bin/bash
xmodmap -e 'keycode 115=Menu'

and placed this is a directory .kde/env as the instructions say.

I can execute the script "manually" but when I restart kde it doesn't appear to trigger the execution of /.kde/env/win-key.sh

Is there a step I'm missing?

---

### Post by aysiu on 2006-04-14
No idea. I just found the link, but I've never actually done it myself.

---

### Post by Hanj on 2006-04-14
I tried the guide and it worked fine, even after I restarted KDE. 
Jlhughes, you say you created the file /.kde/env/win-key.sh. Maybe this is simply a type-o, but it is supposed to be ~/.kde/env/win-key.sh, and that might be the problem. In case you didn't know, that little ~ sign means your home directory, so you should actually create the file /home/jlhughes/.kde/env/win-key.sh (or whatever your username is).

---

### Post by Neo Ex on 2006-04-14
I don't understand why the file must be located in ~/.kde/env. I've ever though that the folder where live the files that are started at the log in is ~/.kde/Autostart :confused:

---

### Post by jlhughes on 2006-04-14
[QUOTE=Hanj]In case you didn't know, that little ~ sign means your home directory, so you should actually create the file /home/jlhughes/.kde/env/win-key.sh (or whatever your username is).[/QUOTE]

Thanks. I'm obviously new to Linux and Ubuntu and didn't understand the meaning of ~ before a directory name.

Moved the directory. Works as advertised.

---

### Post by pranav on 2006-04-14
The link provided works, thank you. But i am able to make only one of the Win keys open the Menu. The keycodes are 115 and 116. Only the 115 key opens the menu.

Any suggestions to make both of them work ?

---

### Post by uteck on 2006-04-14
Have you tried using the Kontrol Center?  There should be a keyboard option in there that will allow you to configure things.

---

### Post by pranav on 2006-04-14
[QUOTE=uteck]Have you tried using the Kontrol Center?  There should be a keyboard option in there that will allow you to configure things.[/QUOTE]


What else are we all talking about ?

The problem was in Kontrol Center assigning the K-Menu a shortcut with the Win-key only.

Now, after following the above link one of the 2 Win keys is working .. but not the other one.

---

### Post by jlhughes on 2006-04-14
[QUOTE=pranav]Now, after following the above link one of the 2 Win keys is working .. but not the other one.[/QUOTE]


The left and right Windows keys have different values. (Actually each has two values -- keypressed, keyreleased.)  I have no idea how to make both Windows keypressed codes do the same thing. I just use the left key.

---

### Post by firecrotch on 2006-04-14
You should just be able to add the following to your win-key.sh script (if your right Win-key is 116):

```
xmodmap -e 'keycode 116=Menu'
```

---

### Post by pranav on 2006-04-16
[QUOTE=firecrotch]You should just be able to add the following to your win-key.sh script (if your right Win-key is 116):

```
xmodmap -e 'keycode 116=Menu'
```[/QUOTE]


I tried it, both win-keys didnt work for me. Any suggestions, maybe i am wrong. Has it worked out for you all ?

---

