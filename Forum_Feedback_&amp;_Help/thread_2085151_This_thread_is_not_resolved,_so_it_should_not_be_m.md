---
title: "This thread is not resolved, so it should not be marked closed?"
date: 2012-11-17
forum: Forum Feedback &amp; Help
---

### Post by One4All on 2012-11-17
First, here is a kind of serious little problem I saw in Ubuntu today (with Unity), on my machine, that could be related to a security issue.

[http://ubuntuforums.org/showthread.php?t=1823861](http://ubuntuforums.org/showthread.php?t=1823861)

My questions are:
 * Where is the bug report?  There should be a bug report at Launchpad for it.
 * If there is a bug report, how am I supposed to be able to find it?
 * Who closed the thread before the thread had a link to a bug report in it?
 * Who is that guy in the black hat who asked for a screen shot?  I am not allowed to send him a message, only a friend request.  What if he is the one who put the trojan in? (I guess it isn't a trojan, but that is what it looks like when it happens.)

Ubuntu is awesome in many ways, it's amusing what kinds of things don't get fixed, that would get fixed if it were made a traditional big company, because someone would be paid to do details diligently.

I did send a message to the one in the thread who typed the answer, so it's possible I'll get a message back from that person.  But I wondered what the community thinks too.

Do I really have to make 24 more posts like this before I can upvote anything?

---

### Post by nothingspecial on 2012-11-17
*Thread moved to **Forum Feedback & Help**.*

> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

The moderator who closed the thread should have posted before closing. We are not robots :)

Start a new thread and link to the old one.

---

### Post by newb85 on 2012-11-17
> **One4All said:**
> First, here is a kind of serious little problem I saw in Ubuntu today (with Unity), on my machine, that could be related to a security issue.

[http://ubuntuforums.org/showthread.php?t=1823861](http://ubuntuforums.org/showthread.php?t=1823861)

Not sure I understand your situation.  The "popup" mentioned in that thread is Apport, the program that reports system bugs.  However, you should *not* be experiencing the same bugs they were in that thread, because they were using releases that are no longer supported.


What release are you running?

What were you doing when Apport came up?

Did anything else go wrong?

---

### Post by One4All on 2012-11-17
> **newb85 said:**
> Not sure I understand your situation.  The "popup" mentioned in that thread is Apport, the program that reports system bugs.  However, you should *not* be experiencing the same bugs they were in that thread, because they were using releases that are no longer supported.

What release are you running?

What were you doing when Apport came up?

Did anything else go wrong?

The bug is that the popup still does not say it is Apport, or give any other indication what it wants to do besides get my password and "report an error".  I would love if it would report to *me* what the error is.

The version I have is 12.10.  I had just closed one app, and I was opening Firefox.  Are you requesting a ps dump?  The thread describes a window appearing for no apparent reason and requesting a password, so I assumed it was the same cause.  I thank you for your questions.  Here are the areas where I realize I fell down, due to your helpful questions:

* I haven't yet run ps aux to figure out what processes there may be unusual
* I haven't yet inspected logs in /var/ as I recently read I should be doing, so I can understand what's there when something weird happens
 * I never checked the dates of that post, very important.

Thank you!  Next time that comes up I will ps aux and look for Apport, at least.
Seems I should post a new thread after I find out more about it.
Thanks for insights.

---

### Post by cariboo on 2012-11-17
The reason the bug reporting application asks for a password, is because as a normal user, you don't have access to some of the logs in /var/log, privileges need to be escalated in order for apport to sent the needed data to create a good bug report.

The application will also ask you before hand, if it needs to send data from a log file that contains personal data, you are given the ability to edit out the personal information before that particular log file is sent.

There are many applications that don't show their real name during normal operation, one example is seahorse, when run, is called Users & Groups.

Much of this confusion when it comes to bug reporting comes from a lack of knowledge about how a linux distribution works, and may seem to some Windows users to be malware, when in fact it is a just a normal part of Ubuntu.

As far as voting up threads, we don't do that here. THe only things you can do after you have attained 25 posts, is edit your user profile, adding an avatar, version used and a signature, that doesn't include a picture.

To the op of this thread, If you want to discuss bug reporting more, I'd suggest you create a new thread, with a link to the closed thread.

---

### Post by deadflowr on 2012-11-17
The Op in the closed thread never filled in the correct password, so a report was never filed.

Here's an interesting thread with a video link from the UDS-R:

[http://ubuntuforums.org/showthread.php?t=2082804]("http://ubuntuforums.org/showthread.php?t=2082804")

---

### Post by One4All on 2012-11-22
Thank you for all the info.  Here is what I have learned

 * The thread I asked about was closed because the OP on it never entered the password so the contents of the crash was never determined (the OP did a reinstall)
* The scary-looking dialog box I experienced might have been from Apport
 * Also I have learned that some crash info is in /var/log/apport.log and apport.log1 (etc)

So I am satisfied as far as this thread is concerned.

(I'll look around some more to find out what happened, and start another thread if I still think there is a real question.)

E pluribus unum     ):P):P):P

---

### Post by cariboo on 2012-11-22
> **One4All said:**
> Thank you for all the info.  Here is what I have learned

 * The thread I asked about was closed because the OP on it never entered the password so the contents of the crash was never determined (the OP did a reinstall)
* The scary-looking dialog box I experienced might have been from Apport
 * Also I have learned that some crash info is in /var/log/apport.log and apport.log1 (etc)

So I am satisfied as far as this thread is concerned.

(I'll look around some more to find out what happened, and start another thread if I still think there is a real question.)

E pluribus unum     ):P):P):P

There is also crash data located in /var/crash, just for completion.

---

