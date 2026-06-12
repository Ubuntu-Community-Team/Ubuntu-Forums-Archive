---
title: "Can't open files directly from Chrome - opens Nautilus"
date: 2011-10-17
forum: Desktop Environments
---

### Post by knicles on 2011-10-17
Hi,
I'm having a problem with Ubuntu 11.10. I don't know what I did, but I can't open a file directly from my Google Chrome or Firefox download list.. it always opens Nautilus first at the file's folder, and then I need to find the file and open it. 
The same happens with other softwares such as Eclipse (I can't open directly my generated TexLipse PDFs) and this is really boring.
I'd appreciate help :) Thank you in advance.

---

### Post by gonzo1984 on 2011-11-04
I have no idea how it happened, but I was having the same problem and this seems to have fixed it:

Remove or comment out (by adding "#" in front of the line)
 x-scheme-handler/file=exo-file-manager.desktop

from this file:
.local/share/applications/mimeapps.list

credit to this post for a solution to a similar problem: [http://askubuntu.com/questions/73979/how-do-i-get-ubuntu-to-open-folders-with-nautilus-by-default](http://askubuntu.com/questions/73979/how-do-i-get-ubuntu-to-open-folders-with-nautilus-by-default)

Cheers!

---

### Post by nickbuntu on 2012-07-09
Thanks for this fix, it works! I think it's because I installed Xubuntu desktop once.

---

