---
title: "Where is the 3d windows setting for compiz-fusion?"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by tcollogne on 2007-10-02
Hello,

While using beryl I had an option to make the windows 3d when rotating the cube, now with the beta of gutsy with compiz-fusion, I can't seem to find that option.

Can somebody tell me where I can find it?

Thank you

---

### Post by joetaxpayer on 2007-10-02
It's an optional plugin that is not included with the CF version in gutsy.  You won't find it in any of the standard repo packages either.  I think there are third party repos that contain the precompiled packages.  Otherwise, it can be installed manually using git, but all of my attempts to do so yesterday were unsuccessful.  I ended up downloading an install script from the compiz-fusion forums, which will install the latest updates and plugins to CF.

Here:  [http://forum.compiz-fusion.org/showthread.php?t=3960&highlight=install+plugin](http://forum.compiz-fusion.org/showthread.php?t=3960&highlight=install+plugin)

You may need to install libcompizconfig0 from the repos to make this work after you install it.  

Otherwise this thread tells how to install everything manually: [http://wiki.opencompositing.org/Install/PluginsFromGit](http://wiki.opencompositing.org/Install/PluginsFromGit)

but like I said, it didn't work for me.  I am new to this whole thing, so I am interested to see how others respond to this question.

---

### Post by joetaxpayer on 2007-10-03
Anyone else?

---

### Post by tcollogne on 2007-10-03
Thanks for the response. I didn't know it was a plugin. Haven't had time to check it out yet.

---

### Post by Rupertronco on 2007-10-03
> **joetaxpayer said:**
> Anyone else?

The reason the new version of the 3d windows won't work when installed from git on gutsy is you're using the wrong version of compiz for it. The compiz required by git plugins is 0.6.X. The way to enable them would be to get rid of the default compiz install and install the entire git version of compiz. Note: This is not recommended for a regular user, it's used to test new versions and it is often unstable. 

There are no pre-compiled gutsy packages available that I am aware of so your options are to wait for Trevino to make a gutsy repository, or install the entire application from git.

---

### Post by joetaxpayer on 2007-10-03
> **Rupertronco said:**
> The reason the new version of the 3d windows won't work when installed from git on gutsy is you're using the wrong version of compiz for it. The compiz required by git plugins is 0.6.X. The way to enable them would be to get rid of the default compiz install and install the entire git version of compiz. Note: This is not recommended for a regular user, it's used to test new versions and it is often unstable. 

There are no pre-compiled gutsy packages available that I am aware of so your options are to wait for Trevino to make a gutsy repository, or install the entire application from git.

Thanks for clarifying.

---

