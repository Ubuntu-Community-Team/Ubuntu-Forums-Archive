---
title: "Configure script hanging compiling cabextract"
date: 2009-05-11
forum: General Help
---

### Post by risingsun on 2009-05-11
Hi,

I was trying to compile the source code for cabextract from [http://www.cabextract.org.uk/](http://www.cabextract.org.uk/)

However the configure script seems to hand on the line "checking for working mktime". I can't find mktime in synaptic and a google search seems to tie it to php which seems a little odd. Would anyone happen to have any suggestions on how to address this or why it's hanging?

Alternatively I noticed that cabextract is listed in synaptic but as version 1.2-3 where the website only has 1.2. Are they one and the same and so could I perhaps use the one from the repositories instead?

There's actually a lot more (possibly a script to run in the absence of mktime? I'm not sure) which is all contained within the configure script if anyone is kind enough to have a look, but is it possible that it's just taking a while to execute (I admit I didn't wait long, it just wasn't outputting anything.)

---

### Post by risingsun on 2009-05-11
Edit: Problem solved, I came across 

[https://bugs.launchpad.net/ubuntu/+source/gcc-4.3/+bug/323528](https://bugs.launchpad.net/ubuntu/+source/gcc-4.3/+bug/323528)

and 

[http://www.archivum.info/gnu.emacs.bug/2008-08/msg00848.html](http://www.archivum.info/gnu.emacs.bug/2008-08/msg00848.html)

both of which highlight a bug with gcc 4.3 and older versions of autoconf. Since the configure script was from 2006, rerunning autoconf with configure.ac present seems to have generated a script that fixed the problem. :)

---

