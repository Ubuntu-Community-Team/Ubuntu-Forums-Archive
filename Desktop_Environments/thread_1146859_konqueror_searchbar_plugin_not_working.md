---
title: "konqueror searchbar plugin not working"
date: 2009-05-03
forum: Desktop Environments
---

### Post by jtappin on 2009-05-03
I've just updated my main machine to Jaunty (via a fresh install, but keeping /home, since I was coming from Hardy and there was a load of cruft on the system).

Now whenever I try to use the konqueror searchbar (konqueror-plugin-searchbar) I get a popup error message saying:
"Protocol not supported"

Since it works just fine on my testing box, I'm assuming there's a configuration incompatibility - but where? 
[FONT="Courier New"]~/.kde/share/config/konquerorrc[/FONT] contains the following for the search bar:
```

[SearchBar]
CurrentEngine=google
GoogleSuggestMode=0
History list=\\0
Mode=1

```
the only difference on the working machine is there's no GoogleSuggestMode line, but removing that doesn't have any effect.

Has anyone else seen this problem, and if so have you found a fix?

---

### Post by jtappin on 2009-05-04
Problem solved.

It turns out that it it necessary to go into "Select Search Engines" and set a default. For some reason while a new home directory has a sensible default,migrating from KDE3 loses it.

---

