---
title: "&lt;b&gt;Why only gftp?&lt;/b&gt;"
date: 2008-02-09
forum: Dell  Ubuntu Support
---

### Post by worxguy on 2008-02-09
I have a new Dell 530n with Ubuntu 7.10 pre-installed but gftp is the only ftp program I can get to work properly. Neither Filezilla nor Firefox/Fire ftp will show the local file directory. Filezilla just shows an empty folder and Fire ftp says it doesn't have proper permissions to access the directory. I have reset permissions for my home directory from the default 755 to 777 and that didn't help either program. Does the Dell setup add some extra security or something?

Fire ftp worked well under Ubuntu 7.10 on my old box, but Firefox was also upgraded when I made the switch.

Any thoughts?
worxguy

---

### Post by PhilOSparta on 2008-02-11
I just purchased a Dell 530N and always use gftp, so when I saw your title, it piqued my interest.  I tried FireFtp and I got the same problem as you.  FireFtp would let me look down through the directory structure anywhere except the home directory.  I researched the problem the best I could and turned on the debug switch down in the extension.
This is the debug info provided when I clicked on my home dir:
```
Error: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsILocalFile.isDirectory]" nsresult: "0x80004005 (NS_ERROR_FAILURE)" location: "JS frame :: chrome://fireftp/content/js/local/localDirTree.js :: anonymous :: line 109" data: no]
You do not have the appropriate permissions or directory does not exist.
```

It appears that there is a bug in FireFtp as reported on this link.
[http://ubuntuforums.org/showthread.php?t=609582](http://ubuntuforums.org/showthread.php?t=609582)

I don't know if this is only a problem with the Dell 530N.

I hope that helps.

Phil

---

### Post by worxguy on 2008-02-11
Thanks for your quick reply, Phil.

It's always nice to know that it isn't you or your local setup that's bummed. I'll be happy with gFTP and maybe try the others again when they get the bugs worked out.

thanks again,
worxguy

---

