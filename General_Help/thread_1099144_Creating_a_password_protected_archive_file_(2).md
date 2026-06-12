---
title: "Creating a password protected archive file (2)"
date: 2009-03-17
forum: General Help
---

### Post by PaulWhipp on 2009-03-17
I needed to post some work on the net and wanted to use a compressed tar with password protection.

Easy one would think...

The archive manager (accessed from accessories) allows the creation of zips with password protection and lets you enter the password under options.

This might work for simple single files but when I use it on my real project folder (33Mb of assorted php, images etc.) it fails with a friendly pop up telling me that "An error occurred while adding files to the archive (null):

Next I thought I'd try pgp. It comes with ubuntu and looks pretty cool so I take my tar of the project and pipe it through thus:
```

~/Temp/spr $ tar -cp spr_site | gpg -c -o spr_project.tar.gpg
~/Temp/spr $ gpg -d spr_project.tar.gpg > test.tar
gpg: CAST5 encrypted data
gpg: encrypted with 1 passphrase
gpg: [don't know]: invalid packet (ctb=76)
gpg: [don't know]: invalid packet (ctb=61)
gpg: WARNING: message was not integrity protected
gpg: [don't know]: invalid packet (ctb=6c)

```

As you can see the errors occur on attempting to restore the tar. Such is life.

I try the trusty and apparently simple zip function that also comes with ubuntu:
```

~/Temp/spr $ tar -cpf spr_project.tar -C ~/Temp/spr spr_site
~/Temp/spr $ zip -r -e spr_project.tar.zip spr_project.tar
Enter password: 
Verify password: 
  adding: spr_project.tar (deflated 68%)
~/Temp/spr $ unzip -d test spr_project.tar.zip
Archive:  spr_project.tar.zip
[spr_project.tar.zip] spr_project.tar password: 
replace test/spr_project.tar? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
  inflating: test/spr_project.tar    

```

Third time lucky!

Actually it was the fourth time because I tried zipping the entire folder rather than zipping the tar but that fell over on re-inflation too saying that there was "invalid compressed data to inflate".

So the bottom line:
To zip an archive you can try the archive manager. When that falls over, use the zip/unzip command line but keep it to a few files.

---

