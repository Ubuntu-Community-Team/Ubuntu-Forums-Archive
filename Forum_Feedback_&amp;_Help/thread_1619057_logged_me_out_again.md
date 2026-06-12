---
title: "logged me out again"
date: 2010-11-11
forum: Forum Feedback &amp; Help
---

### Post by Skaperen on 2010-11-11
I just spent 45 minutes preparing a long post describing a problem, including all the research I did.  And it would not post because UF logged me out.  And it would not save the post across the process of logging in.

This is one of several login/cookie problems with UF that I do not experience with other web forums.  Can someone please get this fixed?  This is the worst case, yet.

---

### Post by Elfy on 2010-11-11
Not that it will help much in this case - but if I am posting something that'll take longer than a few minutes to type and post I write it in an editor.

As it is I can leave my browser logged in for a lot longer than 45 minutes without it logging me out - check the remember me button at login and it will.

---

### Post by Tamlynmac on 2010-11-11
Prior to submitting my post (thread or reply), I use the copy function  to copy my entire post. Then simply reload current page (browser).

If I've timed out the screen will ask me to log back in. After logging  back in I'm returned to the posting window (which is now blank). I then  simply paste my post back in and submit. If posting a thread don't forget to type in the title. Which I generally do last anyway.

If I haven't timed out, the screen returns with the posting window and my post. I then write in my title and just submit my post without pasting.

This procedure has become second nature and I perform this task almost  every time just before posting. It only takes a moment and eliminates frustration. I have a disability that requires the  re-reading (often more than once) of my posts prior to submitting. Just to assure they are  worded correctly. Even then I still error some times. :smile:

---

### Post by Skaperen on 2010-11-20
If I make that "keep me logged in" selection, it should keep me logged in for at least a few hours, right?  On many web sites, such a selection keeps me logged in for a month or even more (though I think that much is excessive).

IMHO, 25 to 30 hours is a reasonable default ... enough to last a day plus some jitter.

What should have been done was make HTTP logins be "out of band" ... e.g. done via HTTP header fields where the web site provides a header that means "you could login here if you want to" and the browser can provide a username and password via an encrypted string in a header.  Visiting a login page would trigger that in most cases.  The browser could do a "login here" button or popup.  If the user chooses to login, the browser fetches the site's username and password from a strongly encrypted local file storing these credentials.  The user only enters the passphrase for the local file once the credentials are saved ... and only as often as the user configures the browser to ask.

Instead, we are stuck with a cookie based mess.

---

### Post by Skaperen on 2010-11-20
The very fact that this error message even exists in the forum software programming shows the problem:

```
Your submission could not be processed because you have logged in since the previous page was loaded.
```

What good programming would support is to store the message in a pending queue, tell the user why it was not yet accepted, and given the user the opportunity to complete the requirements, whatever they are (e.g. providing a subject/title, a category prefix, filling in a captcha, and/or logging in).  If while typing in the post, I get automatically logged out, it should just treat it as not being logged in and ask me to login to complete the posting.

Whether this is entirely a vBulletin programming issue, or something that the UF admins can configure within vBulletin's config tools, I don't know.  It just seems to be very inconvenient.  If there's a reason for doing it this way that I cannot see, can someone point that out?

---

