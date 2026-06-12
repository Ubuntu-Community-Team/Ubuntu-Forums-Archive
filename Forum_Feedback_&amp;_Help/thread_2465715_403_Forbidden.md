---
title: "403 Forbidden"
date: 2021-08-09
forum: Forum Feedback &amp; Help
---

### Post by rsteinmetz70112 on 2021-08-09
I getting occasional 403 Forbidden Errors when I try to post a quick reply or go from the quick reply top the Advanced editor.

---

### Post by Bashing-om on 2021-08-09
rsteinmetz70112 -

+! here also.

Reported and Canonical's sajoupa is looking into the situation.

[INDENT]a work in progress[/INDENT]

---

### Post by sajoupa on 2021-08-10
Hi,

It will help me a lot if you could add details about the conditions triggering the 403: URL of the post you were trying to reply to, and the time you got the error.

Thanks.

---

### Post by TheFu on 2021-08-10
I've been gettings these for weeks now.
When I think a pattern is clear and test it, it works, so clearly my pattern wasn't the issue.
I've had it fail in the last 24 hours from using code tags, then just with sentences.  By moving some words around in the sentences, the post would go through.  Not all code tags with commands fail.
Sometimes 3-15 step posts fail. It is very frustrating.  I was posting s p r u n g e.us links to text replies to get around the issue. Those should still be in the forums for multiple references for posts that didn't work.  I like that pastebin option because it works with **curl** for posting. I suppose I could setup my own pastebin on a webserver I run to get passed the blocked URL from these forums.

---

### Post by rsteinmetz70112 on 2021-08-10
It only started for me in the last week or so. I've had it fail from an empty Quick Reply window or from a Quick Reply moving to the Advanced Editor or trying to post a Quick Reply.
No pattern I can see so far, except for me it seems to involve the Quick Reply.

---

### Post by QIII on 2021-08-10
TheFu -- The word you are having difficulty with has an unwholesome "urban" connotation of a possibly distasteful sexual nature.  At some point it was added to our list of disallowed words.  Might be time to review that.

---

### Post by TheFu on 2021-08-10
> **QIII said:**
> TheFu -- The word you are having difficulty with has an unwholesome "urban" connotation of a possibly distasteful sexual nature.  At some point it was added to our list of disallowed words.  Might be time to review that.

You've lost me.  Sorry.  It isn't any specific word that I can tell which gets blocked in my posts.  Normal written text is being blocked without any code tags or URLs.  Rather than a 403 error, perhaps a content disallowed error?

---

### Post by QIII on 2021-08-10
Heh.  :)

Sorry, the one you had to put spaces into.

---

### Post by TheFu on 2021-08-10
> **QIII said:**
> Heh.  :)

Sorry, the one you had to put spaces into.

That one is extremely minor ... though I don't understand what being infatuated with someone else has to do with a failed spring (bed, springboard, shocks).

If you follow any of the links - use lynx if you like - there are probably 5 examples of posts that were getting 403 Forbidden errors and I was either unable to figure out a way to get around whatever THAT issue was or just gave up.  I've walked away from about 10 posts due to the forbidden error and just decided not to bother.

---

### Post by Bashing-om on 2021-08-10
et all

sajoupa has fixed the 403 issue.

I can affirm that the post I had issues with now all complete :D

- good things do happen -

---

### Post by Bashing-om on 2021-08-10
Nope !

I take back that all is fixed :(
I just 403'd on a new post response.

-yukkie-

---

### Post by Bashing-om on 2021-08-11
et all
Again >>

sajoupa has addressed the latest incidents.

However, please report any abnormalities that you may encounter.

-are we done now ?-

---

### Post by Bashing-om on 2021-08-11
et all
Again >>

sajoupa has addressed the latest incidents.

However, please report any abnormalities that you may encounter.

-are we done now ?-

---

### Post by issh on 2021-08-13
I'm trying to reply to a thread I started here: [https://ubuntuforums.org/showthread.php?t=2465842](https://ubuntuforums.org/showthread.php?t=2465842) . I'm replying with a quote. I am also getting the 403 Forbidden error. Not sure why.

Edit: Maybe it's because I was logged in on both my mobile and PC at the same time? Each from different ip addresses?

---

### Post by TheFu on 2021-08-13
> **issh said:**
> Edit: Maybe it's because I was logged in on both my mobile and PC at the same time? Each from different ip addresses?
That shouldn't matter. The only time I see any issues with session authentication is if I happen to change a VPN exit location, then the session becomes invalidated. I think they tie the session to the IP to prevent session hijacks and session replays by nefarious people.

---

### Post by tea for one on 2021-08-14
403 Forbidden while trying to reply to [https://ubuntuforums.org/showthread.php?t=2465857](https://ubuntuforums.org/showthread.php?t=2465857)
18:10 UK Time Saturday 14 August

18.23 I managed to post a reply but I had to remove:-
```
sudo parted -l
```

Are the code blocks causing problems?

---

### Post by TheFu on 2021-08-14
> **tea for one said:**
> 403 Forbidden while trying to reply to [https://ubuntuforums.org/showthread.php?t=2465857](https://ubuntuforums.org/showthread.php?t=2465857)
18:10 UK Time Saturday 14 August

18.23 I managed to post a reply but I had to remove:-
```
sudo parted -l
```

Are the code blocks causing problems?

It isn't the code blocks alone.  But I haven't been able to see a pattern.  I've had posts without any code blocks get the 403 error. My guess, with ZERO internal information, is there's a regex pattern that isn't finding the close for the pattern, but is finding an open that never ends.  I've had the most 403 issues with short, step-by-step, instructions that include commands, but not necessarily code tags.

Regex patterns can be hairy.

---

### Post by tea for one on 2021-08-14
> **TheFu said:**
> Regex patterns can be hairy.

I hope [COLOR="#0000FF"]sajoupa[/COLOR] (post 3) has a suitable brush and comb..............;)

---

### Post by sajoupa on 2021-08-16
> **issh said:**
> I'm trying to reply to a thread I started here: [https://ubuntuforums.org/showthread.php?t=2465842](https://ubuntuforums.org/showthread.php?t=2465842) . I'm replying with a quote. I am also getting the 403 Forbidden error. Not sure why.

Edit: Maybe it's because I was logged in on both my mobile and PC at the same time? Each from different ip addresses?

Hi,

I couldn't find an entry in the audit logs for a denial on this page.
But I did add a  fix for the other issue reported a few posts after this one, and it's possible that it fixed both.
If it happens again, can you also include the time when it happened ?

Thanks !

---

### Post by sajoupa on 2021-08-16
> **tea for one said:**
> 403 Forbidden while trying to reply to [https://ubuntuforums.org/showthread.php?t=2465857](https://ubuntuforums.org/showthread.php?t=2465857)
18:10 UK Time Saturday 14 August

18.23 I managed to post a reply but I had to remove:-
```
sudo parted -l
```

Are the code blocks causing problems?

Thanks for the report, I could find what was causing the denial, and pushed a fix. Can you try again ?

---

### Post by sajoupa on 2021-08-16
> **tea for one said:**
> I hope [COLOR=#0000FF]sajoupa[/COLOR] (post 3) has a suitable brush and comb..............;)

The difficulty isn't really with regex (even though they **are** hairy), but rather with identifying what's a legitimate use and what's an attack attempt (the logs have few of the former, but a lot of the latter).

---

### Post by TheFu on 2021-08-16
> **sajoupa said:**
> The difficulty isn't really with regex (even though they **are** hairy), but rather with identifying what's a legitimate use and what's an attack attempt (the logs have few of the former, but a lot of the latter).

Understood.  I've been running different sorts of servers for over 25 yrs and was a software developer prior to that (with some overlap). Once worked on a project where we'd use regex to match document TOC and Indexes into the current and different documents in the library. There wasn't any standard format and we had to support type-3 fonts, which are just glyphs, not translated into characters. Thankfully, the type3 font use was minimal, usually just i/I and l/L and 1 stuff to certain in extremely technical documents, readers wouldn't/couldn't confuse the number from the letters due to a bad font selection in the document.

I won't pretend to know what an attack post to forum software looks like.  I've specifically NEVER run any forum software because I didn't feel I could secure it.

Is there any chance to have the post-count used in this filtering?  People with 500+ posts aren't likely to be attackers, so it is just the inappropriate words that need filtering.  Perhaps 500 is too high?  Heck, I wouldn't mind 20K posts being the limit, but we'd all miss out on some great posts by people with more outside interested who only have a few hundred posts.

Seems that a look up for the number of posts would be faster to process than all the anti-attack checks?

Just a though.

---

### Post by tea for one on 2021-08-16
> **sajoupa said:**
> Thanks for the report, I could find what was causing the denial, and pushed a fix. Can you try again ?

I'd rather not try again with the same thread.
A new post with [highlight]sudo parted -l[/highlight] would not be an integral part of the current flow of the thread.

If it is any help, I did manage to post the code subsequently - post 24 [https://ubuntuforums.org/showthread.php?t=2465857&page=3](https://ubuntuforums.org/showthread.php?t=2465857&page=3)

---

### Post by TheFu on 2021-08-16
For reporting issues, what is the ideal way? 
What do you need? 
URL?  Timestamp?  Content?

The the last week or so, about 1 post every 2-3 days has been rejected.

---

### Post by sajoupa on 2021-08-17
> **TheFu said:**
> For reporting issues, what is the ideal way? 
What do you need? 
URL?  Timestamp?  Content?

The the last week or so, about 1 post every 2-3 days has been rejected.

URL + timestamp is perfect. Thanks !

---

### Post by TheFu on 2021-08-17
> **sajoupa said:**
> URL + timestamp is perfect. Thanks !

[https://ubuntuforums.org/newreply.php?do=postreply&t=2465965](https://ubuntuforums.org/newreply.php?do=postreply&t=2465965)
Tue 17 Aug 2021 11:19:05 AM EDT

---

### Post by sajoupa on 2021-08-18
> **TheFu said:**
> [https://ubuntuforums.org/newreply.php?do=postreply&t=2465965](https://ubuntuforums.org/newreply.php?do=postreply&t=2465965)
Tue 17 Aug 2021 11:19:05 AM EDT

Thanks, I found the error, and pushed a fix.

---

### Post by TheFu on 2021-08-27
[https://ubuntuforums.org/showthread.php?t=2466323&p=14056087#post14056087](https://ubuntuforums.org/showthread.php?t=2466323&p=14056087#post14056087)
Fri Aug 27 11:12:00 .... around that time.

I had just posted and that went through, then saw a grammar error and wanted to change "only" to "one" ... which resulted in the 403 Forbidden error.
I had not seen any issues the last week.

---

### Post by sajoupa on 2021-09-01
Thanks for the report, I just pushed a fix for this one.

---

### Post by rsteinmetz70112 on 2021-10-04
I just got the error again editing one of my own posts. 
[https://ubuntuforums.org/showthread.php?t=2467600](https://ubuntuforums.org/showthread.php?t=2467600)

---

### Post by TheFu on 2021-10-04
Got the 403 error yesterday and today trying to create a new thread.
[https://ubuntuforums.org/newthread.php?do=postthread&f=331](https://ubuntuforums.org/newthread.php?do=postthread&f=331) around 14:38 EDT

Lots of code tags.

---

### Post by sajoupa on 2021-10-08
> **TheFu said:**
> Got the 403 error yesterday and today trying to create a new thread.
[https://ubuntuforums.org/newthread.php?do=postthread&f=331](https://ubuntuforums.org/newthread.php?do=postthread&f=331) around 14:38 EDT

Lots of code tags.

Hi,
Sorry for the delay, I just pushed a fix for this error. It should work fine now.

---

### Post by TheFu on 2021-10-13
[https://ubuntuforums.org/editpost.php?do=updatepost&postid=14062723](https://ubuntuforums.org/editpost.php?do=updatepost&postid=14062723)
around Wed 13 Oct 2021 02:31:48 PM EDT

I was trying to add some code tags around a few existing blocks.

---

### Post by TheFu on 2021-10-15
Fri 15 Oct 2021 12:25:41 PM EDT
[https://ubuntuforums.org/editpost.php?do=updatepost&postid=14063059](https://ubuntuforums.org/editpost.php?do=updatepost&postid=14063059)

---

### Post by sajoupa on 2021-10-21
Hi,
I just pushed a fix for the last report. For the previous one I couldn't find the complete relevant logs, but I believe that it should also be covered by that same fix.

--
sajoupa

---

