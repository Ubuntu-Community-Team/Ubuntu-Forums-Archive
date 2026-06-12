---
title: "tracker errpr: locale to UTF8 failed"
date: 2007-10-26
forum: Desktop Environments
---

### Post by DaOane on 2007-10-26
Ubuntu 7.10, tracker 0.6.3

The tracker daemon works, but the tracker-search tool always returns "No results".
On the command line I get the following error when doing a query with tracker-query xxx:

```
** (tracker-query:22401): WARNING **: realpath_in_utf8(): locale to UTF8 failed!
```

Checking the locales with locale -a returns:
```

C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
POSIX

```
Any ideas about what could be wrong? Thanks for any help,

Henning

---

### Post by jamiemcc on 2007-10-26
for command line use tracker-search not tracker-query (that is for rdf queries btw)

Also make sure tracker-status is idle so all search results show up

Also stopwords (useless common words like "the" - see /usr/share/tracker/languages for list of all stopwords) cannot be searched as well

---

