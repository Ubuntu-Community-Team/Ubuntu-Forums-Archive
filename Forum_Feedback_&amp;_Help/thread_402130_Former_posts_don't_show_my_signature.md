---
title: "Former posts don't show my signature"
date: 2007-04-05
forum: Forum Feedback &amp; Help
---

### Post by ubu-for on 2007-04-05
Two days ago I've added a signature to my account, but only my new posts get the signature. I've checked my former posts and recognized that "Show your signature" is not selected.

Do I really have to edit every former post?

THX!

---

### Post by ubu-for on 2007-04-25
Now my signature only shows up, if I'm logged in?!

---

### Post by ubuntu-geek on 2007-04-25
signatures only show to logged in users

---

### Post by ubu-for on 2007-04-25
> **ubuntu-geek said:**
> signatures only show to logged in users

THX!

---

### Post by ubu-for on 2007-06-24
> **ubu-for said:**
> Two days ago I've added a signature to my account, but only my new posts get the signature. I've checked my former posts and recognized that "Show your signature" is not selected.

Could someone do a Forum update to turn on "Show your signature" by default, even if you don't have a signature?

Every time I post without a signature, I have to edit every former post to see my new signature.

---

### Post by matthew on 2007-06-24
I just looked and you don't have a signature in your account. Are you sure you saved it when you created it? Everything in your account settings looks fine.

UserCP->Edit Signature

Type your signature in the box, then scroll down and click "Save Signature"

---

### Post by ubu-for on 2007-06-24
Thanks matthew for your quick reply!

Every time I add a signature to my account, the signature only shows up for my new posts (and former posts with signatures), because signatures are turned off by default for my former 200 posts (and some new ones), which I've posted without a signature.

---

### Post by matthew on 2007-06-24
Odd. I see that in this thread. Don't change anything else in your account for the time being. I'll look into it as much as I can, and if I find anything I'll post here. If I don't, ubuntu-geek will probably be able to look further into the situation later.

One idea: it could just be that the database needs some time to update and the signature may turn up in your older posts after an hour or so...maybe.

---

### Post by ubu-for on 2007-06-24
THX for your help!

BTW For every post here in this thread, I don't get any "Beans"?!

---

### Post by matthew on 2007-06-24
The "beans" thing is easy--beans aren't given for posts in Forum Feedback & Help, the Cafe and the Backyard, and maybe one or two other places. Beans are definitely given in all of the technical support areas, though.

---

### Post by matthew on 2007-06-24
I'm looking here and the post from April 25th in this thread has your new signature on it, but the post from an hour ago doesn't, and again, your newest posts do.

I think we just need to wait for the automated database updates to take effect and your sig should update in all your posts...hopefully, anyway.

---

### Post by ubu-for on 2007-06-24
I don't believe that a database update would make a difference, because two months ago I've waited three days for the update without effect.

Now when I look at my former posts, the option "Show your signature" appears and it's turned off.

---

### Post by matthew on 2007-06-24
Hmm. Okay, that's just odd. Hey, ubuntu-geek! When you have a minute...  :)

---

### Post by kko1 on 2008-02-20
Hello.

I recently added a signature, where I previously had none, and it is not showing for my old posts either. In other words, **empty signatures are not updated in messages. Is this a bug or a feature?**

Instead of starting a new thread about it I decided to post in this thread because it is the same issue. I see that in this particular thread, exactly one post (post #5) does *not* contain a signature.

If I understand it correctly, the signature for every old post (at least in posts where the signature *has* existed) is *supposed to be updated* when the signature holder changes it. **Am I correct?**

If yes, I hope this would occur even for those old posts that never carried a signature. It is not a big issue, but still kind of breaks the intended use of the signature.

kko1

---

### Post by popch on 2008-02-20
> **kko1 said:**
> Hello.

I recently added a signature, where I previously had none, and it is not showing for my old posts either. In other words, **empty signatures are not updated in messages. Is this a bug or a feature?**

You did remember to reload the pages with the old posts in your browser, did you not?

---

### Post by kko1 on 2008-02-20
> **popch said:**
> You did remember to reload the pages with the old posts in your browser, did you not?

I did indeed, and I also waited in case the change doesn't take effect immediately. (The issue of a possible delay is also discussed earlier in this thread.)

But if you will bother taking a look earlier in this thread, at post #5 (not mine), you will see that it is missing a signature, even when other posts in the thread by the same user carry one. Equally, my old posts don't carry a signature - you can check this for instance in the thread that caused me to write a signature in the first place:
[http://ubuntuforums.org/showthread.php?t=693056](http://ubuntuforums.org/showthread.php?t=693056)

kko1

---

### Post by popch on 2008-02-20
I can confirm that some of your posts carry a signature and some do not. I do not think that it is related to the age of a post. I also seem to have seen other users within threads you have posted to which also occasionally lack signatures.

The signatures are actually missing from the html page source, so it is not just a matter of 'lossy' formatting. But then, the markup looks perfectly fine near the place where the signature would be expected. It's just the content of your signature which is missing.

---

### Post by kko1 on 2008-02-22
EDIT: Duplicate post, please remove.

---

### Post by kko1 on 2008-02-22
> **popch said:**
> I can confirm that some of your posts carry a signature and some do not.

Thank you for the confirmation. :D

> **popch said:**
> I do not think that it is related to the age of a post.

No, it is not really related to the *age* of a post, *except insofar as the posts in question are from an earlier time when I used to **not** have a signature at all.*

Now, all I would ask would be an "official" opinion (from someone "in the know") on whether this is **a bug or a feature**. :KS

kko1

---

### Post by kko1 on 2008-02-27
I feel like I should've gone ahead and posted this in a new thread, so my question "**bug or feature**" would show in the thread title. The current title isn't really what I was after, so I'm not sure this has been seen by the "people in the know". (Still, posting in an existing thread was most probably "the right thing to do", and that I did.)

Rationale:
- I'm not interested simply in *my* signature showing or not showing, as it were - this is, after all, a common characteristic of the forum software.
- Instead, I *would* be interested in knowing whether this characteristic / quirk in the forum software is *expected behaviour or not*.

In other words, I do realise that **ubuntu-geek** and other admins are most probably busy, and their time is limited. Thus, knowing their position on the issue would give me (and others wondering the same) an idea of whether to:
- expect a change in this forum characteristic (nevermind "when", only "if"), or
- accept the situation as is.

**Both options are perfectly OK for me...** I'd just like to know which will prevail. ;)

kko1

---

### Post by matthew on 2008-02-27
Sorry for the delay in answering. ubuntu-geek is out this week on personal business, and I just didn't see the revived thread.

I also apologize that we never got around to answering this question. I am guessing this is being caused by page caching on our local server.

If I look at an old thread that I contributed to, and then change my signature, then reload the thread, it shows my old signature for a period of time, and then eventually it changes to the new one.

If I change my signature and then look at an old thread that I contributed to, which I know has not been viewed in a very long time, my new signature appears immediately.

So, I'm going to say it is a feature, resulting from the page caching that is turned on to help reduce database queries and server loads.

Can you confirm that your signature exists correctly on old threads after a long time?

---

### Post by matthew on 2008-02-27
Um...never mind. I just looked at your oldest post, that I'm sure hasn't been viewed in a long time. Hmm, no signature there at all.

Okay, I'm now going to adjust my guess and say that mine gets updated as an admin because of some special feature in my user permissions that I can't find, but that isn't set the same for you.

When ubuntu-geek is back, I'll ask him and see if he has any other ideas on this.

Ultimately, I think it is a software feature, an expected action, but I can't give a good rationale at the moment. If I were to make something up on the spot, I would say it has something to do with database optimization/pruning of posts older than a certain age, but I'm just pulling that out of the air.

---

### Post by kko1 on 2008-02-27
Matthew, thanks for your response. Also, no apology needed, I can appreciate the volume of traffic on these forums.

> **matthew said:**
> Um...never mind. I just looked at your oldest post, that I'm sure hasn't been viewed in a long time. Hmm, no signature there at all.

Okay, I'm now going to adjust my guess and say that...

Let me be more precise here, to help you diagnose the issue.

There are two separate cases.

1) A user *has* previously used a signature when posting, and then changes it.
- In this case, as far as I have seen, the existing signature **is** updated correctly. This may require a delay, as you have described ( = the issue of a cache).
- This has nothing to do with admin status or, as far as I can tell, any other user account specifics (as long as a signature *is* used).

2) And then there's what we have here. This is a case where a user has previously *not* used a signature at all, and then adds one.
- In this case, the user's posts that have been posted *during the time when no signature was used* do **not** get the new signature (or, to be more precise, do not get **a** signature at all). So, the posts that have been posted without a signature remain "unsigned".

- Further, if I understood correctly what *ubu-for* has posted above, and looking at post #5 (that carries no signature) in the middle of this thread, he has been able to get these "unsigned" posts also when subsequently deactivating his signature, then posting an "unsigned" message, and afterwards reactivating his signature. (I have not tried this.) His post #7 also gives some insight into the issue.

3) Oh, and a third, related, case. I don't know (have not tried) if the *showing* of signatures in existing messages is disabled if one disables using signatures, i.e. whether the signature is then hidden for all messages. (If not, though, almost the same could, I assume, be achieved by using a blank but *activated* signature.)


kko1

---

### Post by matthew on 2008-02-27
Interesting. I've sent ubuntu-geek a note. When he is back and has some time, I'm sure this will interest him.

We may concentrate more on the overall forum software upgrade that is in the works (to vBulletin 3.7) before we look at this further, to see if this issue even remains once that has occurred.

---

