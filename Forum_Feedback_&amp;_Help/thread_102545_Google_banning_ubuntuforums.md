---
title: "Google banning ubuntuforums?"
date: 2005-12-12
forum: Forum Feedback &amp; Help
---

### Post by flurdy on 2005-12-12
Searching for ubuntuforums in google,
[http://www.google.com/search?num=20&q=site%3Aubuntuforums.org]("http://www.google.com/search?num=20&q=site%3Aubuntuforums.org"),
google responds with 403 forbidden and a warning about viruses!?!?

However by removing the num=20 (how many links per page) the query works fine. Looks like a caching problem by google. 

How odd.

It did get me concerned for a few secs, then I remembered Im not using Windows.

---

### Post by earobinson on 2005-12-12
weird, no clue whats going on [http://www.google.com/search?num=20&q=site%3Aibm.com](http://www.google.com/search?num=20&q=site%3Aibm.com) works however

---

### Post by flurdy on 2005-12-12
Weird init?

In case google fixes it, [this is what google]("http://www.ivar.co.uk/cargo/googleban.png") is currently responding with when searching for ubuntuforums

---

### Post by flurdy on 2005-12-12
Google dont like forums,
This doesnt work either
[http://www.google.com/search?num=20&q=site%3Amathforum.org]("http://www.google.com/search?num=20&q=site%3Amathforum.org")

---

### Post by earobinson on 2005-12-12
maybe the forum search is bugged Im not worried google will fix this.

---

### Post by megamania on 2005-12-12
works perfectly for me...

---

### Post by flurdy on 2005-12-12
[QUOTE=megamania]works perfectly for me...[/QUOTE]

Does it really?

What url did you use?

Everyone ive spoken today has the same problem

---

### Post by earobinson on 2005-12-12
Weird, Will try it when I get home, right now im on a large windows network.

---

### Post by majikstreet on 2005-12-12
flurdy,
there is a thread about this somewhere on the forums... the bug also is found when you type "phpbb" into the firefox search bar in linux..

---

### Post by earobinson on 2005-12-12
[QUOTE=majikstreet]flurdy,
there is a thread about this somewhere on the forums... the bug also is found when you type "phpbb" into the firefox search bar in linux..[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=101742&highlight=phpbb](http://www.ubuntuforums.org/showthread.php?t=101742&highlight=phpbb) thats the thread

---

### Post by Goddess_of_Linux on 2005-12-12
I can get the follow a okay...
-Fedora Forum
-Linux Forums
-Ubuntu Forums
-Winguides.com/forums which is under Windows Forums Google Search
-Forums.techguy.org
-and lots more...

I am currently using windows and fedora and ubuntu and OS-X, all of them seem to work...

---

### Post by GreyFox503 on 2005-12-13
I went to Google myself and queried "ubuntuforums" and "ubuntuforums.org" and both gave me correct results.

---

### Post by flurdy on 2005-12-13
[QUOTE=GreyFox503]I went to Google myself and queried "ubuntuforums" and "ubuntuforums.org" and both gave me correct results.[/QUOTE]

You didnt read the post.
That has worked fine all along.

But if you search for site:ubuntuforums.org
(which returns all pages within ubuntuforums.org)
and specify you want 20 rows/links/pages returned per page,
then it wont work. 
The final url will be 
/search?num=20&q=site%3Aubuntuforums.org

and if you replace ubuntuforums with other forum sites it also foobars

---

### Post by M3ta7h3ad on 2005-12-13
[QUOTE=flurdy]Searching for ubuntuforums in google,
[http://www.google.com/search?num=20&q=site%3Aubuntuforums.org]("http://www.google.com/search?num=20&q=site%3Aubuntuforums.org"),
google responds with 403 forbidden and a warning about viruses!?!?

However by removing the num=20 (how many links per page) the query works fine. Looks like a caching problem by google. 

How odd.

It did get me concerned for a few secs, then I remembered Im not using Windows.[/QUOTE]

Someone on your subnet or rather several computers on your subnet have been infected by a worm. Google protects itself against dDos attacks and what not by banning searches from an entire subnet for a short period of time. I believe you can find out more info on the help pages at google.

Its not implying that you have a virus, its just someone/or several people on your subnet has one. :)

---

### Post by unkemptwolf on 2005-12-13
Ubuntuforums uses phpbb (unless I am mistaken). That means that what youre seeing is most likely related to this:

[Virus for PHPBB Spreads via Google]("http://news.netcraft.com/archives/2004/12/21/santy_worm_spreads_through_phpbb_forums.html")

---

### Post by ubuntu-geek on 2005-12-13
[quote=unkemptwolf]Ubuntuforums uses phpbb (unless I am mistaken). That means that what youre seeing is most likely related to this:

[Virus for PHPBB Spreads via Google]("http://news.netcraft.com/archives/2004/12/21/santy_worm_spreads_through_phpbb_forums.html")[/quote] 

We use Vbulletin, however over a year ago we used phpbb for about 3 weeks. All my google tests worked fine.

---

### Post by flurdy on 2005-12-13
[QUOTE=M3ta7h3ad]Someone on your subnet or rather several computers on your subnet have been infected by a worm. Google protects itself against dDos attacks and what not by banning searches from an entire subnet for a short period of time. I believe you can find out more info on the help pages at google.

Its not implying that you have a virus, its just someone/or several people on your subnet has one. :)[/QUOTE]

:rolleyes: 
yes that is what one would think, however as it affects everyone, 
it is more related to google protecting itself from phpBB in general and not peoples subnet.

---

### Post by flurdy on 2005-12-13
[QUOTE=ubuntu-geek]We use Vbulletin, however over a year ago we used phpbb for about 3 weeks. All my google tests worked fine.[/QUOTE]

Probably not long enough for google to derive you were using phpBB, or perhaps the phpBB worm was not a problem then.

---

