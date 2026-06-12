---
title: "Firefox Crashed on certain Pages."
date: 2006-09-11
forum: Desktop Environments
---

### Post by Aljn on 2006-09-11
Hey everyone, 
I've recently developed an issue with my firefox browser,
it seems whenever I go to certain sites, it will crash
(the window closes itself) with the following message:

```

alan@alan-desktop:~$ sudo -H  firefox
NP_Initialize
New
open dsp: Device or resource busy
SetWindow
SetWindow
SetWindow
NewStream
WriteReady
Write
decoding...
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 37 error_code 17 request_code 130 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```



I have tested to see if other browsers (Galeon, Mozilla, Opera)
could access the pages [http://mecu.com.au]("http://mecu.com.au") being the worst one (as soon as I click the bookmark, it dies) and it works
fine in those other browsers.

I figured it was a problem with the content, I had a feeling it was flash, 
but I've accessed other pages with flash content ranging from banners to
full blown flash pages, and they didn't crash.

I'm not sure what's wrong, and I'd rather use firefox if I could (I don't
really like the other browsers much).

So, does anyone have any kind of idea what's wrong with my firefox/what the message means, and how to fix it? :confused: 

Thanks in advance ^_^

-Aljn

---

### Post by kerry_s on 2006-09-11
As root got to /etc/X11/xorg.conf and set the default to 24
DefaultDepth	24
ctrl+alt+backspace to restart the x

---

### Post by Aljn on 2006-09-11
> **kerry_s said:**
> As root got to /etc/X11/xorg.conf and set the default to 24
DefaultDepth	24
ctrl+alt+backspace to restart the x

I had a look in my xorg.conf, it's already set to 24 

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "GeForce 7900GT"
    Monitor        "BenQ FP91G+"
    DefaultDepth    24
    Option "MonitorHorizSync" "31-82"
    Option "MonitorVertRefresh" "56-76"
    SubSection     "Display"
    ...

```

What now? o_o

---

### Post by Aljn on 2006-09-11
:-| Bump

---

### Post by kerry_s on 2006-09-11
sorry, had to go to work.

That's weird i had that exact message and googled for hours and that was the fix.

The cause of the crashing is flash not playing nice with xorg. The only thing i can think of is to uninstall flash for now. Or try using the vesa drivers, vesa suck's on my system it has a lagyness so i had flash uninstalled till i found the fix. sorry i can't think of anything else right now.

---

