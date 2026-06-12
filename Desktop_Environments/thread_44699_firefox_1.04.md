---
title: "firefox 1.04"
date: 2005-06-27
forum: Desktop Environments
---

### Post by Leion on 2005-06-27
I tried to install firefox 1.04 over the apt-get but then something failed and i cannot even start up my old 1.02

so i uninstalled and installed again, which still cannot work.

then I go the the official firefox site and get the tar.gz file, which, after i installed, cannot get to work....


sorry i am a novice 
and would appreciate if someone can give me a step by step guide on how to install firefox back   :(

thanks in advance

---

### Post by Lunde on 2005-06-27
[QUOTE=Leion]I tried to install firefox 1.04 over the apt-get but then something failed and i cannot even start up my old 1.02

so i uninstalled and installed again, which still cannot work.

then I go the the official firefox site and get the tar.gz file, which, after i installed, cannot get to work....


sorry i am a novice 
and would appreciate if someone can give me a step by step guide on how to install firefox back   :(

thanks in advance[/QUOTE]

I think the best is to uninstall the new, then the old and then install the old one again

I'm pretty sure I read somwhere that the Ubuntu version is already updated to 1.04, but there is an error in showing the version number. I know I did a fix for that a while back and now I run 1.04 without any spesific installation.

---

### Post by Sionide on 2005-06-27
Remember, this ain't the place to ask questions - please take note of the posts at the top of the forum..

---

### Post by poofyhairguy on 2005-06-27
[QUOTE=Leion]I tried to install firefox 1.04 over the apt-get but then something failed and i cannot even start up my old 1.02
[/QUOTE]


Did you try to use the backport Firefox?

---

### Post by sebdah on 2005-06-27
If someone don't get it right with the versions. You have you update it like this:

1. Open firefox.

2. Surf to about:config

3. Enter "vendorSub" in the filter field and click on "Show All"

4. Double click on the post that remains and change the value to 1.0.4

That should be all. Maybe a restart of firefox, I don't know.

---

### Post by Krash1201 on 2005-06-27
the backports repository has the version that will fix this problem.  in the old version, there is a work around explained on an error page you get if you try to access the extensions web page from mozilla.  supposedly, its a problem with the way the updated version is compiled on the main repositories.  basically it requires changing the version number through about:get, but i don't remeber which line specifically.  your best bet is to update from backports though.

---

