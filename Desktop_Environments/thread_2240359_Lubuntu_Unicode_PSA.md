---
title: "Lubuntu Unicode PSA"
date: 2014-08-19
forum: Desktop Environments
---

### Post by fireflower on 2014-08-19
Was going to post the solution to this problem in the relevant thread, only 3 weeks old, but it was closed. And at that, it was closed without a true solution being posted. I figured it out on my own, and wanted to post the solve. Posting a couple hyperlinks with information that doesn't actually help and no explanation is not a solution!

How to unicode in Lubuntu: Press CTRL+SHIFT+U, *then let go of the keys,* type the code, and press SPACEBAR.

How to unicode in the other 4 distros I tested: Press CTRL+SHIFT+U, type the code, and press SPACEBAR.

Example: u0394 is the unicode for the Greek &#916; (delta) symbol. Comes in handy in Kerbal Space Program, as in "&#916;v". If you attempt to type this in any other DE, distro or OS I have ever used, it works fine holding down the three keys to proc the code while typing the code. But for whatever reason Lubuntu wants to be special. "[Mary Lou]("http://tvtropes.org/pmwiki/pmwiki.php/Main/MarySue")-buntu", if you will. If you try it the "normal" way, you get some bizarre output like _u)#($_ which will then disappear when you hit SPACEBAR rather than render &#916;.

---

### Post by bandjc on 2014-12-04
Doesn't work for me. I have yet to crack this with Lubuntu. 

Could this be FUBARed because I have set dead keys for typing accents?

---

### Post by bandjc on 2014-12-05
Aha! Two Input Methods running! Get rid of xim, set ibus as default, Fireflower's method works PERFICK.

---

