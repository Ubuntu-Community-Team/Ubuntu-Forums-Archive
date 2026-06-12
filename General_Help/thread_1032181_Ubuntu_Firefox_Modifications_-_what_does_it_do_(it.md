---
title: "Ubuntu Firefox Modifications - what does it do (it breaks things)"
date: 2009-01-06
forum: General Help
---

### Post by inspired on 2009-01-06
Hi Folks,
As of a few days ago I am using Ubutnu 8.10 (intrepid) and firefox 3.05. I have just switched from using XP as my main OS to using Ubuntu, and keeping XP for certain things. So I moved my Firefox and thunderbird profile to Ubuntu.

I have a very handy extensions in FF called Web developer toolbar.
Since moving my firefox to Ubuntu this extension does not work. It's toolbar comes up blank.

After some research I found out that:
1) Tab mix plus extension **might** be the issue (for some people)
2) Ubuntu Firefox Modifications extension seems to consistently be the problem.
Apparently disabling this extension (2) will sort this issue out.

I've tried to find conclusive info on what the Ubuntu Firefox Modifications extension actually does, but I've found done. Just a few mixed bits of info.

Can someone please point me to where I can fin a list of what this extension does, so that I know when I am losing when I disable it.

With much thanks,

Jonathan

---

### Post by rHBa on 2009-05-02
Bump, I second that.

I do know it keeps re-adding the Ask.com search bar every time FF updates (annoying).

Surely there must be some official info on the extension somewhere? Where is TFM?

---

### Post by Brandon Williams on 2009-05-02
Here is [the original mailing list post](https://lists.ubuntu.com/archives/ubuntu-devel/2007-August/024137.html) about ubufox. It's not up-to-date with new version, but it will give you an idea.

Everything else that ubufox does is related to look-and-feel, not functionality.

This plugin will only get occasional use, so if it's screwing up another plugin somehow, I recommend that you remove ubufox to make way for the other plugin. Please open a bug against ubufox, though, if this is what fixes the problem.

---

### Post by codeseer on 2009-05-06
I've got to where anytime I install Ubuntu, one of the first things I do is update everything and then remove ubufox along with all the other problematic packages like flash and java that you get from the repositories. I then kill off all traces of flash and java with a vengeance and install the official versions of them.

Since I've been randomly crashing in Intrepid, I'm starting to think the repository version of Firefox is to fault, from the numerous reports saying so in similar issues. Therefore, I'm thinking about adding Firefox to the list of things that just don't work from the repositories and should be removed upon install.

---

### Post by mikehattingh on 2010-06-27
This extension causes problems and has no uninstall to get rid of it go:
System -> Administration -> Synaptic package manager. Search for ubufox and remove ubufox.

---

