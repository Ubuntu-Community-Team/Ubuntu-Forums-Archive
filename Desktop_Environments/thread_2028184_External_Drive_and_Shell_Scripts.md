---
title: "External Drive and Shell Scripts"
date: 2012-07-17
forum: Desktop Environments
---

### Post by ashkot on 2012-07-17
Hi all,
I have installed Ubuntu on my PC as dual boot. I have an enternal drive formatted in NTFS that i want to share between the Ubuntu and Win. 

The problem is i am executing shell script on Ubuntu something like this

@ubuntu > bash myscript.sh > myfile.vcf

The issues are
Instead of my file having extension of .vcf it has an extension of vcf_

Second, when i try to open this file in Windows (its a text file), i can see the file in Windows Explorer but i get message that states "File Not found"

I am assigning permissions to myscript.sh as follows:
chmod +x myscript.sh

Can anyone help with this?

Thanks in advance.
Ashwin

---

### Post by lptr on 2012-07-18
What does your script. Best you would show it to us.

---

### Post by ashkot on 2012-07-18
this is a simple script

#!/bin/bash 
echo "Processing" 
xargs -a Omega-rs-Chr7.txt -I {} tabix -f ALL.chr7.phase1_release_v3.20101123.snps_indels_svs.genotypes.vcf.gz {} >> Data.vcf

The file that is created at the end if Data.vcf_

Where does the _ come from?

I am trying to execute this on a external USB drive using the following
$ bash myscript.sh

---

### Post by lptr on 2012-07-18
> **ashkot said:**
> 
#!/bin/bash 
echo "Processing" 
xargs -a Omega-rs-Chr7.txt -I {} tabix -f ALL.chr7.phase1_release_v3.20101123.snps_indels_svs.genotypes.vcf.gz {} >> Data.vcf


What happens if you don't replace - in other words - further simplifying that line? 

Other approach: If this underline is consistent you could rename the target file inside your script after finished. Right?

---

