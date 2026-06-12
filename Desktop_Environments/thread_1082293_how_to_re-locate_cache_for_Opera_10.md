---
title: "how to re-locate cache for Opera 10?"
date: 2009-02-27
forum: Desktop Environments
---

### Post by zika on 2009-02-27
I know how to make Firefox store its cache in /tmp mounted on tmpfs. I want to do the same (or similar) with Opera 10. how to make it use non-default directory for cache?

also, I now how to use Java 64-bit plugin for Firefox. but I seem not to be able to enable it for Opera 10.

**update:**  cache is moved to /tmp. opera:config -> User Prefs-> Cache Directory4->/tmp/cache4 ... ;)
java remains unsolved.

---

### Post by size_XXM on 2009-06-05
I don't remember Opera ever picking up the java directory correctly, for some reason. [Here's a how-to](http://www.opera.com/docs/linux/plugins/install/#java), I'm using the path */usr/lib64/jvm/java-6-sun/jre/lib/amd64*

On the cache relocation: does it work for you? No problems with history search disappearing after reboot or anything?

---

### Post by zika on 2009-06-06
> **size_XXM said:**
> I don't remember Opera ever picking up the java directory correctly, for some reason. [Here's a how-to]("http://www.opera.com/docs/linux/plugins/install/#java"), I'm using the path */usr/lib64/jvm/java-6-sun/jre/lib/amd64*

On the cache relocation: does it work for you? No problems with history search disappearing after reboot or anything?
After some digging I found that switch myself and (if I remeber good) it worked, I had working Java. I do not have Opera on my machine anymore (it lasted less than two days) ...

---

