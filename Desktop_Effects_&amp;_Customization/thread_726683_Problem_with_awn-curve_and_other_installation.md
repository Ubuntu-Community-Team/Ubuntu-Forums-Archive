---
title: "Problem with awn-curve and other installation"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by zlkoh on 2008-03-16
I have encountered some problems while installing programs like awn or beryl. Btw I am very very new to Ubuntu. First thing first, when installing awn-curve, everything works perfectly until the end part when i was executing this command

sudo gdebi *.deb

I get a dependency error. e.g "The following packages have unmet dependencies:" and there was this line saying something like "libawn-bzr" I have no idea what this is.

Then when i was trying to install beryl, i get the dependency error and was told that i was unable to install that package. 

" emerald: Depends: libwnck18 (>= 2.15.90) but it is not installable"

---

### Post by WFGeppetto on 2008-03-18
ok, I have a very little bit of experience with this. I actually think I may be able to help.

First, go to synaptics, and get that lib file.  Make sure you have enabled the repositories listed in the AWNcurves instructions.  There should be a command that says something like 'gedit blah blah blah' very long code, that will open your list of repositories, and paste the neccessary files into the list.  Or, it will open the list for you to paste the lines into at the bottom.  Read the AWNcurves instructions very carefully, and make sure you didn't miss something.

Then, if you did all that right, and are still having a problem, open synaptics (System-Administration-Synaptic Package Manager).  Click search, and put "libawn" in the search field.  Check mark, and install, and apply all the libawn files that show up, especially libawn-bzr.  If this file does not show up, then you did not enable the proper repositories, and you should recheck the instructions.

The only other problem I know of that you might have, is if you have a 64 bit processor (AMD64), but are running a 32 bit distro of Ubuntu.  You will get errors that say:
"i386 Wrong architecture, package not installable"  

If this is the case, then you need to replace 'sudo gdebi *.deb' with another command.
1st, make sure you are in the AWNcurves folder, then use this command, **only** if it gives you the architecture error:

```
 sudo dpkg -i --force-architecture *.deb
```

Hope that helps.  Again, before you try any of this, recheck the AWNcurves how-to, as I suspect you missed an important line, that enabled the right repositories, or installed the libs(libraryfiles).

---

