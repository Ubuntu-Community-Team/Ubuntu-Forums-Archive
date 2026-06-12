---
title: "kiba-dock crashing!"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by s_spiff on 2007-12-06
I've installed kiba-dock via svn, with no erros. But everytime I start kiba-dock, it works fine for a while. And all of a sudden it crashes. So I checked out what output is the terminal showing :
```

spiff@spiffed:~$ kiba-dock
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension
The program 'kiba-dock' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 29172 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

Anyone, any idea, whats going wrong here?

---

### Post by Fireblend on 2007-12-06
I seriously would recommend switching to AWN. Kiba-dock isn't that well supported and tends to crash pretty often, when I started using Linux I used kiba-dock for a while, but after days of looking for support and trying to fix it, I decided to try AWN, which in my opinion is a far more organized project, and works pretty well.

---

### Post by s_spiff on 2007-12-06
I did use AWN. Infact have it on right now. But AWN doesn't have the option of only launchers..I don't want a taskbar int he dock, which AWN has no matter what. Plus, AWN docks only at the bottom, and I want it on either the left or right edge of the screen. But thanks anyways.

---

