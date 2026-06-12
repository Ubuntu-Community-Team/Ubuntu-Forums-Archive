---
title: "Linux Philosphy"
date: 2010-12-13
forum: Desktop Environments
---

### Post by hatridge on 2010-12-13
Where to begin this topic is a bit of a challenge. I will start by saying that I posted it in "Desktop Environments" because I did not see a topic header titled new (questionable) ideas. If I overlooked this, I apologize. 

  I'll begin by giving you an idea of who I am, as I feel it may also be relevant to this discussion. I was/ am an average end computer user. Like many, I ran Windows for many years and eventually found that at least 30% of my time at the computer was fixing problems dealing with the operating system itself. I am now a happy and free Linux user and have been for about two years. 

 I recently watched a documentary called "[Revolution Os]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBgQtwIwAA&url=http%3A%2F%2Fvideo.google.com%2Fvideoplay%3Fdocid%3D7707585592627775409&rct=j&q=Revolution%20Os&ei=Sl0GTZvCKZGqsAPGlKSjDQ&usg=AFQjCNHZBxm_P5AnSPybs3rAKOkEmdauwg&sig2=Z1fHXFV5JF62a_4f9sBu7A&cad=rja")" featuring Richard Stallman and Linus Torvalds among others. A good film about the whole GNU/Linux philosophy, and how it was created, and has since evolved to where it is today. Personally, I admire the philosophy of community fixes and so forth.

 I want to be clear that I do not write code of any kind and consider myself to be very average when it comes to computers. I do however run a small business and part of that business requires a website. Not having the money to hire out, I proceeded to search the Internet for a free web hosting site. Anything with some kind of web page building tool on it to make it as easy as possible. I found one that was satisfactory until the website grew and now is where I am getting into trouble.

  My site has grow tremendously and I have upgraded my account, pay the big bucks and so on for this company to host it. The site building tool that is supplied by this host has become obsolete for my needs as well as it has bugs in it. I'm told these issues are being looked at but the they have hit "road blocks" because they do not have access to the source code, even though that source code would be beneficial to customer support and the client.

 Now the questions. 
Is there a Linux philosophy type host out there with an open source way about it? With a site builder for us "no time to's". If not, I believe this would be a great asset to the Linux community as I am living proof that you don't have to be a computer "geek" or "nerd" to enjoy Linux. No offense please.
How do you change hosts when you have thousands of web pages? And keep the same registered .com?
Finally how do I back up my site for when and if I decide to change hosts?

  I apologize for the long winded questions.

Thanks:popcorn:

---

### Post by utnubuuser on 2010-12-13
drupal

---

### Post by hatridge on 2010-12-13
that I believe is just the answer I was looking for. Thanks a million.

---

### Post by ingeva on 2010-12-14
> **hatridge said:**
> that I believe is just the answer I was looking for. Thanks a million.
I think that response is not complete.
You are asking a lot more than for just a CMS system,
and that's the only answer you have got.

I'll avoid advertising here, so please contact me on [http://inge.qreply.net](http://inge.qreply.net)
and I'll give you some more tips.

---

### Post by hatridge on 2010-12-14
Please just post your answer here. Whatever email feature that is in your post won't send.
Also there might be someone else this may help.

---

### Post by ingeva on 2010-12-14
> **hatridge said:**
> Please just post your answer here. Whatever email feature that is in your post won't send.
Also there might be someone else this may help.

It sends just fine, but it requires that you give, and verify, you email address.
I think I have things to tell you that are not acceptable in the forum. :)

Try again, and remember to click the verify link in the mail you receive.
This is to block spammers.

---

### Post by TiBaal89 on 2010-12-14
I'd also suggest Drupal.  There can be a bit of a learning curve depending on what you're looking to do, but there exist great online resources plus books on the subject.

> **hatridge said:**
> 
Finally how do I back up my site for when and if I decide to change hosts?

This is (usually) shockingly easy.  Drupal and similar CMS's are two things: a collection of files, and a database.  To move the site you just copy all the files and copy the database.  After that it's just a matter of editing a config file or two to tell the CMS how to connect to the new database.

It's important (and interesting) to realize what's going on with a CMS like Drupal.  The entire thing is just a bunch of scripts.  When you load a page, it runs the script(s), connects to the database, generates the page, gives it to you, and goes away.  There is no persistence.  It's tempting to think, since the interface and admin pages are so complex, that you're using a 'program' in the typical sense, like a desktop gui program - but you're not.  It's just a bunch of scripts that run, retrieve the necessary info, spit it out, and die.

That's why you're able to simply copy all the files and the database to move the site.  It couldn't be easier.

---

