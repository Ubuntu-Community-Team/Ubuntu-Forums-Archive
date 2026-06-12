---
title: "Can't ssh or scp between boxes."
date: 2006-01-03
forum: General Help
---

### Post by chris_andrew on 2006-01-03
Hi, all.

I have two boxes running Breezy.  I need to transfel files between the two, so would like to use scp.  Unfortunately, the connection is refused on port 22.

I have looked at /etc/services, and port 22 seems to be fine (it's not hashed out).  I have tried the scp as root, so it's not a permission problem.  Finally, I can confirm that ssh is installed in /usr/bin, and I have successfully used ssh and scp in the past, on other hosts.  

Hopefully this eliminates the possibility of the error being between the keyboard and chair (me).  

Does anybody know which files I need to edit to permit ssh/ scp?

Many thanks,

Chris.

---

### Post by gnu2tux on 2006-01-03
[QUOTE=chris_andrew]Hi, all.

I have two boxes running Breezy.  I need to transfel files between the two, so would like to use scp.  Unfortunately, the connection is refused on port 22.

I have looked at /etc/services, and port 22 seems to be fine (it's not hashed out).  I have tried the scp as root, so it's not a permission problem.  Finally, I can confirm that ssh is installed in /usr/bin, and I have successfully used ssh and scp in the past, on other hosts.  

Hopefully this eliminates the possibility of the error being between the keyboard and chair (me).  

Does anybody know which files I need to edit to permit ssh/ scp?

Many thanks,

Chris.[/QUOTE]

Ubuntu doesn't install ssh server by default?

try $sudo apt-get install openssh-server (on each machine)

Regards,

Al.

---

### Post by chris_andrew on 2006-01-03
Oops, I saw ssh was available and assumed that was enough.

Thanks very much, Al.

Cheers,

Chris.

---

