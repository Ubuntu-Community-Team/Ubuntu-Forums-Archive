---
title: "dell 6400 emerald theme"
date: 2007-10-19
forum: Dell  Ubuntu Support
---

### Post by aryan_dear on 2007-10-19
Hi,
I have Dell 6400 with ATI x1400. I installed the ubuntu using DVD from [http://mylittleubuntuguide.com](http://mylittleubuntuguide.com)

Beryl is working beautifully on my Dell. But I am unable to apply any emerald theme. I try downloading new themes and applying but nothing gets applied.

Can someone please guide me how to apply these themes for my Dell..

Thanks,
Prateek

---

### Post by ionman on 2007-10-20
It sounds like Beryl might still be using metacity themes, rather than emerald.

Personally I would recommend using Compiz-Fusion rather than Beryl. Beryl was a fork of Compiz, which has now been discontinued. Compiz-Fusion is the name of the project which is porting all (or most) of the Beryl plugins to Compiz now.

If you use compiz, and install compizconfig-settings-manager there is an option under the window decorations plugin to use a different window decorator. In this textbox you want to type

emerald --replace

Hopefully this is helpful!

- ionman

---

