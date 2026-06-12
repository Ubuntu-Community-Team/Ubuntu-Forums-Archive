---
title: "Please Remove The Freaking Search Timer"
date: 2007-01-04
forum: Forum Feedback &amp; Help
---

### Post by OffHand on 2007-01-04
Please remove the timer on searches or decrease it to like 5 seconds. It sucks waiting all the time. I think it's very annoying. Thanks in advance.

/discuss

---

### Post by meng on 2007-01-04
It can be annoying, but one might ask WHY you would need to search more than once every 15 seconds. Be more selective with your searches!

---

### Post by OffHand on 2007-01-04
> **meng said:**
> It can be annoying, but one might ask WHY you would need to search more than once every 15 seconds. Be more selective with your searches!

No thanks. Not an option and not realistic.

---

### Post by meng on 2007-01-04
Well I guess that's the end of the discussion.

---

### Post by 23meg on 2007-01-04
It's there for a reason perhaps, to limit server load. Even if you feel very strongly about it, it would be nicer to ask why it's there in the first place, and whether it would be feasible to remove it.

---

### Post by kEinstein on 2007-01-04
Hmm, I don't get your point meng:
Especially new users will not be able to distinguish 'selective' searches from those that are not... In order to give you a few examples of selective searches that result in no/few inappropriate hits try to solve the following issue: 
I'm struggling to find information on a scrambled **cursor** on a **dual**-head system using **fglrx**. The cursor is only corrupted on the secondary (external) screen. Although I have been able to solve this issue via the search function, it took me some time to figure out the correct - and selective - keywords. :-? 

'fglrx cursor dual'  ... no result, penalty: 15 seconds
'fglrx cursor' ... 1 result - inappropriate (not my sort of scrambled cursor, nor does it appear on the secondary screen only), penalty: 15 seconds
'dual cursor' ... 4 results - we are getting there since I posted a link to the solution in one of the threads. Otherwise you'd have to wait another 15 seconds and rephrase your search 

[...]

Guess what is the appropriate thread name that aims at this very issue?
'xorg, dualscreen, ati problem: mouse cursor garbage' :confused: 

... only searching for 'cursor', 'cursor problem' would lead to the thread - but I tried to be SPECIFIC to limit the amount of results and get reasonable solutions via the bold keywords.   :rolleyes: 

Someone else is trying to find info on this very issue. His thread is named 'Dual Monitors Strange Cursor on Second Monitor' ... guess WHY he has not been able to find the appropriate thread for a day? I'm going to post a link to the relevant thread. 

To sum up: 15 seconds are fine in threads that are covered a houndred dozen times in this forum. But don't propose 15 seconds are fine in a more specific case... ](*,)

---

### Post by meng on 2007-01-04
kEinstein:
I'm not the biggest fan of Google, but did you know that if you searched google for:
dual cursor fglrx ubuntuforums
the second hit gives you the thread you cited as the appropriate one?

Google's server bandwidth is probably ever so slightly bigger than ubuntuforums'.

Yes, I've been hit by the 15-second limit too. Indeed, several times each and every day. I live with it.

---

### Post by 23meg on 2007-01-04
[QUOTE=meng]I'm not the biggest fan of Google, but [/QUOTE]Me neither, but there's even better: "site:[http://www.ubuntuforums.org](http://www.ubuntuforums.org) *foo*" will search for *foo* in the forums.

---

### Post by PriceChild on 2007-01-04
I'm  not the authority on this but....

On average we have 4000 registered users. 3/4 of those being guests who are going to be searching A LOT. 15 seconds IMO is a reasonable amount of time to make a search, and review the results. Would you rather a small amount of users annoyed they have to wait 10 seconds when they make a too precise search, or 5000 users moaning that the forums are slow in general?

Things like this, and removing a couple of stats from the main page have to be done to keep things smooth :)

Its something to think about in that 10 seconds you have to waste :)

Pricey

---

### Post by raul_ on 2007-01-04
It's really annoying with grammar errors though :rolleyes:

---

### Post by kEinstein on 2007-01-04
> **23meg said:**
> Me neither, but there's even better: "site:[http://www.ubuntuforums.org](http://www.ubuntuforums.org) *foo*" will search for *foo* in the forums.

Thank you for your input! I have been searching a lot via the search bar these days - and felt quite annoyed about the time limit. Indeed, the google 'site:URL foo' is a perfect means to bypass server load... I'm going to customize a search plugin for firefox right now. :D

---

### Post by 23meg on 2007-01-04
Good, did you check if there already is one? There is one for the forum's own search here: 

[http://mycroft.mozdev.org/download.html?name=ubuntu+forums&sherlock=yes&opensearch=yes&submitform=Search](http://mycroft.mozdev.org/download.html?name=ubuntu+forums&sherlock=yes&opensearch=yes&submitform=Search)

---

### Post by PriceChild on 2007-01-04
> **23meg said:**
> Good, did you check if there already is one? There is one for the forum's own search here: 

[http://mycroft.mozdev.org/download.html?name=ubuntu+forums&sherlock=yes&opensearch=yes&submitform=Search](http://mycroft.mozdev.org/download.html?name=ubuntu+forums&sherlock=yes&opensearch=yes&submitform=Search)hehe i've got one for the forums and packages.ubuntu.com :)

---

### Post by kEinstein on 2007-01-05
Yes, I already found this one - but again - it uses the forum's search (15 sec. limit applies). I'm thinking of a search plugin that uses google to search the forum via 'site:URL foo'.

---

### Post by matthew on 2007-01-05
> **kEinstein said:**
> Yes, I already found this one - but again - it uses the forum's search (15 sec. limit applies). I'm thinking of a search plugin that uses google to search the forum via 'site:URL foo'.Please post a link if/when you get it put together. :)

---

### Post by steven8 on 2007-01-05
I remember the first time I encountered the 15 second rule.  I said what?, waited the interminable 7 seconds, then searched again.

That's 7 seconds of my life I'll never get back.

---

### Post by Lord Illidan on 2007-01-05
> **steven8 said:**
> I remember the first time I encountered the 15 second rule.  I said what?, waited the interminable 7 seconds, then searched again.

That's 7 seconds of my life I'll never get back.

Aye, let's sue. :mrgreen:

---

### Post by steven8 on 2007-01-05
> Aye, let's sue.

Shame Johnny Cochran's dead. . .

---

### Post by kEinstein on 2007-01-05
Hi there!! 
I have found some time to put a little thingy together :D

[SIZE="4"]**[Search Engine]("http://austrian.n3rds.net/uploads/googleubuntu.tar.gz") for Firefox to search Ubuntuforums.org via Google**[/SIZE]

Q: What does it do?
A: It uses Google to search ubuntuforums.org via implementing a search engine in Firefox. The idea to use 'site:[http://ubuntuforums.org](http://ubuntuforums.org) foo' to search entries has been initiated by 23meg after a [small debate]("http://www.ubuntuforums.org/showthread.php?t=331483") on the 15 sec. time limit when performing searches via the searchbar. 

Q: Why should I use it?
A1: You might want to relief ubuntuforums' server load!
A2: You might want to perform searches without the 15 second limit for whatever reason.

Q: Can I have the code?
A: Of course. Feel free to make changes, improvements or whatever.

Q: Can I customize the plugin to perform searches on other sites?
A: Of course!!! Do the trick by substituting the 'www.ubuntuforums.org' to 'whatsoeverURL' in line 18.


The plugin is available here:
[SIZE="3"][Search Engine]("http://austrian.n3rds.net/uploads/googleubuntu.tar.gz") for Firefox[/SIZE]


As **sudo**, simply untar the content to the following location...
```
/usr/share/firefox/searchplugins
```
... restart Firefox and start using the search engine in the upper right corner (by default)


The archive includes a code 'googleubuntu.src' and a small image 'googleubuntu.gif' to make it look neat.

```
# Firefox plugin file
#
# Google | Ubuntuforums.org search
# by kEinstein 
#
# Last updated: January 5, 2007

<search 
	name="Google | Ubuntuforums.org"
	description="Search Ubuntuforums.org with Google"
	action="http://www.google.com/search"
	searchForm="http://www.ubuntuforums.org/"
	queryEncoding="utf-8"
	queryCharset="utf-8"
	method="GET"
>

<input name="q" value="site%3Ahttp%3A%2F%2Fwww.ubuntuforums.org">
<input name="q" user="">


</search>
```


I am also going to start a new thread - my first one in this forum - and post the plugin.

Cheers!
Hope you enjoy it!

PS: I have tested it using Firefox 2.0.0.1 - I hope it works for you too!

---

### Post by Lord Illidan on 2007-01-05
KEinstein, can you explain how to install it, pls?

EDIT : Ah, you anticipated me :)

---

### Post by kEinstein on 2007-01-05
Of course, I reedited the post - unfortunately I pressed the 'submit' button instead of the 'preview' button.

---

### Post by Lord Illidan on 2007-01-05
> **kEinstein said:**
> Of course, I reedited the post - unfortunately I pressed the 'submit' button instead of the 'preview' button.

Aye, I thought so. Works great.

---

### Post by raul_ on 2007-01-05
Works like a charm, post a HowTo :)

---

### Post by kEinstein on 2007-01-05
Raul, what do you think of exactly? 'How to write my own search engine?'

---

### Post by raul_ on 2007-01-05
No, you can find that in the Mozilla Page :) Just a thread like "Plugin to search forums without time limit" or someting like that and attach your file with the installation instructions ;)

---

### Post by PriceChild on 2007-01-05
You may want to change the descriptions to .org instead of .com :)

---

### Post by kEinstein on 2007-01-05
Yeah, I did so a couple of minutes ago... I don't know why it's not published yet - do new threads have to be approved by the moderators? Sorry, my first thread in this forum.

---

### Post by raul_ on 2007-01-05
I think the How To's have. Once i posted a How To that took so long to get approved, that when it was, it was like 10 pages behind so nobody saw it :mrgreen: but usually it's fast

---

### Post by kEinstein on 2007-01-05
Oouups. :D  Indeed .com instead of .org
Changed it in this thread, as soon as the new thread in the How-To Section is published I'll change  it, too.

---

### Post by PriceChild on 2007-01-05
Thread approved :)

Please please change it from .com to .org :)

---

### Post by ubuntu-geek on 2007-01-05
The search timer is in place to help us keep our server loads nice. We will not be making any changes to it.

---

### Post by po0f on 2007-01-06
kEinstein,

Instead of a whole plugin that gets loaded along with all the bloat that is Firefox, why don't you just create a shortcut?

Go to the [Google](http://www.google.com/) homepage and enter as your search query "site:ubuntuforums.org FOO".  Never mind the results, look at the URL.
```
http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+FOO&btnG=Google+Search
```
We can shorten this to:
```
http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+FOO
```
Now, replace FOO with %s, and create a shortcut with this as the address:
```
http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+%s
```
Give it a keyword, mine is 'guf' (**G**oogle **U**buntu**F**orums).  Now you just have to type in "guf FOO" in the location bar to google search ubuntuforums.  :)

---

### Post by OffHand on 2007-01-06
Thanks for that plugin kEinstein. Really useful.

---

### Post by OffHand on 2007-01-06
> **ubuntu-geek said:**
> The search timer is in place to help us keep our server loads nice. We will not be making any changes to it.


Too bad you do not even consider decreasing the search wait times a bit Ubuntu-Geek. 
Did you ever try changing it to see what the impact would be?

---

### Post by matthew on 2007-01-06
> **OffHand said:**
> Too bad you do not even consider decreasing the search wait times a bit Ubuntu-Geek. 
Did you ever try changing it to see what the impact would be?It was adjusted many times in the past. The current setting was found to be a good balance between usability and server load. 

Too bad you chose the passive-aggressive tone, it makes you seem rude and unfriendly. (Not to mention more than a little self-righteous.)

---

### Post by Stephen Howard on 2007-01-06
I have to agree with the original poster, the search timeout is a pain.  Its so 90s.  

If there really is a problem with the server, then how about doing something like turning on the timer only when load is high?

Or, better still, if load is high, how about limiting the graphics.  For instance, if the server starts to melt, start serving a text only masthead and disable smilies etc.

---

### Post by Stephen Howard on 2007-01-06
oh, you could also stop serving user Avatars - a total waste of space.  There are lots of options to consider before you actual start to reduce access to fundamental features like the search facility.

---

### Post by 23meg on 2007-01-06
> 
Or, better still, if load is high, how about limiting the graphics. For instance, if the server starts to melt, start serving a text only masthead and disable smilies etc.> oh, you could also stop serving user Avatars - a total waste of space. There are lots of options to consider before you actual start to reduce access to fundamental features like the search facility.The kind of load placed on the server by search queries has little to do with the kind placed by serving images.

To all those disturbed by the timer: how about considering donating to the forums if you feel so strongly about this and are serious about making a difference?

---

### Post by OffHand on 2007-01-06
> **matthew said:**
> It was adjusted many times in the past. The current setting was found to be a good balance between usability and server load. 

Too bad you chose the passive-aggressive tone, it makes you seem rude and unfriendly. (Not to mention more than a little self-righteous.)

Oh... I used the word 'sucks'. I'm sorry but.... LOL
If you are that easily offended....

> Please remove the timer on searches or decrease it to like 5 seconds. It sucks waiting all the time. I think it's very annoying. Thanks in advance.

/discuss


---

### Post by Stephen Howard on 2007-01-06
23Meg said:  > The kind of load placed on the server by search queries has little to do with the kind placed by serving images.


I'll take your word for it 23Meg, but it seems to me that every avatar served is taken from a database, and that == load.

As another example, look at the front page - scroll right down to the bottom where no one looks and you'll see that the forum serves up a totally gratuitous list of users - wc showed 462 names.  I'd happily trade that database intensive 'feature' (served to everyone on the main page whether they ask for it or not!) in return for dropping the irritating search timeout.

---

### Post by matthew on 2007-01-06
> **Stephen Howard said:**
> As another example, look at the front page - scroll right down to the bottom where no one looks and you'll see that the forum serves up a totally gratuitous list of users - wc showed 462 names.  I'd happily trade that database intensive 'feature' (served to everyone on the main page whether they ask for it or not!) in return for dropping the irritating search timeout.That feature was removed for an extended period of time while optimizations were made. It's a useful feature that many of us were glad to have returned when it was possible.

Look, I understand why you would like the time between searches limit reset, but it is one among many factors that were weighed in the process of making these forums consistently useful and available, even under heavy loads. I'm sorry you disagree with the decision, but it has been made and ubuntu-geek already said it isn't going to be revisited. If you (plural, not merely the poster I quoted above) wish to continue to rant about it you can do so, but it's not reasonable expect any further reply from staff.

---

### Post by Johan! on 2007-01-06
> **Stephen Howard said:**
> 23Meg said:  


I'll take your word for it 23Meg, but it seems to me that every avatar served is taken from a database, and that == load.

As another example, look at the front page - scroll right down to the bottom where no one looks and you'll see that the forum serves up a totally gratuitous list of users - wc showed 462 names.  I'd happily trade that database intensive 'feature' (served to everyone on the main page whether they ask for it or not!) in return for dropping the irritating search timeout.

Why don't you use poOf's suggestion in [this]("http://ubuntuforums.org/showpost.php?p=1974205&postcount=32") post?
It works great and there's no time limit.

---

### Post by agurk on 2007-01-06
Hmm, using Google to search a forum, sounds like bordering on abuse and the symptom of a problem instead of a solution. Is there *anything* we can do to help here?
I know that Canonical provides the hosting and perhaps this is a reason why not even a fund raising would help (they're their servers, not ours).
If not, I'll shut up, promise. :)

---

### Post by meng on 2007-01-06
> **agurk said:**
> Hmm, using Google to search a forum, sounds like bordering on abuse and the symptom of a problem instead of a solution. Is there *anything* we can do to help here?
Why would it be abuse? Surely you're searching google's cache and not stressing these forums? I hadn't realized Canonical hosted these forums, I thought it was someone else, but in any case I don't see how it's relevant.

---

### Post by matthew on 2007-01-06
> **agurk said:**
> Hmm, using Google to search a forum, sounds like bordering on abuse and the symptom of a problem instead of a solution.I totally understand that perspective. Google does offer this functionality to the public at large so it's not abusive nor a violation of their terms in any way. In fact, it may even help us a little bit in the Google rankings. Now, if we were to offload all searches from our servers to Google's, that would likely cause problems. :)

> **agurk said:**
> Is there *anything* we can do to help here?Unfortunately, I don't think so. I appreciate the attitude, though.

> **agurk said:**
> I know that Canonical provides the hosting and perhaps this is a reason why not even a fund raising would help (they're their servers, not ours).Bingo. We have physical limitations that we are working with. Canonical has been extremely gracious to us but we can't expect such generosity to be unlimited. We're making do with what is available to us and trying to allocate resources in the most useful and equitable way possible. Unfortunately the limits we have mean something has to be sacrificed or compromised on...such as placing a time limit between searches. It's a bummer, but that's life sometimes. You make do the best you can with what you have available to you.

> **agurk said:**
> If not, I'll shut up, promise. :)No stress. We're not opposed to the expression of thoughts, feelings and ideas and any input that comes our way that is helpful and constructive is always welcomed with open arms.

---

### Post by agurk on 2007-01-06
> **meng said:**
> Why would it be abuse? Surely you're searching google's cache and not stressing these forums?
Exactly. We put our search load on someone else (Google). Borderline abuse of Google was my point.

---

### Post by Lord Illidan on 2007-01-06
> **agurk said:**
> Exactly. We put our search load on someone else (Google). Borderline abuse of Google was my point.

Check here :[http://www.google.com/help/features.html](http://www.google.com/help/features.html)

Google advertises this as a feature.
> 
**Site Search**                               [SIZE=-1] The word "site" followed by a colon enables you to restrict your search to a specific             site. To do this, use the **site:sampledomain.com** syntax in the Google search box.[/SIZE]Thus, we are not abusing it.

Edit: And as in terms of the search load, I doubt google search will replace the forum search. It is intended as an alternative in the case of slow forums or timers.

---

### Post by agurk on 2007-01-06
Thanks matthew for explaining. I can live with the Google solution.

(Lord Illidan, I didn't say we were abusing Google, my point was: using a custom made Google search tool to search our own forums is *bordering* on abuse.)

---

### Post by OffHand on 2007-01-06
> **matthew said:**
> No stress. We're not opposed to the expression of thoughts, feelings and ideas and any input that comes our way that is helpful and constructive is always welcomed with open arms.
By calling it ranting?

---

### Post by PriceChild on 2007-01-06
I'm closing this thread.

Reasons have been given why the current situation will not be changing.

Alternatives have been explained to those with larger needs.

Pricey

---

