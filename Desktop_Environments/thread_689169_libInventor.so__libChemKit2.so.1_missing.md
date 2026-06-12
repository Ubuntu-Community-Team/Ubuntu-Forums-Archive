---
title: "libInventor.so / libChemKit2.so.1 missing"
date: 2008-02-06
forum: Desktop Environments
---

### Post by acidk on 2008-02-06
Hi Folks!

Im working with a molecular Modeling program (grid). 
While visualizing and turning molecules the viewer crashes down and I receive:

flo@akb-12:~$ greater
Segmentation fault (core dumped)

Two libraries seem to be missing:
flo@akb-12:/opt/grid$ ldd gview.bin |grep "not found"
        
1) libInventor.so => not found

(I installed libinventor0 via synaptics)

and

2) libChemKit2.so.1 => not found

link 2 Fedora package:(Does not work/ wrong package mentioned here ?????)
[http://rpm.pbone.net/index.php3/stat/4/idpl/1604400/com/OpenMOIV-1.0.2-0.fdr.3.2.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1604400/com/OpenMOIV-1.0.2-0.fdr.3.2.i386.rpm.html)

The program(grid) is compiled on red hat. Do you know alternative packages for Ubuntu or any possible conversions?

---

