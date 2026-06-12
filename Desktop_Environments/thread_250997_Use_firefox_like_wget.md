---
title: "Use firefox like wget?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by geuis on 2006-09-04
Hey, I had a question and I'm just wondering if this is possible.

I'm hammering away at using wget to save single webpages in just the way I want. However, its tricky and not entirely working.

I know that if I do Save As in firefox, it will save ALL of the elements of the page I'm looking at with no problem. Like wget doesn't download images linked from stylesheets, for one thing.

Is there a way from the command line in Linux to have firefox download a given page and save it to a given location? Without having to run the GUI portion at all?

Thanks,

Geuis

---

### Post by aysiu on 2006-09-04
*wget* can download the images and stylesheets, too. If you want just the page and its related files, do ```
wget -c -r -l 1 http://www.*nameofsite*.com
``` If you want the entire website, do ```
wget -c -r http://www.*nameofsite*.com
```

---

### Post by geuis on 2006-09-04
Hi aysiu, there's a reason I was asking about firefox.

I understand how to use wget. This is the string I'm using now:

wget -nd -nH -p -k -E --user-agent="Mozilla/5.0 (Windows; U; Windows NT 5.1; es-ES; rv:1.8.0.6) Gecko/20060728 Firefox/1.5.0.6" [http://www.ubuntuforums.org](http://www.ubuntuforums.org) -Psites/

However we start running into problems such as wget doesn't download the images linked from stylesheets, and if its a dynamic url like index.php?a=123&b=456, wget names the index file as index.php?a=123&b=456.html. I'm sure there are ways around these, among other problems, but I was simply inquiring if anyone has ideas about using Firefox/mozilla with a commandline implement to do it properly.

---

