---
title: "Search gives too many results because it uses &quot;OR&quot;"
date: 2011-08-04
forum: Forum Feedback &amp; Help
---

### Post by Paddy Landau on 2011-08-04
Usually, when I search (I use the Advanced Search), it uses an implied AND with all keywords. So, if I enter (say) [FONT=Courier New]virtualbox 1908[/FONT] in the keywords, it returns only threads with both [FONT=Courier New]virtualbox[/FONT] and [FONT=Courier New]1908[/FONT] in it.

However, today, it is adding an OR between the words, so I get results with either [FONT=Courier New]virtualbox[/FONT] or [FONT=Courier New]1908[/FONT] -- making it hard to find what I'm looking for.

Screenshot:
_[IMG]http://ubuntuforums.org/attachment.php?attachmentid=199232&stc=1&d=1312476657[/IMG]_

How do I get the search facility to use AND instead of OR?

---

### Post by jpeddicord on 2011-08-07
I'm not actually seeing the OR at the moment, but if you want to be explicit, just add AND in between: "virtualbox AND 1908"

If that doesn't get you the results you want, try "+virtualbox +1908". That ensures that both words are present.

---

### Post by Paddy Landau on 2011-08-08
> **jpeddicord said:**
> I'm not actually seeing the OR at the moment, but if you want to be explicit, just add AND in between: "virtualbox AND 1908"

If that doesn't get you the results you want, try "+virtualbox +1908". That ensures that both words are present.
Thanks for the advice, but I have already tried AND -- the search ignores it. I also tried using the + signs as you suggested -- again, ignored. I still get the OR.

This is most frustrating.

Any other ideas? Could it be some setting in the [User Control Panel]("http://ubuntuforums.org/usercp.php")?

---

### Post by sikander3786 on 2011-08-08
For me, including 'and' in the search term has no effect whereas 'or' works by filtering the results the same way as expected.

If none of those words is included, I get results for 'keywords1, keyword2'. Nothing in between so that is reasonable behaviour.

So what I can confirm is that not everyone is experiencing the same behaviour as you. And I couldn't find any settings in User CP, might be some mod can ;)

---

### Post by Paddy Landau on 2011-08-08
@sikander3786: Thanks. It confirms that I am getting different results from you. Here's hoping for a solution...

---

### Post by Paddy Landau on 2011-08-08
Ah, I've just realised something. I noted in parentheses in my first post that I use the Advanced Search. I have discovered that the Advanced Search uses OR (for me), whereas the little search box at the top right of the page uses AND.

Hmm. How do I get the Advanced Search to use AND?

---

### Post by sikander3786 on 2011-08-08
> **Paddy Landau said:**
> Ah, I've just realised something. I noted in parentheses in my first post that I use the Advanced Search. I have discovered that the Advanced Search uses OR (for me), whereas the little search box at the top right of the page uses AND.

Hmm. How do I get the Advanced Search to use AND?
LOL. This just came to my mind. Did you try with some other web browser? It can't be the browser but who knows ;)

---

### Post by Paddy Landau on 2011-08-08
> **sikander3786 said:**
> Did you try with some other web browser? It can't be the browser but who knows ;)
Well, it could be something stored in the cookies.

I just tried with Chromium (also using AND and +), and sadly I get the same results; it still uses OR in the Advanced Search.

** EDIT:** I just logged out, and this time the Advanced Search gives me what I want! Therefore, it must be something to do with my settings.

---

### Post by jpeddicord on 2011-08-08
> **Paddy Landau said:**
> ** EDIT:** I just logged out, and this time the Advanced Search gives me what I want! Therefore, it must be something to do with my settings.

Interesting... there's no User CP setting that I know of that does that. :P

---

### Post by Paddy Landau on 2011-08-09
> **jpeddicord said:**
> Interesting... there's no User CP setting that I know of that does that. :P
Well, if we can't figure it out (and I've tried!), I'll just have to log out whenever I want to search, and log in again to post :(

---

### Post by sikander3786 on 2011-08-09
> **Paddy Landau said:**
> Well, if we can't figure it out (and I've tried!), I'll just have to log out whenever I want to search, and log in again to post :(
Or use a different browser for searching until this is solved ;)

---

### Post by uRock on 2011-08-11
Logging out clears the cookies.

---

### Post by robert shearer on 2011-08-12
Just don't user the forum search, it is very poor...
Instead use your favorite search engine and ...

```
site:ubuntuforums.org  <search terms> 
```

---

### Post by Paddy Landau on 2011-08-12
> **robert shearer said:**
> Just don't user the forum search, it is very poor...
Instead use your favorite search engine and ...
```
site:ubuntuforums.org  <search terms> 
```
Not a bad idea. Thank you.

Still, I'd love to have the search on the forums working, because I often find it useful (in the Advanced Search) to limit the search to the title and to a specific set of sub-forums.

---

### Post by robert shearer on 2011-08-13
> **Paddy Landau said:**
> Not a bad idea. Thank you.

Still, I'd love to have the search on the forums working, because I often find it useful (in the Advanced Search) to limit the search to the title and to a specific set of sub-forums.

Perhaps try...
```
site:ubuntuforums.org  <title> <sub forum>
```  ??

I just tried googling..

site:ubuntuforums.org searching forum feedback 

and the first 3 pages were in the "forum feedback and help" sub forum and the first hit was on this thread !   so seems to work as you desire.... :D

---

### Post by Paddy Landau on 2011-08-13
Thanks, Robert. I'll give it a bash.

---

### Post by jpeddicord on 2011-08-13
[http://search.ubuntu.com/](http://search.ubuntu.com/) may be of use also, if you're looking for something a little more broad.

---

### Post by Paddy Landau on 2011-08-13
> **jpeddicord said:**
> [http://search.ubuntu.com/](http://search.ubuntu.com/) may be of use also, if you're looking for something a little more broad.
Gosh, I'd never seen that. I'll try it, thanks.

---

### Post by Paddy Landau on 2011-09-19
I'm bumping this thread, because...

I'm searching for "k3b hangs", and I select the option "Search Titles Only", otherwise I get a huge number of irrelevant posts.

Unfortunately, even if I log out, I still get posts without "hangs" in the title (see attachment -- note the discrepancy between the keywords and the results).

What's happening? Am I doing something wrong? Why do my searches on the forum no longer work?

I've tried Google as a replacement, but I'm finding it difficult to narrow down the search. The Ubuntu Forums search facility, when it used to work, was perfect.

---

### Post by robert shearer on 2011-09-19
Hi Paddy,
Try...
> site:ubuntuforums.org k3b hangs

in Google and use the filter 'Past year'.
This gives me 59 results all with 'hangs'.

Cheers, Bob.

---

### Post by Paddy Landau on 2011-09-19
> **robert shearer said:**
> ... in Google and use the filter 'Past year'.
This gives me 59 results all with 'hangs'...
Bob, I have read that Google gives different results to different people.

This experiment has just proved it correct.

I get exactly two (!) relevant results.

But thanks for the suggestion.

---

### Post by robert shearer on 2011-09-19
> **Paddy Landau said:**
> Bob, I have read that Google gives different results to different people.

This experiment has just proved it correct.

I get exactly two (!) relevant results.

But thanks for the suggestion.

That does seem strange, so I just used **google.uk **and got the same results as I did before (using Google NZ)..59 !
Then used filters 'past year' **and** 'pages from the UK' (in Google.uk) together and again got 59.

Maybe your Google needs new oil or some anti-freeze...:) otherwise I am at a loss...:confused:

cheers, Bob.

---

### Post by Paddy Landau on 2011-09-19
Ah, I must have done something wrong, sorry. :redface: I get the same results as you now.

Thanks.

---

