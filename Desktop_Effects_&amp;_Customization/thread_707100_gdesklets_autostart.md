---
title: "gdesklets autostart"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by CasPol on 2008-02-25
Hi there;

I have installed gDesklets, and woukd like it ot auto-start when I start Ubuntu. I have tried this using the sessions manager but no luck...

Can ayone help ?

---

### Post by RottenBananas on 2008-02-26
Hey,
I had a hard time with Gdesklets too, If i went into Preferences and Sessions and added gdesklets to the command i had no luck. I also tried gdesklets start but that didnt work either.

What i use is the command gdesklets shell...what sucks is the shell opens as well with the desklets...so every time i start up i have to close the gdesklet window that pops up. But it does get my desklets to show up. So give that a shot until someone else can fix our problem.

-Bananas

---

### Post by CasPol on 2008-02-26
Thanks, that does indeed work !!

Anyone out there who can take this further and help us get rid of the shell screen appearing at the gDesklet auto-start ??

Thanks !

---

### Post by sheazar on 2008-02-26
Try System > Settings > Session, then add a startprogram with the command: gdesklets. Works for me :)

Edit: So if your using the advice from above just remove the word shell from the command.

---

### Post by CasPol on 2008-02-26
Tried that before .... does not work ...pitty ....

---

### Post by RottenBananas on 2008-02-26
It is weird...since i have ubuntu gutsy on my laptop and my desktop...the command gdesklets works on my desktop but not on the laptop. I have to use gdesklets shell. Same exact ubuntu cd used to install on both machines...who knows :confused:

---

### Post by alzan on 2008-03-11
Just add 

```
gdesklets start
```

and the shell will not be executed

---

