---
title: "Newbie, need to install application"
date: 2009-04-20
forum: General Help
---

### Post by JBL121 on 2009-04-20
Want to look at some jpg,s on a CD and read I should use F-spot.

It is under Applications/graphics/f-spot. I click on it but nothing happens.

I downloaded F-spot 0.5.0.3 as a tar file and extracted it to my /home/joe directory.

How do I install it and will it automatically go to the correct directory under root?

Confused in WIsconsin

Joe

---

### Post by Vaphell on 2009-04-20
first try to run already installed f-spot in terminal by typing in 'f-spot'
If there is some error you'll get the message. With it you can look for more precise answer, maybe it is a known problem and there is some workaround.

---

### Post by maheshasolkar on 2009-04-20
Before you download source and install it, let us try to find out what is wrong in the installed version of f-spot.

If you open Terminal (Applications -> Accessories -> Terminal) and type the following:

```
  f-spot
```

and hit enter, do you see any error messages?

By the way, you can double-click on the jpg file in file manager. It will open the file in the default image viewer. That should be sufficient if all you want to do is view the images.

---

### Post by maheshasolkar on 2009-04-20
I would also first try to reinstall f-spot from the repositories:

```
  sudo apt-get remove f-spot
  sudo apt-get install f-spot
```

---

### Post by JBL121 on 2009-04-20
This is what I got in terminal:


@joe-1600:~$ f-spot
[Info  19:39:33.217] Initializing DBus
[Info  19:39:33.554] Initializing Mono.Addins
[Info  19:39:34.093] Starting new FSpot server

(f-spot:6603): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 345 error_code 11 request_code 157 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
joe@joe-1600:~$ 


Does this help

Thanks for all responses

Joe

---

### Post by JBL121 on 2009-04-20
I tried the remove and install someone recommended but results are the same

Hope this helps.

---

### Post by Vaphell on 2009-04-20
do you have ati card by any chance?
because googling indicates problems with radeon/radeonhd drivers

---

### Post by JBL121 on 2009-04-20
It is an old Diamond Banchee PCI (not express just PCI) card.

This is an old backup machine I thought I would try Ubuntu on.

Does this help?

Thanks again

Joe

---

