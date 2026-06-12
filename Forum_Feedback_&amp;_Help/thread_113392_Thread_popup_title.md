---
title: "Thread popup title"
date: 2006-01-06
forum: Forum Feedback &amp; Help
---

### Post by glepore70 on 2006-01-06
Is there any way to disable the thread popup which occurs when the mouse is over a thread link?  It usually displays the first sentences of the post.  This is very annoying when trying to scroll down the page and having these popups appear over and over.  In addition, when a link is clicked on, the popup still appears over the subsequent page (at least on Firefox 1.5) for several seconds.  I have attempted to write a Greasemonkey script to handle this, but, alas, it's beyond me.  Thanks,

---

### Post by xmastree on 2006-01-06
Yeah, I second this request. I too think it's rather annoying.

---

### Post by earobinson on 2006-01-06
i have never noticed it. but IMO options are always a good thing.

---

### Post by horace on 2006-01-06
I find it very intrusive too. It happens because there is a (very lengthy) title attribute on the td tag, but I don't like the use of title attributes as a sort of preview tool like this. I don't know the vBulletin software, but maybe this is a configurable option - though then it would have to be switched off for everybody.

---

### Post by olzak on 2006-01-21
I also second this request and hope somebody can tell us how get rid of these annoying popups.

---

### Post by smoker on 2007-01-09
i know it is a year on, though was this issue ever resolved?

i find this really annoying also.

---

### Post by 23meg on 2007-01-09
Having it pop up only when hovering over the title itself instead of the whole area around it would help a great deal.

---

### Post by VraiChevalier on 2008-03-22
I hope I haven't overlooked something obvious but I cannot find a way to turn off the little preview pop up which appears when the mouse pointer is rolled over the forum threads.

Can anyone tell me if there is a way to disable this feature?

I tried setting the "tooltips" in the Epiphany browsers about:config to "false" but that did not solve it.

---

### Post by bapoumba on 2008-03-23
@ VraiChevalier:  merged your thread in here. As you see, this is a recurring question in FFH ^^

---

### Post by VraiChevalier on 2008-03-23
Well, it seems there is not a simple solution and I have not overlooked something glaringly obvious. I will keep checking this thread for an answer and in the meantime will do some homework and see what I can find out. Perhaps it is just something we have to tolerate.

---

### Post by p_quarles on 2008-03-23
What you're asking about the is the alternate text in the hyperlinks and images. How this is rendered is a feature of the browser and not really of the CMS itself. The issue here seems to be the fact that vBulletin makes the first several lines of a post into the alt-text for links leading to that post. Frankly, I find that useful, as I imagine others do.

---

### Post by 23meg on 2008-03-23
It's not the alternate text; it's the "title" property of the table cells. That's definitely a feature of the CMS.

---

### Post by bapoumba on 2008-04-06
I just noticed the popup is now restricted to a small box with a couple lines, which I like much. It does not span most of the screen as it used to,  I can move the mouse around and avoid it easily, and still get to read the ones I may be interested in.

I suppose we can thank ubuntu-geek for it :KS

---

### Post by chewearn on 2008-04-08
This will disable all tooltips from your Firefox browser:
about:config, set "browser.chrome.toolbar_tips" to false

And I mean ALL tooltips.  Only for those really annoyed by them.

---

### Post by VraiChevalier on 2008-04-15
> **bapoumba said:**
> I suppose we can thank ubuntu-geek for it :KS

Thanks ubuntu-geek!

---

### Post by notwen on 2008-04-17
I tend to use this additional info.  The first sentence in some posts can help me judge whether or not I even want to view the thread.

---

### Post by michaelzap on 2008-05-22
> **notwen said:**
> I tend to use this additional info.  The first sentence in some posts can help me judge whether or not I even want to view the thread.

I also really like these, and all of a sudden I'm not seeing them anymore. Has there been a change in the forums (I can still see them in the page source)? Or is there perhaps some issue with Firefox 3beta5 displaying these?

---

### Post by noynac on 2008-05-23
> **michaelzap said:**
> I also really like these, and all of a sudden I'm not seeing them anymore. Has there been a change in the forums (I can still see them in the page source)? Or is there perhaps some issue with Firefox 3beta5 displaying these?

I complained about these earlier, and I can assure you that they are still displayed in Firefox 3 beta 5. If you find a way to turn them off, please let me know.

---

### Post by michaelzap on 2008-05-23
> **noynac said:**
> I complained about these earlier, and I can assure you that they are still displayed in Firefox 3 beta 5. If you find a way to turn them off, please let me know.

In my case they're off and I want to turn them on!

---

### Post by michaelzap on 2008-05-31
> **michaelzap said:**
> In my case they're off and I want to turn them on!

I decided to do a fresh install of Hardy anyway (to use disk encryption), and now the thread pop-ups are working again. I must have somehow changed a preference or style in my previous Firefox installation that caused them to not pop up. Not sure how that happened, but I'm glad they're back now.

---

### Post by LaRoza on 2008-05-31
> **michaelzap said:**
> I decided to do a fresh install of Hardy anyway (to use disk encryption), and now the thread pop-ups are working again. I must have somehow changed a preference or style in my previous Firefox installation that caused them to not pop up. Not sure how that happened, but I'm glad they're back now.

If you ever want to restore Firefox to its default settings, delete the .mozilla directory. (Back it up if you want to preserve bits of it)

---

