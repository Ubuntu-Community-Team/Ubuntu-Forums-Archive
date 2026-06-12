---
title: "Why the DNS needs to be readjusted"
date: 2007-01-01
forum: Desktop Environments
---

### Post by kinemagician on 2007-01-01
I entered in System->Admin->Network the IPs of  DNS, but it seems that the OS "forgets them" and I have to enter them more than once in a session.  I even saved them in a file, but the inconvenient appeared again.  Any suggestion.  Thanks, Ettore](*,)

---

### Post by navneeth on 2007-01-01
I'm not be able to help you on this one, but I can say that this query should belong to the Networking subforum, not Desktop Environments. ;)

Edit: Welcome to the forums. :)

---

### Post by kinemagician on 2007-01-01
Sorry for the mistake, but I'm a real beginner.

---

### Post by compwiz18 on 2007-01-01
I can help, you need to **sudo chattr +i /etc/resolv.conf** - but before you do, make sure you know that this permanently locks the file, meaning NO ONE can edit it - not even root.  You have to **sudo chattr -i /etc/resolv.conf** the file before it will be editable again.

---

