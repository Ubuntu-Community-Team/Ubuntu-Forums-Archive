---
title: "Chrome keeps blocking my PM replies"
date: 2017-03-10
forum: Forum Feedback &amp; Help
---

### Post by Paddy Landau on 2017-03-10
When I try to reply to a PM, if I type something wrong, Chrome blocks it.

Unfortunately, I haven't figured out what the "wrong" is, although it seems to be related to the length of the message.

Specifically, I can *Submit Message* (thank goodness), but I can't *Go Advanced* or *Preview Message*.

See the attached screenshot. "This page isn't working. Chrome detected unusual code on this page and blocked it to protect your personal information…"

[ATTACH=CONFIG]274070[/ATTACH]

Any ideas how to fix this? Do we need to post a bug report to Google so that it can be ignored?

---

### Post by slickymaster on 2017-03-10
I don't think that it is Chrome related because I can do all those things on Chrome 57.0.2987.98 (64-bit). Are you blocking javascript?

---

### Post by Paddy Landau on 2017-03-10
> **slickymaster said:**
> I don't think that it is Chrome related because I can do all those things on Chrome 56.0.2924.87 (64-bit). Are you blocking javascript?
No, I allow Javascript. I can't test right now, but I'll retry without any extensions and get back to you. My Chrome version is 57.0.2987.98 (64-bit) (it was updated to 57 earlier today).

It's a bit of trial-and-error because, as I say, it complains only when I do some unspecified wrong thing; other times it works :confused:

---

### Post by Paddy Landau on 2017-03-10
I've just tried posting with all Chrome extensions disabled. Unfortunately, it still happens.

I have a suspicion that it's something to do with the [QUOTE] tag, but I'm not at all certain of that.

---

### Post by slickymaster on 2017-03-10
> **Paddy Landau said:**
> I've just tried posting with all Chrome extensions disabled. Unfortunately, it still happens.

I have a suspicion that it's something to do with the QUOTE tag, but I'm not at all certain of that.

That's odd because I'm not seeing that also.

---

### Post by Paddy Landau on 2017-04-02
I've made some advance on finding out what causes this problem.

This problem happens not only on PMs but also on posting, and a number of other people have reported it on other forums.

It happens, among other places, to sites that use vBulletin — which this forum uses.

I raised a [bug with Chromium]("https://bugs.chromium.org/p/chromium/issues/detail?id=706038"), but unfortunately it is not visible to the general public. I have asked them to make it visible. Their response, however, is "won't fix", because:
> [COLOR=#000000]This appears to be a case where the site owner will need to specify x-xss-protection: 0 heaer [sic] since it is posting HTML back to itself.[/COLOR]
I have [further information]("https://productforums.google.com/d/msg/chrome/4MUJd75N4Jw/Lq1EIoPIAQAJ") from someone else:
> Please add this HTTP Header Field: x-xss-protection: 0
Details: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-XSS-Protection](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-XSS-Protection)
The posted link is worth checking, because it explains the problem and how to solve it.

I wonder if this solution can be implemented on this forum to prevent this problem?

---

### Post by slickymaster on 2017-04-03
> **Paddy Landau said:**
> I've made some advance on finding out what causes this problem.

This problem happens not only on PMs but also on posting, and a number of other people have reported it on other forums.

It happens, among other places, to sites that use vBulletin — which this forum uses.

I raised a [bug with Chromium]("https://bugs.chromium.org/p/chromium/issues/detail?id=706038"), but unfortunately it is not visible to the general public. I have asked them to make it visible. Their response, however, is "won't fix", because:

I have [further information]("https://productforums.google.com/d/msg/chrome/4MUJd75N4Jw/Lq1EIoPIAQAJ") from someone else:

The posted link is worth checking, because it explains the problem and how to solve it.

I wonder if this solution can be implemented on this forum to prevent this problem?

I'd advise you to open a ticket with Canonical IS reagrding this, Paddy?

[https://rt.ubuntu.com/](https://rt.ubuntu.com/)

---

### Post by Paddy Landau on 2017-04-04
Thank you, @slickymaster. I have raised a [bug report]("https://rt.ubuntu.com/Ticket/Display.html?id=29781&results=ecd7fb3a131fdba853512e625f6ea834") as you suggest.

---

