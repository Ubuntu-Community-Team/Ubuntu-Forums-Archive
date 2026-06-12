---
title: "Active Directory users in /etc/sudoers"
date: 2009-03-03
forum: Desktop Environments
---

### Post by awreneau on 2009-03-03
I've successfully added my 8.04 machine to W2K3 Active Directory using likewise-open.  I'm authenticating w/o any problems and have added my AD account to the /etc/suders file as well as the following groups in /etc/groups: adm and admin.  My domain account works flawlessly.

Having one other problem.  I'm unable to add a AD group tot he /etc/sudoers file

I've got the following:

%DOMAINNAME\group-name-with-dashes All=(All) All

Each time I :WQ I get prompted w/ an error form VISUDO that reads
"suders file: syntax error, line 24"  Wich reads exactly as I have it above.

has anyone else successfully added a AD group to /etc/sudoers if so, what was the syntax?

---

### Post by awreneau on 2009-03-04
This the line from SUDOERS that is indicated as an error.

%hs\\hd-ww-serveradmin-g0 All=(All) All

Can somebody tell me what is wrong w/ it?

---

### Post by gnarlygeek on 2009-03-06
The only issue I see is that "All" is not entirely uppercase.  I followed the example of uncleBez exactly, just substituted my domain in lowercase.   I'd try that next - good luck.

---

### Post by awreneau on 2009-03-06
Devil is in the details...

That seems to be the fix!

Thanks gnarlygeek

---

