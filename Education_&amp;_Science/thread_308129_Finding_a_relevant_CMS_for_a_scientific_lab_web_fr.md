---
title: "Finding a relevant CMS for a scientific lab web frontend"
date: 2006-11-27
forum: Education &amp; Science
---

### Post by LevTermen on 2006-11-27
Hi,

I need to refresh the current web frontend of my lab, which is as of now based on a custom engine, thus hard to keep up to date and flexible.

I'm in the process of searching a relevant CMS engine (or similar) that would do the job, the automation of publications and projects per lab member by accessing a database being mandatory.

After some quick googling, I've found the following addons for Plone:
[http://www.ecology.uni-kiel.de/ecology/site/projects-en/plone-project]("http://www.ecology.uni-kiel.de/ecology/site/projects-en/plone-project")

Have you ever used such solutions? Which (other) one would you recommend me then?

Thanks!
LevTermen

---

### Post by adamkane on 2007-01-29
You want to make sure that the wiki/CMS is UTF-8 and LaTeX enabled. Most CMSes are not UTF-8 enabled by default.

Zope/Plone is great in that it allows you to create a Python based wiki/CMS. Zope/Plone is not for beginners though:
[http://mcelrath.org/Notes/LatexWiki](http://mcelrath.org/Notes/LatexWiki)

However, if you're still learning, you may want use some of the ready-made LAMP CMS options. Mediawiki has several science related macros/extensions:
[http://meta.wikimedia.org/wiki/ASCIIMath4Wiki](http://meta.wikimedia.org/wiki/ASCIIMath4Wiki)

---

### Post by timmie on 2007-02-01
I'd recommend drupal. It has new features in the latest version and several good modules:
[LIST]
[*][http://drupal.org/project/biblio](http://drupal.org/project/biblio)
[*]RSS-Streaming
[*][http://drupal.org/project/usernode](http://drupal.org/project/usernode)
[*]Search for "academic": [http://drupal.org/search/node/academic](http://drupal.org/search/node/academic)
[/LIST]

Before stepping to Plone/Zope I'd rather test it for 2 month the thing is very heavy and not such a out of the box solution as LAMPs. I was administering one site and it was not easy. Well, the software may have changed...

There are some others for science. Wait. 

If you know some German (or [translate it]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.bitoek.uni-bayreuth.de%2Fedv%2Fde%2Fforschung%2Fproj%2Fdetail.php%3Fid_obj%3D27435&langpair=de%7Cen&hl=de&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools")) you could look at [BayCMS]("http://www.bitoek.uni-bayreuth.de/edv/de/forschung/proj/detail.php?id_obj=27435") which was tailored to serve such purpose:
Projects, Chair members, publications etc.

Maybe just send them a email and ask for the code or cooperation?

---

