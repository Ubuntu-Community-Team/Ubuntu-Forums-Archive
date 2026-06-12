---
title: "Octave 3.2 installation errors"
date: 2010-11-10
forum: Education &amp; Science
---

### Post by NLMark1983 on 2010-11-10
Hi,

I recently started using Ubuntu.
When I was trying to install Octave I got the following errors:

[I]root@mark-laptop:/home/mark# apt-get install octave3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  octave3.2: Depends: libamd2.2.0 (>= 1:3.4.0) but it is not installable
             Depends: libarpack2 (>= 2.1+parpack96.dfsg) but it is not going to be installed
             Depends: libblas3gf but it is not installable or
                      libblas.so.3gf or
                      libatlas3gf-base but it is not going to be installed
             Depends: libcamd2.2.0 (>= 1:3.4.0) but it is not installable
             Depends: libccolamd2.7.1 (>= 1:3.4.0) but it is not installable
             Depends: libcholmod1.7.1 (>= 1:3.4.0) but it is not installable
             Depends: libcxsparse2.2.3 (>= 1:3.4.0) but it is not installable
             Depends: libfftw3-3 but it is not installable
             Depends: libfltk1.1 (>= 1.1.6) but it is not installable
             Depends: libgfortran3 (>= 4.3) but it is not installable
             Depends: liblapack3gf but it is not installable or
                      liblapack.so.3gf or
                      libatlas3gf-base but it is not going to be installed
             Depends: libqrupdate1 (>= 1.0) but it is not going to be installed
             Depends: libumfpack5.4.0 (>= 1:3.4.0) but it is not installable
             Depends: texinfo but it is not installable
             Recommends: libatlas3gf-base but it is not going to be installed
E: Broken packages
root@mark-laptop:/home/mark# [/I]

I  tried 
sudo apt-get autoclean
This didnt solve my problem.
What do I need to do to make it work?

Regards,

Mark

---

### Post by arju305 on 2010-11-11
The most easy way to do that will be from USC.
Just search for octave:
and install GNUOCTAVE and QTOCTAVE.
cheers!!!!!!!!!!

---

### Post by NLMark1983 on 2010-11-19
> **arju305 said:**
> The most easy way to do that will be from USC.
Just search for octave:
and install GNUOCTAVE and QTOCTAVE.
cheers!!!!!!!!!!

I tried to use the USC.
These are the results:

---

### Post by carandraug on 2010-11-21
have you tried to try to install the dependencies manually with apt-get and see what error comes out? To find out why they're not installable.

---

### Post by NLMark1983 on 2010-11-26
> **carandraug said:**
> have you tried to try to install the dependencies manually with apt-get and see what error comes out? To find out why they're not installable.

When I try to install the unmet dependencies manually, either the unmet dependencies cannot be found or have other unmet dependencies that cannot be found...

Strange isn't it? Did anyone have similar problems?

---

### Post by carandraug on 2010-11-26
> **NLMark1983 said:**
> When I try to install the unmet dependencies manually, either the unmet dependencies cannot be found or have other unmet dependencies that cannot be found...

Strange isn't it? Did anyone have similar problems?

And is this problem specific to Octave? Or it happens to all of them. Have you tried to download the package manually from the repository and then install it?

---

### Post by mionescu on 2010-11-27
Do you have enabled the universal (community) repository? Most of the staff needed by Octave is there. You can check this from USC via "Edit->Software Sources"

---

### Post by NLMark1983 on 2010-11-29
> **mionescu said:**
> Do you have enabled the universal (community) repository? Most of the staff needed by Octave is there. You can check this from USC via "Edit->Software Sources"

This did the trick!

Thanks a lot!

---

