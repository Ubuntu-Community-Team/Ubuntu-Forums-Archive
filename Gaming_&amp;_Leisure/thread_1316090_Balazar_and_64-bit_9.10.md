---
title: "Balazar and 64-bit 9.10?"
date: 2009-11-05
forum: Gaming &amp; Leisure
---

### Post by Mr. Hibba on 2009-11-05
Hi all, 

When I try to download Balazar or Balazar Brothers through the Ubuntu Software Center I get the following error message: "Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time." 

If I try to install Balazar by using apt-get, I get the following message(s): "Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  balazar: Depends: python-soya (>= 0.13.2-1) but it is not going to be installed". 

So... I try to apt-get python-soya and get basically the same as above except the line reads, "The following packages have unmet dependencies:
  python-soya: Depends: libode0debian1 (>= 1:0.8.dfsg-3) but it is not installable". So... I then try apt-get on libode0debian1 and get "Package libode0debian1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libode0debian1 has no installation candidate". 

What should I do? 

Thank you for your time. 

Mr. Hibba.

---

### Post by arnab_das on 2010-01-11
same prob. help.

---

### Post by w33k on 2010-01-24
same problem! halp!

---

### Post by ViperScull on 2010-01-29
Download libode0debian1 from:

[http://packages.ubuntu.com/jaunty/i386/libode0debian1/download](http://packages.ubuntu.com/jaunty/i386/libode0debian1/download)   for i386 version

[http://packages.ubuntu.com/jaunty/amd64/libode0debian1/download](http://packages.ubuntu.com/jaunty/amd64/libode0debian1/download)  for amd64 version

Install it. then install python-soya via Synaptic, and then Balazar

---

### Post by Mr. Hibba on 2010-05-17
Wow, I'm sorry for my late reply. My bad... 

Thank you, ViperScull, for the information. :-). 

Also, to whom it may concern, I noticed that in 10.04, the version in the repos now works for 64-bit systems. 

Mr. Hibba.

---

