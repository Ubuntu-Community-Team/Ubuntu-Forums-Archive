---
title: "keep on getting php error when trying to search site"
date: 2012-03-01
forum: Forum Feedback &amp; Help
---

### Post by josephmills on 2012-03-01
title kinda says it all this is the error that I keep on getting 
[php]Fatal error: Maximum execution time of 60 seconds exceeded in /srv/www.ubuntuforums.org/public_html/includes/functions.php on line 4828[/php]
not sure who or what I should do so I made this thread .I am guessing that in functions.php line 4828 there is a timer and that I am asking the search bar to much to fast. or maybe it did not like the fact that I was putting "windows 8" into the search bar don't know.

---

### Post by nothingspecial on 2012-03-01
*Thread moved to **Forum Feedback & Help**.*

---

### Post by CharlesA on 2012-03-01
Worked for me when I tried searching. Seemed to take a little bit longer than usual, but it still finished.

---

### Post by winh8r on 2012-03-01
I just tried the same search and got this result:



> Fatal error: Maximum execution time of 60 seconds exceeded in /srv/www.ubuntuforums.org/public_html/includes/functions.php on line 4830

---

### Post by coffeecat on 2012-03-02
@josephmills, I've managed to reproduce the error you've described. I'll start some investigations but I can't promise anything soon. Do you get this with any other search string?

---

### Post by josephmills on 2012-03-02
Cool thanks for looking into it(I had no clue on what to do ) But in the past with asp and asp.net sites that I have made that not good cross site scripting.Like I said thou I was not sure what to do.

---

### Post by Technoviking on 2012-03-02
The forums staff and Canonical IS are looking into the problem. Hopefully have something soon.

TV

---

### Post by Technoviking on 2012-03-02
We think we have a fix in place, let me know if people still have problems.

TV

---

