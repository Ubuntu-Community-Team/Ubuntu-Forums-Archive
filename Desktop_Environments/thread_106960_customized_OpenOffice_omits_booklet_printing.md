---
title: "customized OpenOffice omits booklet printing"
date: 2005-12-21
forum: Desktop Environments
---

### Post by doubled on 2005-12-21
Perhaps I'm the only user of it, but I have discovered that a feature of OpenOffice is missing from the customized version 2 packaged with Ubuntu: booklet printing, that is, a document that is prepared as normal portrait orientation and then, with a change in the printer properties settings, printed as a booklet.  (Yes, I actually have a use for this feature!)

The problem is this: The printer setting that allows one to use landscape orientation is missing from customized versions of OOo2, where it has been present in pre-2.0 versions and is present in the version downloadable from openoffice.org.  The choice (portrait vs. landscape) should be the second item down after clicking "Properties" in the print dialogue.  But it's not there.  There's another step after that one, but the lack of this choice is a show-stopper.

I know it is present in the official OOo2 version.  Is it possible to install that version in Ubuntu to replace the customized version?  If so, how is it installed?  The installation uses RPMs, and I don't know whether Ubuntu, through the use of Synaptic, can install it.  (Xandros' package manager has a mechanism for converting the RPMs to one big .deb file.)

I'm also hoping that Ubuntu developers will take note and correct this problem in the next version.  But if no one else uses it . . . maybe it's being overlooked.  Suse and Mandriva have the same issue, by the way.

---

### Post by fswasey on 2005-12-30
I am having the same problem.  The lack of this feature is a show stopper in me converting from Fedora Core 4 to Ubuntu "breezy badger".  

My wife and I both generate brochures for conventions in this manner.

I have installed the OOo2 2.0 packages from

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

but they have the same problem... :(

---

### Post by kaamos on 2005-12-30
The version packaged with ubuntu 5.10 is not a release version, but a release candidate. So installing a new version from openoffice.org might be a good idea in any case.

---

### Post by fswasey on 2006-01-01
An alternative is to rebuild the Ubuntu package but do NOT apply the printer-properties-disable.diff patch.   (It does take the better part of a day to build the package from source on my 1.1GHz system.)

Hopefully, that patch is a left over from the OpenOffice version 1 patches because it is a real mistake on OpenOffice 2.

---

### Post by doubled on 2006-01-05
Thanks to all of you for commenting. I'm glad to know there is at least one other person in the galaxy using booklet printing! (My use is for wedding services.)

Since I haven't the technical skill to rebuild the Ubuntu version, I'll hope that the developers for Dapper will hear about this issue and put back what has been left out of the official OOo 2.0.1 version.

---

### Post by doubled on 2006-04-02
[QUOTE=doubled]Thanks to all of you for commenting. I'm glad to know there is at least one other person in the galaxy using booklet printing! (My use is for wedding services.)

Since I haven't the technical skill to rebuild the Ubuntu version, I'll hope that the developers for Dapper will hear about this issue and put back what has been left out of the official OOo 2.0.1 version.[/QUOTE]

I am very happy to note that in Dapper Flight5 the build of OpenOffice has the restored option of printing portrait or landscape in the print dialog. This is very good news for those of us who use this feature. My thanks to the developers!!

---

