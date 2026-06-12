---
title: "On Upgrade, Address Book is Empty"
date: 2005-12-21
forum: General Help
---

### Post by Octane on 2005-12-21
I just upgraded to KDE 3.5, which means new Kontact too. Somehow, all of my contacts just disappeared. Not a single one of them comes up in the Contacts tab (or in KAddressbook) and only Recent Addresses come up when writing an email.

Any ideas what's going on? This may be very costly... Thank you!

---

### Post by Octane on 2005-12-22
bump

---

### Post by Octane on 2005-12-24
last bump

---

### Post by asimon on 2005-12-24
I just encountered the same problem on Dapper but I was able to recover my addresses. This was what I did:

From a terminal window (i.e. konsole)
```
$ cd ~/.kde/share/apps/kabc/
$ ls -l
total 181
drwx------ 2 andreas andreas  1416 2005-12-24 22:24 lock
drwx------ 2 andreas andreas    48 2004-07-29 15:44 logos
drwx------ 2 andreas andreas    48 2004-07-29 15:44 photos
drwx------ 2 andreas andreas    48 2004-07-29 15:44 sounds
-rw------- 1 andreas andreas     0 2005-12-24 22:24 std.vcf
-rw------- 1 andreas andreas     0 2005-12-19 21:10 std.vcf_1
-rw------- 1 andreas andreas     0 2005-12-20 18:26 std.vcf_2
-rw------- 1 andreas andreas     0 2005-12-21 19:26 std.vcf_3
-rw------- 1 andreas andreas     0 2005-12-22 16:19 std.vcf_4
-rw------- 1 andreas andreas     0 2005-12-23 01:27 std.vcf_5
-rw------- 1 andreas andreas     0 2005-12-24 22:24 std.vcf_6
-rw------- 1 andreas andreas     0 2005-12-18 23:28 std.vcf_7
-rw------- 1 andreas andreas  93172 2005-12-09 16:18 std.vcfbp6Lmb.new
-rw------- 1 andreas andreas     0 2005-12-16 13:38 std.vcfmRszZa.new
-rw------- 1 andreas andreas     0 2005-10-21 00:01 std.vcfyO5obc.new

```
As you can see the file std.vcf which usually contains all addresses was empty but there was still a copy std.vcfbp6Lmb.new there which contained all my addresses. Thus I copied this over to /tmp and imported those addresses again into KDE's addressbook.

```

$ cp std.vcfbp6Lmb.new /tmp/std.vcf

```
Open the adressbook, choose from the menu 'File -> Import -> Import vCard...' and point it to /tmp/std.vcf.
Of course your file will probably be named slightly different and if you have bad luck there is no copy there ...

---

### Post by Octane on 2005-12-27
Thank you so friggin much

---

