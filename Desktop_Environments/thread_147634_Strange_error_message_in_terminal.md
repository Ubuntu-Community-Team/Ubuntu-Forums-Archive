---
title: "Strange error message in terminal"
date: 2006-03-20
forum: Desktop Environments
---

### Post by mdofl1 on 2006-03-20
Hello

First let me say that this forum has been the best that I have ever dealt with in the Linux community.  The people on here do an incredible job at replying and being helpful.  

Now saying that, I get the following message when I use the terminal as su:

configuration error - unknown item 'QUOTAS_ENAB' (notify administrator)
configuration error - unknown item 'NOLOGIN_STR' (notify administrator)
configuration error - unknown item 'ENV_HZ' (notify administrator)
configuration error - unknown item 'CHFN_AUTH' (notify administrator)
configuration error - unknown item 'CLOSE_SESSIONS' (notify administrator)

I just recently upgraded to Dapper and I am curious if this is problem due that or soemthing else.  


TIA,
-C

---

### Post by stuporglue on 2006-03-20
When you log into su -- ie. changing to root user?

Maybe check your root users .bashrc, and see if it tries to set any of those variables. There may be a line like "export FOO=blahfoowhatever".

---

### Post by jvolkman on 2006-03-20
I have this problem in Dapper.  It's with any user, not just root.  E.g., su <other-non-root-user> does it as well.

---

### Post by jvolkman on 2006-03-20
The problem has something to do with the file /etc/login.defs.  I had a file /etc/login.defs.dpkg-dist, which I assume was an updated version that wasn't installed.  I copied that file over and the errors are gone.

---

### Post by jamaas on 2006-04-12
Could you please give some detail about how you fixed this ... I have same problem but don't know what o put where !

Thanks

Jim

[QUOTE=jvolkman]The problem has something to do with the file /etc/login.defs.  I had a file /etc/login.defs.dpkg-dist, which I assume was an updated version that wasn't installed.  I copied that file over and the errors are gone.[/QUOTE]

---

### Post by GraemeWorthy on 2006-04-26
hey, i fixed it pretty easy.

i just copied the new login.defs over, as suggested above:
first save a copy.
then move over the new one.

 mv login.defs login.defs.breezy
 mv login.defs.dpkg-dist login.defs

worked for me.

---

### Post by jamaas on 2006-04-27
Worked for me too, thanks!

Jim
[QUOTE=GraemeWorthy]hey, i fixed it pretty easy.

i just copied the new login.defs over, as suggested above:
first save a copy.
then move over the new one.

 mv login.defs login.defs.breezy
 mv login.defs.dpkg-dist login.defs

worked for me.[/QUOTE]

---

