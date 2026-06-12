---
title: "Add/Remove isn't listing anything"
date: 2008-12-20
forum: General Help
---

### Post by dannytatom on 2008-12-20
When I open **Add/Remove Apps**, it doesn't list anything.  There's no errors, and Synaptic works just fine.  Screenshot attached.

Any ideas why it's broken? :(

---

### Post by dannytatom on 2008-12-20
I just tried restarting, but it did nothing. :/

---

### Post by sandyd on 2008-12-21
try tunning
sudo apt-get install  --reinstall app-install-data app-install-data-commercial

(all in one line)

---

### Post by dannytatom on 2008-12-21
That worked, thanks!  Any idea why it would've messed up to begin with?

---

### Post by susanw on 2009-01-14
Just had this same problem and your code worked perfectly,

thank you!!

---

### Post by t12121 on 2009-01-19
> **carlee said:**
> try tunning
sudo apt-get install  --reinstall app-install-data app-install-data-commercial

(all in one line)

Thanks worked for me also.

---

### Post by beau.raines on 2009-02-05
Worked for me too!
:D
Thanks

---

### Post by mb_webguy on 2009-02-05
I had a similar issue recently, and found that "sudo update-apt-xapian-index" fixed the problem.

---

### Post by bloke3142 on 2009-02-15
Sorted my problem too.

Thanks.

---

