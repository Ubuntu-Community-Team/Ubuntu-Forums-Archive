---
title: "problem install texlive"
date: 2012-04-30
forum: Education &amp; Science
---

### Post by mj125 on 2012-04-30
hi
i try to install texlive  from dvd
i install perl-tk and i write 
sudo ./install-tl -gui perltk

i get this error:
Installing [0001/2261, time/total: ??:??/??:??]: 12many [376k]
Downloaded /home/masoud/Application/archive/12many.source.tar.xz, size equal, but md5sum differs;
downloading again.
./tlpkg/installer/xz/xzdec.x86_64-linux: (stdin): File format not recognized
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
untar: untarring /usr/local/texlive/2011/temp/12many.source.tar failed (in /usr/local/texlive/2011/texmf-dist)
untarring /usr/local/texlive/2011/temp/12many.source.tar failed, stopping install.
Installation failed.
Rerunning the installer will try to restart the installation.
Or you can restart by running the installer with:
  install-tl --profile installation.profile [EXTRA-ARGS]
Not creating a log file but flushing messages to stderr.
Installing TeX Live 2011 from: /home/masoud/Application
Platform: x86_64-linux => 'x86_64 with GNU/Linux'
Distribution: inst (compressed)
Directory for temporary files: /tmp
Loading /home/masoud/Application/tlpkg/texlive.tlpdb
Installer revision: 23172
Database revision: 23180
Installing [0001/2261, time/total: ??:??/??:??]: 12many [376k]
Downloaded /home/masoud/Application/archive/12many.source.tar.xz, size equal, but md5sum differs;
downloading again.
untar: untarring /usr/local/texlive/2011/temp/12many.source.tar failed (in /usr/local/texlive/2011/texmf-dist)
untarring /usr/local/texlive/2011/temp/12many.source.tar failed, stopping install.
Installation failed.
Rerunning the installer will try to restart the installation.
Or you can restart by running the installer with:
  install-tl --profile installation.profile [EXTRA-ARGS]

please help me
thank you

---

### Post by wukongjiaozi on 2012-06-01
hi
I also got the same problem.
Did you install it by an iso mirror?

you can download the error file and paste it into your install directory and install again.
It may help.

---

### Post by Bachstelze on 2012-06-01
Why not just install it from the repos?

---

### Post by PC_load_letter on 2012-06-03
> **Bachstelze said:**
> Why not just install it from the repos?

+1. From the terminal type: 

```
sudo apt-get install texlive
```

The version in 12.04 repos is the 2009 version, so unless you want a feature that only comes with the latest version, the one in the repos is pretty good actually.

---

