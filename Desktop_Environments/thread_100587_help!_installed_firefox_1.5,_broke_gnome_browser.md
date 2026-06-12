---
title: "help! installed firefox 1.5, broke gnome browser"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Tsingi on 2005-12-07
trying to run devhelp from the applications menu does not work.

trying to run it from a terminal gets me the following message: 
error while loading shared libraries: libgtkembedmoz.so: cannot open shared object file: No such file or directory

That looks like a mozilla file to me, so I'm assuming that my custom install of Firefox 1.5 broke the path.

I could just reinstall the default browser for ubuntu, but I need to use Firefox 1.5 because it has SVG support and I want to work with it.  I'd like it to be the default browser as well.

Is there an official 1.5 install for firefox?  and if not, can anyone tell me, or point me to docs that would help me install it so that the libraries are in the right place?  (assuming that Firefox has the same libs)

Other suggestions?

Thanks:)
Rick.

---

### Post by abou on 2005-12-07
To be honest, I don't know how that could happen.

---

### Post by Joe_CoT on 2005-12-07
if you read the [Firefox 1.5 backport](http://ubuntuforums.org/showthread.php?t=96595) topic, you'd see that the reason they're not jumping for joy to add firefox 1.5 to Breezy is that it _really_ fucks up the programs that depend on it. Your best bet is to remove Firefox 1.5, reinstall firefox 1.0.x, and wait until dapper or further developments.

---

### Post by Tsingi on 2005-12-07
[QUOTE=bobfnordman]if you read the [Firefox 1.5 backport](http://ubuntuforums.org/showthread.php?t=96595) topic, you'd see that the reason they're not jumping for joy to add firefox 1.5 to Breezy is that it _really_ fucks up the programs that depend on it. Your best bet is to remove Firefox 1.5, reinstall firefox 1.0.x, and wait until dapper or further developments.[/QUOTE]

I'm working with SVG support in firefox, there isn't any in 1.0.x, so that isn't an option if I want to continue to do the development I'm doing.

I could serve the files up with apache and use firefox on windows, but that's a pain.  (alt-tab is faster than switching puters)

However, thanks for shedding some light on the problem.

---

### Post by Joe_CoT on 2005-12-07
if you *really* need firefox 1.5, just install it to another location (not overwriting firefox 1), and use it that way.

---

