---
title: "Alter Command line 2 Run AP in a Window"
date: 2009-12-06
forum: Desktop Environments
---

### Post by sandman3838 on 2009-12-06
Hello
Sorry about asking this.  I have come across this issue before, I never made a note on it before, but I just never thought I would need it.

I have this program the runs full screen.
I would like to run it Windowed?
The Command Line Ends with:

+menu 1 +fullscreen 1

Suggestions any one? 

Also, can one also specify the resolution for the program to run in?

Thanks everyone.

---

### Post by akashiraffee on 2009-12-06
> **sandman3838 said:**
> 
I have this program the runs full screen.
I would like to run it Windowed?
The Command Line Ends with:

+menu 1 +fullscreen 1

 Also, can one also specify the resolution for the program to run in?

Command line arguments are passed directly to the program by the shell/OS, so this is 100% dependent on the individual program.  Many programs that can run fullscreen will accept:

--fullscreen

Also, many more will accept a standard xorg style geometry request:

--geometry 1200x800+0+0

The two 0's would be offset left and offset from top.

However, your window manager can screw with this.  Some of them do.

Command line switches can be found in the "man" pages.  If you're not sure what something is called, try

apropos graphics

this will give you a list of man pages for applications with "graphics" in their short description.

---

