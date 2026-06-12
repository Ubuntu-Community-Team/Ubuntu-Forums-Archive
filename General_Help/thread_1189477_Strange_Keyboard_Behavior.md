---
title: "Strange Keyboard Behavior"
date: 2009-06-16
forum: General Help
---

### Post by HunterThomson on 2009-06-16
Thank you for your time.

This is about a friends Ubuntu Laptop I installed Ubuntu on but manage through SSH. So, I will not be able to give as much detail as I would like.

It seems her keybord mapping got messed up somehow. Most of the keys mean the same but some of the keys do strange things.

Here is a direct quote form the email resposes I got form her.



> I did do a bunch of updates before but I don't think it was immediately before.  I was listening to music, then I shut down my computer for the night.  then I turned it on and the problem manifested.  Only one key changes.  F somtimes equals fasd, and sometime  ;jkl .  Y = Y>; then turn caps on.  G = g> then it disappears and directs me to username.There might be one or two nore changes but I can't remember

> I boot upon i hit y and it prints Y-> then turns on caps.  It does this no matter how many times you boot up.  the F button however, changes to fasd or ;jkl randomly, independent of booting up

To make it more clear. When she presses the "f" key one time. It will print ";jkl" or "fasd".

I was thinking of defineing the keyboard layout in xorg.conf but it seems to me that it is a bug or some application is doing it. So, a modification to xorg.conf would not work if it is another application that is changing the keys.

Any Ideas would be vary helpfull.

---

### Post by Toadmund on 2009-06-16
I would write 'e' and got 'we', I would type 'c' and got "xc"

New keyboard solved the problem.

I tried taking it apart and cleaning with rubbing alcohol and fixed it, but the old membrane was finicky and soon got worse.

Try another keyboard and see if it is just a crapped out keyboard.

---

### Post by HunterThomson on 2009-06-16
> **Toadmund said:**
> I would write 'e' and got 'we', I would type 'c' and got "xc"

New keyboard solved the problem.

I tried taking it apart and cleaning with rubbing alcohol and fixed it, but the old membrane was finicky and soon got worse.

Try another keyboard and see if it is just a crapped out keyboard.

Right on. It's and old dell laptop. Ya it dose seem like it may be a hardware problem. If her comptuer started printing chinese characters or the layout changed and stayed changed in the same way I would say software. I'll tell her to plug in a keyboard form here desktop and see if that helps. If it dose then ya it is a hardware problem. Thanks for the idea. I didn't think of that. A fresh mind always seems to help. I'm thinking software all the time and forgot about hardware :P

---

### Post by HunterThomson on 2009-06-23
Ya I was just dumb. It was the keyboard that was broken.

Thanks aging for the fresh perspective of the problem :)

---

