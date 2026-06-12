---
title: "Changing weight of MIME type matches?"
date: 2008-12-14
forum: General Help
---

### Post by Endolith on 2008-12-14
I'm trying to solve [Bug 185165]("https://bugs.launchpad.net/ubuntu/+source/mime-support/+bug/185165"), but I don't know how to proceed.  There are two MIME types that match .url files, since there are two kinds of .url files.

In the case of a Linux .url file (text/x-uri), there's nothing in the file except a URL in plain text, so there's no magic word to grab and it's identified by the .url glob.

In the case of the Windows .url file (application/x-mswinurl), the extension is also .url, but there will be a [InternetShortcut] or [DEFAULT] tag at the beginning of the file.  Currently all .url files are recognized as text/x-uri, and a file is only recognized as application/x-mswinurl if you change the file's extension.  How do we make it so that Windows files are recognized based on both the extension and the magic words?

---

