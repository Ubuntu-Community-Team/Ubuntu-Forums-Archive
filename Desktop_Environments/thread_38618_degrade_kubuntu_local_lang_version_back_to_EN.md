---
title: "degrade kubuntu local lang version back to EN"
date: 2005-06-01
forum: Desktop Environments
---

### Post by jayprakash on 2005-06-01
I've installed kubuntu and I wanted to try it in Czech. But I found out that the translation is absolutly terrible. (No offence, I'm very thankfull for all that work on ubuntu but local versions are not ready.)

please, what all should I do (unninstal/reinstal) to get the orriginal EN version?
(complete reinstall is not possible any more, it would kill me to do everything again)

Thank you

---

### Post by Mez on 2005-06-01
I'm assuming you can still understand it though... so you can tell where things re?

I hops so!
If you goto Control panel -> Regional and Accessibility -> Country/Region and Laguage

You should hopefully see more than one language listed there

if not, click on add language -> other -> US English

then, select "czech" and click "remove language"

Click "apply" then ok, wait until it applyss it's changes and then hit ctrl+alt+backspace to restart X.

Login, and your labiguage should be english

Now, to complertely remove the Czech langauge use the following code

```
sudo apt-get remove --purge kde-i18n-cs
```

Hope this heelps!

---

### Post by jayprakash on 2005-06-02
tnx,
this helped fer kde...

but here are more applications..
for example firefox, oofice ... 
this i think should be enough to unninstal locale package, right?
But what concerns me the most is terminal in local lang :(, and it is totaly terrible! The worst is MidnightCommander, it's nearly unreadable...

---

