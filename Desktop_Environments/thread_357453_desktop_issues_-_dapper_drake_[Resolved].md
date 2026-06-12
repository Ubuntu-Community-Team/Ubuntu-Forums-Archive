---
title: "desktop issues - dapper drake [Resolved]"
date: 2007-02-09
forum: Desktop Environments
---

### Post by adza on 2007-02-09
Hi there, i've got some really wierd things going on in my desktop and i was hoping someone could help me to fix them...
 1) i didn't put these here, but there is now a garbage bin and a suspiciously windows 'computer' icon on my desktop... i can't seem to remove them... my major concern is how they got there, they appeared there the other day.. i must've done an update or something..
2) this one is more worrying, i can't seem to use the updates feature in the taskbar.. i see the icon telling me there is updates available and click on it, it displays the window asking for root pswd, i supply pswd and nothing happens....??
3) my keyboard doesn't seem to be working properly (i know - it must be alright, i'm typing this yeah? hehe).... things have changed, like i can't [ALT]+[TAB] anymore, and holding down backspace or delete wont delete multiple characters... i have to repeatedly press the key to delete line etc etc...

Can someone please help me as to how i can diagnose what has made these changes and remove them?

-- This is my one week aniversary of ubuntu/linux!! woo-hoo!! :D

---

### Post by adza on 2007-02-10
well... there has been some progress made here but i don't understand what's happened... I managed to get into synaptic after all but only through sudo synaptic in the terminal and it opened and i could install the updates... Could anyone help me as to why this would work through the terminal but not by system-->administration-->synaptic package manager.

I also found a thread that has experienced similar issues as me with the key strokes and alt+tab etc not working... [http://www.ubuntuforums.org/showthread.php?t=239338&highlight=gnome+keyboard+properties+quit](http://www.ubuntuforums.org/showthread.php?t=239338&highlight=gnome+keyboard+properties+quit)

i will edit this post when they are re-installed to let you know if it worked :)

***edit*** well the re-install of the gnome stuff sort of worked, it removed the computer icon and garbage bin icon from the desktop and re-enabled my keyboard preferences so i could set the repeat keys again. However, still can't ALT+TAB though.. i remember when i first installed i couldn't either, then i tried installing beryl which didn't work although after that i could ALT+TAB.....?? I'm very confused at the moment, to say the least... Still can't open synaptic from menu either...?

---

### Post by aysiu on 2007-02-18
I have no idea about the Alt-Tab, but...

If you have random icons appearing on your desktop, those can usually be adjusted by going to the Configuration Editor. Alt-F2 ```
gconf-editor
``` Apps > Nautilus > Desktop and uncheck the boxes for showing the computer and trash, etc.

*sudo synaptic* is not the way to go, even though it appears to "work." Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Since the menu items doesn't appear to work, we'll have to use the terminal to diagnose the problem. Can you post (just copy and paste from the terminal to this thread) the output of these two commands when you try to enter your password? ```
gksudo synaptic
``` ```
gksu synaptic
```

---

### Post by adza on 2007-02-18
aysiu, thanks for the help, however this problem has fixed itself... well let me be more frank... my IDE HDD that ubuntu was installed on died yesterday (dead completely... :() so i have re-installed on a new one, just finished getting back up today... i don't think that format/re-install is the best solution for the problem however.. hehe (although it worked for me)

---

### Post by aysiu on 2007-02-18
So *all* the problems are fixed? Synaptic? Alt-Tab?

---

### Post by adza on 2007-02-18
yeah... it appears so, although give me a day or two!! hehe

---

