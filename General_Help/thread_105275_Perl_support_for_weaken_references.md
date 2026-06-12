---
title: "Perl support for weaken references"
date: 2005-12-18
forum: General Help
---

### Post by valiente on 2005-12-18
Ubuntu 5.04 included a working Perl compiled with (default) support for weaken references, but Ubuntu 5.10 doesn't. Weaken references are in the core in Perl 5.8, and solve major memory leakage problems. I suspect the Perl package (5.8.7) supplied with Ubuntu 5.10 was compiled by explicitly switching off the default support for weaken references. I can recompile it on my laptop, but It might be interesting to have the Ubuntu 5.10 Perl package replaced by one with support for weaken references.

---

