---
title: "Intrepid broke subversion with client certificates"
date: 2009-01-06
forum: General Help
---

### Post by hemna on 2009-01-06
Howdy,
  I recently upgraded my ubuntu to Intrepid and now subversion fails to work with collabnet when it requires a certificate.

Here is a snippet of my ~/.subversion/servers

[INDENT][global]
ssl-client-cert-file = /home/me/.subversion/mycertb.p12
ssl-client-cert-password = <my real password>[/INDENT]


[INDENT]me@dev:~/devel/myproject/$ svn up
Authentication realm: [https://myproject.csd200a.com:443](https://myproject.csd200a.com:443)
Client certificate filename:
Authentication realm: [https://myproject.csd200a.com:443](https://myproject.csd200a.com:443)
Client certificate filename:
Authentication realm: [https://myproject.csd200a.com:443](https://myproject.csd200a.com:443)
Client certificate filename:
svn: OPTIONS of 'https://myproject.csd200a.com/svn/myporject/trunk/tvision': SSL negotiation failed: SSL error: GnuTLS internal error. ([https://myproject.csd200a.com](https://myproject.csd200a.com))[/INDENT]

(note: myproject isn't the real name of the project or server...due to it being a project for my job)

Also, 
  I noticed that if I comment out the ssl-client-cert-password entry in the ~/.subversion/servers file, I never get prompted to enter the certificate passcode.  
This worked fine before I upgraded to Intrepid, which looks like svn is 1.5.1

I'm able to hit the server in firefox and authenticate with firefox's copy of the certificate.

---

### Post by wiggly on 2009-05-15
Just installed Jaunty on my desktop and this problem is still there.

This is a bit of a blocker for me upgrading my work laptop from Gutsy.

Will look for a bug report in launchpad and attempt to add one if I can't find one.

---

