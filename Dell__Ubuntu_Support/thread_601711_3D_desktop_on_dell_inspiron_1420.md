---
title: "3D desktop on dell inspiron 1420"
date: 2007-11-03
forum: Dell  Ubuntu Support
---

### Post by wallas on 2007-11-03
Hello

I've just installed Gutsy (7.10) on my inspiron 1420 laptop. It's clearly better than 7.04, it was even easier to install.

However, I haven't been able to make de 3d desktop work. I've been looking for another forum threads but I can't find anybody to have my problem.

I've gone to System>Preferences>Advenced Desktop (Compiz Config), but when I select 3D Effects, it doesn't happen anything, neither with de "trembling" windows.:(

I've a gma3000 video card, integrated.

Thanks a lot.

W.-

---

### Post by fcojbb on 2007-11-06
> **wallas said:**
> Hello

I've just installed Gutsy (7.10) on my inspiron 1420 laptop. It's clearly better than 7.04, it was even easier to install.

However, I haven't been able to make de 3d desktop work. I've been looking for another forum threads but I can't find anybody to have my problem.

I've gone to System>Preferences>Advenced Desktop (Compiz Config), but when I select 3D Effects, it doesn't happen anything, neither with de "trembling" windows.:(

I've a gma3000 video card, integrated.

Thanks a lot.

W.-

hello, 

In a terminal write this:

```
sudo gedit /usr/bin/compiz
```

and replace this line:

T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2972" # i965 (x3000)

for this:

#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2972" # i965 (x3000)


save the file.

Then write in the terminal this:

```
compiz
```

it's done.

Goodbye

---

### Post by wallas on 2007-11-06
Thaks for your answer... but

it appeared this when i wrote

>compiz

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

I even restarted, but it didn't work. :(

is there anything i haven't done?

W.-

---

### Post by sciurus on 2007-11-06
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152226](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152226)

---

