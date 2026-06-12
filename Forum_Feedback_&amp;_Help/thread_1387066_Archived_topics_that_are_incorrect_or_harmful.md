---
title: "Archived topics that are incorrect or harmful"
date: 2010-01-21
forum: Forum Feedback &amp; Help
---

### Post by Kenno on 2010-01-21
I feel there should be a mechanism to correct wrong or harmful information in the archive. Google from time to time drops me into an incorrect archive thread and it's extremely annoying that nothing can be done about it.

The thread I'm talking about right now is this one:
[http://ubuntuforums.org/showthread.php?t=288053](http://ubuntuforums.org/showthread.php?t=288053)

(first hit if one Googles for ["mkdtemp: private socket dir: Permission denied"]("http://www.google.com/#q="mkdtemp%3A+private+socket+dir%3A+Permission+denied"") and linked from several blogs, such as [http://joomla.unlikelysource.com/index.php?option=com_content&view=article&id=28:article-mkdtemp&catid=10:tutorials-howto&Itemid=33](http://joomla.unlikelysource.com/index.php?option=com_content&view=article&id=28:article-mkdtemp&catid=10:tutorials-howto&Itemid=33) )

Wile setting the permissions to 777 does allow users to log in, it also may allow one user to eavesdrop on and tamper with another user's session (and potentially other stuff). tmp directories should always have the sticky bit set, so the correct permissions are 1777 . See [http://en.wikipedia.org/wiki/Sticky_bit#Usage](http://en.wikipedia.org/wiki/Sticky_bit#Usage)

Hopefully, some forum admin is going to tag the thread, like they did in
[http://ubuntuforums.org/showthread.php?t=677185](http://ubuntuforums.org/showthread.php?t=677185)
While that would be nice and good and everything, this is not the first time I encounter a case like that. Usually I'm too busy to report it so I just silently curse the forum and continue what I'm doing. I feel there should be a better mechanism to add corrections to archived threads.

---

### Post by Kenno on 2010-02-03
*bump*

---

### Post by RabbitWho on 2010-02-03
I'd love if we could just delete all the archived topics which are just linked to other archived topics. 

Sometimes someones asks a question and they just get a link to some time that question was posted before (Sometimes it wasn't even answered properly the first time, or the next thread just has another link in it). 
And somehow that's what comes up when you google a problem. No wonder people keep posting new threads that have been answered already when googeling for an answer results in 15-20 threads, most of which just link you to other threads, sometimes to completely different questions! 

Agreed we should be able to flag threads as "useless" and somehow decrease their possition on the search results and on google.

---

### Post by lisati on 2010-02-03
> **RabbitWho said:**
> Agreed we should be able to flag threads as "useless" and somehow decrease their possition on the search results and on google.

Maybe some kind of thumbs up or thumbs down system. 
The forums did have a "thank you" feature, but it was disabled last year; if memory serves correctly it was partly due to abuse and partly from database problems.

---

### Post by coldfusion1313 on 2010-02-04
> **lisati said:**
> Maybe some kind of thumbs up or thumbs down system.
That would be pretty nice.
I really hate when archives do not give me what I want, or they give me the wrong thing.

---

### Post by Perfect Storm on 2010-02-04
> **lisati said:**
> Maybe some kind of thumbs up or thumbs down system. 
The forums did have a "thank you" feature, but it was disabled last year; if memory serves correctly it was partly due to abuse and partly from database problems.

Well, it acrually worked well. The few abuses with the "Thank you" system the staff to care off.
It was simple the plugin was old and never updated which made our servers unstable.

---

### Post by lisati on 2010-02-04
> **Artificial Intelligence said:**
> Well, it acrually worked well. The few abuses with the "Thank you" system the staff to care off.
It was simple the plugin was old and never updated which made our servers unstable.

Thank you. I stand corrected.

---

### Post by Kenno on 2010-02-08
The thumbs up and thumbs down system seem interesting; it would be nice if someone could somehow reintroduce it.

Yet, it wouldn't allow the subtle correction needed in
[http://ubuntuforums.org/showthread.php?t=288053](http://ubuntuforums.org/showthread.php?t=288053)
For now, can someone please change the 777 to 1777 and the a+w to a+rwxt ? (or just add a warning)

---

