---
title: "How do I search for a string"
date: 2010-01-29
forum: Forum Feedback &amp; Help
---

### Post by Pelgar on 2010-01-29
Could someone please tell me how to search for a string literal in the Ubuntu Forums? I've tried to find help myself but if it's here somewhere I've been unable to locate it. I have tried enclosing the string in quotation marks, using & between words and even && but nothing seems to work.
If I type "set default resolution" in the Search or Advanced Search text box every post with the work set, default or resolution is listed. There has to be a way to list only those post that have all three words in that order, right?

---

### Post by lisati on 2010-01-29
Dissatisfaction after using the forum's search facility comes up from time to time. Sometimes it's easier to use [Google]("http://lmgtfy.com/?q=%22set+default+resolution%22+site:ubuntuforums.org").

---

### Post by Pelgar on 2010-01-29
Thanks for the prompt reply lisati. Your use Google suggestion actually led me to the Ubuntu Forums solution. I went to [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/) and did my "set default resolution" search. It worked very well but I noticed that Google converted my string to set+default+resolution before doing the actual search. I came back to the Ubuntu Forums and used plus signs, like Google, and it works here too. Now I know!

---

### Post by Morbius1 on 2010-01-29
If you use Firefox ( works with 3.0x anyway ):

Create a new text file with the following code:

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
```Save the above file with an src extension like ubuntu-forums.src to the following location:

/usr/lib/firefox-addons/searchplugins

Restart firefox, select "Ubuntu-Forums" and use the search box to query the forums.

Much as I'd like to take credit for this I found it on another forum.

---

### Post by ajgreeny on 2010-01-29
Or try **[http://www.uboontu.com/](http://www.uboontu.com/)** as your search site.  It contains mostly ubuntuforums, but also various wiki sites etc etc, and can be very useful.

Did you know that rather like the last post, which I didn't know anything about, you can just use the google search box with:-
**your search phrase site:ubuntuforums.org**
That can also be extremely useful.

---

### Post by Pelgar on 2010-01-29
Morbius1, Thanks for the tip! I love that sort of thing and will give it a try. I'll let you know how it works out with Firefox 3.5.7. 

ajgreeny, I did not know I could use **site:ubuntuforums.org **with a search phrase but I will give that a try too. That one will be very helpful for searches at a lot of sites.

Many thanks to both of you.


I may have prematurely marked this one solved. Using plus signs does get only post with all the words in Ubuntu Forum searches but does not bring up only post with that string. 

**[http://www.uboontu.com/](http://www.uboontu.com/)** does work so it is now solved at least. Thanks again ajgreeny.

---

### Post by Pelgar on 2010-01-29
Morbius1, the script you suggested works great in Firefox 3.5.7! Thanks again
If any other newbies try the script, you access it in Firefox via the Search drop-down in the top right corner of the Firefox screen. It took me a lot longer to find it in Firefox than it did to follow Morbius1's excellent instructions and get the .src file written and on the HD. 

ajgreeny, **site:ubuntuforums.org **works well with both Google and Yahoo. It does not seem to work with either if you use a string literal however. But it is still a great new tool that will be used a lot in my quest to learn my way around Ubuntu. Thanks

---

### Post by ajgreeny on 2010-01-30
> It does not seem to work with either if you use a string literal however.What exactly do you mean by that?  What is string literal?

---

### Post by Pelgar on 2010-01-30
Well what I meant last night was:
typing ***"this is a test"** **site:ubuntuforums.org*** into a Google or Yahoo search generated an error but today it works. I have no idea what's up with that. I probably left the closing quotation mark off last night of something along those lines.

When I say string literal I'm referring to a sting in quotation marks. I just looked string literal up at wikipedia and they say it is a programming term. I spend more time programming than anything else but did not realize that string literal was a programming term. Sorry for the confusion!

---

