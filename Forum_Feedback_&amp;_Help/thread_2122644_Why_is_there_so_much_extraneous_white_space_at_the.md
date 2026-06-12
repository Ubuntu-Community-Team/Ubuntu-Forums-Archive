---
title: "Why is there so much extraneous white space at the bottom of this post?"
date: 2013-03-05
forum: Forum Feedback &amp; Help
---

### Post by SeijiSensei on 2013-03-05
[http://ubuntuforums.org/showthread.php?t=2122627&p=12543441&viewfull=1#post12543441](http://ubuntuforums.org/showthread.php?t=2122627&p=12543441&viewfull=1#post12543441)

There are no extra returns after the end of the posting text, yet there is a lot of empty space below the published message text.  Is this something I can fix myself?

BTW, I'm using the format with the poster's information in the left column.  The info on top design is incredibly wasteful and clunky.

---

### Post by mc4man on 2013-03-06
you may be interested in this thread, looks much better after implementing
[http://ubuntuforums.org/showthread.php?t=2121348](http://ubuntuforums.org/showthread.php?t=2121348)

---

### Post by SeijiSensei on 2013-03-06
Thanks for the tip.  

Still, I think it would be better if the default layout were less "spacy."  If the issue is the spacing in the left column, why can't we remove all the extra space between the "Beans" line and the "Report Post" button?

I've looked at the source code for the left column and need to track down the CSS for the various divs.  I wonder if one of them has too much bottom padding.

It also might have something to do with having a signature or an avatar or both.  Your posting has neither and is displayed with much less extraneous space at the bottom than mine right above it.

---

### Post by Elfy on 2013-03-06
> **SeijiSensei said:**
> Thanks for the tip.  

Still, I think it would be better if the default layout were less "spacy."  If the issue is the spacing in the left column, why can't we remove all the extra space between the "Beans" line and the "Report Post" button?

I've looked at the source code for the left column and need to track down the CSS for the various divs.  I wonder if one of them has too much bottom padding.

It also might have something to do with having a signature or an avatar or both.  Your posting has neither and is displayed with much less extraneous space at the bottom than mine right above it.

Someone will be looking at that - it's an issue of time and people with sufficient access being available.

---

### Post by SeijiSensei on 2013-03-06
Thanks for the update, Elfy.  If I see anything obvious when I browse the stylesheet I'll let you know.

It does seem to have something to do with signatures, probably more than avatars.  It's a bit tough to test the various combinations.  Signatures are easier to test since they are not added to old messages.  Testing with and without an avatar is tougher because once you enable the avatar it appears with every post.  

For now, I'm just going to drop my signature, I guess, because I don't like having a three line post take up my entire browser window.

---

