---
title: "Kile and TexLive2007"
date: 2007-03-13
forum: Education &amp; Science
---

### Post by Xierxes on 2007-03-13
Hi all,

I have recently installed Kile (make/make install) and TexLive 2007.  I am having some difficulty accessing the Tex binaries from within Kile. The  [HowTo]("http://ubuntuforums.org/showthread.php?p=807144") for this setup recommend adding configurations and explicitly adding the path to each of the applications required (i.e bibtex, latex etc).  This does not seem elegant, and I was wondering if anybody knows if the 'default' application paths are hard coded into Kile, or are accessed via a configuration file.  I have looked at .kilerc and could not identify a path.  I have even looked through the source code of Kile (albeit briefly)  and could not find it there either. I know that my paths are correct, as when running latex --version in the Konsole tab in Kile, I get an appropriate response.  I have asked this question in the Kile support forums on sourceforge with no answer (yet). I am a relative newbie to Linux (haven't used it since my software engineering degree at uni - some years ago!) although am not afraid to get my hands a bit dirty digging!

Cheers
Rob

---

### Post by Xierxes on 2007-03-13
Hi all,

I have admitted defeat on this one at the moment (I do have  a MSc thesis to write) although I will be endeavouring to find the solution. It only took me about 30 seconds to change the paths manually, compared to two days searching for answers.  Not the desired solution, but as a (relative) newbie I did learn a lot about Linux - and sometimes it is not the destination, but the journey that is important, :) 

Cheers
Rob

---

### Post by mzilhao on 2007-03-13
why didn't you just install kile and tetex from the repos?
works great...

---

### Post by Xierxes on 2007-03-14
I wanted to install TexLive rather than tetex as tetex is no longer being maintained. I dont know if TexLIve2007 is in the repo's yet, and I only had it on a CD.  I also felt that I could learn something by installing myself, rather than reliance on the package managers (I thought I would start with something I understood!).

Cheers

---

### Post by cinnabar on 2007-03-15
TeXLive and Kile are both in the repos and work great together (that's what I use on my Kubuntu box).  It's great that you want to learn to install things yourself but sometimes it's better to save yourself the stress.

---

### Post by ahmatti on 2007-03-16
I find texlive if much better than tetex. I also use Miktex package manager for installing missing packages.  

Howto for installing miktex: [https://help.ubuntu.com/community/MiktexPackageManager](https://help.ubuntu.com/community/MiktexPackageManager)

Howto for using Miktex package manager: [http://dojo.miktex.org/blogs/christian_schenk/articles/mpmunix.aspx](http://dojo.miktex.org/blogs/christian_schenk/articles/mpmunix.aspx)

---

### Post by Xierxes on 2007-04-23
Hi all,

I posted a question on Kile's sourceforge forum, and it appears that this problem was unknown by the developers of Kile. A patch has been released, and the discussion about this problem can be viewed [here]("http://sourceforge.net/forum/forum.php?thread_id=1700810&forum_id=292014")

Cheers

---

