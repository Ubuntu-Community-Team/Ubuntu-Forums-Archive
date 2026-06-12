---
title: "Problems with &quot;samba share&quot; after return from standby/sleep with Ubuntu 8.10"
date: 2009-05-28
forum: Desktop Environments
---

### Post by alanh on 2009-05-28
I have a DNS-323 NAS Drive which I'm accessing from a desktop running Ubuntu 8.10.  When I first mount the DNS-323 share, everything is hunky-dory.  I can access folders and files and save them.   However, when my desktop has returned from standby I have problems saving files, which manifests itself in a number of ways:

(1) If I "drag and drop" copy a file from another location (ie: my desktop), the original file modification date is not preserved, ie; it becomes the date and time I copied the file.
(2) If I open, edit and try to re-save an OpenOffice file, I get a "permissions" error.
(3) If I open, edit and re-save a text file, I get a "not a directory error"
(4) rsync gives error messages like: failed to set times on "dir_name"; not a directory (20)
(5) If my Thunderbird mailboxes are located on the DNS-323, TB keeps downloading the same email from the POP server over and over.

The permissions for the folders on the DNS-323 share all seem to be ok.

I think this started happening when I "upgraded" from Ubuntu  7:10 to 8:10 but I'm not sure because that upgrade also caused a ******** of other problems with samba shares, which have taken months to sort out.  This seems to be last remaining problem before I can get back to where I was with Ubuntu 7.10. (Note, the "upgrade" from 7.10 to 8.10 was a clean install).

Any help would be much appreciated but  - unless there is a very good reason - please don't suggest "upgrading" to 9.04, I'm looking for some stability and I'm getting a bit tired of the "improvements" I get with each new Ubuntu release.

---

