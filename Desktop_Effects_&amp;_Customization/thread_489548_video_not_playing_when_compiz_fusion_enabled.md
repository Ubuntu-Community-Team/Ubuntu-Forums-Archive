---
title: "video not playing when compiz fusion enabled"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by cyneuron on 2007-07-01
hello there.

i have successfully installed compiz-fusion on my ubuntu feisty system. i run it by running compiz --replace in alt-F2. my system is fully updated.

but my videos are not playing when compiz is enabled. Totem just starts and then closes by itself without playing video. no other problem like crash occurs., while videos play normally without compiz enabled.

everything else works fine.

please help me.

my system is : 
acer aspire 1641 laptop
Intel centrino mobile : intel 915 chipset : 512 MB RAM : 128 MB shared in graphics (with Max DVT (or something like this) enabled in bios, i really dont know what is this, but it was the max. setting in bios after 128 Mb for graphic memory so i enabled it)

by the way is there any way to enable right from boot up or having something in system tray which may be used to toggle compiz with normal desktop, rather than running this command after loggin in ?

---

### Post by hyperair on 2007-07-01
Ah, I know that problem pretty well. If you run totem in the command line you'd get something along the lines of not enough resources. That's the hard truth.. your computer does not have enough resources to watch movies on totem while using Compiz Fusion. Try using another movie player, such as MPlayer (sudo apt-get install mplayer) or VLC (sudo apt-get install vlc)

---

### Post by sendas on 2007-08-05
I am having the same problem on my laptop while running compiz. Shouldn't I have enough resources to run compiz and totem?

Toshiba Laptop 1.6ghz dual core
2GB of ram
950 Intel video card 224MB of shared ram

when I run totem from the console it says 

```
$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 47 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I'm not sure but I would think 224mb of video ram and 2GB of system ram should be plenty for compiz and divx playback in totem

---

### Post by sendas on 2007-08-05
Never Mind. 

I fixed it by the instructions found here [http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback](http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback)

I also had to install gnome-media before I could gstreamer-properties

---

