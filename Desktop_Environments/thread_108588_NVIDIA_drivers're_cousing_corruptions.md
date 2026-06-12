---
title: "NVIDIA drivers're cousing corruptions"
date: 2005-12-26
forum: Desktop Environments
---

### Post by ashrack on 2005-12-26
With NVIDIA drivers I sometimes get the following corruptions.
[IMG]http://www2.arnes.si/~aurank1/nvidia.png[/IMG]
I already tried 2different drivers. One from the repositories and one from NVIDIA itself:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-7676/NVIDIA-Linux-x86-1.0-7676-pkg1.run)

Could this be fixed?

---

### Post by ashrack on 2005-12-27
bump

---

### Post by ashrack on 2005-12-30
any1

---

### Post by Dr. Nick on 2005-12-30
Is firefox the only application it happens in? I had corruption much worse than that and my probelm was my colordepth setting was to high, this want a nvidia card though.

Do you get that corruption using the nv drivers instead of nvidia in your xorg.conf?

---

### Post by ashrack on 2005-12-31
[QUOTE=Dr. Nick]Is firefox the only application it happens in? I had corruption much worse than that and my probelm was my colordepth setting was to high, this want a nvidia card though.

Do you get that corruption using the nv drivers instead of nvidia in your xorg.conf?[/QUOTE]
With "nv" drivers I don't get corruption. 
I believe this corruptions only occur in FF but I am not 100% sure

---

### Post by ashrack on 2006-01-01
bump

---

### Post by dto on 2006-01-01
Just out of curiosity, which nvidia card do you have? I'm having a similar issue. I have kubuntu on three different computers (2 desktop, 1 laptop) that all have different nvidia cards. The only issue I have on any of them is that FF crashes on the laptop. If I run it from a terminal, it always ends with this: 
```
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 120 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```Edit: Oops -- now I see it in your sig.  I really should pay more attention. :)

---

### Post by ashrack on 2006-01-03
But nothing crashes 4 me. I only display the corruption for about a minute and then they dissapear, when I open another window

---

### Post by Dr. Nick on 2006-01-04
Hmm i have started to notice this aswell, though my corruption doesnt happen to the firefox ui but instead the webpages. If i do a real fast scroll or sometimes on page load it gets "streaky"


I dont have the time or knowledge to investigate right now, just wanted to say you are not alone and  I believe it to be a FF problem since its the only application I see it on.

I didnt notice it when i first saw your post since i was on another comp withouth a nvidia card, but now that I am on mine with a nvidia I start so see some anomilies.

---

