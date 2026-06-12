---
title: "msr-tools"
date: 2009-03-31
forum: General Help
---

### Post by sol_kanar on 2009-03-31
Hi!

I need to understand exactly how the utilities "rdmsr" and "wrmsr" (included in package "msr-tools") work. The "man" page about them is quite unsatisfying. 

I know that "rdmsr" reads a value from a Machine Specific Register (given its address); I tried the following syntax ( the address is 0x00000198 ):

```
rdmsr 198
rdmsr 198h
rdmsr 0x198
rdmsr 0x00000198
```

but nothing worked, I keep getting the same error:
```
rdmsr:open: No such file or directory

```

Could anyone please help me? Thanks in advance for your help! :-)

---

### Post by BrokenString on 2009-04-05
Hi,

I installed the msr-tools package using aptitude and I had the same problem. I solved it by downloading the msr-tools source archive and running the MAKEDEV-cpuid-msr script that came with it. After this, my previously installed package started working.

I think it was trying to read from /dev/cpu/*, but none of these "devices" existed until the script created them. I guess there should be something in the installation of the package to deal with that?

Hope that helps.

-- BrokenString

---

### Post by sol_kanar on 2009-04-06
> **BrokenString said:**
> Hi,

I installed the msr-tools package using aptitude and I had the same problem. I solved it by downloading the msr-tools source archive and running the MAKEDEV-cpuid-msr script that came with it. After this, my previously installed package started working.

I think it was trying to read from /dev/cpu/*, but none of these "devices" existed until the script created them. I guess there should be something in the installation of the package to deal with that?

Hope that helps.

-- BrokenString

That helps and SOLVES THE PROBLEM! 
Thank you, you are my savior! ^___^

---

### Post by jacktow on 2010-02-13
This should also do the trick:

```
sudo modprobe msr
```

---

