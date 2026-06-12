---
title: "GDebi Should Replace Software Center for Quick Installs"
date: 2014-05-13
forum: Desktop Environments
---

### Post by gerowen on 2014-05-13
Just a suggestion.  Apologies if this is in the wrong place, but I couldn't really find a forum for suggestions.

In my opinion, gdebi does a much better job of helping general users install .deb packages.  I manage a number of Ubuntu computers for users who just want a computer to surf the internet and do some basic work with.  However, on one or two occasions one of them has found and attempted to download a .deb file (Skype or something), and when they double click it, the Software Center takes a good 20+ seconds to load and then transition to the page where they can hit "Install" on that executable, so usually what happens is the user will double click their deb file, and then double click it again, and again, because nothing is happening.  I've started pre-installing gdebi and associating .deb files with it to make life easier for them.  GDebi starts up much faster and seems more straight forward for both me and regular users, not to mention giving some more technical details in less screen space for people like me.  Even the Debian guys removed the Software Center (I'm guessing ported upstream by you guys?) from Debian 7 because nobody used it in Debian 6.

Why is GDebi no longer even installed by default?  I think the Software Center is handy in some instances, say on a clean install for queuing up a long list of stuff to install, but generally speaking it's frustratingly slow and it's one of the first things I replace ( with Synaptic and GDebi).

I'm not ranting or angry, it's just an observation and a suggestion based on my experience and opinion.

---

### Post by buzzingrobot on 2014-05-13
Gdebi installs packages, but that's all. It doesn't list and describe available packages, etc.

Gdebi can easily become the default deb installer by adjusting property settings, typically in the file manager.

---

### Post by gerowen on 2014-05-13
> **buzzingrobot said:**
> Gdebi installs packages, but that's all. It doesn't list and describe available packages, etc.

Gdebi can easily become the default deb installer by adjusting property settings, typically in the file manager.

That's what I was saying, that GDebi should be the default handler for .deb files.  I use Synaptic and sometimes the software center for searching the repos, but if a user goes to a website, downloads a piece of software in .deb format, GDebi would be a much faster and simpler way to install that software I think.  I have been setting it as default, and was just offering a suggestion that the Ubuntu devs do the same in the future.

---

