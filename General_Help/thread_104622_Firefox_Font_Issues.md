---
title: "Firefox Font Issues"
date: 2005-12-16
forum: General Help
---

### Post by michaelb on 2005-12-16
Hello,

I recently installed some new fonts, which went smoothly (I can use them in programs such as Gimp). However, now Firefox has started using "Alien" (one of particularly unreadable fonts I downloaded) as its default font. Whenever I try to change the default font in the options menu, Firefox locks up and crashes. No other programs seem to be affected this way. Also, I was careful not to delete or edit any existing fonts when I was installing the new fonts. Is there a config file that I could edit directly to try changing the default font? Is there some other issue? Or should I be posting this at a Mozilla board? ; )

Thanks in advanced!

---

### Post by BrooksOfSheffield on 2005-12-16
In the address bar type

about:config

Scroll down to the section beginning with font.name.<variable>

You can double-click any entry and change the font there.

Hope this helps...

---

### Post by rcerreto on 2005-12-16
Down into  .mozilla/firefox/.../chrome there's a file named  userChrome.css
Edit that file to change the font firefox uses:

* {
   font-size: 10pt !important;  /* change the font size the way you like */
   font-family: "Your preferred font here" !important;
}

HTH

---

### Post by michaelb on 2005-12-17
Thanks for the suggestions! While they did not fix the problem, as I just now discovered that several other programs were exhibiting the same symptoms (namely ZINF and Mozilla), they did remind me of the user chrome file, which is very handy.

I fixed the problem temporarily: I renamed the directory which contained the fonts that I added and restarted FFX. At least I can properly read websites now. It will do for now (and probably for quite some time given my propensity to procrastinate).

Thanks again!

---

