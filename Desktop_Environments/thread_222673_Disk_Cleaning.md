---
title: "Disk Cleaning"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Sq322 on 2006-07-25
Ok, so I know about apt-get clean

Is there anything else that helps free up disk space from unnecessary clutter?

---

### Post by jstroot on 2006-08-04
I want to know this as well. 
A better question might be, is there stuff I can get rid of without un-installing anything?

---

### Post by mlind on 2006-08-04
cronjobs keep the unnecessary clutter away. other than that you should specify what you mean by clutter?

temporary files are usually on /tmp which is cleaned regulary. You have to clean unwanted stuff from your $HOME directory manually though.
for removing orphaned/unnecessary packages, use deborphan and maybe debfoster. install stuff using aptitude, not apt-get.

---

### Post by jstroot on 2006-08-04
> **mlind said:**
> .
for removing orphaned/unnecessary packages, use deborphan and maybe 
debfoster. install stuff using aptitude, not apt-get.
What is the differenc between aptitude and apt-get?

Also, last time I used Deborphan, it listed packages and libraries that I *pretty sure* are being used. 

I'll give debfoster a try.

Thanks

---

### Post by mlind on 2006-08-04
> **jstroot said:**
> What is the differenc between aptitude and apt-get?

Also, last time I used Deborphan, it listed packages and libraries that I [i]KNOW[/] are being used. 

I'll give debfoster a try.

Thanks

aptitude is smarter of the two. It removes orphaned dependecies automatically.
deborphan manual page states that it "finds packages that have no packages depending on them".
It only cares if some other package uses those.

---

### Post by jstroot on 2006-08-04
@mlind.
Thanks for the help!!! it is NOT unappreciated. Thank you.

I'm glad you've told me this info, but it leads to another question. 

I like the apt-get update manager. Is there on for aptitude, or do I just have to update manually?

-Jstroot

---

### Post by mlind on 2006-08-04
> **jstroot said:**
> @mlind.
Thanks for the help!!! it is NOT unappreciated. Thank you.

I'm glad you've told me this info, but it leads to another question. 

I like the apt-get update manager. Is there on for aptitude, or do I just have to update manually?

-Jstroot

I'm not sure, but I think aptitude is currently "unique" (on Dapper) when it comes to smart package handling.

---

### Post by etank on 2006-08-04
Some more info on apt-get vs. aptitude.
[http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

---

### Post by mlind on 2006-08-04
> **etank said:**
> Some more info on apt-get vs. aptitude.
[http://www.psychocats.net/ubuntu/aptitude.php](http://www.psychocats.net/ubuntu/aptitude.php)

aptitude can't really handle *install -f* which is useful when you manually install one package using dpkg and want missing dependencies from repositories.
aptitude always offers pretty nasty resolution which is to remove  half of the installed packages, when apt-get offers to install just the missing ones.

Maybe I'm using it wrongly?

---

