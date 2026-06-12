---
title: "Chrome repeatedly blocks people from posting to this forum"
date: 2018-08-26
forum: Forum Feedback &amp; Help
---

### Post by Paddy Landau on 2018-08-26
Back in March 2017, Google added a new feature to Chrome to prevent XSS attacks. Unfortunately, it wasn't well tested, and it caused havoc with vBulletin forums.

Specifically, if your post or PM has a reference to another thread in the same forum, when you "Preview Post" or "Preview Message", Chrome raises the entirely misleading and highly frustrating error:
> This page isn’t working
Chrome detected unusual code on this page and blocked it to protect your personal information (for example, passwords, phone numbers and credit cards).
(I got the same error when trying to post this message because of the link below.)

As you probably know, Google is highly unresponsive to bug reports, and has marked the bug report on its own site as "won't fix".

The solution (which is really a workaround) is:
> Please add this HTTP Header Field: x-xss-protection: 0
Details: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-XSS-Protection
I [raised this]("https://ubuntuforums.org/showthread.php?t=2355209") back then, and [reported a bug]("https://rt.ubuntu.com/Ticket/Display.html?id=29781") as requested, but it's over a year later and this problem still hits. It gives a bad impression to Chrome users, who think that the fault lies with Ubuntu Forums and not Google.

Could this issue be raised a level, please?

---

### Post by Paddy Landau on 2018-12-27
I wonder if this could be looked at, please? It's been a while now, and it still causes problems. (In fact, submitting this thread gave the problem.)

Information:
[LIST]
[*][Original Ubuntu Forums thread]("https://ubuntuforums.org/showthread.php?t=2355209")
[*][Bug report ticket]("https://rt.ubuntu.com/Ticket/Display.html?id=29781&results=ecd7fb3a131fdba853512e625f6ea834") to Canonical, unanswered
[*][Bug report 706038]("https://bugs.chromium.org/p/chromium/issues/detail?id=706038")
[*][Bug report 702542]("https://bugs.chromium.org/p/chromium/issues/detail?id=702542")
[/LIST]

Summary:
[LIST]
[*]Trying to preview your post when it contains a link back to its own forum causes Chrome to throw a security error.
[*]The solution is for the website (in this case [Ubuntu Forums]("https://ubuntuforums.org/")) to add this header:
[FONT=lucida sans unicode]x-xss-protection: 0[/FONT]
[/LIST]

Thank you

---

