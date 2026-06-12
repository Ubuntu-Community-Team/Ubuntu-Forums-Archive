---
title: "Repositry URI's out of date?"
date: 2005-10-17
forum: Desktop Environments
---

### Post by 0ptiK on 2005-10-17
Wrong forum sorry :S

---

### Post by migueljacq on 2005-10-18
Your repositories are for Hoary but you posted this in Breezy. Are you using Breezy or Hoary?

If it's Breezy, view this thread for the official Breezy repositories

[http://www.ubuntuforums.org/showthread.php?p=411974](http://www.ubuntuforums.org/showthread.php?p=411974) (post #7)

---

### Post by 0ptiK on 2005-10-18
Right you are Mig ... my bad, using Hoary 

Now ... where was that delete button? :S

---

### Post by migueljacq on 2005-10-18
That being the case...

I believe the backports were removed, so you need to insert a # at the start of each line related to the backports. Someone can correct me if I'm wrong!
The first couple of errors seem to be related to your Hoary Installation disc, ie it is looking for it to get packages from. I think you can fix this in Synaptic. However I'm not an ubuntu expert so maybe someone can back all this up.

Miguel

EDIT: Go to Synaptic >> Edit >> Add CD ROM and insert the Hoary installation disc. Let me know if this was the problem

---

### Post by 0ptiK on 2005-10-18
Thanks Mig, that's fixed it, although now I get this little bugger:

W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

So there's no backports at all anymore?

---

### Post by migueljacq on 2005-10-18
[QUOTE=0ptiK]Thanks Mig, that's fixed it, although now I get this little bugger:

W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

So there's no backports at all anymore?[/QUOTE]

Not sure about that error at all, sorry.
As far as I know, the backports are gone. Some people say it's temporary and others say they're not coming back. If you search around the forum for 'backports' you might find out more :)

---

### Post by 0ptiK on 2005-10-18
Shall do, thanks again ;)

---

