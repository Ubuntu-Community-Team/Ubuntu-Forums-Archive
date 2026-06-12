---
title: "emacs manual"
date: 2007-11-18
forum: Desktop Environments
---

### Post by emacdona on 2007-11-18
What happened to the Emacs manual? Wasn't there a package called something like "emacs-doc" that installed the complete Emacs manual in all its glory (in info format)?

I can't find any package that has the emacs manual... and when I open info, the closest thing I see is the "Emacs FAQ".

please help... I need that manual!

Thanks,
Ed

---

### Post by Embedded Linux Guy on 2007-11-19
From info I see this entry for the Emacs manual:

* Emacs (emacs-snapshot): (emacs-snapshot/emacs).
                                        The extensible self-documenting text
                                        editor.

This is emacs 22.1.50 on Gutsy Gibbon.  The info files are installed in /usr/share/info/emacs-snapshot/ by emacs-snapshot-common.

---

### Post by emacdona on 2007-11-21
Do you have the development (snapshot) version of emacs installed? I have the stable version... which (apparently) doesn't come with the info manual.

I'm going to install the snapshot version as soon as I'm finished typing this. I can't live without that manual :-)

Thanks,
Ed

---

### Post by deserthowler on 2007-11-23
You should be able to find a PDF version of the emacs manual through the FSF website.

Earl

---

### Post by emacdona on 2007-11-24
Thanks for the tip. I prefer the info version, though. I actually have a printed version, I just like the info format because I can read it from within Emacs, plus I've taken time to learn a lot of Info commands (so I can move around pretty easily in it).

What really bothers me, though, is that it appears to have disappeared from the distro and not that much noise appears to be being made...

---

### Post by emacdona on 2007-11-26
Aha! This link contains an explanation and a fix (the fix is an additional package you can install):
[https://bugs.launchpad.net/ubuntu/+source/emacs21/+bug/73840](https://bugs.launchpad.net/ubuntu/+source/emacs21/+bug/73840)

"The version of emacs21 that is currently in feisty (21.4a+1-1ubuntu1) has been crippled by Debian, and should be uncrippled in Ubuntu. Namely: info fiiles that Emacs users depend on for daily use have been removed..."

I really do like the choice of words by the author of this bug report: "The version of emacs21 currently in feisty [...] has been crippled by Debian [...]"

I'm still in shock that more people aren't upset by this. If you read the comments on the link pasted above, you'll see someone say "[...] Emacs has a very strong and not-easily-sundered integration with its manual [...]"

They're right. The emacs info manual is a *part* of Emacs. I know Debian has reasons for taking it out, and I don't hold that against them (well, maybe I do a little)... I'm not shocked about that. I'll say it one more time: I *am* shocked that there's not a huge uproar about this. 

*sigh* 
Maybe not as many people use Emacs anymore?

---

### Post by Embedded Linux Guy on 2007-11-26
> 
Maybe not as many people use Emacs anymore?

I hope it's rather because people are using Emacs 22 or pre-23!

---

