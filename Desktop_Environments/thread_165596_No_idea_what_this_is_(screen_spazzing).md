---
title: "No idea what this is (screen spazzing)"
date: 2006-04-24
forum: Desktop Environments
---

### Post by tonyisntcreative on 2006-04-24
I just recently built a new PC.  I have been running Ubuntu Breezy on my old one for months with no problems (other than the computer being slow.)

For the most part, everything runs flawlessy and very fast, but every once in a while when I'm browsing the web everything just seems to freak out.  Here are screens of two instances when this has happened.  I have no idea what could be causing this.

If you need any certain info I'll provide it.

---

### Post by henriquemaia on 2006-04-24
Please give more details. Your specs, for instance.

ps: those screenshots look like a graphical card issue - proprietary drivers bug?

---

### Post by tonyisntcreative on 2006-04-24
ASUS A8N-E
Athlon 64 3500+
PNY GeForce 6600GT

It could be the video card...that makes some sense to me.  I don't know what I'd do to fix it, though.

---

### Post by henriquemaia on 2006-04-24
[QUOTE=tonyisntcreative]ASUS A8N-E
Athlon 64 3500+
PNY GeForce 6600GT

It could be the video card...that makes some sense to me.  I don't know what I'd do to fix it, though.[/QUOTE]

Are you running latest Nvidia drivers or Xorg nv driver?

---

### Post by tonyisntcreative on 2006-04-24
Just the default nv driver.

---

### Post by henriquemaia on 2006-04-24
[QUOTE=tonyisntcreative]Just the default nv driver.[/QUOTE]

Try installing the latest Nvidia drivers. That might help.

---

### Post by nelson2006 on 2006-04-24
[SIZE="2"]Hello, I have a Toshiba Satellite A105-S2712 with Dapper Drake Beta installed and everytime I press Shift+F5 I get the same first screenshot :-k .[/SIZE]

---

### Post by henriquemaia on 2006-04-24
[QUOTE=nelson2006][SIZE="2"]Hello, I have a Toshiba Satellite A105-S2712 with Dapper Drake Beta installed and everytime I press Shift+F5 I get the same first screenshot :-k .[/SIZE][/QUOTE]

But your computer freezes after that?

---

### Post by nelson2006 on 2006-04-24
[SIZE="2"]Yes, it does freezes, can't even open terminal. Have to shutdown and turn on again. After trying twice, I don't even think of pressing those two buttons together again [-( .[/SIZE]

---

### Post by tonyisntcreative on 2006-04-24
Mine doesn't freeze when it does it, the screen just goes whacko.

I'm going to try the new driver.  It hasn't done it in a bit, but if the problem persists later tonight or tomorrow I will let you all know.

---

### Post by tonyisntcreative on 2006-04-25
I'm having trouble updating my driver the way it is outlined on the Nvidia website.

However, I stumbled across [This]("http://doc.gwos.org/index.php/Install_Nvidia_driver") page and followed the steps without a problem.  In xorg.conf it still says I'm using the nv driver, though /shrug.

It hasn't flipped out since last night, but I have a feeling it will later on, yet.

---

### Post by tonyisntcreative on 2006-04-25
Yep, it just did it again.  Ironically, as I was coming to view this page.  Anyways, the NVIDIA-Linux-x86-1.0-8756-pkg1.run will not work.  This is the log for it.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Apr 25 20:37:10 2006

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : (not specified)
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
WARNING: Skipping the runlevel check (the utility `runlevel` failed to run).
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC test with CC="cc".
-> gcc-version-check failed:
   
   
   You appear to be comiling the NVIDIA kernel module with a different compiler
   than the one that was used to compile the running kernel.  The Linux 2.6 ker
   nel module loader rejects kernel modules built with a version of gcc that do
   es not exactly match that of the compiler used to build the running kernel. 
   The compiler used to compile the kernel was gcc 3.4; the current compiler is
   gcc 4.0.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' RPM installed.  If you
       know the correct kernel source files are installed, you may specify the
       kernel source path with the '--kernel-source-path' command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```I don't know what exactly to do.

---

