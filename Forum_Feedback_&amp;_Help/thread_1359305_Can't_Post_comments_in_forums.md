---
title: "Can't Post comments in forums"
date: 2009-12-19
forum: Forum Feedback &amp; Help
---

### Post by tanics on 2009-12-19
Hello,
I am new to ubuntu and no nothing about computer.

Whenever I try to post something on any computer forums, the message does not get posted.

Is it a problem of java? I have icedtea installed in my computer.
or is it a problem of flash plug-in? I have a open source flash plug in installed in my firefox browser(3.0).

I am a user of jaunty 9.04.

Now I am using Opera 10.1; here sometimes the message get posted.

Help required - 

Thanks in advance.

---

### Post by chuina on 2009-12-19
"Can't Post comments in forums"

then how did u post this ?

---

### Post by tanics on 2009-12-19
Hi Chunia,

I have posted this message by using Opera Browser. I have been here from August this year and I habe never been able to post before.
Then I tried to post by using Firefox. Can you help me in this regard?

---

### Post by tanics on 2010-01-08
I want to mention somethings again - 

1) I have changed my Java from Open JDK to Sun Java.
2) After that I can post from Opera Browser.
3) But still can not post from Firefox browser.

Can anybody help me.

---

### Post by howefield on 2010-01-08
You have posted on a few occasions over the last few weeks.

Are you sure it is not a case of losing your posts and not being able to find them ?

---

### Post by tanics on 2010-01-08
@howefield before posting todays comment I have tried to post it from Firefox. 
1) After sometime the browser send me "newreply.php" - 0 bytes; it ask me to save or open it?
2) I save it and found that I have not been able to post.
3)It happens every time I tried to post something on any forums.
4) Even I have not been able to respond to the WELCOME Letter of this forum till I downloaded Opera.

---

### Post by tanics on 2010-02-04
I am posting this message from google chrome and I can post from here .

But still can't post from Firefox 3.0.17.

---

### Post by Chris Edgell on 2010-02-04
It took me sometime to realize that sometimes I simply was not signed in.  (Logged in)

Find the top of some page where you see boxes for name and password and enter your name and password.

---

### Post by Rex Bouwense on 2010-02-04
> **Chris Edgell said:**
> It took me sometime to realize that sometimes I simply was not signed in.  (Logged in)

Find the top of some page where you see boxes for name and password and enter your name and password.

Chris.  I thought I was the only one that made that mistake.  When I finally realized why I couldn't post I really felt stupid.  Thanks for sharing.  I later found out that many of my problems are caused by my noob status.

---

### Post by Iowan on 2010-02-04
> **tanics said:**
> ... 
1) After sometime the browser send me "newreply.php" - 0 bytes; it ask me to save or open it?
2) I save it and found that I have not been able to post.
...I've never needed to install additional software to post to the forums. I've had problems staying logged in if I shut off cookies, and the posting icons don't work without Java/Javascript. 
That save/open option for "newreply.php" sounds unusual...

---

### Post by tanics on 2010-02-05
Thank you @Chris, @Rex and @Iowan for all the suggestions.
Let me repeat my problems so that you could help me - 

1) I can't post comments here in this forum and also on other web-forums ( I visited) from FIREFOX 3.0.17 browser; though I can do the same from Opera 10.10 browser and from Google chrome browser.

2)I have Sun Java and Javascript installed in my system and also got Adobe flash player installed.

3) I also can't check "YAHOO Mail" from any of the browser I have got.

4) Also I can't edit my profile in few websites ( though I can view them).

5) Are these symptoms related to "Shockwave Player"?

Kindly suggest some remedies.

Finally, I have tried to post in this forum only when I am signed in.

---

### Post by doas777 on 2010-02-05
> **Iowan said:**
> I've never needed to install additional software to post to the forums. I've had problems staying logged in if I shut off cookies, and the posting icons don't work without Java/Javascript. 
That save/open option for "newreply.php" sounds unusual...


usually that means there is no handler for that extension type, so it is treated as a binarywrite() instead of a redirect or transfer. happens to some folks with ASP occasionally, if the browser doesn't recognize how to render an aspx.

---

### Post by ratcheer on 2010-02-05
I want to say that I have the exact same problem when I try to post here from my Windows host. I cannot post from Firefox or MSIE, but I can post from Opera or Chrome. I can post to all other forums I know of with any browser, it is only Ubuntuforums.org that I have problems with.

From my Ubuntu host, I can post here with FF, Opera, and Chrome.

When I try to post from Win with FF or MSIE, it tells me that my message "must be greater than 0 bytes" and it has blanked out whatever I typed in the Message: box.

Tim

---

### Post by lisati on 2010-02-05
> **tanics said:**
>  
1) After sometime the browser send me "newreply.php" - 0 bytes; it ask me to save or open it?


This almost sounds as if your browser is trying to download the web page instead of displaying it. Are you left-clicking or right-clicking?

---

### Post by tanics on 2010-02-05
@lisati after I click the left mouse button pointing over to "Submit Reply" the above mentioned problems happens.

@doas777 your explanation seems most convincing to me. Can you suggest some remedies; also help me with "yahoo mail problem".

---

### Post by doas777 on 2010-02-08
not on the client. I'm sure if you dug into firefox deep enough, and knew what you were doing you could clear it up. I would just reinstall firefox though. your experience is not normal, so hopefully a code refresh will take care of it.

---

### Post by zakshdw on 2010-02-19
i had this same problem, but it just magically fixed itself...........spooky!:popcorn:

---

### Post by ratcheer on 2010-02-19
I have recently had the same problem with Firefox 3.6 on Karmic. So, I dug into it and found that clearing the browser cache helps, at least temporarily. It also fixed it on my Windows machine.

Tim

---

### Post by argos3016 on 2010-02-19
same problem

---

### Post by axel_2078 on 2010-02-20
I was seemingly able to post this morning, but the posts never actually showed up in the forum. I say seemingly because after I made the post, it took me to the next screen where it showed me my post was successful. However, I noticed that I couldn't find it in the forum where I posted it and running a search for it yielded no results. I also thought it was strange that the most recent post from each forum was "1 hour ago". That's really odd because people are always on here and posting. It seems to be working now though.  Odd....

---

### Post by tanics on 2010-02-25
now posting from OpenSolaris 2009.06 ( guest OS)/ using firefox 3.1/ only short messages can be posted

---

### Post by tanics on 2010-02-25
Two things important- posting from firefox (from guest os) and complete removal of firefox in Host following doas777 suggestion

---

### Post by cariboo on 2010-02-25
When you removed Firefox, did you also remove ~/.mozilla in your home directory? To me your problems may stem from a corrupted profile.

---

### Post by tanics on 2010-02-26
cariboo907
yes I have also removed ~/.mozilla in my home directory, though nothing seems to have changed.

---

### Post by tanics on 2010-02-28
Following all the suggestions I have reinstalled firefox and has noted that I can post short messages but not a full reply. Any suggestion?
Thanks for all the help.

---

