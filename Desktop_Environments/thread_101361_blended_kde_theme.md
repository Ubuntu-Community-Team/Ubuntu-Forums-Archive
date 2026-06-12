---
title: "blended kde theme"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Josef K. on 2005-12-09
I missed **so** much blended theme in kde :(
unfortunately blended kde porting needs dekorator and there's no way I can install it

did anybody managed to use that theme or install dekorator?

trying compiling dekorator I got this error:
> 
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

where are those headers?!

---

### Post by limit223 on 2005-12-09
Generally speaking about KDE...those headers are: kdebase-dev and kdelibs-dev.. but referring to Kubuntu could be kde-devel ...or related to media kdemultimedia-dev.... If I do not get wrong all kde*-dev are actually KDE headers.

---

### Post by Josef K. on 2005-12-10
I found it! ^___________^
missing headers were in kdelibs-dev

guess I should make an howto for this messy thing :\

---

