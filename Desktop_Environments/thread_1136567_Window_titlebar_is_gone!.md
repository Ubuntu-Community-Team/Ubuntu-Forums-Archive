---
title: "Window titlebar is gone!"
date: 2009-04-25
forum: Desktop Environments
---

### Post by LongMan[RUS] on 2009-04-25
Hi!

After update to 9.04 and manipulations with UNR i have all windows opening in fullscreen mode and without titlebar (line with window name).

It is not user-dependent. Recently created users have the same problem?

How can i return the default behavior?

Thaks in advance!

P.S. Netbook remix is uninstalled now.

---

### Post by andrea000 on 2009-04-25
Is it the windows boarder or gnome?Mine just did 
the same thing try ctrl+alt+backspace and see if 
that fixes it it did mine but i'm on 8.10 Intrepid

---

### Post by LongMan[RUS] on 2009-04-25
> **andrea000 said:**
> Is it the windows boarder or gnome?Mine just did 
the same thing try ctrl+alt+backspace and see if 
that fixes it it did mine but i'm on 8.10 Intrepid

ctrl+alt+backspace no more works in 9.04

It doesnt matter what the border is - i can change theme, but windows still opened in fulscreen :-(

---

### Post by ninjapirate89 on 2009-04-25
The only thing I can think of that may be your problem is if you have the CompizConfig Settings Manager installed and have unchecked Window Decoration. Have you been playing with the Compiz effects recently?

---

### Post by LongMan[RUS] on 2009-04-25
> **ninjapirate89 said:**
> The only thing I can think of that may be your problem is if you have the CompizConfig Settings Manager installed and have unchecked Window Decoration. Have you been playing with the Compiz effects recently?

I wanted, but i havent drivers for it. I cant turn on visual effects :-(

---

### Post by andrea000 on 2009-04-25
> **'LongMan[RUS] said:**
> ctrl+alt+backspace no more works in 9.04

It doesnt matter what the border is - i can change theme, but windows still opened in fulscreen :-(

Sorry like i said i'm on 8.10 so i dont know the changes they made in 9.04

---

### Post by ninjapirate89 on 2009-04-25
> **'LongMan[RUS] said:**
> I wanted, but i havent drivers for it. I cant turn on visual effects :-(

I'll see if I can Google something that may help.

---

### Post by LongMan[RUS] on 2009-04-25
> **ninjapirate89 said:**
> I'll see if I can Google something that may help.

I already googled and found nothing, but thank you very much. I apreciate that :-)

(sorry for my English)

---

### Post by ninjapirate89 on 2009-04-25
Try opening a terminal and typing in ```
gtk-window-decorator
```

---

### Post by ninjapirate89 on 2009-04-25
> **'LongMan[RUS] said:**
> I already googled and found nothing, but thank you very much. I apreciate that :-)

(sorry for my English)

I didn't even notice.

---

### Post by LongMan[RUS] on 2009-04-25
> **ninjapirate89 said:**
> Try opening a terminal and typing in ```
gtk-window-decorator
```

Nothing happened... I am going to reinstall Ubuntu :-(

Thank you very much for you time and attention.

---

### Post by LongMan[RUS] on 2009-04-25
OMIGOD! Solved!

sudo apt-get remove maximus

---

### Post by ninjapirate89 on 2009-04-25
Sorry again I couldn't be of more help, but I'm glad to hear your issue was resolved.

---

### Post by kiwikat on 2009-04-27
> **'LongMan[RUS] said:**
> OMIGOD! Solved!

sudo apt-get remove maximus

Thanks a TON for that.  It was literally killing me and my eee. :KS

---

### Post by moddedcomputers on 2009-05-02
> **'LongMan[RUS] said:**
> I already googled and found nothing, but thank you very much. I apreciate that :-)

(sorry for my English)
compiz is only partly installed, on a stock install. Open synaptics package manager, search for compiz.  You need "Compiz Fusion Icon" or Compiz icon. Also might look at Emerald theme manager. It does the window decoration.
~Mike~

---

### Post by shakma on 2010-09-16
w00t!  You're the man, longman.  I know this thread is a year old, but me and MY eeepc were about to re-install Ubuntu, too.  I went through the exact same process you did.  Netbook Remix is not for me, but it just didn't want to go away!

Thanks again.

Peace.

---

