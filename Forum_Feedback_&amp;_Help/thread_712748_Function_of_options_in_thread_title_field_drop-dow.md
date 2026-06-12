---
title: "Function of options in thread title field drop-down menu"
date: 2008-03-02
forum: Forum Feedback &amp; Help
---

### Post by Forrest Gumpp on 2008-03-02
I just recently used the quote button for the purpose of taking a quote from a post in one thread, and placing it in a post being made to a different thread.

Before attempting to submit the post I clicked on the title field box and a drop-down menu appeared.  That menu appeared to hold the names of the last five threads that I had viewed.  I clicked on one of the titles displayed in this list as it was the one wherein I wanted the post containing the quote to appear.  That click moved that title into the title field.

Thinking that that action had determined the thread to which the post would now be made, I went ahead and submitted.  My post did not go to the thread I thought I had selected.

What did I do wrong?

---

### Post by p_quarles on 2008-03-02
Is this the same post you reported earlier? If so, I did see that, but wasn't sure what you were talking about. This clarifies it (as much as something this strange can be clarified, I guess), but I'm not sure how it happened. 

If you want, give me the link to the thread where you meant to post it, and I'll move it.

As for the bug, that's something for the site admins to look into. If I understand what you're saying correctly, that is strange indeed.

---

### Post by Forrest Gumpp on 2008-03-02
p_quarles,

Yes it is the post that I reported.

The thread to which I was attempting to make the post was:  [http://ubuntuforums.org/showthread.php?t=193427](http://ubuntuforums.org/showthread.php?t=193427)

Thanks for moving it for me.

What I find even more interesting was that the post that went to the wrong thread retained the new thread title I had selected.  So anyone reading down the posts in the FAQ related thread would have possibly become mightily confused.  I'm surprised the system accepted that without throwing a hissy fit.  Curious.

---

### Post by p_quarles on 2008-03-02
Okay, fixed. That's a strange error, I have to say.

---

### Post by Forrest Gumpp on 2008-03-02
I have just noticed a slight ambiguity in the title for this thread.

The way it stands, it implies that I was opening a new thread when I encountered the problem described.  That was not the case.  I was attempting to take a quote from an ordinary post in one thread and place it within an ordinary post I was attempting to make to a different thread.

Perhaps a moderator could remove the word 'new' from the title?  I don't want to confuse other viewers or the title search comparator.

Should I mark this thread as solved?  My problem has been fixed, but it seems a bug may exist that has not been resolved.

---

### Post by p_quarles on 2008-03-02
The word "new" was removed from the thread title at your request. 

Please leave this unsolved, though, since this may be a bug in the forum software.

---

### Post by Forrest Gumpp on 2008-03-02
Its happened again!  This post has gone to the wrong thread:  [http://ubuntuforums.org/showpost.php?p=4441249&postcount=20](http://ubuntuforums.org/showpost.php?p=4441249&postcount=20)
You can see from its post title that it doesn't belong, and where it should have gone, i.e. to:[http://ubuntuforums.org/showthread.php?t=711065&page=4](http://ubuntuforums.org/showthread.php?t=711065&page=4)

This is exactly what I did.

I opened the 'Ideas for funding....' thread, and went to the post from which I wanted to quote.

I selected the text I wanted, and then clicked the quote button.

The 'Reply to Thread' page displayed, with the entire contents of the post from which I thought I had selected just one paragraph to quote in the message window.

I selected and deleted all the text I did not want to quote.

I then copied the text of my post from Gedit into the message window.

I then clicked in the thread title field and got only one choice in the drop-down, the then current title of 'Ideas for funding...'.

I clicked in the title field again and deleted all text.

I clicked again and this time the drop-down displayed a number of threads I had recently viewed.  I selected 'An Ubuntu Forums 'Thanks Bank'....' and clicked it.

The title of the thread in which I wanted the post, with its included quote, to go, was now in the title field.

I clicked 'submit'

Bingo!  Posted in the wrong thread, but with the thread title intended showing immediately above the post in the wrong thread.

I can't believe this is a bug.  I keep feeling its my technique, somehow.  That's why the long explanation.

I wont try it again until I (or the Forum staff) have got to the bottom of this.  Sorry for the trouble caused.

---

### Post by popch on 2008-03-02
Gotcha.

I see two areas where you might misunderstand the way this software works.

One: Once you click on 'quote' or 'post reply' within a thread, the forum software decides which thread your post will go to, and that's the thread you are in while clicking on the button. You can give your reply another title and change it in a number of ways, but you can not move it to another thread. Not all the kings men can do it. Administrators can, though.

Two: Clicking on the 'quote' button simply opens the 'reply to thread' window with the complete post quoted where you clicked on 'quote'. The function does not take into account what you select before clicking, or how you hold your mouth and so on.

---

### Post by Forrest Gumpp on 2008-03-02
popch.

Thanks for the explanation.  I had that feeling that I was somehow doing it wrongly.

It seems you are saying that the 'quote' function cannot be used to transfer a quote from one thread to another.

What then is the point of being able to make choices from the drop-down menu to place in the title field?

Also, why does the software accept any title other than that of the 'true' thread when a post is eventually submitted?  The fact that it clearly will is a potential source of confusion.  I don't know whether that would be described as a bug, but I could imagine it.

Is it the case that if I had opened a message window from the intended receiving thread, and copied the quote across from the message window opened in the source thread, that I may have been able to quote across threads?

---

### Post by popch on 2008-03-02
> **Forrest Gumpp said:**
> It seems you are saying that the 'quote' function cannot be used to transfer a quote from one thread to another.

Quite. That's the impression I get when I read your bug report. 

I am using this post to test my hypothesis. If it works as I maintain, then the post is in the same thread as the post I am answering, and it carries the title 'Believer or not?' which appears to be quite apt.

---

### Post by popch on 2008-03-02
> **Forrest Gumpp said:**
> It seems you are saying that the 'quote' function cannot be used to transfer a quote from one thread to another.

My last post seems to have established that without a doubt.

> **Forrest Gumpp said:**
> What then is the point of being able to make choices from the drop-down menu to place in the title field?

Beats me. I don't see the point, either.

> **Forrest Gumpp said:**
> Also, why does the software accept any title other than that of the 'true' thread when a post is eventually submitted? 

It doesn't. Once you managed to clear the title field, the drop down shows a lengthy list in ascending order. You just scroll down to 'Re: Fu..', and there you are.

I just did exactly that, with the added twist that I first deleted the last word in the original title. The drop down list now contains the original title as well as my newly truncated one.

I do not think that it's a bug. A dragonfly?

> **Forrest Gumpp said:**
> Is it the case that if I had opened a message window from the intended receiving thread, and copied the quote across from the message window opened in the source thread, that I may have been able to quote across threads?

Yes. I do that all the time.

---

### Post by Forrest Gumpp on 2008-03-02
Confirmed, message received in thread being validated.

Momentarily off topic, is your desktop Gnome, and by any chance do you reside/work in Zurich?

---

### Post by popch on 2008-03-02
> **Forrest Gumpp said:**
> Confirmed, message received in thread being validated.

Momentarily off topic, is your desktop Gnome, and by any chance do you reside/work in Zurich?

Gnome, but not Zurich, Also, I do not work for any bank. But I do love gnome bread which is not from Zurich, either.

---

### Post by Forrest Gumpp on 2008-03-03
I have just observed a further curiosity of the type demonstrated by popch earlier in this thread when part of a thread title was removed, yet the truncated title was still able to be posted to the same thread.

In this thread:  [http://ubuntuforums.org/showthread.php?t=713662](http://ubuntuforums.org/showthread.php?t=713662)
it appears in the index, and in the 'show all posts' option of the userID drop-down menu, marked as [SOLVED].

The opening post recitation of the title also shows up as "[SOLVED]...", but none of the following posts title recitations show the [SOLVED] marking.

Is this a bug or a feature?

---

### Post by LaRoza on 2008-03-03
> **Forrest Gumpp said:**
> I have just observed a further curiosity of the type demonstrated by popch earlier in this thread when part of a thread title was removed, yet the truncated title was still able to be posted to the same thread.

In this thread:  [http://ubuntuforums.org/showthread.php?t=713662](http://ubuntuforums.org/showthread.php?t=713662)
it appears in the index, and in the 'show all posts' option of the userID drop-down menu, marked as [SOLVED].

The opening post recitation of the title also shows up as "[SOLVED]...", but none of the following posts title recitations show the [SOLVED] marking.

Is this a bug or a feature?

You can give every post a title (see this post's title), it is just by default the OP's title. It isn't updated when the OP is changed, because the title is set by the user (with a default).

---

### Post by Forrest Gumpp on 2008-03-03
Thanks for the clarification.  I'm still leaving this thread unmarked as solved as per earlier advice.  Feel free to mark it so yourself (I'm assuming as a moderator you can do this) when the bug status is resolved or whatever.

---

