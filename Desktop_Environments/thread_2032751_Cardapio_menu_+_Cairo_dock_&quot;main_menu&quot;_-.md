---
title: "Cardapio menu + Cairo dock &quot;main menu&quot; -problems."
date: 2012-07-24
forum: Desktop Environments
---

### Post by Janiporo on 2012-07-24
First of all, I would use Cairo's own "main menu"-launcher, but it is buggy, sometimes opens correct, other times opens incorrectly and there appears scrollbars at the top and bottom.

Solution for me would be using Cardapio-menu. I have installed it with following method:
```
sudo add-apt-repository ppa:cardapio-team/unstable
sudo apt-get update
sudo apt-get install cardapio cardapio-gnomeshell    

```

But it does not launch. Icon is there, when clicked it just jumps (like it is supposed to), but nothing else happens.

Some information here, but none of them concern Cairo dock --> [https://launchpad.net/cardapio](https://launchpad.net/cardapio)

Any great ideas?


EDIT: It launches when I type "Cardapio" to terminal, but starts up slowly.

---

### Post by Janiporo on 2012-07-25
I also have installed the following packages:
blt
cardapio-gnomepanel
python-keybinder
python-tk
tk8.5

Somewhere they said its working depends on some gnome-things, and I do not know which ones.

Any ideas at all?

---

### Post by Janiporo on 2012-07-26
Now I did custom launcher for it, works okay, but is at the middle of the screen. Just figuring it out.

---

### Post by Janiporo on 2012-07-26
It does not work properly with custom launcher, and I can not change its launch position, goes always in the middle of the screen. Tried compiz "Place windows", did not work.

Still no ideas, people?

Is there anyone that has working Cardapio menu + Cairo dock + Xubuntu ?

---

### Post by Janiporo on 2012-07-29
Opened a thread in launchpad --> [https://answers.launchpad.net/cardapio/+question/204300](https://answers.launchpad.net/cardapio/+question/204300)

This does nearly the trick (try in terminal If you like):
```
cardapio show-near-mouse
```


*monologue*

---

### Post by tdlam on 2012-09-24
ummm all this is nice and all including the link you sent but NONE of it addresses the issue...that being that Cardapio wont appear where we need it...which is at the menu button. The problem is still not solved and it appears the folks on the Cardapio link you sent are not willing or don't care to address it = FAIL@ Cardapio folks.
weird...its a nice menu system but patently broken in my opinion. I mean what is the use of posting all that info on their site about how to set it up then folks are having these problems and they don't even seem to want to deal with it? Just a sloppy work around?

---

### Post by Fady10 on 2012-09-24
before starting ubuntu select ubuntu 2D from your log in screen

---

