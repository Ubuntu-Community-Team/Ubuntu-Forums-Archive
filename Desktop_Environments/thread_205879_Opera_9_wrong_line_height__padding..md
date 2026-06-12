---
title: "Opera 9 wrong line height / padding."
date: 2006-06-29
forum: Desktop Environments
---

### Post by daiwai on 2006-06-29
I am using Opera 9 shared QT on Kubuntu. On some sites there is a wrong line height. This happens on wikipedia for example. The static QT version does not have this problem.

For a screenshot please see:
[http://my.opera.com/community/forums/topic.dml?id=141272](http://my.opera.com/community/forums/topic.dml?id=141272)

Any ideas what may cause this problem? Is that a problem/bug of Opera or Kubuntu/QT?
Thanks!

---

### Post by daiwai on 2006-07-02
Anybody? :confused:

---

### Post by dpaint4 on 2006-07-02
Are you sure you're not just unused to the way Opera renders padding and line-height? Opera's CSS compliance is very very strict and often sites will appear 'broken' in Opera when the only real issue is that they're badly coded or non-compliant sites.

So I guess I'm asking, are you comparing this rendering problem to a previous satisfactory Opera install, or some other browser that you like?

If you're already used to Opera and this is a new issue, then I'm stumped becaus Opera's rendering has always been completely universal for me, and as a web designer, I like Opera because it's the number one browser to open up if I want to see all of my mistakes violently rendered in the absolute most horrifying way.

---

### Post by daiwai on 2006-07-02
Thank you for your reply. 

I am comparing my 8.54 install with the current version 9 (version 9 is not installed via apt, it was just extracted in a folder and run from there). As I said in my first post, the problem only occurs with the shared QT version. If I understand it correctly that version uses the QT librariers  installed with Kubuntu instead of Opera's, so my guess was that there is something wrong/different with Kubuntu's QT libraries (at least when used by Opera 9).

I can now also describe the problem more precisely: the problem occurs when relative units (em) are used for specifying the line height in CSS. Opera doesn't seem to honor the value behind the decimal point in that case. On the Wikipedia pages, for example, they use a line-height of 1.5em for normal text. However Opera 9 (shared QT on Kubuntu) renders it like 1.0em. 

Attached is a screenshot of this page [http://daiwai.de/test/lineheight.html](http://daiwai.de/test/lineheight.html) is rendered by my Opera 9.

---

### Post by daiwai on 2006-07-11
Any ideas?

---

### Post by daiwai on 2006-07-27
I found an issue that could probably be related.

Konqueror (3.5.3 on Kubuntu) doesn't seem to take decimals into account when doing calculations in JavaScript.

For example:

```

    var num = 28.453;

    var result = Math.round(num * 100) / 100 ); // result should be 28.45

```

please see [http://daiwai.de/test/jsdecimals.html](http://daiwai.de/test/jsdecimals.html) for a test case.

in both Opera 9 shared QT and Konqueror the result is 28. In Firefox correctly calculates 28.45.



Can anyone confirm this behaviour?
Thanks.

---

### Post by daiwai on 2006-07-29
Wow, I thought there might be some people who have either Opera or Konqueror available on their Kubuntu. :confused:

---

### Post by woobit on 2006-07-29
My Opera 9 Build 344 gives me:

28.453 rounded to 2 decimals is 28.45 (should be 28.45)

If that helps

---

### Post by daiwai on 2006-07-29
Thanks, are you using the shared or static qt version? 

Do you get the same result in Konqueror?

---

### Post by Kræn Knude on 2006-08-01
I have the same problem and it seems to me that your explanation is very good, but how do we fix it?

Wikipedia is almost impossible to read right now because of this :(

*edit* - seems like someone found a solution: [http://ubuntuforums.org/showthread.php?t=202030&highlight=opera+kubuntu](http://ubuntuforums.org/showthread.php?t=202030&highlight=opera+kubuntu)

Haven't tried it myself yet

---

### Post by daiwai on 2006-08-01
I found a solution on the Opera forums [http://my.opera.com/community/forums/topic.dml?id=144404](http://my.opera.com/community/forums/topic.dml?id=144404)

You just have to purge the **scim-qtimm** package. Unfortunately kubuntu-desktop depends on that package, so it has to be removed, too, but I don't think this is a problem on a stable Kubuntu version.

```

sudo apt-get remove kubuntu-desktop
sudo dpkg --purge scim-qtimm

```

---

### Post by Kræn Knude on 2006-08-02
It works wonderfully!

Thanks a lot. This has been a problem for me for quite a while now (well since opera9).

---

