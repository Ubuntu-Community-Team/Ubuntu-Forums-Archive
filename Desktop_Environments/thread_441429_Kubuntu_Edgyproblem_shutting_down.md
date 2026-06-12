---
title: "Kubuntu Edgy:problem shutting down"
date: 2007-05-12
forum: Desktop Environments
---

### Post by eldersoares on 2007-05-12
hi
if i shut down through the power button, ok! but through kde, it doesnt work well... everything closes but the pc doesnt turn off... the same with rebooting. through kdm works well, too. i've been searching in the forum and changed somenthings, but nothing different happened... in /etc/modules i added
apm power_off=1

and in /etc/apci/powetbtn.sh i added the P in
/sbin/shutdown -hP now "Power button pressed"

plz help!
thanx!

---

### Post by eldersoares on 2007-06-29
some1 help me please!!!

---

### Post by bailout on 2007-06-29
Not really a proper fix but what I do is logout and then shutdown from the kdm screen. Never had the problem when doing it this way.

---

