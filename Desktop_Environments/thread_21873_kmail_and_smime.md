---
title: "kmail and s/mime"
date: 2005-03-24
forum: Desktop Environments
---

### Post by tonym on 2005-03-24
I've just installed kubuntu. 

I wish to use both GPG and S/MIME for encryption in kmail.  GPG works easily but I can't find any info on how to set up S/MIME.  Can anyone point me at any info?

Regards

Tony Middleton.

---

### Post by Ironi on 2005-03-24
Try this:

1. apt-get install gnupg2 gnupg-agent dirmngr kleopatra gpgsm pinentry-qt

2. Restart your X session so that gnupg-agent runs (it adds an entry to /etc/X11/Xsession.d).

3. Run KMail and make sure that "S/MIME (gpgsm)" is available and configurable in Settings -> Configure KMail -> Security -> Crypto Backends.

Additional steps may or may not be required (e.g. adding pinentry-qt to gpg-agent.conf); I haven't tested the above. More info (somewhat obsolete) is available from these two links:

[http://kmail.kde.org/kmail-pgpmime-howto.html](http://kmail.kde.org/kmail-pgpmime-howto.html)
[http://lists.debian.org/debian-kde/2004/09/msg00102.html](http://lists.debian.org/debian-kde/2004/09/msg00102.html)

---

### Post by tonym on 2005-03-25
I've set up as described above and it looks promising.  However I can't import my s/mime certificates into kleopatra.  This appears to be a [known problem.](http://www.gnupg.org/aegypten/development.en.html#howto_import_external_certs)  So far I've not been able to get the described work around to work,  but I haven't given up yet.

Regards

Tony Middleton

---

### Post by o4xah on 2005-12-05
It works ;) with kmail+smime+pgp .
I made before only 'apt-get update && apt-get upgrade'

Thanx for tip 'Ironi' :)

---

### Post by Cinquero on 2007-07-18
Does not work for me. It always complains about an invalid IPC call when talking to "gpgsm --server". Using Ubuntu 7.04. Maybe gpgsm is too new for kleopatra 3.5.6??

---

