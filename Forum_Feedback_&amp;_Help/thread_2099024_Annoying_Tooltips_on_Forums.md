---
title: "Annoying Tooltips on Forums"
date: 2012-12-28
forum: Forum Feedback &amp; Help
---

### Post by superDave972 on 2012-12-28
Does anybody else find this annoying? Whenever I am browsing the forums and looking for one that interests me, there is a constant, large, tooltip popping up that displays the latest post in the particular thread. 

I like the ability to view the latest post in each thread, but I have always thought tooltips are one of the most annoying features ever developed. Perhaps there can be an option in our profiles to turn them off?

Or, maybe the latest post can be displayed in a status bar on the bottom of the page when the user hovers their mouse over the thread title?

---

### Post by Elfy on 2012-12-28
Nothing in the profile that you can turn off I'm afraid.

You can do it in [firefox]("http://ubuntuforums.org/showpost.php?p=9218153&postcount=2") and [opera]("http://ubuntuforums.org/showpost.php?p=9218652&postcount=7") - I'd hazard a guess that the same is possible in other browsers - but I've no idea about those.

---

### Post by vasa1 on 2012-12-28
You'll see the tooltip if your mouse cursor is over the middle column where the thread title is. Just make sure the mouse cursor isn't there but to the left or right of this column. Then you shouldn't see the tooltip. (I find the facility quite useful.)

---

### Post by haqking on 2012-12-28
You could always not hover over the thread ;-)

The only need to hover over them is to view the tooltip.

You can browse the latest threads without hovering over them and you can click on one to view it without hovering for a tooltip.

I only ever see the tooltip when I want to view the latest post without viewing the thread.

---

### Post by superDave972 on 2012-12-28
> **Elfy said:**
> Nothing in the profile that you can turn off I'm afraid.

You can do it in [firefox]("http://ubuntuforums.org/showpost.php?p=9218153&postcount=2") and [opera]("http://ubuntuforums.org/showpost.php?p=9218652&postcount=7") - I'd hazard a guess that the same is possible in other browsers - but I've no idea about those.

Thank you for this information.  I just switched back to Firefox for this sole reason.
I searched for a long time on how to disable tooltips in Chrome, but apparently, they don't let you do that.  I rarely find myself desiring the use of tooltips. Thanks!

---

### Post by vasa1 on 2013-12-25
> **Elfy said:**
> Nothing in the profile that you can turn off I'm afraid.

You can do it in [firefox]("http://ubuntuforums.org/showpost.php?p=9218153&postcount=2") and [opera]("http://ubuntuforums.org/showpost.php?p=9218652&postcount=7") - I'd hazard a guess that the same is possible in other browsers - but I've no idea about those.

Few days away from "necro" but I just found out how to selectively disable the tooltip OP talks about when using Firefox. Elfy (formerly known as forestpiskie) [posted a solution]("http://ubuntuforums.org/showpost.php?p=9218153&postcount=2") that turns off **all** "chrome" tooltips: toggle "browser.chrome.toolbar_tips" to *false* in about:config.

To turn off just the tooltip previewing the latest post contents, one can use
```
#aHTMLTooltip { display: none !important }
``` in userChrome.css or in a Stylish sheet.

Note that this hack will prevent all tooltips *only* on the webpage itself. The tooltips related to the "chrome" of the browser are unaffected. If you don't want to see any tooltips at all then the "about:config" does that.

---

