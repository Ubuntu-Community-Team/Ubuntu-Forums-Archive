---
title: "Cannot install steam under wine"
date: 2005-12-10
forum: Gaming &amp; Leisure
---

### Post by dccool879 on 2005-12-10
I have 2 questions, first where do i install fonts?

and second, i get this error when i try to install steam,

[email]haro@ubuntu:~/.wine[/email]/drive_c$ sudo wine SteamInstall.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
[email]haro@ubuntu:~/.wine[/email]/drive_c$

thanks!

---

### Post by YokoZar on 2005-12-10
[QUOTE=dccool879]I have 2 questions, first where do i install fonts?

and second, i get this error when i try to install steam,

[email]haro@ubuntu:~/.wine[/email]/drive_c$ sudo wine SteamInstall.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
[email]haro@ubuntu:~/.wine[/email]/drive_c$

thanks![/QUOTE]Do not run Wine as root.

You can put fonts in Wine's virtual windows drive at ~/.wine/drive_c/system/fonts

---

### Post by Rackerz on 2005-12-10
Also, Cedega is better for running 'Steam'

---

### Post by YokoZar on 2005-12-10
[QUOTE=Rackerz]Also, Cedega is better for running 'Steam'[/QUOTE]
Half Life 1 and Steam works perfectly under regular Wine if you follow the short howto here:

[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)  (scroll down to the green part)

---

### Post by dccool879 on 2005-12-10
But how do I fix my error?

[email]haro@ubuntu:~/.wine[/email]/drive_c$ wine SteamInstall.exe
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

---

### Post by dccool879 on 2005-12-10
ok, i get this for everything i do under wine
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
help?? xserver is running....

---

### Post by YokoZar on 2005-12-10
[QUOTE=dccool879]ok, i get this for everything i do under wine
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXxf86dga.so.1: cannot open shared object file: No such file or directory
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
help?? xserver is running....[/QUOTE]
The Wine packages at winehq.org only work with Breezy.  Are you using an old version of the package?  What does wine --version say?  APT shouldn't let you install without that library as it is a dependency.

---

### Post by dccool879 on 2005-12-11
i am using breezy, i got the deb from the apt directory and used some command to force it to work with the 64 bit release, i can't remember which i am not at home. could this be the problem? becuase i am using the 64 bit release?

---

