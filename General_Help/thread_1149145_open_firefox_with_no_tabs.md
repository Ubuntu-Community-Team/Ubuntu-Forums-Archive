---
title: "open firefox with no tabs"
date: 2009-05-04
forum: General Help
---

### Post by nbv4 on 2009-05-04
I have firefox set to save tabs from the previous session. Someone recently tricked me into clicking on a Last Measure link (google it, it's a malicious link). Now whenever I open firefox, that malicious link is open in a tab, which causes me to have to close firefox killing the process. How can I open firefox with no tabs open?

---

### Post by paradigm2 on 2009-05-04
Hmmm.  One possible way (I'm not 100% sure, be warned) ...

Go to a terminal and enter:

```

firefox -safe-mode

```

This should start firefox in safe mode and then you can use and close it normally.  Try that.

I'll research for another way...of no one else comes up with it.  You likely just need to delete a certain file or such in your ~/.mozilla/firefox directory.

---

### Post by nbv4 on 2009-05-04
> **paradigm2 said:**
> Hmmm.  One possible way (I'm not 100% sure, be warned) ...

Go to a terminal and enter:

```

firefox -safe-mode

```

This should start firefox in safe mode and then you can use and close it normally.  Try that.

I'll research for another way...of no one else comes up with it.  You likely just need to delete a certain file or such in your ~/.mozilla/firefox directory.safe mode has an option to disable just about everything.... except for saved tabs. even in safe mode the malicious link comes up. I've been looking around the ~/.mozilla folder, but I'm not seeing anything.

---

### Post by paradigm2 on 2009-05-04
If that does not work, I beleive I have found a better way.

Go to the directory:

~/.mozilla/firefox

and look for a directory called something like ghm6j66w.default (it will be different than this name).

Type 'cd <insert name of that directory>

then do

```

mv sessionstore.js oldsessionstore.js.bak

```

And start firefox normally.  It should work.

---

### Post by paradigm2 on 2009-05-04
> **nbv4 said:**
> safe mode has an option to disable just about everything.... except for saved tabs. even in safe mode the malicious link comes up. I've been looking around the ~/.mozilla folder, but I'm not seeing anything.

It looks like it is kept in sessionstore.js within ~/.mozilla/firefox/blahblahwhateverhere.default/ 

Opening that file on my machine showed me the tabs I had open before.

---

### Post by nbv4 on 2009-05-04
> **paradigm2 said:**
> If that does not work, I beleive I have found a better way.

Go to the directory:

~/.mozilla/firefox

and look for a directory called something like ghm6j66w.default (it will be different than this name).

Type 'cd <insert name of that directory>

then do

```

mv sessionstore.js oldsessionstore.js.bak

```

And start firefox normally.  It should work.

yay that worked. Thanks a lot. This seems like a common problem that should have a more intuitive solution though...

---

### Post by paradigm2 on 2009-05-04
> **nbv4 said:**
> yay that worked. Thanks a lot. This seems like a common problem that should have a more intuitive solution though...

You're welcome. :)

Yss, I agree.  It probably should be an option in safe mode.  That would be intuitive.

---

