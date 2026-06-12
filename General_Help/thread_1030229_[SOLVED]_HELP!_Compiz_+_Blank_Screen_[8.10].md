---
title: "[SOLVED] HELP! Compiz + Blank Screen [8.10]"
date: 2009-01-04
forum: General Help
---

### Post by Schok on 2009-01-04
I just installed ccsm [compizconfig settings manager?] and was turning on some of the effects and when i came to "bicubic filter" (i think) the screen stuck, and then it went blank with some graphic glitches. But i can still see and use the mouse.
How do i disable compiz if i cant see anything?

ubuntu 8.10 on a Genuine Intel CPU T1350 @ 1.86GHz, Mobile Intel 945GM Express Chipset Family

Any help is appreciated!

---

### Post by Forlong on 2009-01-04
> **Schok said:**
> How do i disable compiz if i cant see anything?
1.) (While in the garbled GNOME session) hit [Ctrl]+[Alt]+[F1]

2.) Log in to your account in the text console

3.) Run ```
DISPLAY=:0.0 metacity --replace

```
4.) Go back to your graphical interface via [Alt]+[F7]

---

### Post by fela on 2009-01-04
If you can't see anything, you can go to a virtual terminal (Ctrl + Alt + F1), log in with your details and issue the following command:

```
killall compiz
```

(You can try compiz.real instead but I'm not sure). Compiz should be configured to fall back to metacity, but you could end up with no window borders until you log back in again. I'm sure there's an easier and better solution to this, but I'm just telling you what I'd probably do! :P

---

### Post by fela on 2009-01-04
> **Forlong said:**
> 1.) (While in the garbled GNOME session) hit [Ctrl]+[Alt]+[F1]

2.) Log in to your account in the text console

3.) Run ```
DISPLAY=:0.0 metacity --replace

```
4.) Go back to your graphical interface via [Alt]+[F7]

Ahhhh, so that's how you select which display to use while in a virtual Terminal. Thanks alot!

---

### Post by Schok on 2009-01-04
That was fast!! thanks so much, IT WORKED! i just started using ubuntu and managed to convince my dad to use it..and going to spread around the word that ubuntu is the BEST!

long live ubuntu~

---

### Post by fela on 2009-01-04
> **Schok said:**
> That was fast!! thanks so much, IT WORKED! i just started using ubuntu and managed to convince my dad to use it..and going to spread around the word that ubuntu is the BEST!

long live ubuntu~

Yes, long live Ubuntu!!! Totally!:popcorn:

---

