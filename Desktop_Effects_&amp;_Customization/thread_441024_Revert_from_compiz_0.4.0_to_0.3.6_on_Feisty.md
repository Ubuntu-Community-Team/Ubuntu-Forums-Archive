---
title: "Revert from compiz 0.4.0 to 0.3.6 on Feisty"
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by HydroDiOxide on 2007-05-12
Hi there,

I've got some problems with the new 0.4.0 compiz release on Ubuntu Feisty (show desktop when moving mouse to the lower right corner and zoom don't work any more). I quess it's in the release and to make sure I'd like to revert back to the 0.3.6 release to try it out. But I don't know how... I can't find 0.3.6 in synaptic anymore.

---

### Post by jmartos on 2007-05-12
I do not see a 0.4.0 compiz release? where did you get it?

---

### Post by Ateo on 2007-05-12
If you don't see compiz-0.3.6 in synaptic, then you have some sources in your source list that is pulling the newest compiz in for you. Remove that. Reload synaptic and you should see the 0.3.6 version there.

Or did you install 0.4.0 yourself with a deb file?

---

### Post by HydroDiOxide on 2007-05-13
@jmartos. It was an automatic update.

I can't remember putting any compiz sources in my sources.list. I'm not near my Feisty box now, but I'll take a look later this evening.

---

### Post by Ateo on 2007-05-13
You must have done something because 0.4.0 is not in the Ubuntu supported repositories (and probably will never be). Sorry, but you *DID* change something.

---

### Post by HydroDiOxide on 2007-05-13
I managed to get the 0.3.6 release back in synaptic (there WAS an exotic repository in synaptic). After reinstalling it my problems were solved. Clearly the set of 0.4.0 elements of compiz were not working allright with the 0.3.6 elements or there is some kind of big in the 0.4.0 release causing 'show desktop' and 'zoom' to not work correctly.

---

### Post by bittergourd on 2007-05-16
try "force version" in the Package menu, or Ctrl+E on the package.  Then choose 0.3.6... 

-E

---

