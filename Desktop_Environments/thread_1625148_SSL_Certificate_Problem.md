---
title: "SSL Certificate Problem"
date: 2010-11-18
forum: Desktop Environments
---

### Post by throese on 2010-11-18
So, why is it NOW giving me this problem? It was working just fine yesterday. I accidentally hit update in the update manager and then canceled it. Then I updated the SSL things to see if that would make the problem go away. No luck.

It keeps popping up and it's beginning to get on my nerves and in the way of other things. What do I do?

View attachment for what it looks like, please.

---

### Post by habl on 2010-11-19
Same problem here. Friend of my got the same problem. Empathy is working fine, only pidgin is heaving problems. Looks like an faulty update indeed, I updated my laptop yesterday, after that MSN in pidgin ain't working anymore.

On my desktop everything is still working fine, but didn't updated it yet.

---

### Post by Skabeh on 2010-11-19
[http://ubuntuforums.org/showthread.php?p=10134419](http://ubuntuforums.org/showthread.php?p=10134419)

---

### Post by lisati on 2010-11-19
Is this problem really solved? If so, an answer would be nice.....

---

### Post by habl on 2010-11-19
A bit fast in with setting it on solved indeed, it doesn't work for me unfortunately. Have no idea what to try next :s

---

### Post by habl on 2010-11-19
Ok problem is solved. Solution as follow:

Delete everything in:
/home/myuser/.purple/certificates/x509/tls_peers

Download this certificate:
[http://files.andreineculau.com/projects/pidgin/omega.contacts.msn.com.2.txt](http://files.andreineculau.com/projects/pidgin/omega.contacts.msn.com.2.txt)

Save it without the .txt in the same folder:
/home/myuser/.purple/certificates/x509/tls_peers

Restart pidgin.

---

### Post by throese on 2010-11-19
Yeah, sorry bout not responding. I just removed Pidgin entirely and am using the default IM program, Empathy. =)

---

### Post by bagy on 2010-11-19
> **habl said:**
> Ok problem is solved. Solution as follow:

Delete everything in:
/home/myuser/.purple/certificates/x509/tls_peers

Download this certificate:
[http://files.andreineculau.com/projects/pidgin/omega.contacts.msn.com.2.txt](http://files.andreineculau.com/projects/pidgin/omega.contacts.msn.com.2.txt)

Save it without the .txt in the same folder:
/home/myuser/.purple/certificates/x509/tls_peers

Restart pidgin.

Tnx man :)

---

