---
title: "crystallography and molecular dynamics packages in synaptic"
date: 2008-03-03
forum: Education &amp; Science
---

### Post by nkamesh on 2008-03-03
hi 

I am a newbie to the linux world and recently installed ubuntu. Its been only a month since i joined graduate school and hoping to carry out research in crystallography.

I used ubuntu to install gromacs 3.3-1.5 using the synaptic and it worked like charm. I would however want the recent gromacs 3.3.3 version to be included in the repositories. That would be immensely beneficial. 

Also, I have not been able to install the CCP4 crystallography suite of programs ([www.ccp4.ac.uk](www.ccp4.ac.uk)) smoothly  eventhough when I have all the dependent files installed. Is it possible that the ubuntu version be uploaded in the repositories. For example the ccp4mg, has some bugs when run in ubuntu. 

it would be great if both the gromacs 3.3.3 and the ccp4 suite are tested in ubuntu and uploaded in the repos.

are there any crystallographers using ubuntu, that successfully installed the ccp4 suite (including the COOT package) ?.

---

### Post by LaserJock on 2008-03-03
> **nkamesh said:**
> hi 

I am a newbie to the linux world and recently installed ubuntu. Its been only a month since i joined graduate school and hoping to carry out research in crystallography.

I used ubuntu to install gromacs 3.3-1.5 using the synaptic and it worked like charm. I would however want the recent gromacs 3.3.3 version to be included in the repositories. That would be immensely beneficial. 

Also, I have not been able to install the CCP4 crystallography suite of programs ([www.ccp4.ac.uk](www.ccp4.ac.uk)) smoothly  eventhough when I have all the dependent files installed. Is it possible that the ubuntu version be uploaded in the repositories. For example the ccp4mg, has some bugs when run in ubuntu. 

it would be great if both the gromacs 3.3.3 and the ccp4 suite are tested in ubuntu and uploaded in the repos.

are there any crystallographers using ubuntu, that successfully installed the ccp4 suite (including the COOT package) ?.

Do you have any info on what specifically gromacs 3.3.3 would have over 3.3.2 which is what is scheduled to be released in Ubuntu 8.04? If we have a compelling reason we can file a Feature Freeze exception to try to get it in.

ccp4 is unfortunately not free enough to go into the usual Ubuntu repos. It probably would qualify for the Multiverse repo, which is used for non-free software, though.

-LaserJock

---

### Post by nkamesh on 2008-03-03
There seem to be some issues with a small number of missing interactions between atoms when using a simulation box like the "rhombic dodecahedron"([http://www.gromacs.org/gromacs/revisions/](http://www.gromacs.org/gromacs/revisions/))
 
I think its a commonly used simulation box and therefore would be important that the rectified features in the Gromacs be made available.

As for CCP4 suite  - they are free set of programs for the crystallographic academic community and has some of the most versatile and most used packages. So they are definitely free for academic use. It would be great if it comes into the ubuntu repos after testing.

---

### Post by Biochem on 2008-03-04
What Laserjock referer to with the word "free" is not only free of charge but also free to distribute and modify the software. In the case of CCP4 their licence stipulate:

1) Commercial organisations should contact us directly to arrange a licence.

2) The licence must be signed, and returned by fax or post (NOT email) to the following address:

So it is not free to modify and Canonical would probably have to call them to be sure that they have the right to distribute CCP4 in their repository. Also, the fact that you have your institution have to sign and fax the licence probably make it a bit complicated to put in the official repos.

---

### Post by joshypyesudas on 2009-03-17
I installed Gromacs using Synaptic package manger in Ubuntu 8.10. But I dont know how to start and check whether Gromacs is installed. Could anyone please help me.

---

