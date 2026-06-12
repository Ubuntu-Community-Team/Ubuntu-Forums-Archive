---
title: "QtOctave Packages do not install"
date: 2010-11-21
forum: Education &amp; Science
---

### Post by lubobuba on 2010-11-21
Hello,

I have problems installing Octave packages through QtOctave's [COLOR="Blue"]config/install Octave packages[/COLOR]. I tried to install through the GUI many packages but it never worked. Then I tried to go manually through the process, by downloading the .tar.gz file to the machine and using **>>> pkg install /tmp/qopm_packages/physicalconstants-0.1.7.tar.gz**

The error I am getting is:
```


[COLOR="Red"]couldn't create installation directory /usr/share/octave/packages/3.2/physicalc
onstants-0.1.7 : Permission denied
error: called from `pkg>copy_files' in file /usr/share/octave/3.2.4/m/pkg/pkg.m
 near line 1431, column 7
error: called from:
error:   /usr/share/octave/3.2.4/m/pkg/pkg.m at line 756, column 5
error:   /usr/share/octave/3.2.4/m/pkg/pkg.m at line 287, column 7[/COLOR]
```

---

