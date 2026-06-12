---
title: "Media Players close"
date: 2009-01-26
forum: General Help
---

### Post by giutax on 2009-01-26
hello. I have an issue where my media players close when trying to play .mp3's. The mp3's will only work in rhythm box. If I try to play them in BOXEE or Totem movie player the player just quits with no errors that I can find. It may play 1 out 0f 10 times if that. They work fine on my other intrepid install just not this one. Fresh install on Lenovo T60p laptop. I am not sure where to even look because it is happening in multiple apps and works fine in another.

---

### Post by ajcham on 2009-01-26
Could you try starting Totem or BOXEE from a Terminal, then reproduce the error and see if any useful error information has been output to the console.

---

### Post by giutax on 2009-03-25
When i run totem in the terminal i get this:

ja@ja:~$ sudo totem
** (totem:12787): DEBUG: Init of Python module
** (totem:12787): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:12787): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:12787): DEBUG: Creating Python plugin instance
** (totem:12787): DEBUG: Init of Python module
** (totem:12787): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:12787): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:12787): DEBUG: Creating Python plugin instance

** (totem:12787): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 46 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** glibc detected *** totem: double free or corruption (!prev): 0x09d6be10 ***

I get this when trying to open a *.mp3, it happens with all music and video files. The player just closes after trying to open the files.

---

### Post by giutax on 2009-03-30
Upgrading to Jaunty Beta fixed this issue.

---

