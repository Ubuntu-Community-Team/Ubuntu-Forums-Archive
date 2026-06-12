---
title: "My themes looks ugly"
date: 2006-12-27
forum: Desktop Environments
---

### Post by b3njo on 2006-12-27
I've got some troubles with installing new themes. The temes i install looks verry ugly , if you look on my desktop [_here_]("http://img360.imageshack.us/img360/3668/uglyxf0.png") dor an example. And look on the orginal [_here_]("http://www.deviantart.com/deviation/29569009/") you will se it's verry diffirent and ugly and the colors is not matched and the bar of the bottom is ugly. I have smiliar problems with all new themes i try to install. And yes, i put every theme in /home/b3njo/.theme. :p 

Any one who knows whats wrong?

---

### Post by Lord Illidan on 2006-12-27
Edit the themedetails and chose different controls.

---

### Post by b3njo on 2006-12-27
Where? Under System / Preference / Themes? :confused:

---

### Post by mcduck on 2006-12-28
No, that's not the problem. But instead, I bet you haven't installed theme engine that theme is using..

Looks like rezlooks to me. Also, you'd better install gtk2-engines-pixbuf from the universe repositories, many themes need that to work correctly.

---

### Post by b3njo on 2006-12-28
Yeah.. It works!! Thanks!!!! :D

---

### Post by phunkycow on 2006-12-28
> **mcduck said:**
> Also, you'd better install gtk2-engines-pixbuf from the universe repositories, many themes need that to work correctly.

Thank you! I had the same problem. Just solved it with your tip :)

---

### Post by ComplexNumber on 2006-12-28
> **mcduck said:**
> No, that's not the problem. But instead, I bet you haven't installed theme engine that theme is using..

Looks like rezlooks to me. Also, you'd better install gtk2-engines-pixbuf from the universe repositories, many themes need that to work correctly.
thats the right answer. its because the gtk-engine that should be used for that theme isn't installed.

edit: damn! i should have read the posts after that.

---

