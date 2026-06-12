---
title: "trouble using Alien to convert deb to rpm file"
date: 2009-01-07
forum: General Help
---

### Post by chinni.joy on 2009-01-07
Hi,

   I m trying to convert deb file to rpm.when type  'alien -r myfile.deb'
 instead of creating rpm file it displayed error on output in terminal.
 
  Output:

   Warning: Skipping conversion of scripts in package : postrm
   Warning: Use the --scripts parameter to include the scripts.
   Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Alien/Package/Deb.pm line 582.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Alien/Package/Deb.pm line 585.
mkdir: invalid option -- 0
Try `mkdir --help' for more information.
unable to mkdir -0:  at /usr/share/perl5/Alien/Package.pm line 257.


please help to solve my problem ..:confused:

---

### Post by ibutho on 2009-01-07
Have you tried using sudo in front of the alien command e.g.
```
sudo alien -r myfile.deb
```

---

### Post by chinni.joy on 2009-01-07
Yes, I tried with sudo alien -r myfile.deb .but  same output

---

### Post by jnw222 on 2009-01-07
i thought alien only allows rpm->deb not deb->rpm

---

### Post by chinni.joy on 2009-01-07
we have option -r or --to-rpm  which is for convert deb file to rpm according alien manual page
                       
                     -kumar

---

### Post by chinni.joy on 2009-01-07
Please some one help me to solve my problem

---

### Post by ibutho on 2009-01-07
Try the following
```
sudo alien -r --scripts myfile.deb
```

---

### Post by chinni.joy on 2009-01-08
hi ibutho,

 I tried with sudo alien -r scripts myfile.deb .its worked fine on others system. it is not  working on my machine.The output below please look at once 
 
OutPut:
 
Modification of a read-only value attempted at /usr/bin/alien line 363.
Usage: alien [options] file [...]
  file [...]                Package file or files to convert.
  -d, --to-deb              Generate a Debian deb package (default).
     Enables these options:
       --patch=<patch>      Specify patch file to use instead of automatically
                            looking for patch in /var/lib/alien.
       --nopatch	    Do not use patches.
       --anypatch           Use even old version os patches.
       -s, --single         Like --generate, but do not create .orig
                            directory.
       --fixperms           Munge/fix permissions and owners.
       --test               Test generated packages with lintian.
  -r, --to-rpm              Generate a Red Hat rpm package.
      --to-slp              Generate a Stampede slp package.
  -l, --to-lsb              Generate a LSB package.
  -t, --to-tgz              Generate a Slackware tgz package.
     Enables these options:
       --description=<desc> Specify package description.
       --version=<version>  Specify package version.
  -p, --to-pkg              Generate a Solaris pkg package.
  -i, --install             Install generated package.
  -g, --generate            Generate build tree, but do not build package.
  -c, --scripts             Include scripts in package.
  -v, --verbose             Display each command alien runs.
      --veryverbose         Be verbose, and also display output of run commands.
  -k, --keep-version        Do not change version of generated package.
      --bump=number         Increment package version by this number.
  -h, --help                Display this help message.
  -V, --version		    Display alien's version number.

Segmentation fault

---

### Post by ibutho on 2009-01-09
Unfortunately I am out of ideas. I don't know if anything has changed in recent versions of alien (its not a tool I use very often).

---

