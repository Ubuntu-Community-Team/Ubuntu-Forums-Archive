---
title: "MATLAB crashes when displaying graphics (SOLVED)"
date: 2013-04-06
forum: Education &amp; Science
---

### Post by kiul on 2013-04-06
[COLOR=#000000]There is another opengl issue in newer Matlab releases (e.g. R2013a):[/COLOR]

[COLOR=#000000]Matlab crashes when using "opengl info" or displaying opengl-based graphics required in 3D applications, as for example "vol3D.m" etc... [/COLOR]

[COLOR=#000000]I've solved this problem following the instructions posted in:[/COLOR]

[https://wiki.archlinux.org/index.php/Matlab](https://wiki.archlinux.org/index.php/Matlab)

[COLOR=#000000]regarding with:[/COLOR]

[B]
[COLOR=#000000][FONT=sans-serif]To identify this error, start MATLAB with[/FONT][/COLOR]

```
LIBGL_DEBUG=verbose matlab
```
[COLOR=#000000][FONT=sans-serif]
from the terminal and try to collect OpenGL information with opengl info from the MATLAB command prompt. If it crashes again and there is an output line like[/FONT][/COLOR]

libGL error: dlopen /usr/lib/xorg/modules/dri/swrast_dri.so failed (/usr/local/MATLAB/R2011b/bin/glnxa64/../../sys/os/glnxa64/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/lib/xorg/modules/dri/swrast_dri.so))[COLOR=#000000][FONT=sans-serif]then the problem is that MATLAB uses its own GNU C++ library, which is an older version than the up-to-date version on your Archlinux system. Make MATLAB use the current C++ library for your system by[/FONT][/COLOR]

```
cd /usr/local/MATLAB/R(your release)/sys/os/glnxa64
sudo unlink libstdc++.so.6sudo ln -s /usr/lib/libstdc++.so.6
```

In our case, Ubuntu (x86_64), the following symbolic link:

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libstdc++.so.6
```


has to be used instead of the latter one (/usr/lib/libstdc++.so.6) posted in Archlinux.

Hope it helps you [/B];)

---

