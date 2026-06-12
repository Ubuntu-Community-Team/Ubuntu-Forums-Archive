---
title: "Cant run synaptic or sudo apt-get anything"
date: 2009-03-16
forum: General Help
---

### Post by lenswipe on 2009-03-16
Tried to install uae from synaptic as i was missing the old amiga games and wanted an emulator to run amiga ROMs. 

When i clicked install though i got a message in synaptic telling me in short to run sudo dpkg --configure -a to fix some problem or other which i duly did. Now i cant open synaptic or run sudo apt-get anything.

If i run synaptic from terminal it just says segmentation fault.

If i run sudo apt-get anything it says the same.

I went to ubuntu IRC where ActionParsnip told me to run 

```
sudo apt-get --reinstall install synaptic

```

Which i did and got the expected error of segmentation fault. He then told me to run 
```
dmesg | tail
```

Which produced the following output:

```
robert@C01:~$ dmesg | tail
[  340.477914] apt-check[8231]: segfault at 2ec2d62c eip b7c1827e esp bfda1cd0 error 4
[  353.923961] ACPI: Transitioning device [FAN0] to D0
[  353.923968] ACPI: Transitioning device [FAN0] to D0
[  353.923971] ACPI: Unable to turn cooling device [f7c49b40] 'on'
[  462.576115] synaptic[8391]: segfault at 2cf51624 eip b7ecb27e esp bfb94730 error 4
[  469.262068] ACPI: Transitioning device [FAN0] to D3
[  469.262079] ACPI: Transitioning device [FAN0] to D3
[  469.262084] ACPI: Unable to turn cooling device [f7c49b40] 'off'
[  574.253243] apt-get[8547]: segfault at 2ecb9624 eip b7f0427e esp bfdf93d0 error 4
[  580.227535] apt-check[8552]: segfault at 2ec8962c eip b7c7427e esp bf89f7d0 error 4
robert@C01:~$
```

Which spoke of error code 4.

An error code neither of us could make head nor tail of. 

Anyone got any ideas?


-L

---

### Post by kuja on 2009-03-17
Wow, looks tough. Try downloading the appropriate versions of apt and dpkg from the repositories and reinstalling them. For 8.10 I've posted the appropriate links below.

32-bit
[http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.14ubuntu6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.14ubuntu6_i386.deb)

64-bit
[http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.14.20ubuntu6_amd64.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.14ubuntu6_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.14ubuntu6_amd64.deb)

To install the packages once downloaded use "dpkg --install <filename>" For example, "dpkg --install dpkg_1.14.20ubuntu6_i386.deb"

Maybe this will work. Don't know. It's worth a try at any rate.

---

### Post by nelskurian on 2009-03-17
> If i run synaptic from terminal it just says segmentation fault.Could try 
```

sudo rm /var/cache/apt/*.bin
sudo apt-get update
```

I've heard corrupt cache might do that.You might want to save those files first --

---

### Post by hyper_ch on 2009-03-17
providing the exact error message usually helps troubleshooting.

---

### Post by lenswipe on 2009-03-17
> **nelskurian said:**
> Could try 
```

sudo rm /var/cache/apt/*.bin
sudo apt-get update
```

I've heard corrupt cache might do that.You might want to save those files first --


I dont see a file called *.bin


Also with regards the previous poster, i cant post the exact error message because i cant get into synaptic to make it show the error message again.

-Lenswipe

---

### Post by fieroboom on 2009-03-17
> **lenswipe said:**
> I dont see a file called *.bin


Also with regards the previous poster, i cant post the exact error message because i cant get into synaptic to make it show the error message again.

-Lenswipe

The asterisk is a wildcard, meaning that command will remove anything in your apt cache with a .bin file extension.
Does this segfault only happen with apt/synaptic?
-Paul

---

### Post by nelskurian on 2009-03-18
> **fieroboom said:**
> The asterisk is a wildcard, meaning that command will remove anything in your apt cache with a .bin file extension.
Does this segfault only happen with apt/synaptic?
-Paul
R you try that?

---

### Post by lenswipe on 2009-03-27
yeah its only with synaptic or apt

Can someone help me fix this because its a real **** not being able to install things like emacs.

-L

---

### Post by albinootje on 2009-03-27
> **lenswipe said:**
> 
[  340.477914] apt-check[8231]: segfault at 2ec2d62c eip b7c1827e esp bfda1cd0 error 4
[  353.923961] ACPI: Transitioning device [FAN0] to D0
[  353.923968] ACPI: Transitioning device [FAN0] to D0
[  353.923971] ACPI: Unable to turn cooling device [f7c49b40] 'on'
Are there more programs segfaulting ? Do you have a cooling problem ? And did you run a memtest ?

---

### Post by lenswipe on 2009-04-03
> **albinootje said:**
> Are there more programs segfaulting ? Do you have a cooling problem ? And did you run a memtest ?

nothing else is segfaulting and how do i run a mem test?

Also i cant run .debs because they wont install either.

---

### Post by albinootje on 2009-04-03
> **lenswipe said:**
> nothing else is segfaulting and how do i run a mem test?

Also i cant run .debs because they wont install either.

Memtest86 should be available in the grub boot menu, but after rereading your posting it looks like only something inside the dpkg/apt structure is messed up.

Did you already consider backing up your data, and reinstall ?

---

