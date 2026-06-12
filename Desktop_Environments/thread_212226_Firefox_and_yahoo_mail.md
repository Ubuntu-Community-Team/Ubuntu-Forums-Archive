---
title: "Firefox and yahoo mail"
date: 2006-07-09
forum: Desktop Environments
---

### Post by iitywygms on 2006-07-09
I have the latest version of dapper, all updates, and Firefox version 1.5.0.4 Lately, when i go to my home page (my yahoo) it takes forever to load. 7 8 seconds.  Other pages seem to load just fine.  
Sometimes when I click on the link to check my email firefox will just close.  I have to retry several times to get to my yahoo mail.  The really weird thing is that the new mail notification in message center is not showing up any more.
I switch to my windblows computer and everything is superfast and the email notification is there.
I checked to make sure flash is working and it is, so is java.  What could be causing this?

---

### Post by Psquared on 2006-11-12
An incompatible extension most likely. Remove them one-by-one until you find the offending one. Most likely Tab Mix Plus - but could be Sidebar or others. Only way is by process of elimination. Are you using FF 2.0 in Edgy? That is where I am having the problem.

It is also possible that its something Yahoo changed to keep from using certain email notifications in FF.

---

### Post by Psquared on 2006-11-12
I went through every extension and found out that, at least in FF 2.0, its the **Firefox Showcase extension** that causes FF to crash when trying to read Yahoo Mail. I uninstalled this extension and it works fine now.

If anyone is having this trouble, regardless of what version FF you are using or whether you are using Hoary, Dapper or Edgy, remove this extension. If anyone is having success using this extension (can read your Yahoo Email without crashing FF) Post the version you are using. I tried updating it but I have the latest version. (or had!!)

---

### Post by joseprio on 2006-11-26
> **Psquared said:**
> I went through every extension and found out that, at least in FF 2.0, its the **Firefox Showcase extension** that causes FF to crash when trying to read Yahoo Mail. I uninstalled this extension and it works fine now.

If anyone is having this trouble, regardless of what version FF you are using or whether you are using Hoary, Dapper or Edgy, remove this extension. If anyone is having success using this extension (can read your Yahoo Email without crashing FF) Post the version you are using. I tried updating it but I have the latest version. (or had!!)

Hi!

I'm the author of Showcase extension...

One question: did you enable the "thumbnail caching"? It's on the "Advanced" tab in the extension configuration panel, and it's the only thing I can think of that could crash your browser in normal usage. I added some changes to that, so this error will probably disappear in the next version.

This new version will be released as soon as the translators finish their job, which should be in two weeks or less.

---

### Post by swtch on 2008-07-16
Happened to me and I disabled/re-enabled Ubuntu Firefox Modifications (under extensions in Add-ons).  This enabled the features that some users obviously already had by default.

---

