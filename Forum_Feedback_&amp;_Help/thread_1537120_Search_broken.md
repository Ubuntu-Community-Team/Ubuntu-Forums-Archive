---
title: "Search broken"
date: 2010-07-23
forum: Forum Feedback &amp; Help
---

### Post by likemagic on 2010-07-23
Hi,

I have used bulletin boards since the mid 80's and I have never seen one with such a broken search. Without a proper search the history & accumulated knowledge is useless.

I tried searching the "installation & upgrades" for upgrade "10.04" and get:
"Sorry - no matches. Please try some different terms" which is absolute bullshit.

Maurice
Ubuntu 9.10 (alt install) with problems upgrading to 10.04 on VIA EPIA-M motherboard

---

### Post by JackNocturne on 2010-07-23
> **likemagic said:**
> Hi,

I have used bulletin boards since the mid 80's and I have never seen one with such a broken search. Without a proper search the history & accumulated knowledge is useless.

I tried searching the "installation & upgrades" for upgrade "10.04" and get:
"Sorry - no matches. Please try some different terms" which is absolute bullshit.

Maurice
Ubuntu 9.10 (alt install) with problems upgrading to 10.04 on VIA EPIA-M motherboard


Search using **google** , include **ubuntuforums** in your search, i never use the site searcher
,somehow it doesn't search what i want

---

### Post by ajgreeny on 2010-07-23
Try [www.googlubuntu.com](www.googlubuntu.com) as well; it searches other sites as well as this forum and is very good.

---

### Post by VastOne on 2010-07-24
What of the OP's original issue and questions though...

I have always had a difficult time with searches here and am just curious as to why they are so bad?

Example...searching for threads with last.fm, will not bring any results because "last" is too common of a word.

That is quite lame as I am not searching for last but last.fm and what determines a word as too common?

I do use google and googleubuntu for searches effectively but there a lot of stickies that point out using the search features here, not to mention that I advocate that same advice to users,  but it is to the point of telling ppl to go outside the forum to find the results that will bring them right back to the forum...this is kind of dizzying~!!!

---

### Post by ajgreeny on 2010-07-26
> **VastOne said:**
> What of the OP's original issue and questions though...

I have always had a difficult time with searches here and am just curious as to why they are so bad?

Example...searching for threads with last.fm, will not bring any results because "last" is too common of a word.

That is quite lame as I am not searching for last but last.fm and what determines a word as too common?

I do use google and googleubuntu for searches effectively but there a lot of stickies that point out using the search features here, not to mention that I advocate that same advice to users,  but it is to the point of telling ppl to go outside the forum to find the results that will bring them right back to the forum...this is kind of dizzying~!!!
Well, yes, I agree it would be good to help answer the OP's question, but I'm not sure how we can do anything to improve the search facility on this forum.  I presume it's a problem related to the software used to host the forum, vBulletin(?) so it is probably out of the forums total control.

Our answers were just workarounds I agree, but better than nothing, and if you want to search just ubuntuforums, you can use ```
searchword or phrase site:ubuntuforums,org
``` in the google search box, instead of using googlubuntu.com

---

### Post by sisco311 on 2010-07-26
Hopefully vBulletin 4.0 will solve this issue. According to their web site, they have improved the search engine.

---

### Post by Morbius1 on 2010-07-26
Create a small file:
```
gksu gedit /usr/lib/firefox-addons/searchplugins/ubuntu-forums.src
```With this content:
```
<search 
 name="Ubuntu-Forums"
 method="GET"
 action="http://www.google.com/search"
 queryCharset="utf-8"
> 

  <input name="q" user>
  <input name="sitesearch" value="ubuntuforums.org">
</search>
```Save the file and restart firefox.

You should now have a new entry in the search drop-down box labeled "Ubuntu Forums" It's basically an automated way of doing what **ajgreeny **suggested[B].
[/B]

---

### Post by VastOne on 2010-07-26
> **Morbius1 said:**
> Create a small file:
```
gksu gedit /usr/lib/firefox-addons/searchplugins/ubuntu-forums.src
```With this content:
```
<search 
 name="Ubuntu-Forums"
 method="GET"
 action="http://www.google.com/search"
 queryCharset="utf-8"
> 

  <input name="q" user>
  <input name="sitesearch" value="ubuntuforums.org">
</search>
```Save the file and restart firefox.

You should now have a new entry in the search drop-down box labeled "Ubuntu Forums" It's basically an automated way of doing what **ajgreeny **suggested[B].
[/B]

lol, I have been using this and ajgreeny suggested for years, bit I bet this will open some other eyes!

---

### Post by VastOne on 2010-07-26
> **Morbius1 said:**
> Create a small file:
```
gksu gedit /usr/lib/firefox-addons/searchplugins/ubuntu-forums.src
```With this content:
```
<search 
 name="Ubuntu-Forums"
 method="GET"
 action="http://www.google.com/search"
 queryCharset="utf-8"
> 

  <input name="q" user>
  <input name="sitesearch" value="ubuntuforums.org">
</search>
```Save the file and restart firefox.

You should now have a new entry in the search drop-down box labeled "Ubuntu Forums" It's basically an automated way of doing what **ajgreeny **suggested[B].
[/B]

Morbius,

Would you happen to know where to place this file if you are using Chromium?

I looked but there is no plugin directory structure under the Chromium setup.

Thanks

Thanks

---

### Post by Morbius1 on 2010-07-27
> **VastOne said:**
> Morbius,

Would you happen to know where to place this file if you are using Chromium?

I looked but there is no plugin directory structure under the Chromium setup.

Thanks
No I don't know how to do this on Chromium. I'm still looking for a "Print" button on the $&#@ thing :p

---

