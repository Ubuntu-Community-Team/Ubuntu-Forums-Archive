---
title: "Is defoma broken?"
date: 2005-12-23
forum: General Help
---

### Post by Paul Jones on 2005-12-23
When I try to use defoma-hints, I get "defoma-hints Can't locate FreeType.pm", which is a Perl package that interfaces to FreeType version 1 ([http://freetype.sourceforge.net/index2.html)](http://freetype.sourceforge.net/index2.html)).  I assume you have to have the FreeType lib to be able to use the Perl package but building it proves to be a challenge because it's pretty old code and there are some missing .h files I will have to track down.  Other folks on the net have reported this problem but I saw no solution.

I wonder why  FreeType 1 isn't packaged along with or referenced by the defoma package.  (I didn't see anything on Debian except FreeType 2 and tests for FreeType 1)

Anyone else using defoma?

---

