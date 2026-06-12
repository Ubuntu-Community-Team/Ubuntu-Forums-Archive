---
title: "Firefox: unable to post wordpress, ubuntuforums or OWA form"
date: 2009-02-11
forum: Desktop Environments
---

### Post by Triptol on 2009-02-11
Don't know what is going on here. I use wordpress as my blog and for my company I also have to use Outlook Web Access (OWA).

When I try to post something to my blog, or write an email with OWA with firefox the following happens:

- A long time nothing happens ;-)
- After that long loooooong time firefox asks me whether I want to open or save the post.php (for wordpress), newthread.php (for ubuntuforums) or some .eml file (for OWA).

I already tried the following:
- aptitude purge firefox && aptitude install firefox
- mv .mozilla .mozilla.old

and combinations of the above. 

I personally think something with my mime types is broken, but I have no clue what package is responsible.

Any ideas?

---

### Post by Triptol on 2009-02-12
Found the solution [here]("http://forums.vpslink.com/web-servers/2231-firefox-tries-download-my-php-files.html").

Seems that all you have to do is clear the cache.

---

### Post by Triptol on 2009-04-26
As a last update: seems the D-Link router was at fault as well.

---

