---
title: "Movie players wont work from nautilus , somtimes !"
date: 2006-01-15
forum: Desktop Environments
---

### Post by thegladaitor on 2006-01-15
ON quite a few occasions I have had this problem where the mvoie that I open from nautilus in Mplayer or totem just open for a split second and close almost immediately without no error. When I run the mplayer from the command line , the movie works. I tried to open the terminal , run nautilus and then click on the file , but as soon as nautilus is opened , the terminal returns to the shell .

Rarely , when I run from totem , it also restarts the X .

After a reboot the system behaves well and sometimes I might get an error or might go soothly...cant find the prob...please help me figuring te prob...

Has nyone had this problem ?
Can someone help me n finding this out ?


PS : I got the error  while running from Totem from terminal . As i said mplayer works from the terminal 

thegladiator@thegladiator:/media/hda5/Movies/ronin$ totem ronin.avi

(totem:8220): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:8220): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 90 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

