---
title: "Unshar Utilities Don't Install."
date: 2005-10-29
forum: Desktop Environments
---

### Post by Phreakist on 2005-10-29
Hey,

I'm trying to install the shar/unshar utilities but for some reason whenever I try to install them they won't and i get an error in the installation terminal that says this:

Preconfiguring Packages ...
dpkg: syntax error: unknown group 'postdrop' in statusoverride file

any help?

Phreak

---

### Post by Xian on 2005-10-30
Post the contents of these files:

/var/lib/dpkg/statoverride

/var/lib/dpkg/statoverride-old

---

### Post by Phreakist on 2005-10-30
StatOverride:

root postdrop 02555 /usr/sbin/postqueue
postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop

StatOverride-Old:

postfix postdrop 02710 /var/spool/postfix/public
root postdrop 02555 /usr/sbin/postdrop


Phreak

---

### Post by Phreakist on 2005-11-03
any help?

---

### Post by DaveLinde on 2006-01-18
I have the same problem, see [http://www.ubuntuforums.org/showthread.php?t=116085]("http://www.ubuntuforums.org/showthread.php?t=116085")

Did this one get solved?  How?

---

### Post by kbuntu on 2007-05-02
This problem is not to do with what you are trying to install right now, but with what you install before this.

Reconfiguring the package "postfix" should solve the problem.

Do
[FONT="Courier New"]sudo dpkg-reconfigure postfix[/FONT]

Choose the default values (unless you want to do something and you know what you are doing).

This is probably a bug, as installation of postfix should have ideally configured it completely.

HTH.

---

