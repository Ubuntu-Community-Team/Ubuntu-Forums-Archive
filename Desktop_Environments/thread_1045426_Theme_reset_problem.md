---
title: "Theme reset problem"
date: 2009-01-20
forum: Desktop Environments
---

### Post by FireJet on 2009-01-20
Hello, 

I've been having a problem with my GNOME/GTK themes lately, or specifically a custom one I made, which looks like this:

[IMG]http://img84.imageshack.us/img84/8048/screenielinux118dq0.png[/IMG]

But then at seemingly arbitrary times (sometimes half a day, sometimes less than an hour), everything resets, and all my GTK apps seem to completely lose their skinning, like so:

[IMG]http://img132.imageshack.us/img132/309/screenielinux119nr1.png[/IMG]

But, as soon as I open up the appearance settings, it sets it back to my theme. Both operations send my CPU to pretty much full usage, and everything lags for about ~20 while this is happening. 

I've searched around and couldn't find anything similar. Any help?

---

### Post by FireJet on 2009-01-21
Figured out the problem was with gnome-settings-daemon, and this is the error I get after it runs:

```

firejet@bfs-desktop:~$ gnome-settings-daemon --no-daemon 
desired is = /home/firejet/.config/monitors.xml.desired
reading configuration...
done
error MATCHESShutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7043 error_code 8 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[1232550496,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

```

---

### Post by midnightreport on 2009-07-20
I'm a bit confused, how did you solve the theme reset problem (or did you solve it)?

---

