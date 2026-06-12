---
title: "AWN Error =/ (slight noob)"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by sKaD on 2007-10-30
[IMG]http://img89.imageshack.us/img89/6347/screenshotbm2.png[/IMG]

I ran compiz in the terminal, but nothing much came from it:

[img]http://img502.imageshack.us/img502/4725/screenshot1lw0.png[/img]

=/ please help :(

---

### Post by MrFSL on 2007-10-30
Which distribution of Ubuntu are you using? Feisty? Gutsy?

What graphics card or chip do you have? Nvidia? ATI? Intel?

You have to get a composite desktop manager started before you can use awm; and that means knowing where we are starting.

---

### Post by sKaD on 2007-10-30
I'm using Gutsy and I have an ATI chip (ATI Radeon Xpress 1150 Series), it's on my laptop (Gateway MA3) =/

Thanks for the reply :)

---

### Post by MrFSL on 2007-10-30
First you will have to make sure that 3D drivers are configured for your graphics chip. This might help:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Next you will need to start compiz. Might I suggest:
```
compiz --replace
```

Finally start awm.

---

