---
title: "Beryl doesn't work"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by miLl3niUm on 2007-06-30
I installed these packages:
beryl
beryl-manager
emerald
emerald-themes

My questions:
1. When I start beryl manager I can see it on tray but I can't enable Beryl. How do I enable it?
2. How can I apply a theme from emerald theme manager? I click on any of them but nothing happens.

---

### Post by thecommodore on 2007-06-30
Yesss, I have that exact same problem.

Except, I just went to Terminal and typed in:

```
$ beryl
```

My screen flickered and the title bars disappeared and it froze.

Any help?

---

### Post by miLl3niUm on 2007-06-30
Same here, I press Alt+F2, type "beryl" but the screen looks weird and I restart my computer.

---

### Post by miLl3niUm on 2007-06-30
Anyone?

---

### Post by crimesaucer on 2007-06-30
This is the guide you want to follow: [http://wiki.beryl-project.org/wiki/Support_for_ATI_cards](http://wiki.beryl-project.org/wiki/Support_for_ATI_cards)

The Beryl site is working now...you might also want to check out Compiz Fusion...I used to use Beryl, now I'm running Compiz Fusion and it works really nicely so far. Plus it was really easy to install from the stickied post above.

---

### Post by miLl3niUm on 2007-07-01
How do I enable it? I select it from the window manager but no effects are applied.

EDIT: (Compiz Fusion)

---

### Post by miLl3niUm on 2007-07-01
In that page it says:
> Please make sure your card is supported for accelerated graphics. In a terminal type:

glxinfo | grep direct

If you get this output back, your card should work:

direct rendering: Yes

If you get a "no" from this test, please install the correct driver. 

I get "no" and I have to do this:
> Use the Feisty's RestrictedDriversManager to install the Graphics card drivers.

When I click that I get:
> Your hardware does not need any restricted drivers.

---

### Post by miLl3niUm on 2007-07-01
Come on!

---

