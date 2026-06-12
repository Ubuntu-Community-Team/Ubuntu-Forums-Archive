---
title: "unity-scope-calculator in 13.10 - step down from 13.04 and scopes ppa"
date: 2013-10-30
forum: Desktop Environments
---

### Post by VaclavC on 2013-10-30
I used calculator scope in previous versions and, by my opinion, it is really handy. But new (official) implementation in 13.10 seems to me much worse. Mostly it does not work at all when I type some formula, I must click on 'Calculator' in 'Filter results'. It is also much slower now, older implemetation from Scopes Packagers ppa was instant. And when I press enter on the result, gnome-calculator is started. Old behavior, when the result was copied to clipboard, was much better.

In short, we have now official calculator scope, but it lost all its usability. Is there any way how "reconfigure" it to old speed and behavior?

---

### Post by grahammechanical on 2013-10-30
I have never used scopes in that way but the other day someone was asking about the weather scope and how it defaults to cities in the USA. I found that filtering by weather would produce results for non USA locations. For example, Birmingham UK and filter by weather would give results for Birmingham UK and not Birmingham US.

Someone else pointed out that weather:Birmingham UK was the way to search. It seems that the colon ( : ) does the same as using the filter option. It works with the calculator as well.
 
calculator:100/5  gives a search result of 25. Does that give you your usability back?

Regards.

---

### Post by VaclavC on 2013-10-30
A bit. Type "calculator:" is too long, it needs something shorter ("calc:" for example). This solves first two problems. But the last problem remains: when I press enter, it starts gnome-calculator instead of storing result in clipboard. This is useless. When I want to work with gnome-calculator gui, I'll run it. When I use calculator scope, I need to do some quick calculation and paste its result somewhere. I don't see any reason why to run gnome-calculator gui when I already have my result.

---

### Post by mc4man on 2013-10-31
> **VaclavC said:**
> A bit. Type "calculator:" is too long, it needs something shorter ("calc:" for example). This solves first two problems. But the last problem remains: when I press enter, it starts gnome-calculator instead of storing result in clipboard. This is useless. When I want to work with gnome-calculator gui, I'll run it. When I use calculator scope, I need to do some quick calculation and paste its result somewhere. I don't see any reason why to run gnome-calculator gui when I already have my result.
Seems reasonable , as far as calc: testing the waters here
[https://bugs.launchpad.net/ubuntu/+source/unity-scope-calculator/+bug/1246601](https://bugs.launchpad.net/ubuntu/+source/unity-scope-calculator/+bug/1246601)

Maybe file a bug about no means to copy results out from the scope directly.

---

### Post by VaclavC on 2013-10-31
Filled this bug:

[https://bugs.launchpad.net/ubuntu/+source/unity-scope-calculator/+bug/1246636](https://bugs.launchpad.net/ubuntu/+source/unity-scope-calculator/+bug/1246636)

And why we must write calculator: or calc: or whatever? Why it is not working like before? Version from Scopes Packagers PPA was simple and powerful (one can say 'perfect'), I don't understand, why they changed it. Is there some reason emereged from Unity changes?

---

### Post by timshel862 on 2014-02-04
I agree completely that the new version has lost a lot of usability. Whenever I type a calculation, online results arrive and are presented before than the calc result, which makes no sense. Local search should always come first, and fast.
I have another question regarding functionality: one cannot type formulas starting with parenthesis, can they? So (2+2)*2 doesn't give any result, but 2*(2+2) does. Any ideas if this is a bug?

PD: Also, if I deactivate online search in privacy and I type a formula to get faster results, the dash gives me nothing. I have to manually hit the filter button and activate the info plugin to get any result. Is there a way to always activate a filter? And to give preference to a search plugin before others?

Thanks!

---

### Post by VaclavC on 2014-02-04
Sometimes I don't even get an application as result, I must manually click to "Applications" filter. I like Unity concept, but in 13.10 it lost much of its usability.

---

### Post by grn on 2014-03-02
Hi VaclavC,

Could you find a way to resolve this issue? I suffer the same. unity-scope-calculator is one thing that I had gotten extremely used to. But the lag now is impractical.

---

### Post by VaclavC on 2014-03-02
Hi grn, click on affected in related bug report ([https://bugs.launchpad.net/ubuntu/+s...r/+bug/1246636]("https://bugs.launchpad.net/ubuntu/+source/unity-scope-calculator/+bug/1246636")) to increase its priority (a bit ;-). I don't know how to write or modify unity scopes right now. It shouldn't be too difficult, but I don't have any time to inspect it.

---

