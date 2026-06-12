---
title: "Songbird won't start after update"
date: 2009-04-22
forum: General Help
---

### Post by mern1 on 2009-04-22
I recently discovered how to update songbird (run songbird as root to enable "check for updates" under Help).  However, after a successful update songbird will no longer start (as my user or root).  There are 3-4 songbird processes running but no window.  When I try to start songbird again I get an error message telling me it's already running and I need to close the others first.  Even after killing these processes and trying again I get the same problem.  Please help, I'm totally clueless.  Thanks

---

### Post by Vadi on 2009-04-22
I don't think songbirds update functionality is integrated well in linux (you should never run apps as root anyway, so this just shows it).

Best bet is to try to uninstall it, and get the updated version from here: [http://www.getdeb.net/search.php?keywords=songbird](http://www.getdeb.net/search.php?keywords=songbird)

---

### Post by vernonrj on 2009-04-22
If the above doesn't work, I deleted ~/.songbird2 and it worked.

---

### Post by mern1 on 2009-04-22
Deleting the ~/.songbird2 file did nothing.  How do I go about uninstalling songbird and then reinstalling it after downloading the .tar?

---

