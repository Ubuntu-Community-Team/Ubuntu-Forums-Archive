---
title: "Enabling desktop effects?"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by Cavs23 on 2008-02-04
I have followed all tutorials and when I go to change it to extra or custom it says, "Desktop effects can not be enabled". What can be an issue.. Supposably I have installed compiz but I am not sure. I have been using feisty for about 4 days now. And I run a nvidia geforce 7600


this is my compiz terminal

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0292 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Segmentation fault (core dumped)

---

### Post by FuturePilot on 2008-02-05
I wonder if it might have something to do with Emerald. Try removing Emerald first 
```
sudo apt-get remove --purge emerald
```
Then do 
```
compiz --replace
```

---

### Post by Cavs23 on 2008-02-05
```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0292 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2680x1050) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Segmentation fault (core dumped)
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 342 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Okay I did that and got that. Could any of this be because I have dual monitors?

---

### Post by bmeyer on 2008-02-06
I have dual monitors as well and am getting the exact same output.  Anyone have any ideas?

---

### Post by tomstrummer on 2008-02-07
Same problem -- dual widescreen monitors (configured as generic 1600x1200 LCD panels).  Desktop effects worked when I was only using one monitor, but when I added the second compiz went away.

Here is my 'compiz' output:
```
$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 18:00.0 0300: 10de:029e (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3200x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 349 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault
```

Also I am using the non-free NVidia drivers.

Any ideas?  Thanks.

---

