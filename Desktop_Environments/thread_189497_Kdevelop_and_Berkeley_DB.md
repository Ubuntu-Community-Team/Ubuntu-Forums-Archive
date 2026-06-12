---
title: "Kdevelop and Berkeley DB"
date: 2006-06-05
forum: Desktop Environments
---

### Post by kulashaker on 2006-06-05
Hi,

I just installed 6.06 on my IBM T42 laptop. Have to say that I am pleasantly surprised with the dapper - smooooth installation, and you can play around with the system while it's installing. Sweet!

I just tried to install KDevelop 3.3.3 though and the ./configure outputs: 

**checking for Berkeley DB >= 3... configure: error: no - please install Berkeley DB >= 3 and <= 4.1**

dpkg tells me that I have libdb4.3 installed. So I tried to install 4.1 or older, but apt runs into unmet dependencies when I try to remove libdb4.3:

**openoffice.org-l10n-en-gb: Depends: openoffice.org-common (>= 2.0.2) but it is not going to be installed or language-support-en but it is not going to be installed**

Can anyone here help me fix this?

Thanks in advance,
cc

---

