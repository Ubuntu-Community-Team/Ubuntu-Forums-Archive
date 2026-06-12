---
title: "problem with wget"
date: 2006-09-04
forum: Desktop Environments
---

### Post by geuis on 2006-09-04
Hi, hoping someone can answer something for me about wget.

If I use straight url's, no problem. [http://www.cnn.com](http://www.cnn.com), [http://www.ubuntuforums.org](http://www.ubuntuforums.org), etc.

However, when I am using dynamic urls I start running into problems.

If I use [http://jtpre.com/index.php?page=jtpmi](http://jtpre.com/index.php?page=jtpmi) its storing the index.php file as index.php?page=jtpmi.html. How can I make it drop everything after ?page=... 

Here's my wget string:
wget -nd -nH -p -k -E --user-agent="Mozilla/5.0 (Windows; U; Windows NT 5.1; es-ES; rv:1.8.0.6) Gecko/20060728 Firefox/1.5.0.6" [http://jtpre.com/index.php?page=jtpmi](http://jtpre.com/index.php?page=jtpmi) -Psites/

---

