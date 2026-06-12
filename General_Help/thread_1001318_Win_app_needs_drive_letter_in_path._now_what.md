---
title: "Win app needs drive letter in path. now what?"
date: 2008-12-03
forum: General Help
---

### Post by walter_j on 2008-12-03
I must use a oracle db using java over a vpn connection. When I want to save the results of a query to a local file, the java app will not let me unless the path includes a drive letter (ie C:\data ). Is there a way around this in ubuntu 8.10? TIA

Walter

---

### Post by iaculallad on 2008-12-03
Can you not change the current path on a configuration file? Like instead of "C:\data" -> "/media/C_Drive/data"? Be sure to change the mount point as it serves only as a sample.

---

### Post by walter_j on 2008-12-03
> **iaculallad said:**
> Can you not change the current path on a configuration file? Like instead of "C:\data" -> "/media/C_Drive/data"? Be sure to change the mount point as it serves only as a sample.

The app is on a remote pc, and is accessed via java (using Opera). I tried entering a file name only which doesn't work, and a valid linux path which also doesn't work. The app insists on a drive letter in the path. I don't have access to the source code of the java app, so any solution would have to come from my local linux pc. I wonder if wine and internet explorer would work? Does wine allow me to enter a drive letter in a path?

---

### Post by josephellengar on 2008-12-03
> **walter_j said:**
> The app is on a remote pc, and is accessed via java (using Opera). I tried entering a file name only which doesn't work, and a valid linux path which also doesn't work. The app insists on a drive letter in the path. I don't have access to the source code of the java app, so any solution would have to come from my local linux pc. I wonder if wine and internet explorer would work? Does wine allow me to enter a drive letter in a path?

Yes.  In the wine configuration thing you can assign drive letters to any valid linux path.  For example, I assigned drive letters to my flash drive mountpoint, my C:, etcetera.  It's under applications->wine->configure wine-> drives tab.  I've never tried to install IE in it, but I suspect it would work.  Good luck!

---

### Post by walter_j on 2008-12-03
Sorry. I was using the linux opera, and accessing the java app over vpn. It just occurred to me both of you were telling me to set up a wine config file and use a win browser in wine. I'll give it a try. The only trick is  java under wine now. I'll give it a go.


Thanks guys!

---

### Post by walter_j on 2008-12-04
Unfortunately I can't get java running under wine. I installed java for windows with wine, but had trouble getting a browser to work with java. I tried a bunch of browsers ie firefox, opera, ie and others but no go. It'll be easier to dual boot, or on a windows pc.

Thanks

---

### Post by solitaire on 2008-12-04
Does the program accept UNC paths?

i.e. \\computer\shared\folder\path\database

---

### Post by Kellemora on 2008-12-05
Hi Walter

Don't know if this will work or not, but perhaps you can assign a drive letter Y in wine and symlnk it to /media/C_Drive.  Or whatever file you need it linked to.

Your Ubuntu drive is Drive Z in Wine, perhaps you might try that angle to see what happens?

Good Luck

TTUL
Gary

---

### Post by walter_j on 2008-12-11
nuttin worked. But thanks for the help. i still learned something...


Walter

---

