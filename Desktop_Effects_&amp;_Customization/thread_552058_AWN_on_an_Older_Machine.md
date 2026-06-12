---
title: "AWN on an Older Machine"
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by duhsutter on 2007-09-16
I have installed Avant Window Navigator on my desktop, but it does not run. I read that you need to have compiz or Beryl. My machine is too old for them (I think, 733MHz Pentium Three and 256MB RAM). Any Ideas? (I think I installed xcompmgr, but I have no clue if that worked.) Thanks

---

### Post by SendDerek on 2007-09-16
There was a tutorial featured on Digg.com on how to run AWN without compiz.  The link is here:

[http://www.cypherbios.org/blog/?p=43&language=en](http://www.cypherbios.org/blog/?p=43&language=en)

Hope this helps...

---

### Post by viergeame on 2007-09-16
I have a Pentium III 733MHz and both Beryl and Compiz-Fusion run on my machine.  I have a bit more RAM, but they run beautifully on here even with a good majority of the plugins running.  You could probably run them too as long as you are ok with not having every little bit of the eyecandy going at once.

---

### Post by duhsutter on 2007-09-16
Okay, I followed the install and now have Compiz... but it doesn't do anything. I can't get desktop cube to work, or AWN.  I am at a loss.

---

### Post by viergeame on 2007-09-16
Have you tried opening it in a terminal to see if you get any errors?  If not, try that and post any errors you get.  The first time I installed it I had the same problem as you.  I had the setting manager but nothing happened when I tried to open it.  What I ended up doing was doing a complete uninstall and doing it over again and for some reason it worked perfectly the second time.  Reinstalling seems to have some sort of crazy magic effect on Compiz.

Also, what repository are you using?  I used Amararoth's (hopefully that is spelled right).

---

### Post by duhsutter on 2007-09-16
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

I have a feeling I need Xgl? I think I used amaroth's Repository. Thanks for your help.

---

