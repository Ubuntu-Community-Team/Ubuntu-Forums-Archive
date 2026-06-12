---
title: "How to Change Unity Panel Transparency by Default"
date: 2013-11-08
forum: Desktop Environments
---

### Post by dannymichel on 2013-11-08
I know you can change the transparency of the unity panel using the tweak tool, but I was wondering what file I would edit in a theme's files to change the transparency of the panel by default. Is it possible? Anyone ever done it?

---

### Post by mc4man on 2013-11-08
Well it's not a theme deal, unity default settings are either in gconf & dconf depending on what Ubuntu release.

Currently they are determined by schemas in /usr/share/glib-2.0/schemas

You can alter those by a certain method though for the most part are only useful when a user account is created
(though I guess one could make use of any avail. means to 'reset to default' to also take advantage of changed default(s)

There is a slight danger in altering schemas in that if done wrong that schemas is ignored which can have some nasty results
(though overall pretty easy & a warning is always issued if done wrong.

If you wish to pursue further then just ask.

---

