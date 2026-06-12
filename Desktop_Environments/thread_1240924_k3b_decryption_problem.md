---
title: "k3b decryption problem"
date: 2009-08-15
forum: Desktop Environments
---

### Post by Avanesov on 2009-08-15
I just moved back to Kubuntu from Sabayon (Gentoo based kde system) and k3b isnt reading encrypted discs. On the Sabayon system if a disc was encrypted it would say it was downloading the required css files for decryption, but on my current Kubuntu system it just errors out with "cannot read encrypted disc". What do I need to install to get k3b to copy the encrypted discs again?


EDIT: libdvdcss is now installed, but doesnt work correctly for some reason. It fails to download the css files.

---

### Post by SoftwareExplorer on 2009-08-16
If you mean DVD's then you probably need libdvdcss. 
If you have amd64 (64 bit) Ubuntu -> [http://packages.medibuntu.org/pool/f...ntu1_amd64.deb]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb")
If you have i386 (normal, 32 bit ) Ubuntu -> [http://packages.medibuntu.org/pool/f...untu1_i386.deb]("http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb")

Hope that helps.

---

### Post by SoftwareExplorer on 2009-08-16
The reason libdvdcss doesn't automatically install is that it isn't in the default repositories because of patent issues.

---

### Post by Avanesov on 2009-08-16
I have libdvdcss installed....it errors downloading the css files....but it works from a sabayon install i have (with the same dvd).

The only major differance between the distros that im aware of is that the sabayon install is kde 4.2 and my kubuntu install is kde 4.3. But I dont think that should affect libdvdcss, or would it?

---

### Post by krazyd on 2009-08-16
that should be 'libdvdcss**2**' ...

---

### Post by SoftwareExplorer on 2009-08-17
> **krazyd said:**
> that should be 'libdvdcss**2**' ...
Thanks, I almost got it right! :)

---

### Post by SoftwareExplorer on 2009-08-17
> **Avanesov said:**
> I have libdvdcss installed....it errors downloading the css files....but it works from a sabayon install i have (with the same dvd).

The only major differance between the distros that im aware of is that the sabayon install is kde 4.2 and my kubuntu install is kde 4.3. But I dont think that should affect libdvdcss, or would it?
I don't think that the kde version would have much to do with it. The difference might be what is installed by default. 
What have you done to try to fix the problem so far? (Including what I suggested.) If there is an error copy and paste it here. Its alot easier to see what is going on when you know what the error is instead of having to guess.

---

