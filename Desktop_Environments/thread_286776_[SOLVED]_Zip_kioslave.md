---
title: "[SOLVED] Zip kioslave"
date: 2006-10-28
forum: Desktop Environments
---

### Post by mikyt on 2006-10-28
Hi!
I've been using Kubuntu Breezy for about one year and every time I clicked on a zip, tar or tgz file it was opened by konqueror using the appropriate kioslave, so I could read every archive as if it were a normal folder.

After updating to Edgy via apt-get, archive files are opened with Ark, that, altough working correctly, is much less convenient.
The kioslaves are still working correctly (that is, if I type zip://filename in konqueror the file is opened), but it isn't done automatically as before.

Does anyone know how I could setup the system in order to have it working as before?

Thank you!

---

### Post by blackrax on 2006-11-13
Yup, I have the same problem - don't remember when it happened though. Did you find a solution? I've googled and searched various forums, but come up empty handed.

BTW, I have the same issue with the other compressed formats.

Cheers,
Blackrax

---

### Post by mikyt on 2006-11-14
I've searched everywhere I could think of but with no luck. However, I had problems with other compressed formats too. To be precise, with every compressed format that Breezy was able to handle.

---

### Post by banano on 2006-11-14
Hi, I ran into the same problems and finally found a solution.

Ckeck /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application  for following files:

x-tar.desktop
x-tarz.desktop
x-tbz.desktop
x-tgz.desktop
x-zip.desktop

Look if they only contain

[Property::X-KDE-LocalProtocol]
Type=
Value=

because this should actually be

Type=**QString**
Value=**tar** (or **zip** in case of x-zip.desktop)

I copied all the files to ~/.kde/share/mimelnk/application and edited them as described. Now konqueror uses the desired kioslaves (at least for me it works)

Good luck - banano


> **mikyt said:**
> I've searched everywhere I could think of but with no luck. However, I had problems with other compressed formats too. To be precise, with every compressed format that Breezy was able to handle.

---

### Post by Blutack on 2006-11-14
Erm I just went configure konqueror, file assoc, click 'Application', choose show in embedded viewer.  Worked for me.

---

### Post by mikyt on 2006-11-14
> Ckeck /usr/share/kubuntu-default-settings/kde-profile/default/share/mimelnk/application for following files:

x-tar.desktop
[...]

Wonderful! It's the solution I was looking for! Thank you!

> Erm I just went configure konqueror, file assoc, click 'Application', choose show in embedded viewer.  Worked for me.
I had tried that too, but it didn't work for me.

---

### Post by chemist109 on 2007-09-19
Just wanted to add my thanks to banano.  His solution fixed this nagging problem for me.  Should it be posted as a bug?

---

### Post by mikyt on 2007-09-19
> **chemist109 said:**
> Should it be posted as a bug?
I don't know if it's a bug or a feature request, but I think it should definitely be posted. 
It's a very convenient thing and I think it should be enabled by default, as it used to be.

---

