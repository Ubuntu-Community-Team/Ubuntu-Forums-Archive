---
title: "xchat-gnome broken!"
date: 2006-08-21
forum: Desktop Environments
---

### Post by noxel on 2006-08-21
After running xchat-gnome once, i accidentally changed some tinting/transparency setting, and then it closed and i've never been able to re-open it. I've tried re-installing it in Synaptic, but that hasn't helped.

The error i get:

```
The program 'xchat-gnome' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 285 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I've tried downloading and compiling xchat-gnome myself, but i get a bunch of missing dependencies, some of which i can't even apparently install because of XGL. 

Anyways, if anyone knows a fix then i'd be very thankful.

---

### Post by maniacmusician on 2006-08-21
you could try deleting the hidden xchat folder (maybe .xchat-gnome ?) and opening it. might be a good idea to back it up first though.

---

### Post by noxel on 2006-08-22
Sorry, but where exactly would i find this hidden directory? I'm not sure where it is.

---

### Post by noxel on 2006-08-22
Bump. Anyone have any idea?

---

### Post by sandpaperback on 2006-08-23
I've got the same error.  The .xchat2 folder is in your home directory (hidden), but deleting it didn't do anything for me.  I can also confirm that it crashed as soon as I clicked the "enable transparency" option.  I'm also running XGL/Compiz, so I imagine it's some kind of conflict there.

**Edit:**

I fixed it.  Open a terminal and run gconf-editor.  Navigate to apps/xchat/main_window.  Set the background_transparency to 0 (zero).  

Open xchat-gnome.  

Right now you have a completely transparent backgroud.  Change to either a solid color or an image background.  Just avoid the transparency slider. :grin:

---

### Post by noxel on 2006-08-26
Thanks alot! That solved the problem. :D

---

### Post by Lunar_Lamp on 2006-08-29
Solved it for me also, thanks!

---

