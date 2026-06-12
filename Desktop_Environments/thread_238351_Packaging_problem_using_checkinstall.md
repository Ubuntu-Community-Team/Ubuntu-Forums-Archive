---
title: "Packaging problem using checkinstall"
date: 2006-08-17
forum: Desktop Environments
---

### Post by derbaschti on 2006-08-17
Hi,

I am trying to create a ubuntu package of some programs we use in our lab.
We obtain them as readily compiled binaries from the software vendor (OpenEye Inc.) 

In order to produce the package I installed checkinstall and wrote a suitable  install.sh script: 

```
#!/bin/sh

cp -R openeye/ /opt/
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/babel3-2.1 /usr/bin/babel
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/checkcff-2.2 /usr/bin/checkcff
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/chunker-2.2 /usr/bin/chunker
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/eon-1.1 /usr/bin/eon
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/fred2.1.2 /usr/bin/fred
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/fredPA2.1.2 /usr/bin/fredPA
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/ligand_info2.1.2 /usr/bin/ligand_info
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/makefraglib-2.1.0 /usr/bin/makefraglib
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/makerocsdb-2.2 /usr/bin/makerocsdb
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/masc_prep2.1.2 /usr/bin/masc_prep
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/mdl2sma-1.1 /usr/bin/mdl2sma
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/mol2nam-1.4 /usr/bin/mol2nam
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/nam2mol-1.4 /usr/bin/nam2mol
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/omega2-2.1.0 /usr/bin/omega
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/rocs-2.2 /usr/bin/rocs
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/sma2mdl-1.1 /usr/bin/sma2mdl
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/smartsopt-1.1 /usr/bin/smartsopt
ln --symbolic /opt/openeye/arch/suse-9.1-i586/bin/vida2 /usr/bin/vida
```

As you can see, everything is under the openeye/ directory and only needs to be copied to /opt/ and linked properly.

The building of the package goes fine, as well as installation. 

But when I try to deinstall the package with 

```
sudo dpkg -r openeyesuite
```

I get

```
(Reading database ... 75862 files and directories currently installed.)
Removing openeyesuite ...
dpkg - warning: while removing openeyesuite, directory `/opt' not empty so not removed.

```

So obviously, it removes everything just as it should, but then tries to remove the entire /opt directory. 

How can I prevent this strange behaviour?

---

### Post by mlind on 2006-08-17
Does your package contain .postrm rule (file) which is trying to remove /opt directory?

---

### Post by derbaschti on 2006-08-18
Thanks for the reply.How can I find out if the package contains this file?

---

### Post by derbaschti on 2006-08-18
So I found out that the .postrm files are located at /var/lib/dpkg/info, but there is no .postrm file for my package. The only thing that is there, is a file called openeyesuite.info:

```

/.
/opt
/opt/openeye
/opt/openeye/arch
/opt/openeye/arch/suse-9.1-g++3.3-x86_64
/opt/openeye/arch/suse-9.1-g++3.3-x86_64/lib
/opt/openeye/arch/suse-9.1-g++3.3-x86_64/lib/liboedepict-1.3.a
/opt/openeye/arch/suse-9.1-g++3.4-i586
/opt/openeye/arch/suse-9.1-g++3.4-i586/lib
/opt/openeye/arch/suse-9.1-g++3.4-i586/lib/liboefizzchem1.1.a
/opt/openeye/arch/suse-9.1-g++3.4-i586/lib/liboegrid1.1.a
/opt/openeye/arch/suse-9.1-g++3.4-i586/lib/liboeiupac-1.4.a
/opt/openeye/arch/suse-9.1-g++3.4-i586/lib/liboeshape1.6.0.a
/opt/openeye/arch/suse-9.1-g++3.4-i586/lib/liboesmack-1.1.a
/opt/openeye/arch/suse-9.1-i586
/opt/openeye/arch/suse-9.1-i586/bin
/opt/openeye/arch/suse-9.1-i586/bin/babel3-2.1
/opt/openeye/arch/suse-9.1-i586/bin/checkcff-2.2
/opt/openeye/arch/suse-9.1-i586/bin/chunker-2.2
/opt/openeye/arch/suse-9.1-i586/bin/eon-1.1
/opt/openeye/arch/suse-9.1-i586/bin/filter-2.0
/opt/openeye/arch/suse-9.1-i586/bin/flipper-2.1.0
/opt/openeye/arch/suse-9.1-i586/bin/fred2.1.2
/opt/openeye/arch/suse-9.1-i586/bin/fredPA2.1.2
/opt/openeye/arch/suse-9.1-i586/bin/ligand_info2.1.2
/opt/openeye/arch/suse-9.1-i586/bin/makefraglib-2.1.0
/opt/openeye/arch/suse-9.1-i586/bin/makerocsdb-2.2
/opt/openeye/arch/suse-9.1-i586/bin/masc_prep2.1.2
/opt/openeye/arch/suse-9.1-i586/bin/mdl2sma-1.1
/opt/openeye/arch/suse-9.1-i586/bin/mol2nam-1.4
/opt/openeye/arch/suse-9.1-i586/bin/nam2mol-1.4
/opt/openeye/arch/suse-9.1-i586/bin/omega2-2.1.0
/opt/openeye/arch/suse-9.1-i586/bin/rocs-2.2
/opt/openeye/arch/suse-9.1-i586/bin/sma2mdl-1.1
/opt/openeye/arch/suse-9.1-i586/bin/smartsopt-1.1
/opt/openeye/arch/suse-9.1-i586/bin/vida2
/opt/openeye/arch/suse-9.1-i586/bin/_vida-2.1.2
/opt/openeye/arch/suse-9.1-i586/bin/_vida2_bin.sh

```

This is just the beginning of the file, but I am pretty sure, that the problem is caused by the first 2 lines...

Any suggestions?

---

### Post by mlind on 2006-08-18
I've never used checkinstall myself, so it was just a wild guess..
Maybe its documentation provides tips for this issue.

---

### Post by derbaschti on 2006-08-19
OK, I removed the first 2 lines from the .info file and the package deinstalls cleanly. Now I only have to prevent checkinstall from creating these lines...

---

