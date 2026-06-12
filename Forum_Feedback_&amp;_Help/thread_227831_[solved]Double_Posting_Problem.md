---
title: "[solved]Double Posting Problem"
date: 2006-08-01
forum: Forum Feedback &amp; Help
---

### Post by Dr. Nick on 2006-08-01
I just notied this behavior within the last hour or two. Whenever I quick reply to a thread I get this error

** 		 			The following errors occurred when this message was submitted: 		 	   	 		 			** 			[LIST=1]
[*]**This forum requires that you wait 20 seconds between posts. Please try again in 20 seconds.**[/LIST]My reply posts once, but it appears it tries to post again. I have reproduced this several times in the last 10mins or so. I am not using my "back" button or anything similar that would generate that. Pushing quick reply throws me to that page automatically

---

### Post by Dr. Nick on 2006-08-01
....Just a test to make sure it happens again...

It did the same thing, displays the above error and shows my post below it in the "advanced view"

---

### Post by aysiu on 2006-08-01
I've had the same happen to me as well.

---

### Post by TravisNewman on 2006-08-01
ditto, I posted this in the mod forum before I realized it was already reported here. So we know about it :) I guess we need to wait for Ryan to see it.

---

### Post by Dr. Nick on 2006-08-01
OK, I was curious to know if it was just me or others aswell, luckily it isnt double posting, what a mess that would make. :)

EDIT

It didnt do it that time... weird :confused:

---

### Post by TravisNewman on 2006-08-01
yeah, I'm thrilled we put in that 20 second limit.

---

### Post by Jucato on 2006-08-02
I'm experiencing the same error.

Is something wrong with the forums? (The RSS feeds are also down...)

------------
EDIT: It seems the error only happens when replying through the Quick Reply function. Doesn't happen when you reply by Quoting.

---

### Post by slimdog360 on 2006-08-02
same thing is hapening to me, you can notice a couple of double posts Ive made in the cafe.

edit: argh it happened to me again when replying to this post

---

### Post by anaconda on 2006-08-02
Same for me..

But what do you mean it isn't doubleposting??

If you wait for the 20s and continue it will doublepost...

Like this  :(

---

### Post by anaconda on 2006-08-02
Same for me..

But what do you mean it isn't doubleposting??

If you wait for the 20s and continue it will doublepost...

Like this  :(

---

### Post by jvtm on 2006-08-02
RSS feeds are broken because one PHP include (/includes/class_xml.php) file wants to output some debug info.

The non-xml output types, like [http://ubuntuforums.org/external.php?type=js&forumids=20](http://ubuntuforums.org/external.php?type=js&forumids=20) work just fine.

Please, fix it.

Are there any alternative ways to get the USN as RSS feed? Some mail archive maybe?

---

### Post by Jucato on 2006-08-02
(Yes, I've tried the "Has this already been asked" button before posting this)

I seem to be running into some problems with the forums today. One of them has been confirmed by other people in another thread. The others I'm not so sure of, so I'm asking them here.

1. When replying through Quick Reply, you are warned that you are posting within the 20 second time limit. This is the problem confirmed by other people.

2. The RSS feeds are down. For example, this RSS Feed for the Absolute Beginner section: [http://www.ubuntuforums.org/external.php?type=rss2&forumids=73](http://www.ubuntuforums.org/external.php?type=rss2&forumids=73)
Might not be a big thing for others, but this is the primary way I'm able to check new posts/questions on the forum and see if I can be of any help.

3. Very minor problem: the favicon for the forum seems to be not working. If you have previously displayed it before, there's no problem. But once you make a new bookmark, the favicon no longer displays.

Is there something wrong with the forums today? I haven't heard a peep from any of the admins. Hope to hear from them soon.

---

### Post by TravisNewman on 2006-08-02
threads merged

---

### Post by zxee on 2006-08-02
I noticed this double trouble this morning (EST) also.
I guess the short term work-around is just to use a button other than quick reply and delete the quoted remarks if they're unnecessary.

---

### Post by LKRaider on 2006-08-02
How do we delete our double-postings? :S
I have seen a few on the forums already...

Btw, isn't there a way to make the forum system disallow double-posting completely? Just check the previous message in the thread, and if **equal** to the new post (same poster too), block it.

---

### Post by richbarna on 2006-08-02
> **LKRaider said:**
> How do we delete our double-postings? :S
I have seen a few on the forums already...

Btw, isn't there a way to make the forum system disallow double-posting completely? Just check the previous message in the thread, and if **equal** to the new post (same poster too), block it.

Ok now :)

---

### Post by richbarna on 2006-08-02
No, it's back again :(

---

### Post by DoktorSeven on 2006-08-02
Yep, I get the double posting thing as well.  I just know that if I see the "wait 20 seconds" thing, it's likely already posted my response, and just reopen the thread in a new 'Fox tab to confirm, and exit the post screen if it has.

---

### Post by Dr. Nick on 2006-08-02
Now I see this page aswell

**This post is a duplicate of a post that you have posted in the last five minutes. You will be redirected to that thread.**
                                          [Click here if your browser does not automatically redirect you.]("http://ubuntuforums.org/showthread.php?t=228217")

---

### Post by dolson on 2006-08-02
Hooray for making changes on a live system!

---

### Post by Jucato on 2006-08-03
RSS feeds are still down. I'm having a hard time trying to keep up with new posts. Unanswered posts will only show posts that don't have answers, new or not. "Last (insert time here)" will display all posts from all sections within that time frame...

Oh well... :(

---

### Post by K.Mandla on 2006-08-03
I see everything twice!

(Where's Yossarian at?)

---

### Post by orb9220 on 2006-08-03
Same problem for me.

But if you disregard the error you will find that it did post anyway.

---

### Post by Jucato on 2006-08-03
I hate to "nag" but it has been, what, almost 2 days? Still no "official" word from any of the forum admins. Not even a "yes there is a problem and we are working on it right now"? I'm guessing they're having a slight lack of personnel problem?

---

### Post by orb9220 on 2006-08-03
Well this is getting weird came back after watching "Hero" great flick.

And my first two posts no problems. Then on my third post.

This forum requires that you wait 20 seconds between posts. Please try again in 18 seconds.

Which I just middle-click to close tab because the post went thru anyway.

---

### Post by ubuntu-geek on 2006-08-03
This issue has been fixed.

---

