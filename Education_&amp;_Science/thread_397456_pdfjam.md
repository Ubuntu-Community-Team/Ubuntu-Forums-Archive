---
title: "pdfjam"
date: 2007-03-30
forum: Education &amp; Science
---

### Post by PeterC on 2007-03-30
Hi,

I have installed Tex Live 2007 on Kubuntu 6.10.

Now, I would like to install pdfjam.

1) When I run 'apt-get install pdfjam', pdfjam wants to install some additional tetex packages (libkpathsea4 libt1-5 pdfjam tetex-base tetex-bin tetex-extra tex-common) 131 MB!

Will these packages mess up my Tex Live installation?

2) Can I install (and use) pdfjam without installing the tetex packages?

Thanks

---

### Post by tweedledee on 2007-03-31
> **PeterC said:**
> Hi,

I have installed Tex Live 2007 on Kubuntu 6.10.

Now, I would like to install pdfjam.

1) When I run 'apt-get install pdfjam', pdfjam wants to install some additional tetex packages (libkpathsea4 libt1-5 pdfjam tetex-base tetex-bin tetex-extra tex-common) 131 MB!

Will these packages mess up my Tex Live installation?

2) Can I install (and use) pdfjam without installing the tetex packages?

Thanks

Use these answers with caution, but...
1) I don't think so.  It's really drawing on the tetex-extras and related dependencies, so shouldn't affect the main installation.

2) No.  At least not without getting the source and compliing yourself, and even so you'd need most of it.

---

