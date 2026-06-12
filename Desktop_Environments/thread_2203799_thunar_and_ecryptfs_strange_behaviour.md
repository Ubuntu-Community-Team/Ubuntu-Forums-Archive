---
title: "thunar and ecryptfs: strange behaviour"
date: 2014-02-05
forum: Desktop Environments
---

### Post by oneone on 2014-02-05
I am running xubuntu, 13.10, amd64. 

The combination of [thunar]("http://en.wikipedia.org/wiki/Thunar") and [ecryptfs]("http://ecryptfs.org/") leads to the following, unexpected behaviour:
[LIST=1]
[*]Create a [FONT=courier new]~/Private[/FONT] folder by running [FONT=courier new]ecryptfs-setup-private[/FONT].
[*]Mount the private folder with [FONT=courier new]ecryptfs-mount-private[/FONT].
[*]drag&drop or copy&paste a file into [FONT=courier new]~/Private[/FONT] using thunar.
[/LIST]

Now the copied file 
[LIST]
[*]appears in [FONT=courier new]~/Private[/FONT] but has **0 bytes** and
[*]appears in [FONT=courier new]~/.Private[/FONT] with encrypted filename but **plaintext content**.
[/LIST]

If I copy the file using [FONT=courier new]cp[/FONT] in the terminal, it is working as expected. The copied file is shown in thunar in [FONT=courier new]~/Private[/FONT], with expected content and it is present in [FONT=courier new]~/.Private[/FONT] with encrypted filename and encrypted content.

It seems as if thunar accesses a ecryptfs mount point in an unexpected, unwanted way.

Can anyone confirm this or is this just happening on my machine? Is it a bug?

---

