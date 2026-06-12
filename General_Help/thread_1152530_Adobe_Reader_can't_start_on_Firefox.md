---
title: "Adobe Reader can't start on Firefox"
date: 2009-05-07
forum: General Help
---

### Post by satimis on 2009-05-07
Hi folks,

Ubuntu 8.04
Firefox
Adobe Reader 9

Adobe Reader doesn't start on browser.  On browsing websites having .pdf fire they ask to install Adobe Reader.  However Adobe Reader 9 is running on this box.

Applications -> Office -> Adobe Reader 9 
starts the application.


$ locate nppdf.so```

/opt/Adobe/Reader9/Browser/intellinux/nppdf.so
/root/.mozilla/plugins/nppdf.so
/usr/lib/firefox/plugins/nppdf.so
/usr/lib/firefox-addons/plugins/nppdf.so
/usr/lib/mozilla/plugins/nppdf.so

```

$ ls -al /opt/Adobe/Reader9/Browser/intellinux/nppdf.so ```

-rwxr-xr-x 1 10490 floppy 179552 2009-02-28 08:14 /opt/Adobe/Reader9/Browser/intellinux/nppdf.so

```

$ ls -l /root/.mozilla/plugins/nppdf.so ```

-rwxr-xr-x 1 root root 179552 2009-04-25 21:56 /root/.mozilla/plugins/nppdf.so

```

$ ls -l /usr/lib/firefox/plugins/nppdf.so ```

-rwxr-xr-x 1 root root 179552 2009-04-25 21:56 /usr/lib/firefox/plugins/nppdf.so

```

$ ls -l /usr/lib/firefox-addons/plugins/nppdf.so```
 
-rwxr-xr-x 1 root root 179552 2009-04-25 21:56 /usr/lib/firefox-addons/plugins/nppdf.so

```

$ ls -al /usr/lib/mozilla/plugins/nppdf.so ```

-rwxr-xr-x 1 root root 179552 2009-04-25 21:56 /usr/lib/mozilla/plugins/nppdf.so

```


nppdf.so is already there.  Please advise how to solve the problem.  TIA


B.R.
satimis

---

