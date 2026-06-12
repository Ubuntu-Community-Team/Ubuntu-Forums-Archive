---
title: "gphoto2 permissions for non sudo use"
date: 2006-02-27
forum: Desktop Environments
---

### Post by hollowhead on 2006-02-27
I'm sure this is an old one and has come up before on the forums.  However, when I searched I could find anything in the archives.  

When I plug my camera in I get 

"** Error ('Could not claim the USB device') ***

	      Could not claim interface 0 (Operation not permitted). Make sure no
	      other program or kernel module (e.g. dc2xx or stv680) is using the 
	      device and you have read/write access to the device. "  I kmow this is a permission thing since everything works as SU.

Doing this give the following output
 ls -lR /proc/bus/usb
/proc/bus/usb:
total 0
dr-xr-xr-x  2 root root 0 2006-02-27 08:25 001
dr-xr-xr-x  2 root root 0 2006-02-27 08:25 002
dr-xr-xr-x  2 root root 0 2006-02-27 08:25 003
dr-xr-xr-x  2 root root 0 2006-02-27 08:25 004
-r--r--r--  1 root root 0 2006-02-27 08:25 devices

/proc/bus/usb/001:
total 0
-rw-r--r--  1 root root 43 2006-02-27 08:25 001

/proc/bus/usb/002:
total 0
-rw-r--r--  1 root root 43 2006-02-27 08:25 001
-rw-r--r--  1 root root 50 2006-02-27 08:25 002

/proc/bus/usb/003:
total 0
-rw-r--r--  1 root root 43 2006-02-27 08:25 001

/proc/bus/usb/004:

 which is strange since I can plug in ubstick and read and write to it.  Group plugdev contains me as a user. I'm sure the solution is simple can anyone help.  Ta.

---

### Post by patrick295767 on 2006-05-05
did you find the way since the time ?,

I have same problems ... 

Thank you :-)

---

### Post by DarkStarAeon on 2007-02-12
I have the same problem :(

---

### Post by chris_w on 2007-03-10
Hi All,

not sure if you have solved your usb probs, but Ive just been googling for a slightly unrelated usb issue and found both this thread and hopefully an answer to the problem you have.

See [http://search.cpan.org/~gwadej/Device-USB-0.20/lib/Device/USB/FAQ.pod](http://search.cpan.org/~gwadej/Device-USB-0.20/lib/Device/USB/FAQ.pod)

Hope that helps

---

