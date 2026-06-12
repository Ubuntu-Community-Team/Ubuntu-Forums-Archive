---
title: "lilypond-data error"
date: 2006-03-02
forum: Desktop Environments
---

### Post by thepocketdrummer on 2006-03-02
I keep getting this error with lilypond that is screwing up everything I want to do.

I get this error message.

Removing lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing lilypond-data (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 lilypond-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

Please help me fix this.

---

### Post by bluevoodoo1 on 2006-03-02
check this out

[http://ubuntuforums.org/showthread.php?p=680286#post680286](http://ubuntuforums.org/showthread.php?p=680286#post680286)

or

[http://ubuntuforums.org/showthread.php?t=103013&highlight=lilypond](http://ubuntuforums.org/showthread.php?t=103013&highlight=lilypond)

I had that problem before, I think to solve it you have to install kpsewhich, then uninstall lilypond-data, then uninstall kpsewhich. Check the links, they should help.

---

