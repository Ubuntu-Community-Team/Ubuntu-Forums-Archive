---
title: "openoffice 2.0.3 official dapper upgrade error"
date: 2006-07-27
forum: Desktop Environments
---

### Post by lisa-m on 2006-07-27
today i saw the update manager pop-up telling me ther eis a new version of openoffice, it seems the official ubuntu team has now updated openoffice to 2.0.3, however when i try to update i get the following error, i've tried updating with update manager and synaptic with this same result:

 E: /var/cache/apt/archives/openoffice.org-calc_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/scalc.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-writer_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/swriter.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-draw_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/sdraw.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-impress_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/simpress.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-math_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/smath.idx/DICTIONARY', which is also in package openoffice.org-help-en-us
E: /var/cache/apt/archives/openoffice.org-base_2.0.3-2dapper1_i386.deb: trying to overwrite `/usr/lib/openoffice/help/en/sdatabase.idx/DICTIONARY', which is also in package openoffice.org-help-en-us

can some one explain to me why it cannot overright those files. Because synaptic has root access. If this is one of those problem that should be posted in the bug reports to the ubuntu team, can somebody please do it for me, because i don't know how to file bug reports for ubuntu. 

Thanks for any help

EDIT: well it seems after you remove package openoffice.org-help-en-us and try updating then it works fine. and then you just re-install any other needed packages that were remove because of openoffice.org-help-en-us. package.

---

### Post by be4truth on 2007-01-21
try this one for dapper.
[http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523)
works fine with me!

---

