---
title: "package won't fix (gcc-4.3-base)"
date: 2008-12-11
forum: General Help
---

### Post by snirpyor on 2008-12-11
I updated against "debian experimental", shouldn't have done that. Been trying to fix everything since. I guess one issue remaining:
 
Some packages won't install and it all comes down to:
*Depends: gcc-4.3-base (= 4.3.2-1ubuntu11) but 4.3.2-2~exp3 is to be installed*
 
I guess debian overwrote the *ubuntu11* version for the *~exp3* version. Is there any way to get the correct package back?
 
Trying to remove gcc-4.3-base results in:
[I]WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing![/I]
[long list here]
[I]You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'[/I]
 
Adept shows gcc-4.3-base as version 4.3.2-2~exp3 but does not offer an update option.
 
Where to go from here? Delete the package anyway? Is there someway to mark the debian package for update (identify it as older version?)? Am I thinking along the right lines here?

---

