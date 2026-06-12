---
title: "Firefox Security Issue"
date: 2005-11-29
forum: Desktop Environments
---

### Post by skjantzen on 2005-11-29
When I try to access my webmail through my IP provider, I get a security alert and it won't let me into my webmail. The alert I get is as follows:

Firefox and webmail.shaw.ca cannot communicate securely because they have no common encryption algorithms.

Not sure if this is an Ubuntu issue, but I've never seen this when I had Fedora Core 3 or 4 installed. I've used linux for two years and have always been able to access my webmail. I've just installed Ubuntu and really like it except for this small problem. 

Scott

---

### Post by dcstar on 2005-11-29
[QUOTE=skjantzen]When I try to access my webmail through my IP provider, I get a security alert and it won't let me into my webmail. The alert I get is as follows:

Firefox and webmail.shaw.ca cannot communicate securely because they have no common encryption algorithms.

Not sure if this is an Ubuntu issue, but I've never seen this when I had Fedora Core 3 or 4 installed. I've used linux for two years and have always been able to access my webmail. I've just installed Ubuntu and really like it except for this small problem. 

Scott[/QUOTE]
Do any HTTPS sites work for you?

---

### Post by jambo on 2005-12-04
I am getting the same error, also at webmail.shaw.ca
I can go to other secure HTTPS sites, i.e. my bank, gmail, etc.  It is only Shaw Webmail that seems to fail.  It seems this is a problem with their website, but it works fine with older versions of firefox (i.e. firefox 1.0.2 will work with that website).
I have seen this issue only in Linux, beginning in firefox 1.0.4  It happens with Ubuntu 5.10 which currently has firefox 1.0.7 and also on my Debian partition.  This bug does not occur when running firefox in Windows.

---

### Post by towsonu2003 on 2005-12-04
I can enter the site no problem (though dont know sign in info :) so cant login)... I have java disabled and javascript enabled but blocked with extension NoScript, cookies enabled. using ff 1.5. Maybe relevant? 

if you are stuck, try epiphany, galeon, lynx (text based), and elinks (text based) to see if it's firefox specific / or ubuntu specific...

---

### Post by dcstar on 2005-12-04
Found this at:

[http://members.shaw.ca/Limulus/ubuntu.html](http://members.shaw.ca/Limulus/ubuntu.html)

[I]Here was an annoying problem; when I went to check my shaw webmail, I got the error message:

Firefox and webmail.shaw.ca cannot communicate securely
because they have no common encryption algorithms.

(which I wasn't getting from an XP computer...) A little searching led me to the solution: Go to about:config, find "security.ssl3.rsa_rc4_40_md5" and double click to change to "true". Shaw webmail should now work.[/I]


Seems to work!

---

### Post by skjantzen on 2005-12-22
Thanks for your help. The fix you suggested worked for me too.

skjantzen

---

### Post by angkor on 2005-12-22
On Firefox 1.5 I could enter the site, but Firefox warned me the site was using a low-grade security protocol.

---

