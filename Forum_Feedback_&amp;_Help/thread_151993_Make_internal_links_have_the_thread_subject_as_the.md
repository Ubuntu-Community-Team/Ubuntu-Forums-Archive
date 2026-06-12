---
title: "Make internal links have the thread subject as the link name?"
date: 2006-03-28
forum: Forum Feedback &amp; Help
---

### Post by aysiu on 2006-03-28
Maybe I'm just living in a dream world, but I'll throw it out there in the hopes that it's feasible, relatively easy to implement, and desirable for at several people out there.

Linking to other threads in the Ubuntu Forums is a popular activity. I do it, myself, quite often.

Unfortunately, when one links to a thread, it usually looks something like this:

[http://www.ubuntuforums.org/showthread.php?t=109397](http://www.ubuntuforums.org/showthread.php?t=109397)

Instead of something like this:

[If not Brown, then what?](http://www.ubuntuforums.org/showthread.php?t=109397)

Any chance the forums could "magically" make it so that internal links appear as the thread subject heading instead of gobbledygook--*ubuntuforums.org/showthread.php?t=######*?

---

### Post by Sutekh on 2006-03-29
I like the idea alot.   

When I link somewhere I always try to use the title of the thread (or article) and the source.   So posting a link to a thread on the Forums, I go to the extra effort to make it look like

[Ubuntu Forums - If not Brown, then what?](http://www.ubuntuforums.org/showthread.php?t=109397)

I think its helpful for people to know where I'm telling them to go rather than saying ["go here"](http://www.ubuntuforums.org/showthread.php?t=109397).  I could be the only one though; I am something of a perfectionist.

I know that the forums can "automatically parse links in text" maybe it can also do this.



On reflection though, the way I link it might be a bit harder to automate than the simpler way aysiu suggested.

---

### Post by aysiu on 2006-03-29
Wow.

I'm amazed only Sutekh and I care about this.

---

### Post by mstlyevil on 2006-03-29
[QUOTE=aysiu]Wow.

I'm amazed only Sutekh and I care about this.[/QUOTE]

Me cares too!

Edit: I know a line like the one I wrote above just bugs the hell out of an English teacher. (My brother is studying to become an English teacher.)

---

### Post by aysiu on 2006-03-29
Thanks for the affirmation, Mstlyevil.

Kassetra or Ubuntu-Geek want to weigh in on this?

A nice compromise would be to have it appear as gobbledygook but show the thread title if you mouseover on it. I don't know if that's easier or more difficult to set up...

**Edit**: [quote=mstlyevil]Edit: I know a line like the one I wrote above just bugs the hell out of an English teacher. (My brother is studying to become an English teacher.)[/quote] Actually, it's just fine--unabashedly colloquial. What really gets under my skin is people overcorrecting themselves, saying "so-and-so and I" when they really should be saying "so-and-so and me."

For example, I hear a lot of people say something like, "Yes, when you gave that report to Rita and I, we were at lunch." You don't give reports to *Rita and I*. You give reports to *Rita and me*. To realize how incorrect this is, just make a logical substitution for *Rita and I*: "Yes, when you gave that report to we, we were at lunch."

---

### Post by Sutekh on 2006-03-29
> **aysiu]
For example, I hear a lot of people say something like, "Yes, when you gave that report to Rita and I, we were at lunch." You don't give reports to *Rita and I*. You give reports to *Rita and me*. To realize how incorrect this is, just make a logical substitution for *Rita and I*: "Yes, when you gave that report to we, we were at lunch."[/QUOTE]
The way I always worked it out was to remove the "so-and-so" and see how the sentence turns out.

Thus "gave that report to Rita and I" becomes "gave that report to I".  Totally wrong.  

On the other hand "gave that report to Rita and me" becomes "gave that report to me".  

Anyway so off topic now, thanks Mstlyevil [-( 

 said:**
> 
A nice compromise would be to have it appear as gobbledygook but show the thread title if you mouseover on it. I don't know if that's easier or more difficult to set up...That would be really cool, and I would be very impressed if it could be done.

---

### Post by aysiu on 2006-03-29
[QUOTE=Sutekh]The way I always worked it out was to remove the "so-and-so" and see how the sentence turns out.

Thus "gave that report to Rita and I" becomes "gave that report to I".  Totally wrong.  

On the other hand "gave that report to Rita and me" becomes "gave that report to me".[/quote] That works, too.

> 
That would be really cool, and I would be very impressed if it could be done. I suggest it only because something similar happens with threads right now. If you hover over the thread with your mouse, a preview of the first line (or lines, if you're not using Firefox) of the thread appears. I figured maybe it wouldn't be too hard to do a similar hack for URLs to bring up the thread title.

---

### Post by BluGold on 2006-03-30
Why not both? As in See/check 'thread title' here 'link'.
Or, 'thread title' at 'link'.
Or, _________________
JAT (Just A Thought)              ...BluGold

---

### Post by TLE on 2006-04-03
I think it would be nice if it just replaced the yabelyjoda, I not to happy about the mouse over idea as I try to use my mouse as little as possible "Type as you find, thank you Firefox".
It could of course also be something that you could choose between in the options or something
Regards TLE

---

### Post by aysiu on 2006-04-03
I know the staff are busy as always, but can we hear from any of the administration on whether this is feasible/ desirable for them, and what the timeframe would be if it were to be implemented?

---

### Post by ubuntu-geek on 2006-04-03
hmm interesting idea.. i'll have to think about this.. you could always use the wysiwig editor and make it look "pretty" without much effort..

---

### Post by Cap'n Refsmmat on 2006-04-04
I have a feeling it would take a lot of CPU to do, especially if there were a lot of links in a thread.

On forumview, it doesn't cost vB any extra queries because it is already extracting thread information. On threadview, however, it would have to look up information on other unrelated threads, so you'd end up taking a DB query or two per link and that would slow things way down.

---

### Post by aysiu on 2006-04-04
Maybe I'm not understanding all the technical stuff involved, but I would think it would be something that happens *as you post*, not every time a thread is viewed.

For example, when I type a URL in my post, I'm typing the URL. When I submit the post, the [URL] brackets are automatically added. When I go back to edit my post, I see that the post itself (in raw form) now has those [URL] brackets.

Hopefully this would be the same sort of thing. When you hit the submit button, somehow VBulletin would be programmed to retrieve the subject heading and change http://www.ubuntuforums.org/showthread.php?t=109397 with [url= and all that jazz]Subject Title of Thread[ /url] in the actual post.

---

