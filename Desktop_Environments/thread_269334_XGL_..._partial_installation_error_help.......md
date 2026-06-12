---
title: "XGL ... partial installation error help......"
date: 2006-10-01
forum: Desktop Environments
---

### Post by agentstewie on 2006-10-01
Hey guys, im fairly new to ubuntu, ( i have used linux before... mainly fedora core) and I am running into the issue where I partially installed XGL, I couldn't finish because of this error:XGL to start


```
Script started on Sun 01 Oct 2006 02:01:26 PM CDT
rahul@behera-laptop:
rahul@behera-laptop:~$ sudo apt-get install compiz xserver-xgl libgl1-mesa xserv 
er-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes


Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done



Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree... Done


xserver-xgl is already the newest version.

libgl1-mesa is already the newest version.

xserver-xorg is already the newest version.

libglitz-glx1 is already the newest version.

compiz-gnome is already the newest version.

Note, selecting emerald instead of cgwd

emerald is already the newest version.

[b]Package cgwd-themes is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source

However the following packages replace it:

  emerald-themes

E: Package cgwd-themes has no installation candidate

[/b]
Script done on Sun 01 Oct 2006 02:01:34 PM CDT

```


I don't know why it cant find the file....



As a result of this, I am not able login correctly to GNOME, It shows up with a grey screen and blinks back and forth between the grey screen and the command line login screen (looks exactly like when you would hit Cntrl + Alt + F4)

Another error...
```
rahul@behera-laptop:~/.wine/drive_c/Program Files/Adobe/Photoshop 7.0$ wine Photoshop.exe
fixme:actctx:QueryActCtxW 80000010 0x116283c (nil) 1 0x33fdc4 8 (nil)
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  148 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  37
  Current serial number in output stream:  37
rahul@behera-laptop:~/.wine/drive_c/Program Files/Adobe/Photoshop 7.0$

```

Any ideas on how to fix this problem??
After we find a solution, please help me finish the installation of XGL, I have to show my class mates in school that Linux is better than Mac/Windows

I am able to start X from the command line, but not getting the GNOME login screen.

To help you all, I am attaching the error messages from the startx command and Xorg error log file.

---

