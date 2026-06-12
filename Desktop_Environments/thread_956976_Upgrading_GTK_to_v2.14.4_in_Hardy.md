---
title: "Upgrading GTK to v2.14.4 in Hardy"
date: 2008-10-23
forum: Desktop Environments
---

### Post by x1a4 on 2008-10-23
Hi,
What's an *easy* way to upgrade GTK to version 2.14.4 in hardy? 

Thank you.

---

### Post by inigomontoya on 2008-10-24
I temporarily added either the debian lenny or sid repositories and updated it that way.  No promises that it will work for you.  I took a risk and it worked.

---

### Post by x1a4 on 2008-10-24
Just tried but both Lenny and Sid have 2.12.x versions.

---

### Post by inigomontoya on 2008-10-24
Oh now I remember, I actually compiled it from source.  Ubuntu didn't have new enough versions of the dependencies so that is what I got from the Debian lenny/sid repositories. It was a pain in the butt.

---

### Post by x1a4 on 2008-11-14
bump

---

### Post by mssever on 2008-11-15
I'm pretty sure there's no *easy* way to upgrade GTK aside from upgrading to Intrepid. Since it's a library, there'll be lots of dependency issues, and you may well end up upgrading all of Gnome by the time you're through. If you need a newer version, you'll probably be better off running Intrepid (in a VM if you want to keep your main machine on Hardy).

---

