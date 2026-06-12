---
title: "How to make Beryl start when I boot my machine?"
date: 2007-11-04
forum: Desktop Environments
---

### Post by Ruslan Auroville on 2007-11-04
Hi,
I would like Beryl to start when I boot my computer. I'm using Kubuntu/KDE. Can anyone help?
Thanks.

---

### Post by bingoUV on 2007-11-04
> **Ruslan Auroville said:**
> Hi,
I would like Beryl to start when I boot my computer. I'm using Kubuntu/KDE. Can anyone help?
Thanks.

Try this
```

ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager

```

---

### Post by Ruslan Auroville on 2007-11-04
Thank you BingoUV! Now Beryl manager starts when I boot. But it seems there is still one thing that needs to be done in order to make Beryl Window Manager be operational at a startup. 
Now After I used the command you suggested I can see that Beryl Manager active on the panel, but when I right-click on the icon and point at Select Window Manager it shows me that there is by default KWin marked. Is it possible to change it and make instaed Beryl there by default?
Thanks.

---

### Post by Ruslan Auroville on 2007-11-04
Please, ignore my previous question. Everything runs well.
Thanks again, bingoUV!

---

### Post by Ruslan Auroville on 2007-11-04
Ooops... mistake! Beryl Window Manager still does not start when I boot the machine. So, my previous question still stands. Sorry for confusion.
Solution will be appreciated.
Thanks

---

### Post by bingoUV on 2007-11-04
Does it never start automatically, or it starts sometimes?

For me it sometimes does not start, so I click on beryl icon, and make beryl my window manager. Does this work for you? I do not know the complete solution.

---

### Post by Ruslan Auroville on 2007-11-04
Yes, it is like that - sometimes it starts automatically, and sometimes - not. And I have started doing the same thing as you do to make it work when it doesn't start.
I also got a bug today - telling that there is something wrong with Aquamarine KDE Decorator, which I'm using with Beryl. I'm going to submit the bug, perhaps these things are connected? Let's see what comes out of it...
Which decorator are you using?

Thanks again bingoUV.

---

### Post by bingoUV on 2007-11-04
> **Ruslan Auroville said:**
> Yes, it is like that - sometimes it starts automatically, and sometimes - not. And I have started doing the same thing as you do to make it work when it doesn't start.
I also got a bug today - telling that there is something wrong with Aquamarine KDE Decorator, which I'm using with Beryl. I'm going to submit the bug, perhaps these things are connected? Let's see what comes out of it...
Which decorator are you using?

Thanks again bingoUV.

I use gnome, with emerald themes. Seems like beryl issue. 

For me, it mostly works (85% of times). What is your success rate?

---

### Post by Ruslan Auroville on 2007-11-05
For me it works automatically in about 20% cases or one out of five.

---

### Post by stinger30au on 2007-11-05
i need to find the answer myself.

i have got Ubuntu Ultimate 1.6 and have enabled Beryl.i would like it to start on default.

in the past to cure stuff like that when the program is running i have cloed all windows and done this


system->perferences->session

and save current session.

works for my gdesklet stuff

but not beryl :-(

---

### Post by stinger30au on 2007-11-05
SOLVED!!!

heres what i have done and restarted my pc a few times.

system-preferences-session

go to startup programs and click the add button

in there put this

beryl-manager in the name,command,comment section

then go to the last tab that says "session options"

click on save session

restart. done

---

