---
title: "adesklets - any good?"
date: 2005-06-09
forum: Desktop Environments
---

### Post by foxy123 on 2005-06-09
Could anyone who is using it comment on its performance? 

I ahve currently gdesklets installed and it works ok apart from the fact that the python uses 20% of CPU every few seconds, which makes things like screensavers and games jerk every time. It's not a big deal for me, but I would prefer something more optimised.

Another thing is the choice of desklets. I had a look at their official site and I cannot say that I found plenty of them. At least the number is more modest than in gdesklets case.

I am asking it because I have a trouble installing adesklets from apt (some dependency conflict), so I wonder if it's worth hassle to make it work after all.

---

### Post by drummer on 2005-06-09
[QUOTE=foxy123]Could anyone who is using it comment on its performance? 

I ahve currently gdesklets installed and it works ok apart from the fact that the python uses 20% of CPU every few seconds, which makes things like screensavers and games jerk every time. It's not a big deal for me, but I would prefer something more optimised.

Another thing is the choice of desklets. I had a look at their official site and I cannot say that I found plenty of them. At least the number is more modest than in gdesklets case.

I am asking it because I have a trouble installing adesklets from apt (some dependency conflict), so I wonder if it's worth hassle to make it work after all.[/QUOTE]
 I've installed from source after going to the website (couldn't see package in apt) and all went OK after installing libreadline5-dev to satisfy dependency. You also need to do  " ./configure --with-python-force-detection " before compilation for it to work properly. The only problems I have is that I can't see any config applet like gdesklets and can't see how to move/place the desklets where I want on the desktop :(

It doesn't seem as configurable and established as gdesklets, but i guess it's still pretty new and early in development (first release Jan '05) compared to gdesklets.

It does look nice though.. I'm playing with the launcher - yab - atm.. very smooth

---

