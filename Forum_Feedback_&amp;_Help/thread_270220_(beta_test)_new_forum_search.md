---
title: "(beta test) new forum search"
date: 2006-10-02
forum: Forum Feedback &amp; Help
---

### Post by ubuntu-geek on 2006-10-02
Hello all..

As we work to improve the forums we have possibly found a solution to our slow searches. Using the new search we shaved about 9-10 seconds off searches as well as loads off our database server.

The search on the forums main page is using the new search code. You will now be able to do better refined searches such as..

"match all", "match phrase" and "match any"

You will notice new threads will be delayed about 20 minutes in the new search. This is because we run a cron job to rebuild the index of new posts.

---

### Post by Tomosaur on 2006-10-03
I really dislike the new search. The thread titles seem to always be in bold, no matter whether they've been posted in (since your last visit) or not. Is this intentional, or a bug? I'm undecided as to whether the last post preview is a good idea or not, but I prefer the old style of bold text to indicate new posts.

---

### Post by ubuntu-geek on 2006-10-03
> **Tomosaur said:**
> I really dislike the new search. The thread titles seem to always be in bold, no matter whether they've been posted in (since your last visit) or not. Is this intentional, or a bug? I'm undecided as to whether the last post preview is a good idea or not, but I prefer the old style of bold text to indicate new posts.
I think I know what you mean. The search was displaying "post" views instead of the normal (default) thread view on the search result page. This is now fixed.

---

### Post by dolphinsonar on 2006-10-05
Do you discourage the use of this [search engine firefox plugin]("http://mycroft.mozdev.org/download.html?name=ubuntu&sherlock=yes&opensearch=&submitform=Search"):

[IMG]http://mycroft.mozdev.org/images/apple.png[/IMG] [IMG]http://mycroft.mozdev.org/images/ok.png[/IMG] [IMG]http://mycroft.mozdev.org/install.php/7130/ubuntuforums.png[/IMG] _Ubuntu Forums_ [IMG]http://mycroft.mozdev.org/images/semi.png[/IMG] [IMG]http://mycroft.mozdev.org/images/flags/WW.png[/IMG] (_ubuntuforums.org_)

Its pretty handy, I use it all the time, I hope it doesn't hurt the server load...

---

### Post by mips on 2006-10-05
Does this mean the  		Search Forums *OLD METHOD* is eventually going to fall away ? I hope not.

---

### Post by ubuntu-geek on 2006-10-05
> **mips said:**
> Does this mean the  		Search Forums *OLD METHOD* is eventually going to fall away ? I hope not.
Yeah, 95% sure it will. It is just to taxing on the servers right now. I should note the new search doesn't have all the features added yet.

---

### Post by mips on 2006-10-05
> **ubuntu-geek said:**
> Yeah, 95% sure it will. It is just to taxing on the servers right now. I should note the new search doesn't have all the features added yet.

Ok. So does this mean we will have a search by userid field etc. I use the userid field a lot.

---

### Post by ubuntu-geek on 2006-10-05
> **mips said:**
> Ok. So does this mean we will have a search by userid field etc. I use the userid field a lot.
Yes you will be able to search by userid :)

---

### Post by ubuntu-geek on 2006-10-06
The new search has been implemented. You can now search using "match all", "match phrase" and "match any"  just like with search engines.

---

### Post by Zyzzyx on 2006-10-06
A'right, so we're up and going.

But its back to the default of listing posts as the result, not threads. And I'm not seeing anywhere to change it.

---

### Post by kleeman on 2006-10-06
When I search for posts by my username I only recover threads which I started not threads that I have replied to (I selected posts not threads). This is quite annoying as it is my main method for keeping track of other people's responses to my posts. I used the old search all the time so this change has seriously compromised my ability to efficiently use the site...

I am assuming this is a bug.

---

### Post by GStubbs43 on 2006-10-06
You can just click the quick search and select "Find all Your Posts" ;)

---

### Post by kleeman on 2006-10-06
Yeah that works although it does not show who and when last responded in the thread which is useful. I still think the problem I mentioned above is a bug. Why specify that your posts are being searched for and then only show threads you started....

---

### Post by ubuntu-geek on 2006-10-06
There are a few bugs.. :)

---

### Post by mips on 2006-10-07
> **ubuntu-geek said:**
> There are a few bugs.. :)

Would the following be one of them ?

If I enter my userid into User Name field and change/select nothing else I only see posts from a week back and nothing newer ?

The previous search would return a list of ALL my posts on a per thread basis up to the very minute.

This is just an example, usually I also use the Key Word(s) feature in conjunction with the above.

---

### Post by Kateikyoushi on 2006-10-07
> **dolphinsonar said:**
> Do you discourage the use of this [search engine firefox plugin]("http://mycroft.mozdev.org/download.html?name=ubuntu&sherlock=yes&opensearch=&submitform=Search"):

[IMG]http://mycroft.mozdev.org/images/apple.png[/IMG] [IMG]http://mycroft.mozdev.org/images/ok.png[/IMG] [IMG]http://mycroft.mozdev.org/install.php/7130/ubuntuforums.png[/IMG] _Ubuntu Forums_ [IMG]http://mycroft.mozdev.org/images/semi.png[/IMG] [IMG]http://mycroft.mozdev.org/images/flags/WW.png[/IMG] (_ubuntuforums.org_)

Its pretty handy, I use it all the time, I hope it doesn't hurt the server load...

I didn't know about this, is a new one (which is compatible with the new search engine) in the making ?

---

### Post by ubuntu-geek on 2006-10-07
> **mips said:**
> Would the following be one of them ?

If I enter my userid into User Name field and change/select nothing else I only see posts from a week back and nothing newer ?

The previous search would return a list of ALL my posts on a per thread basis up to the very minute.

This is just an example, usually I also use the Key Word(s) feature in conjunction with the above.
Yeah good find.. thanks for pointing that out.

---

### Post by LKRaider on 2006-10-08
I used to do this search to keep track of all threads I ever posted in, and it showed them in thread view mode:
[http://ubuntuforums.org/search.php?do=process&showposts=0&starteronly=0&exactname=1&searchuser=LKRaider](http://ubuntuforums.org/search.php?do=process&showposts=0&starteronly=0&exactname=1&searchuser=LKRaider)

Now that search doesn't work anymore as it did. I can't keep track of wether the threads were updated or not :(

---

### Post by amorangi on 2006-10-08
A lot of results are missing - searches that used to return 20+ results now return about 3. It's made this forum, which used to be an excellent resource, a very mediocre one.

---

### Post by Sef on 2006-10-08
> A lot of results are missing - searches that used to return 20+ results now return about 3. It's made this forum, which used to be an excellent resource, a very mediocre one.

The new search is a beta, so bugs are to be expected.  In time the bugs will be worked out and you will be able to search like before.

---

### Post by mips on 2006-10-08
> **amorangi said:**
> A lot of results are missing - searches that used to return 20+ results now return about 3. It's made this forum, which used to be an excellent resource, a very mediocre one.

Be patient, they are fixing things. For a free forum you seem a bit ungratefull.

---

### Post by amorangi on 2006-10-08
I'm not being ungrateful, I don't know where you get that from, I'm providing feedback. 

There seems to be a real problem with a lot of ad hominem attacks for providing negative feedback throughout this forum. 1 negative feedback is worth 10 positive feedbacks, or else how will things ever improve? Accepting critisism is a mark of maturity and wisdom.

---

### Post by ubuntu-geek on 2006-10-08
Amorgani thanks for pointing this out. The new search uses boolean search methods unlike the old way, so yeah in a sense searching is going to be a little different. However, more accurate.

There are still some kinds we are working out, the trade off is worth the amout of server resources we are saving right now in preperation for the Eft release.

---

### Post by bluenova on 2006-10-09
Is it just me, or are others finding it really hard to find relevent posts now? I used to get really good results, now I'm finding it hard to get anything.

Any tips? For instance how do I find out about converting mpg to vob? I don't think I can search with the terms mpg or vob any more, perhaps they are too short.

For now I'm having to use google
site:ubuntuforums.org searchterm

---

### Post by picpak on 2006-10-09
Agreed. I searched "usplash" and got no results!

---

### Post by ubuntu-geek on 2006-10-09
> **picpak said:**
> Agreed. I searched "usplash" and got no results!
because I turned the search off real quick.. :) to fix a few things..

---

### Post by ubuntu-geek on 2006-10-09
You can now search for three letter keywords.. Also the new search engine uses full text.

---

### Post by McQuaid on 2006-10-10
Here's another vote for the old method.  I know it can be tough to change users ways, and I'm not being ungrateful either, and yes it's great you've taken a load of the servers.  But it seems right now at the cost of the search.  This is one of the biggest assets ubuntu has, and now it has been a source of frustration.  

I could list my dislikes but in the end I'd be just listing off the features of the old search to be reincorporated.  I guess a big thing is the actual results are not visually digestable.  I don't want to see bits of each post and see threads, I liked just seeing the title post and who posted last and when, # of replies etc.  Yes, pretty much all that info is there and more, it just feels some what jarring trying to filter out what's not relevant and focusing in on the posts believed to be by the user as what he/she is looking for.

It was perfect, I could always find relevant searches and it was never a source of frustration.  When these things are already in motion I doubt you'd be going back but I felt I had to through my 2 cents in as well.

Yes it's a definite benefit that it's saving the servers, but if you did a poll and found the majority of users don't like the new search, would that sway you?

Again, I'm sure a lot of work is being done, and I understand it's not the greatest feeling when one works hard on something and one feels that it's not appreciated.  But maybe another way of tackling this would be to look at other database optimizations while maintaining the same face for the search.

---

### Post by bluenova on 2006-10-10
Thanks for adding 3 letter search ubuntu-geek.

The speed of the site has certainly got better, I guess there are just a few things to work out to get the search working well.

---

### Post by ubuntu-geek on 2006-10-10
> **McQuaid said:**
> Here's another vote for the old method.  I know it can be tough to change users ways, and I'm not being ungrateful either, and yes it's great you've taken a load of the servers.  But it seems right now at the cost of the search.  This is one of the biggest assets ubuntu has, and now it has been a source of frustration.  

I could list my dislikes but in the end I'd be just listing off the features of the old search to be reincorporated.  I guess a big thing is the actual results are not visually digestable.  I don't want to see bits of each post and see threads, I liked just seeing the title post and who posted last and when, # of replies etc.  Yes, pretty much all that info is there and more, it just feels some what jarring trying to filter out what's not relevant and focusing in on the posts believed to be by the user as what he/she is looking for.

It was perfect, I could always find relevant searches and it was never a source of frustration.  When these things are already in motion I doubt you'd be going back but I felt I had to through my 2 cents in as well.

Yes it's a definite benefit that it's saving the servers, but if you did a poll and found the majority of users don't like the new search, would that sway you?

Again, I'm sure a lot of work is being done, and I understand it's not the greatest feeling when one works hard on something and one feels that it's not appreciated.  But maybe another way of tackling this would be to look at other database optimizations while maintaining the same face for the search.
The old search method wont be coming back unless a miracle happens and we somehow receive another server for forum searching.

---

### Post by McQuaid on 2006-10-11
Yes, I think I pretty much said that I know once these things are in motion, they're not going back to the old way.  But I just did a search and the results were displayed the old way!! This was my biggest gripe and can definitely with it.

---

### Post by mips on 2006-10-12
ubuntu-geek,

Would it not be a better option to have the Key Word(s) field default to 'Search Entire Post' instead of 'Search Titles Only'

You don't find much with a titles search and it's a bit annoying having to click the dropdown everytime in order to change the default.

---

### Post by ubuntu-geek on 2006-10-12
> **mips said:**
> ubuntu-geek,

Would it not be a better option to have the Key Word(s) field default to 'Search Entire Post' instead of 'Search Titles Only'

You don't find much with a titles search and it's a bit annoying having to click the dropdown everytime in order to change the default.
If you search via the normal search page it will default to use the entire post. However, I'll have to check the search on the upper right corner and on the frontpage those might only search titles.

---

### Post by mips on 2006-10-12
> **ubuntu-geek said:**
> If you search via the normal search page it will default to use the entire post. However, I'll have to check the search on the upper right corner and on the frontpage those might only search titles.

I think I'm loosing my mind. I could have sworn the search page was set to Subject Title as I had to manually change it. Thanks though.

---

### Post by hopstah on 2006-11-04
i agree that having the quick search boxes default to searching the entire post as opposed to just the thread title would be great.  searching the thread titles only is much less useful than the entire post, since so many posts are titled with "help!" and other worthless strings.

---

