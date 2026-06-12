---
title: "Hard disk sleep"
date: 2005-12-13
forum: General Help
---

### Post by Randy Sparks on 2005-12-13
Does anybody know if it's possible to configure the hard disk to sleep after a set period under Ubuntu? 

I've searched Synaptic but can't find an actual program that does the job. I know this can be done using hdparm but I'm looking for a better way of doing it.

---

### Post by 23meg on 2005-12-13
Why isn't hdparm a good enough way for you? If you're using a laptop, you may consider looking into laptop-mode.

---

### Post by Randy Sparks on 2005-12-13
hdparm's a dangerous program to be playing around with. It helps if you understand I'm trying to instruct others how to sleep their hard disk, and don't want them crashing their computers by mistyping. 

I'll look into laptop-mode. Nowadays modern computers seem to include an ACPI system as good as most notebooks, so there's a good chance it will work with desktop computers too.

---

### Post by 23meg on 2005-12-13
One good thing about giving instructions online in command line form is that there's no chance of mistyping as long as you're giving exact commands; people can just copy and paste. Whereas if you give GUI instructions they can misclick and mess things up. Besides, hdparm may be dangerous in general but putting drives to sleep with it shouldn't be dangerous, since it will just invoke the standard power saving functions in use.

---

### Post by Randy Sparks on 2005-12-13
Well, any command issued with sudo is potentially dangerous for all kinds of reasons. But I think that Ubuntu should have some kind of GUI option for configuring power saving.

laptop-mode actually requires you to set the disk spindown using hdparm anyway and is designed to minimise waiting around while spin-up takes place. According to its readme: "Laptopmode is used to minimize the time that the hard disk needs to be spun up,
to conserve battery power on laptops."

---

### Post by 23meg on 2005-12-13
> Well, any command issued with sudo is potentially dangerous for all kinds of reasons. But I think that Ubuntu should have some kind of GUI option for configuring power saving.Isn't that self contradictory?

In any case, putting a system device to sleep will require superuser status, so it will be dangerous by your definition. IMHO, as long as one follows the exact procedure, invoking an ACPI event shouldn't be dangerous.

---

### Post by Mr. Electric Wizard on 2005-12-13
how do you set laptop mode?

---

### Post by 23meg on 2005-12-13
```
sudo laptop-mode start
```

---

