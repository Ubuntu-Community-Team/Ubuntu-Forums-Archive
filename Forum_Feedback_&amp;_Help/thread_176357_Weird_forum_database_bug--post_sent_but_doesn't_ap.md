---
title: "Weird forum database bug--post sent but doesn't appear to be sent"
date: 2006-05-14
forum: Forum Feedback &amp; Help
---

### Post by aysiu on 2006-05-14
Sometimes when I'm replying to posts, I get a weird error about the forum database.

The post went through, but if I click "refresh," I get that the thread is invalid.

If I go back to my original post and try to re-submit it, I get that it's a duplicate of my previous post.

And then I get redirected to the thread, where I see my post actually *did* get through.

Anyone else experiencing this?

---

### Post by cgjones on 2006-05-14
Yeah, this has happened to me a couple of times recently. I end up with double or triple posts, even when I don't hit back or refresh.

---

### Post by richbarna on 2006-05-14
Huge forum, Thousands of posts per day, I suppose it only stands to reason that there will be a few glitches.

---

### Post by aysiu on 2006-05-14
[QUOTE=richbarna]Huge forum, Thousands of posts per day, I suppose it only stands to reason that there will be a few glitches.[/QUOTE] Except that I've experienced this about ten times in the past three days, and never before that in the previous year.

---

### Post by Sef on 2006-05-14
> Except that I've experienced this about ten times in the past three days, and never before that in the previous year.

Same here.  I was planning on posting it today.   It is a bit of a pain in the derriere.  I going to check if i go in through a post under the sidebar or through the forum itself or both.

---

### Post by matthew on 2006-05-14
Happened to me once today--that was the first time since I registered with these forums. Definitely unusual behavior.

---

### Post by ubuntu-geek on 2006-05-16
It's a known bug..

---

### Post by aysiu on 2006-05-16
[QUOTE=ubuntu-geek]It's a known bug..[/QUOTE] Is it a vBulletin bug or our implementation of it's bug? Also, any idea why it's come up only recently...?

---

### Post by ubuntu-geek on 2006-05-16
Its a vbulletin bug when using a master/slave database.

if you must know

[http://www.vbulletin.com/forum/bugs35.php?do=view&bugid=2276&status=43](http://www.vbulletin.com/forum/bugs35.php?do=view&bugid=2276&status=43)

---

### Post by matthew on 2006-05-16
[quote=ubuntu-geek]Its a vbulletin bug when using a master/slave database.[/quote][Which we started using about a week ago]("http://ubuntuforums.org/showthread.php?t=172784")...makes sense. Thanks for the update. We'll look forward to the vBulletin folks fixing it in a future update.

---

### Post by ubuntu-geek on 2006-05-16
I have some ideas to improve this issue but until I have time we'll have to deal with it.. :( Probably in the next week or so

---

### Post by ubuntu-geek on 2006-05-16
Ok I made some changes (didnt take as long as I thought) please let me know if you see this again.

---

### Post by matthew on 2006-05-16
[quote=ubuntu-geek]Ok I made some changes (didnt take as long as I thought) please let me know if you see this again.[/quote]Dude! You seriously rock.

---

### Post by ubuntu-geek on 2006-05-18
Ok guys made some more changes to improve stability. Please let me know if these errors pop up again..

---

