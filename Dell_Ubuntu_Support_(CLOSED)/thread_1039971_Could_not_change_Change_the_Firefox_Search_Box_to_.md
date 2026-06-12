---
title: "Could not change Change the Firefox Search Box to Use Google's New Favicon"
date: 2009-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shiningkenmonster on 2009-01-15
here is the link for windows firefox. but no help with ubuntu's firefox. is there a command line to do this too?

[http://lifehacker.com/5130910/change-the-firefox-search-box-to-use-googles-new-favicon](http://lifehacker.com/5130910/change-the-firefox-search-box-to-use-googles-new-favicon)

> mc4man says:
Very simple
Go here and right click on link "save link as"
That will download 'google.xml' to your desktop

[http://mozillalinks.org/wp/2009/01/u...favicon-again/](http://mozillalinks.org/wp/2009/01/u...favicon-again/)

Then search in filesystem for google.xml and replace with the new one.

Should be in /usr/libs/firefox-addons/searchplugins

Tested and works fine.

Edit: I would copy the old one somewhere before replacing in case you want to go back to orig.

Which i did get right click and use 'save link as' to download the new google.xml - I found the actual file folder. But it would not let me copy the new google.xml to the old google.xml - yet it would not let me delete the old google.xml

is there another way around this to get this to work. I believe this doesn't work because dell and canonical made a custom web browser like wire-protect,  instead of the original firefox. which should work but it doesn't. does anyone else have this kind of problem who has the dell's custom version of Ubuntu running on LPIA. Which is updating the new Google icon on the search box, for the web browser ? anyone found a solution?

---

