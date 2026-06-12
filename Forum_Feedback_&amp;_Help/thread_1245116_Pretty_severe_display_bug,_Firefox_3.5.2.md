---
title: "Pretty severe display bug, Firefox 3.5.2"
date: 2009-08-20
forum: Forum Feedback &amp; Help
---

### Post by Eisenwinter on 2009-08-20
During the last several days, I've encountered pretty serious display bugs, only in UbuntuForums.

Initially I thought the admins might be testing something, maybe a new script, I wasn't really sure, but now I finally decided to take a screenshot, since it's been going on for like 5 days now.

[_Here_]("http://trashis.alrig.ht/ubuntuforums_display_bug.png") is one form of display bug. This isn't the only one I've encountered.

---

### Post by bapoumba on 2009-08-20
> **Eisenwinter said:**
> During the last several days, I've encountered pretty serious display bugs, only in UbuntuForums.

Initially I thought the admins might be testing something, maybe a new script, I wasn't really sure, but now I finally decided to take a screenshot, since it's been going on for like 5 days now.

[_Here_]("http://trashis.alrig.ht/ubuntuforums_display_bug.png") is one form of display bug. This isn't the only one I've encountered.
Must be something on your end. Try clearing the cache. Have you set up some special fonts or preferences ?

---

### Post by nomnomnom on 2009-08-20
> **bapoumba said:**
> Must be something on your end. Try clearing the cache. Have you set up some special fonts or preferences ?

I've had similar issues too.

---

### Post by bapoumba on 2009-08-20
> **nomnomnom said:**
> I've had similar issues too.

Hmm, in that case, when it happens, please take a screenshot and note (bottom right of the page) if you are on lingonberry or billberry. Thanks.

---

### Post by The Toxic Mite on 2009-08-20
> **bapoumba said:**
> Hmm, in that case, when it happens, please take a screenshot and note (bottom right of the page) if you are on lingonberry or billberry. Thanks.
 
What's the difference between "lingonberry" and "billberry"?
 
:confused:

---

### Post by Joeb454 on 2009-08-20
> **The Toxic Mite said:**
> What's the difference between "lingonberry" and "billberry"?
 
:confused:

lingonberry is one of the servers, bilberry is the other ;)

What they do is provide load balancing, so some queries/sessions will be on lingonberry, and others on bilberry - this is to try and minimize downtime due to large amounts of visitors

---

### Post by Eisenwinter on 2009-08-22
Right now I'm on lingoberry, there are display bugs here too.

Sometimes some of the page's source code is shown throughout the page.

---

### Post by nomnomnom on 2009-08-22
> **Eisenwinter said:**
> Right now I'm on lingoberry, there are display bugs here too.

Sometimes some of the page's source code is shown throughout the page.

Since Karmic updated yesterday, I no longer have this or any other issues.

Are you using Shiretoko on Jaunty?

---

### Post by Eisenwinter on 2009-08-22
I use Firefox 3.5.2 (Shiretoko is its codename, yes), on Arch Linux.

This problem has only been going on for about a week, there is a possibility that it's related to Firefox only, but we can't rule out the fact that it might be a problem with the server.

2 more screenshots, taking 5 minutes ago:

[http://trashis.alrig.ht/UbuntuForumsBug_Weird_chars.png](http://trashis.alrig.ht/UbuntuForumsBug_Weird_chars.png)
[http://trashis.alrig.ht/UbuntuForumsBug_WhatTheHell.png](http://trashis.alrig.ht/UbuntuForumsBug_WhatTheHell.png)

---

### Post by nomnomnom on 2009-08-22
It's still fine here...

---

### Post by jeffathehutt on 2009-08-22
> **Eisenwinter said:**
> I use Firefox 3.5.2 (Shiretoko is its codename, yes), on Arch Linux.

I too use Firefox 3.5.2 on Arch, and I have **not** noticed any problems on bilberry.  Seems like it may be a problem with lingonberry since we run the same software.

---

### Post by Eisenwinter on 2009-08-23
It really does seem like the problem is only in lingoberry, I'm on it right now, and have just encountered display bugs again.

---

### Post by nomnomnom on 2009-08-23
> **Eisenwinter said:**
> It really does seem like the problem is only in lingoberry, I'm on it right now, and have just encountered display bugs again.

2 Things;

1 - What addons are you using with Firefox?

2 - Why are you using Raleigh? It's so ugly it *hurts*.

---

### Post by Eisenwinter on 2009-08-23
I use Flash (native 64-bit) and AdBlock+.

I don't know what you mean by "Raleigh", but I assume it's a font - I simply didn't bother changing the default one.

---

### Post by LookTJ on 2009-08-24
Those are weird screenies.

But I have the same plugins, browser, and distro with no problems on the server you are having issues with

The thing that might be the issue is your DNS.  Have you tried reproducing this bug in Windows or another distro?

---

### Post by bapoumba on 2009-08-24
I have installed karmic and am currently testing with Fx 3.5.2. We'll see, no problem so far (except it is slow, I use epiphany-webkit).

---

### Post by nomnomnom on 2009-08-24
> **Eisenwinter said:**
> I use Flash (native 64-bit) and AdBlock+.

I don't know what you mean by "Raleigh", but I assume it's a font - I simply didn't bother changing the default one.

I'm using both of those on Ubuntu Karmic x64 and have had no issues like yours for about 3 days.

Raleigh is the name of the default GTK2 theme. That *extremely ugly* grey theme you're using **is** Raleigh. :P

---

### Post by Eisenwinter on 2009-08-24
Oh, well, I like to keep it simple, it doesn't bother me.

---

### Post by nomnomnom on 2009-08-24
> **Eisenwinter said:**
> Oh, well, I like to keep it simple, it doesn't bother me.

Each to their own... ;)

---

### Post by dmizer on 2009-08-24
Try adding ubuntuforums to the adblock plus whitelist, or disable it.

A little while back, I had a few problems on the forums as a result of adblock plus. There are no ads on these forums, so there's no reason to use it here anyway.

---

### Post by dmizer on 2009-08-24
> **Eisenwinter said:**
> I use Firefox 3.5.2 (Shiretoko is its codename, yes), on Arch Linux.

This problem has only been going on for about a week, there is a possibility that it's related to Firefox only, but we can't rule out the fact that it might be a problem with the server.

2 more screenshots, taking 5 minutes ago:

[http://trashis.alrig.ht/UbuntuForumsBug_Weird_chars.png](http://trashis.alrig.ht/UbuntuForumsBug_Weird_chars.png)
[http://trashis.alrig.ht/UbuntuForumsBug_WhatTheHell.png](http://trashis.alrig.ht/UbuntuForumsBug_WhatTheHell.png)

The first one is a problem with character encoding, try changing the character encoding (or adding a new encoding) under view > character encoding. I have that problem all the time in Japanese.

You're obviously using some kind of plugin or something to change how firefox renders the forums (those colors are certainly not ubuntuforums standard), so that's likely what's breaking things.

---

### Post by Eisenwinter on 2009-09-04
I have no issues on bilberry, and right now I've been on lingoberry for about 30 minutes, and haven't encountered the same display bugs.

In fact I haven't encountered them in days. Was something done to lingoberry? It might have been a problem on my end after all, if not.

---

