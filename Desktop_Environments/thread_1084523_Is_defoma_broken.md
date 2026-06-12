---
title: "Is defoma broken?"
date: 2009-03-02
forum: Desktop Environments
---

### Post by theOtherMarino on 2009-03-02
Hello all,

In an old (2005) post ([http://ubuntuforums.org/showthread.php?t=107596&highlight=defoma-hints+Can%27t+locate+FreeType.pm](http://ubuntuforums.org/showthread.php?t=107596&highlight=defoma-hints+Can%27t+locate+FreeType.pm)), Paul Jones wrote:
	
> Is defoma broken?
When I try to use defoma-hints, I get "defoma-hints Can't locate FreeType.pm", which is a Perl package that interfaces to FreeType version 1 ([http://freetype.sourceforge.net/index2.html](http://freetype.sourceforge.net/index2.html)). I assume you have to have the FreeType lib to be able to use the Perl package but building it proves to be a challenge because it's pretty old code and there are some missing .h files I will have to track down. Other folks on the net have reported this problem but I saw no solution.

I wonder why FreeType 1 isn't packaged along with or referenced by the defoma package. (I didn't see anything on Debian except FreeType 2 and tests for FreeType 1)

Anyone else using defoma?

I encounter the same problem. Nothind new since 2005? Is defoma still maintained however?

And, oh... Found also this :

> Debian Changelog defoma (0.11.10-0.2) 
2008
defoma (0.11.10-0.2) unstable; urgency=high

   * Non-maintainer upload.
   * Do not build the dfontmgr binary package anymore [...]

I tried to get the dfontmgr through Synaptic, but yes, it is broken.

Well, well...

Marino

---

