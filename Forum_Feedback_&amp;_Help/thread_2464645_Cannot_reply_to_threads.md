---
title: "Cannot reply to threads"
date: 2021-07-07
forum: Forum Feedback &amp; Help
---

### Post by monkeybrain20122 on 2021-07-07
Since the update when I tried to post reply I often get
[h=1]Forbidden[/h] You don't have permission to access this resource.
 [HR][/HR] Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443


This happens sporadically, not sure if this one will get posted.

---

### Post by CharlesA on 2021-07-07
That has happened off and on in the past. Most of the time, you can save your post content and then try again in a little bit and it'll post OK.

---

### Post by monkeybrain20122 on 2021-07-07
> **CharlesA said:**
> That has happened off and on in the past. Most of the time, you can save your post content and then try again in a little bit and it'll post OK.

It seems that using code tags results in error above. Without them it posts ok.

---

### Post by sajoupa on 2021-07-08
Indeed, the PHP tags generated false positives.
It should now be fixed.
[PHP]This could have been real PHP code, but it's just a test.[/PHP]
This was due to having updated security packages on the frontends. In more recent versions, the default configuration and rule IDs were changed, so we lost some customizations.
Sorry for the inconvenience.

--
sajoupa
Canonical IS

---

### Post by yetimon_64 on 2021-07-08
> **monkeybrain20122 said:**
> It seems that using code tags results in error above. Without them it posts ok.

I was getting the same error here about 12 to 14 hours ago with quote tags or when trying to mark multiple posts for quoting. Trying again now here to see if quote tags work properly yet. **Edit**: yes, working now.

---

### Post by guiverc on 2021-07-08
I've had issues last 26+ hours, with & without code tags (but not always; I had no issues posting to tug-of-war but not where it mattered; a Lubuntu thread, or in fact here).

---

### Post by TheFu on 2021-07-08
I'm still seeing problems replying - even in the last 30 minutes.

---

