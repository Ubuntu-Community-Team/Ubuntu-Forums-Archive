---
title: "This is odd."
date: 2005-04-28
forum: Forum Feedback &amp; Help
---

### Post by dirtydan on 2005-04-28
If I try to go directly to a sub forum ie Security Announcements I'm not logged in. If I go through the parent forum ie Offical Ubuntu Announcements then Security Announcements I stay logged in. I'm using Netscape 7.2 browser and Windows 98 (it's my wife's computer). Is this a bug or a feature?

---

### Post by AgenT on 2005-05-16
[QUOTE=dirtydan]If I try to go directly to a sub forum ie Security Announcements I'm not logged in. If I go through the parent forum ie Offical Ubuntu Announcements then Security Announcements I stay logged in. I'm using Netscape 7.2 browser and Windows 98 (it's my wife's computer). Is this a bug or a feature?[/QUOTE]

This is because, for whatever strange reason, some links point to the domain with www and others without. And for another strange reason, the cookies are www specific. That is to say, some links are like [http://www.ubuntuforums.org](http://www.ubuntuforums.org) and others [http://ubuntuforums.org](http://ubuntuforums.org). These two issues combined create the strange situation that if one logs in to the www part, the cookie set is www specific so that any website that does not have the www will not initiate the cookie. Hence you will not be logged in.

Quick Solution: Login to both [http://www.ubuntuforums.org](http://www.ubuntuforums.org) and [http://ubuntuforums.org](http://ubuntuforums.org).

---

### Post by ubuntu-geek on 2005-05-16
hello, I just fixed this I would suggest deleting your cookie and then re-logging into the forums so it will store the correct cookie information for *.ubuntuforum.org :)

---

### Post by AgenT on 2005-05-16
[QUOTE=ubuntu-geek]hello, I just fixed this I would suggest deleting your cookie and then re-logging into the forums so it will store the correct cookie information for *.ubuntuforum.org :)[/QUOTE]

Wow, talk about a quick response :razz:

---

### Post by dirtydan on 2005-05-20
That's better. Thanks.

---

