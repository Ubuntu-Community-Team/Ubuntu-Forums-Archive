---
title: "Rendering of code tags"
date: 2013-03-11
forum: Forum Feedback &amp; Help
---

### Post by r-senior on 2013-03-11
Is there an option for "only show scrollbars where necessary" that could be turned on in this new version of the board? I'm fairly sure the old version didn't add all these distracting scrollbars?

For example:

[http://ubuntuforums.org/showthread.php?t=2124013&p=12553113#post12553113](http://ubuntuforums.org/showthread.php?t=2124013&p=12553113#post12553113)

---

### Post by CharlesA on 2013-03-13
Not sure, but I'm pretty sure it can be fixed via CSS.

---

### Post by coffeecat on 2013-03-14
> **r-senior said:**
> I'm fairly sure the old version didn't add all these distracting scrollbars?

The pre-upgrade version did show the horizontal scrollbars in the same way *in Firefox*. A horizontal scrollbar is shown where there is a very long line in order to prevent wrapping of the line. It probably would be possible to prevent the appearance of horizontal scrollbars by allowing line wrap, and another forum software, phpbb, does in fact do that. But that makes the rendering of code confusing or even misleading, by giving the visual appearance of newlines where there are none. 

Vertical scrollbars are added when there are more than 30 lines, and this also is unchanged from pre-upgrade.

**EDIT:** I've amended the above to be clear that it applies to Firefox. I've discovered that in Chrome or Chromium in Ubuntu, the code box in the post you link doesn't add a horizontal scrollbar but wraps the line according to the width of the browser window. If I make the browser window very narrow, it wraps the line into 4 lines and also adds a vertical scrollbar. Which way of rendering code boxes is to be preferred would be a matter of debate, I guess. I'll check what happens in other browsers.

---

### Post by coffeecat on 2013-03-14
> **coffeecat said:**
> I'll check what happens in other browsers.

Safari 5.1.7 and Internet Explorer 9 behave the same way as Chrome/Chromium. In brief: no horizontal scrollbar and wraps long lines. Firefox, in contrast, preserves the integrity of long lines of code at the expense of adding a horizontal scrollbar.

---

### Post by CharlesA on 2013-03-14
> **coffeecat said:**
> Safari 5.1.7 and Internet Explorer 9 behave the same way as Chrome/Chromium. In brief: no horizontal scrollbar and wraps long lines. Firefox, in contrast, preserves the integrity of long lines of code at the expense of adding a horizontal scrollbar.

Huh. That makes me wonder if Firefox is the odd man out when it comes to rendering pre tags, even when they are styled a specific way with CSS.

I noticed the same thing with my site when I wanted the horizontal scroll bar instead of having the code wrap, but the only way I got it to work was to use p tags with a specific class instead of pre tags, even though the css was the same.

Thanks for checking into it. :)

---

### Post by r-senior on 2013-03-15
Thanks for looking into it. I've just looked at that link again and the scrollbars have gone. Same machine, same browser (Chromium).

When I was looking at it the other evening, the text was wrapped and had both vertical *and* horizontal scrollbars. Scrolling vertically was necessary to see all the text. I should have taken a screenshot but I didn't.

I'm going to mark as solved in the sense that the problem has disappeared for me. I was on a hotel WiFi at the time but I can't see how that would have affected it.

---

