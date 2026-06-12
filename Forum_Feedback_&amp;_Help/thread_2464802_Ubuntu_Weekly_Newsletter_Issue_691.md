---
title: "Ubuntu Weekly Newsletter Issue 691"
date: 2021-07-12
forum: Forum Feedback &amp; Help
---

### Post by Bashing-om on 2021-07-12
Hey -

With the migration to new hardware and the updates, it appears I have lost access to the newsletter subforum.
In attempting to post this latest issue I get:
> You don't have permission to access this resource.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443

Some one available to fix my permissions so I can complete the posting ?

thanks

----------

wildmanne39 is on it 

thanks again

---

### Post by QIII on 2021-07-12
I just took a look.  I don't see anything in your profile that would keep you out.

I made a couple of test posts there wondering if I might get the same results, but I was able to post.  I jailed them to clean up, so they aren't there now.

Try again now and let's see if it was something transitory.

---

### Post by Bashing-om on 2021-07-12
thanks Qiii

I try again and advise :)

---

### Post by Bashing-om on 2021-07-12
QIII

Yuk still - continue to receive 403 forbidden when attempting to post. Want that I hold the thread open ?

---

### Post by QIII on 2021-07-12
Can you post a test answer to the most recent previous issue?

---

### Post by Bashing-om on 2021-07-12
Yes; I am able to post a reply to last week's issue.

---

### Post by QIII on 2021-07-12
So, you are getting the 403 message when you attempt to start a new thread for the current issue?

---

### Post by Bashing-om on 2021-07-12
^ That is correct  >> You don't have permission to access this resource.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443


I still have the thread open pending posting.
Does it affect that this support thread has the same title name ?

Yukkie

---

### Post by QIII on 2021-07-12
I doubt it, given that people post the same thread in multiple places all the time and we have to jail the duplicates.

Let me have another staff member with lower privileges to see what they can do.

---

### Post by Bashing-om on 2021-07-12
standing by

---

### Post by QIII on 2021-07-12
Is this happening immediately after clicking "Post New Thread" or when you have added content and click submit?

---

### Post by Bashing-om on 2021-07-12
added the content - also when preview is activated :(

---

### Post by QIII on 2021-07-12
I conducted an experiment in which I attempted to copy and paste the content of the previous thread.  I got the same 403 message.

We think it might be something that Canonical IS added in hardening the site.  It's not just you.  :)

---

### Post by QIII on 2021-07-12
Now that we have established that this is a problem with the Forum software and not your account, I'm moving this out of the Resolution Centre to Forum Feedback and Help.

---

### Post by Bashing-om on 2021-07-12
thanks -

---

### Post by sajoupa on 2021-07-13
Hi,

I could identify what was making this post trigger a permission denied, and updated the security rules to allow it.
I don't have a reproducer though, so couldn't confirm that it's now totally fixed. If the issue persists would you mind pastebin'ing the post contents so that I can look further ?

Thanks,
--
sajoupa
Canonical IS

---

### Post by guiverc on 2021-07-13
@sajoupa

[https://paste.ubuntu.com/p/jrpHQ82Gsp/](https://paste.ubuntu.com/p/jrpHQ82Gsp/)

That maybe what bashing-om posts directly ; or it's the basis of it anyway.

(I've never posted UWN to UF)

---

### Post by sajoupa on 2021-07-13
Thanks.
I've reproduced and validated a fix in the testing environment, it should now also be fixed in prod.

---

### Post by QIII on 2021-07-13
Thanks, sajoupa!

---

