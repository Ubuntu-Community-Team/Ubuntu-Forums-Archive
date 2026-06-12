---
title: "The program 'XYZ' received an X Window System error"
date: 2008-01-18
forum: Desktop Environments
---

### Post by puccio on 2008-01-18
Hi,

after a regular update of the packages that I did this morning for my Ubuntu Gutsy Gibbon (I update them regularly as soon as the orange advices pops up) I started experiencing crashes when launching some video applications.

Here a sample while trying to launch **gxine**:
[INDENT]The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 323 error_code 8 request_code 142 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/INDENT]

Here a sample while trying to launch **Eclipse**:
[INDENT]The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 444 error_code 11 request_code 151 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/INDENT]

**My system configuration**:
[LIST]
[*] **Dell Inspiron 6400**
[*]ATI card using **fglrx** driver
[*] Ubuntu **Gutsy Gibbon**
[*] Desktop manager Gnome
[/LIST]

and as I said, before today everything was working, something happened after the upgrade of the latest package releases...   How could I try to switch back to the state of packages of yesterday to try if it really depends on this?

---

### Post by ironclaw on 2008-01-18
I think it's a problem with the updates (I think it was xorg) that came out. This thread has several more people with that problem: [http://ubuntuforums.org/showthread.php?t=671065]("http://ubuntuforums.org/showthread.php?t=671065")

---

### Post by puccio on 2008-01-18
Thanks,

I joined the discussion in the other thread!

---

### Post by divali on 2008-01-19
I too updated Xorg and had a great difficulty starting up. and when I finally got to my desktop I found 
many apps unable to start, appletts missing and  I Ican't reinstall Nvidia drivers.

As soon as a fix is done for xorg do let us all know via this thread. Please.

---

### Post by Skweek on 2008-01-19
I believe an update to this fix is available now.

---

