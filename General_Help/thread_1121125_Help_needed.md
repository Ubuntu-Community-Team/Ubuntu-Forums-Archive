---
title: "Help needed"
date: 2009-04-09
forum: General Help
---

### Post by eruptionjoojo on 2009-04-09
Hi All,

I'm using Kubuntu 8.10 - 32 bit version ............


I get this Error while trying to apply the Updates or installing anything:-

dpkg: parse error, in file `/var/lib/dpkg/available' near line 26967 package `language-pack-gnome-fi':
 MSDOS EOF (^Z) in field name `'
E: Sub-process /usr/bin/dpkg returned an error code (2)

So,currently i'm unable to install anything or update my OS ............


any help would be greatly appreciated ..............

thnxx in advance .............

---

### Post by knattlhuber on 2009-04-09
Could be a broken package.
Open the Synaptic Package Manager and in the left column select the "Custom Filters" button. Then from the list in the box above, select "Broken". If a package comes up, try to remove it.
If that doesn't work, let us know.

---

### Post by eruptionjoojo on 2009-04-09
> **knattlhuber said:**
> Could be a broken package.
Open the Synaptic Package Manager and in the left column select the "Custom Filters" button. Then from the list in the box above, select "Broken". If a package comes up, try to remove it.
If that doesn't work, let us know.

thnxx a lot for your reply ................


no package is listed under the above mentioned head i.e. synaptic>custom filters>broken .................

---

### Post by knattlhuber on 2009-04-09
Try

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by eruptionjoojo on 2009-04-09
> **knattlhuber said:**
> Try

```
sudo dpkg --clear-avail && sudo apt-get update
```

thnxx a lot for your reply ..............


i guess the command "sudo dpkg --clear-avail && sudo apt-get update" did the job but though i'm not much sure (need some time to try some other installations as well) ............ 

in order to test i tried to update the OS using Synaptic .........  though it showed some dpkg error at first ............. but then the process continued and was successfully complete (i suppose) ...............

thnxx agian for your useful inputs ..........

---

