---
title: "local copy of Wikipedia via Mediawiki =&gt; interwiki"
date: 2009-02-02
forum: General Help
---

### Post by der_hede on 2009-02-02
This is for everyone trying to mirror the Wikipedia for offline viewing at your own localhost :popcorn:

This is not ubuntu related but I want to help everyone else with this problem who searches the way I searched the Internet via search engines and I do not know where else to write it down... I do not have a personal blog and I simply want to spread my anger to the world.

I've downloaded the latest Wikipedia dump (dewiki-latest-pages-articles.xml.bz2 in my case) and successfully added it to my local mysql database. After installing mediawiki and apache2 and some other tools, everything worked fine at http://localhost/wiki/... , EXCEPT the Main Page (Hauptseite) and the navigation sidebar. These were linked to http://en.wikipedia.org/. Even the plain http://localhost/wiki/index.php w/o any Article redirected to http://en.wikipedia.org/wiki/Main_Page.

I've searched the net, read the Mediawiki Manual from top to bottom, to no avail. I even greped the mediawiki installation directory and searched the hole database for "en.wikipedia.org". Didn't found a solution.
I wondered why the link resolves to en.wiki... although I've downloaded the de.wiki... data, but I didn't got it.

Then I've tried to reverse engineer the wikipedia scripts (I'm not a programmer so I call it this way ;-) ) and finally found a solution. 

These are interwiki Links, i.e. handled like "external links", and resolved via the interwiki table in the database.
I changed the "wikipedia" entry from en.wikipedia.org to localhost, et voilà: it works :D

If I did have known what interwiki is before starting my work, I hadn't lost so much time...

---

### Post by ssam on 2009-02-10
a simpler solution would be to use something like aarddict

---

