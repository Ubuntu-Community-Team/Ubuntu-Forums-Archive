---
title: "Netgen 4.9.13 not run."
date: 2013-01-25
forum: Education &amp; Science
---

### Post by ybUnetgen on 2013-01-25
Hi, 

I just installed Netgen on Ubuntu 12.04.  But I am not able to run it.  Here is what I got.  Could anybody help out?  Thank you very much. 

NETGEN-4.9.13
Developed at RWTH Aachen University, Germany
and Johannes Kepler University Linz, Austria
Including OpenCascade geometry kernel
Parsing ng.tcl
optfile ./ng.opt does not exist - using default values
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  546
  Current serial number in output stream:  546

---

### Post by paupitz on 2013-03-12
Hi

After upgrade to Ubuntu 12.10 got a similar problem:

NETGEN-4.9.13
Developed at RWTH Aachen University, Germany
and Johannes Kepler University Linz, Austria
Including OpenCascade geometry kernel
Parsing ng.tcl
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  490
  Current serial number in output stream:  491

---

