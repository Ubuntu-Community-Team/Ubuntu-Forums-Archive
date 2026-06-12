---
title: "Displaying GAMESS calculations with MolPlt"
date: 2009-10-08
forum: Education &amp; Science
---

### Post by LowDepth on 2009-10-08
Hey there, I'm trying to display calculated frequencies with MolPlt. 
My input file for GAMESS is as follows:

```
!   File created by the GAMESS Input Deck Generator Plugin for Avogadro
 $BASIS GBASIS=STO NGAUSS=3 $END
 $CONTRL SCFTYP=RHF RUNTYP=HESSIAN MOLPLT=.TRUE. $END
 $FORCE METHOD=ANALYTIC VIBANL=.TRUE. $END

 $DATA 
Title
C1
C     6.0     0.35675     1.20424    -0.00000
C     6.0     1.63137     0.65021     0.00000
C     6.0     1.79292    -0.73139    -0.00000
C     6.0     0.67592    -1.56085     0.00000
C     6.0    -0.60154    -1.01394    -0.00000
C     6.0    -0.76885     0.37322     0.00001
H     1.0     0.23508     2.29473     0.00000
H     1.0     2.50949     1.30500    -0.00000
H     1.0     2.79831    -1.16608     0.00000
H     1.0     0.80141    -2.64893    -0.00000
H     1.0    -1.47720    -1.67624     0.00000
C     6.0    -2.11390     0.98361     0.00001
Cl    17.0    -3.46877    -0.17434    -0.00000
O     8.0    -2.37097     2.16076    -0.00001
 $END
```

Now I want to display the results. What do I have to do to make MolPlt display me intensity versus wavenumber? I get a .dat file from GAMESS but when I open it with MolPlt and choose "subwindow - frequencies" the opening window just stays blank.


regards

---

### Post by LowDepth on 2009-10-15
My problems are solved. I didn't know, that I have to write all GAMESS output to a logfile via ```
./rungms jobname.inp >jobname.log
```

Now that I've done it MolPlt can extract all useful information out of this jobname.log file.

---

