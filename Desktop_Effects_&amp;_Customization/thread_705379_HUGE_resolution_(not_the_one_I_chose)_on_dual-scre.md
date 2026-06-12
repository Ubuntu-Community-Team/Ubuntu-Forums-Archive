---
title: "HUGE resolution (not the one I chose) on dual-screen"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by Mg++ on 2008-02-23
Hi,

I'm new in the Linux Ubuntu Community, and I can't make my Ubuntu Gutsy Gibbon working in dual screen with a 19" NEC HR19 (driver found) and a 15" Lite-On K15AN (driver not found, using generic) : the resolution used on the Nec's so huge ! I noticed a 3072*1536 resolution thanks to a call to 'compiz' within the terminal. As my monitor only supports 1280*1024 max, guess what ? I can "move the view of the desktop, hovering the borders of the screen using the mouse". Very strange, and quite hindering ; I'd even say : it's unusable...

It's been several months I intend to fix this (I'm on Windows meanwhile) so if you helped me, it would be nice of you ;) 

Another thing, perhaps linked to this one ; the command I quoted before lead to the log :
> totox@Dune:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3072x1536) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
The program 'gtk-window-decorator' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 341 error_code 181 request_code 157 minor_code 8)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)
Obviously I'm not able to translate, but I think it shows the reason why my "desktop effects couldn't be launched" (quoting)... That's indeed the other thing I'd like to fix.

Thanks aforehead.

N.B. I apologize for the language, I'm French...

---

### Post by arimaniac on 2008-03-02
I also have a 2 screen configuration so:
2 Identical LG L1910S 

I would recommend that you should start by finding drivers for your monitor (if any :( ).
Then download updated drivers for your card if you haven't done so.

And in my opinion the fact that you are having different screen 
sizes and the one uses generic drivers MAY be the wrong part... 

Why don't try a different monitor (change the 15" with a 19") 
with its drivers as a test and see what happens???

-ariMaNiaC

---

