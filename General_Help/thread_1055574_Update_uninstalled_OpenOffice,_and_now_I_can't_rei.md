---
title: "Update uninstalled OpenOffice, and now I can't reinstall"
date: 2009-01-30
forum: General Help
---

### Post by mb_webguy on 2009-01-30
I'm using the openoffice-pkgs PPA for OOo3.  Today, Update Manager showed I had some updates.  OpenOffice was listed, but I didn't notice that it said anything about it being removed.  When I confirmed the update, however, all OpenOffice packages were uninstalled.  Now, when I try to reinstall it, I get what seems to be some circular dependency problems.  In Synaptic, when I try to check openoffice.org for installation, I get:```
openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
 Depends: openoffice.org-impress but it is not going to be installed
 Depends: openoffice.org-draw but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-report-builder-bin but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed
 Depends: openoffice.org-writer2latex but it is not going to be installed
 Depends: openoffice.org-filter-mobiledev but it is not going to be installed
 Depends: openoffice.org-java-common but it is not going to be installed
 Recommends: openoffice.org-filter-binfilter but it is not going to be installed
```

Attempting to check openoffice.org-core results in:```
openoffice.org-core:
 Depends: openoffice.org-common but it is not going to be installed

```

Checking openoffice.org-common gives me:```
openoffice.org-common:
 Depends: dictionaries-common but it is not going to be installed or
	openoffice.org-updatedicts
 Depends: openoffice.org-style-human but it is not going to be installed or
 	openoffice.org-style-tango but it is not going to be installed or
 	openoffice.org-style-crystal but it is not going to be installed or
 	openoffice.org-style-galaxy but it is not going to be installed
```

I can install dictionaries-common, but when I try to check any of the style packages, I get:```
openoffice.org-style-human:
 Depends: openoffice.org-common but it is not going to be installed

```

I can't install openoffice.org-common because I need to install a series of dependencies ending in the style packages, but I can't install the style packages because they depend on openoffice.org-common.  All I've done in the past day that could have caused this is that I uninstalled Evolution last night.  On the other hand, I don't see any Evolution packages in any of the error messages.

Is there a way around this, or do I just have to wait for openoffice-pkgs to fix the PPA?

---

### Post by bdamon on 2009-01-30
Just had the same thing happen here as well.

---

### Post by oggb4mp3 on 2009-01-30
Yep, me too.  Somthing is b0rked.

---

### Post by Aearenda on 2009-01-30
The PPA repository seems to be inconsistent at present, and the best thing to do is wait for it to be sorted out.

When Update Manager says it doesn't want to upgrade everything, it's usually right!

---

### Post by sunny_nwho on 2009-01-30
Even I screwed up my system any help would be great

---

### Post by jimibond283 on 2009-01-31
Hey there, 

The same thing happened to me.  I'm glad this isn't only me.  I thought I was going nuts.  

I deleted to OOo PPA and just installed OOo 2.4.1 in the regular repositories for immediate work purposes.  

I'll just wait until they fix this.  I'm sure it won't take long.

---

### Post by DigitalAxis on 2009-01-31
I've got the same issue; it refuses to install openoffice.org-common because it requires dictionaries-common 0.98.14 while the only one actually available to install is 0.98.9

And this is somehow OpenOffice.Org 2.4 still; I search for all openoffice packages and I don't get ANY mention of version 3 (PPA is down again?).  Unless we've got the wrong version of openoffice.org-common coming through, everyone is going to be having problems with that version mismatch.

---

### Post by David Valentine on 2009-01-31
Thanks for the heads-up, folks.  I wondered why Synaptic wanted to remove all my openoffice packages, and am glad I checked here.

This is not the first time that an update has borked people's installations.  I remember an xorg update that caused a raft of computers to no longer be able to load x.  It seems like there should be an ALERT section at the top of these forums to annouce major updates that are causing problems and should not be allowed to run.  My hope would be that the ppa maintainers would also see the issues and roll back the updates before too many more systems get hosed.

---

### Post by Aearenda on 2009-01-31
> it refuses to install openoffice.org-common because it requires dictionaries-common 0.98.14 while the only one actually available to install is 0.98.9
0.98.14 was built 41 minutes ago in the PPA. Patience, people!

EDIT: That dictionaries-common build has fixed it for me - my upgrade is now complete (on Intrepid - hardy packages are still being built as I write).

---

### Post by mb_webguy on 2009-01-31
Yup.  The OOo PPA for Intrepid is fixed.  I'm pretending to mark this thread SOLVED.

---

### Post by Aearenda on 2009-01-31
Hey, I can see your pretend SOLVED marker in red if I close one eye!

---

