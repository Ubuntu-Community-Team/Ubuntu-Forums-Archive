---
title: "Quick Question?"
date: 2008-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by grenet on 2008-06-16
I'm getting this error message when trying to update:

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/hardy/Release.gpg](http://archive.ubuntustudio.org/ubuntustudio/dists/hardy/Release.gpg)  Could not resolve 'archive.ubuntustudio.org'

W: Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntustudio.org/ubuntustudio/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'archive.ubuntustudio.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Can anyone offer some insight into how I would fix this problem?

Thanks in advance.

---

### Post by Muflon on 2008-06-17
I had a similar problem, caused by connecting to the internet via a proxy server.  If you also connect via a proxy server then you may need to configure your settings in 'Synaptic Package Manager', Settings \ Preferences \ Network.

Muflon

---

