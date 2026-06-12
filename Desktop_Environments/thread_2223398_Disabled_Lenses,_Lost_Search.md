---
title: "Disabled Lenses, Lost Search"
date: 2014-05-10
forum: Desktop Environments
---

### Post by stevie6 on 2014-05-10
I was trying to get rid of dash plugins within the search so I could enable individual ones.  So I created & copied a list of my scopes and used:


*gsettings set com.canonical.Unity.Lenses disabled-scopes "[$(find /usr/share/unity/scopes/ -name \*.scope -printf "'%P',"|sed -es':/:-:g' -e's/,$//')]"*

which totally blanked out the search HUD -as in no access to installed apps or files. However when I try to use

*gsettings set com.canonical.Unity.Lenses enable-scopes "['whatever.scope']" *

to get indivdual (or all) back I get "no such key enable-scopes".  I've tried Unity--reset (depreciated) and CCSM (no effect on the search) and 
[I]
dconf reset -f /org/compiz/ & unity --reset-icons &disown 
[/I]
to, by now, get the whole thing back.  So, what am I not doing right?

---

### Post by grumblebum2 on 2014-05-10
There is no key **enable-scopes**.
Not sure how scopes work but obviously some of the scopes you disabled using
```
find /usr/share/unity/scopes/ -name \*.scope -printf "'%P',"|sed -es':/:-:g' -e's/,$//'
```
are needed for basic dash functionality.

And wouldn't running this return fuctionality....
```
gsettings [COLOR="#FF0000"]reset[/COLOR] com.canonical.Unity.Lenses disabled-scopes
```

---

### Post by stevie6 on 2014-05-10
YES! it did. Thank you very much. And now I shall learn to just live with the darn things.

---

### Post by grumblebum2 on 2014-05-10
> **stevie6 said:**
> YES! it did. Thank you very much. And now I shall learn to just live with the darn things.
From the trusty iso manifest these are the default installed scopes....
```
unity-scope-audacious	0.1+13.10.20130927.1-0ubuntu1
unity-scope-calculator	0.1+13.10.20130723-0ubuntu1
unity-scope-chromiumbookmarks	0.1+13.10.20130723-0ubuntu1
unity-scope-clementine	0.1+13.10.20130723-0ubuntu1
unity-scope-colourlovers	0.1+13.10.20130723-0ubuntu1
unity-scope-devhelp	0.1+13.10.20130809.1-0ubuntu1
unity-scope-firefoxbookmarks	0.1+13.10.20130809.1-0ubuntu1
unity-scope-gdrive	0.9+13.10.20130723-0ubuntu1
unity-scope-gmusicbrowser	0.1+13.10.20130723-0ubuntu1
unity-scope-gourmet	0.1+13.10.20130723-0ubuntu1
unity-scope-guayadeque	0.1+13.10.20130927.1-0ubuntu1
**unity-scope-home**	6.8.2+14.04.20131029.1-0ubuntu1
unity-scope-manpages	3.0+13.10.20130723-0ubuntu1
unity-scope-musicstores	6.9.0+13.10.20131011-0ubuntu1
unity-scope-musique	0.1+13.10.20130723-0ubuntu1
unity-scope-openclipart	0.1+13.10.20130723-0ubuntu1
unity-scope-texdoc	0.1+13.10.20130723-0ubuntu1
unity-scope-tomboy	0.1+13.10.20130723-0ubuntu1
unity-scope-video-remote	0.3.15+13.10.20130920-0ubuntu1
unity-scope-virtualbox	0.1+13.10.20130723-0ubuntu1
unity-scope-yelp	0.1+13.10.20130723-0ubuntu1
unity-scope-zotero	0.1+13.10.20130723-0ubuntu1
```

I use synaptic to remove all except **unity-scope-home**.

---

