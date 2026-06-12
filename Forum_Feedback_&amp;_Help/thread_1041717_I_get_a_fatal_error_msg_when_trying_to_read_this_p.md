---
title: "I get a fatal error msg when trying to read this post"
date: 2009-01-16
forum: Forum Feedback &amp; Help
---

### Post by Lostin60's on 2009-01-16
JoshMuffin has a thread called Bump. I know it's accessible because the replies to it keep going up. But when I click on it I get
Fatal error: Allowed memory size of 536870912 bytes exhausted (tried to allocate 145161 bytes) in /srv/www.ubuntuforums.org/public_html/showthread.php on line 1272
Does anyone know why I am getting this, only on that one thread. And can I fix it? Any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by cmnorton on 2009-01-17
Try clearing your cache in your browser, and try re-displaying the page causing the problem.
Shut the browser down, and try re-displaying the page causing the problem.
Reboot, re-start the browser, and try re-displaying the page causing the problem.

Setting your error aside for a moment, the other day I could not get firefox to download the latest version of a pdf file on a web site I maintain. I knew the pdf file was new, and double checked it. After clearing the cache, all was well.

Maybe there was an error, and it is not there now, and you are still caching some problem.

Also, look in your logs under /var/log.

---

