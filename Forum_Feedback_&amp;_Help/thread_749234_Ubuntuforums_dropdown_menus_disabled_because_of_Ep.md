---
title: "Ubuntuforums dropdown menus disabled because of Epiphany useragent"
date: 2008-04-08
forum: Forum Feedback &amp; Help
---

### Post by jrib on 2008-04-08
The forums seem to use the useragent to decide whether or not to display the dropdown. As a result, dropdown menus are disabled when viewing the forums in Epiphany (at least on hardy) by default.

To see that the forum's drop down menus work fine when epiphany reports itself as firefox:
* visit about:config in epiphany
* right click -> new -> string: general.useragent.override
* set the value to: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9b5) Gecko/2008040514 Firefox/3.0b5
* refresh your forums page
* observe drop down menus now work

The issue was originally posted in: [http://ubuntuforums.org/showthread.php?t=748635](http://ubuntuforums.org/showthread.php?t=748635) .

The forums should be changed so that they treat epiphany's useragent the same as firefox's.

---

### Post by wieman01 on 2008-04-08
The admins are working on the issue. Thanks for taking the time to report this bug.

---

