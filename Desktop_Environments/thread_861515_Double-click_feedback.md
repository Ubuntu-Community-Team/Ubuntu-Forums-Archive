---
title: "Double-click feedback"
date: 2008-07-16
forum: Desktop Environments
---

### Post by sicofante on 2008-07-16
I was searching the internet for a Gnome behaviour that bothers me a lot. It's about Gnome not providing feedback to make the user know a double-click has been received and an action is being taken. I found this:

[http://osdir.com/ml/gnome.nautilus/2003-08/msg00093.html](http://osdir.com/ml/gnome.nautilus/2003-08/msg00093.html)

Well, it's a 2003 post and its first reply says the following version of Nautilus would fix it.

I haven't really researched any further (I decided to come here and just ask), but I can see my Gnome desktop doesn't provide any feedback when I double-click on my home folder or a document.

Is there any fix for this? It's terribly annoying and my customers complaint loudly about it.

Thanks for any help.

---

### Post by scragar on 2008-07-16
I don't know about a real fix, I but I always have system monitor running and set I/O to be bright yellow(so it stands out against red(unfreindly/normal processes), black(none) and blue(freindly)), when I double click on something I can often tell it's working by the surge of yellow in the bar. I know not everyone wants to do that, and that it's far from an ideal solution, but it is something you can use(See what other people say as well though, this is an intresting topic).



Tested it, and the cursor changes for a little while when it starts opening the program, although not for long.

---

### Post by sicofante on 2008-07-16
Oh no... I was hoping it was just my newbeeness. So you're saying this is just not fixed yet in Gnome? :roll: I'm astonished.

I guess I'll have to go to their mailing lists and ask.

---

### Post by calum on 2008-07-24
> **sicofante said:**
> 
I haven't really researched any further (I decided to come here and just ask), but I can see my Gnome desktop doesn't provide any feedback when I double-click on my home folder or a document.

Strange, mine does... I see the pointer change to the 'busy' cursor, and an item in my window list on the panel saying "Opening (whatever application)"...

---

### Post by sicofante on 2008-08-01
I've been testing this on different computers and here are my "conclusions" (or should I say "no-conclusions"):

1- Opening a desktop folder (like the Home folder) NEVER gives any feedback. After a reboot, this may take a few seconds during which the user simply doesn't know what's going on at all. In older computers the caching doesn't seem to help that much and the issue persists every time you open the folder.

2- Opening a folder inside a Nautilus window does give a busy cursor SOMETIMES. Some other times, there's no indication at all, but I must say it never takes as long as the first time opening of the desktop Home folder, so even if it's still wrong behaviour, it's not as serious.

3- Opening a document or application, be it on the desktop or inside a Nautilus folder, gives a busy cursor only SOMETIMES again, but at least the task bar shows a new item representing the window being opened, which somewhat alleviates the problem.

I've posted a message on the Gnome developers list and they don't seem to give a damn (not a single reply). I think a possible workaround would be a Compiz effect, similar to what happens when you click on a panel's shortcut (like Firefox). If that happened after every double-click (single-click for those like me who switched the default behaviour), the user would have a clue and it would be enough.

---

### Post by calum on 2008-08-08
> **sicofante said:**
> 
I've posted a message on the Gnome developers list and they don't seem to give a damn (not a single reply). I think a possible workaround would be a Compiz effect, similar to what happens when you click on a panel's shortcut (like Firefox). If that happened after every double-click (single-click for those like me who switched the default behaviour), the user would have a clue and it would be enough.
To be fair, going in all-guns-blazing with incorrect observations isn't the best way to get the GNOME developers' attention... e.g. it's just not true to say that opening an application never gives any feedback, because, as you've since noted, it "sometimes" does (every time, on my GNOME desktop, FWIW).  It's up to each application to configure itself to do so, which isn't ideal, but all common GNOME apps should do so by now.  You might consider filing bugs against any that don't.

Perhaps, had you listed your observations and a possible solution, as you've done in your most recent post here, you would have garnered more feedback.

If you have loudly-complaining customers, it suggests you run a business-- in which case, the best way to get important bugs fixed is to buy support from Canonical, which will allow you to escalate such issues.  Otherwise, your only real options are:

a) time, patience and reasoned discussion with the community
b) fixing it yourself

Such is life with large open source software projects...

---

### Post by sicofante on 2008-08-08
Points taken. This is a 2003 bug, however, and it isn't solved. A community that so proudly speaks every other day about its famous Gnome HIG shouldn't be so picky about the particular manners of anyone pointing that error.

I've turned to the usability list and I've got some feedback now. No much improvement so far, but at least I have a conversation going on...

---

