---
title: "Sdl?"
date: 2005-02-19
forum: Desktop Environments
---

### Post by brk3 on 2005-02-19
Hi,
Lately when I try to run any game powered by sdl I get this:

  init: sdl
  Unable to initialize SDL (No available video device)

Its really annoying because it means I pretty much cant play any games at the moment. Ive tried asking around on irc but havent got a solution. Can anyone help or has anyone had this problem?

---

### Post by Yukonjack on 2005-02-19
This from the Debian site

The code name for Debian's development distribution is "sid", aliased to "unstable". Most of the development work that is done in Debian, is uploaded to this distribution. This distribution will never get released; instead, packages from it will propagate into testing and then into a real release.

Please note that security updates for "unstable" distribution are not managed by the security team. Hence, "unstable" does not get security updates in a timely manner. For more information please see the Security Team's FAQ.

"sid" is subject to massive changes and in-place library updates. This can result in a very "unstable" system which contains packages that cannot be installed due to missing libraries, dependencies that cannot be fulfilled etc. Use it at your own risk!

---

### Post by Qdlaty on 2005-02-19
A simple question, do you have SDL libraries instaled?
Did you check game/program dependencies in case other SDL packages?

---

### Post by brk3 on 2005-02-19
Yes of course, I definitly have all I need installed. Im talking about games that used to work - any game that uses SDL(even simple pygames give this error) .
Its a standard error handler in the code when initialising sdl, I just dont know why its not working on mine.  I cant think of anything ive changed since it used to work other than installing kdelibs for amarok

Any other suggestions?

---

### Post by kassetra on 2005-02-19
hmmm.  This is usually caused by SDL being unable to open the X display... Try this in another window:
  ```
xhost + localhost
``` 
 
 also, are you using an nvidia or ati graphics card?
 
 If nvidia, do you have glx uncommented and the dri commented in your xfree86 / xorg config files?  
 Do you have the nvidia drivers installed? 
 Does your xfree86/xorg config look similar to this (doesn't have to be the same identifier):
  ```
[font=verdana, arial, helvetica][size=2] Section "**Device**"
     Identifier  "GFFX 5800nu"
     Driver      "nvidia"
     Option      "NvAGP" "3"
     #VideoRam    131072
     # Insert Clocks lines here if appropriate
 EndSection[/size][/font]
```

---

### Post by brk3 on 2005-02-20
I tried that xhost + localhost, it says:

localhost being added to access control list

but it hasnt worked. Also yes, I have an nvidia card with the drivers installed and xfree config file altered so that cant be it..
I notice that 'Load dri' isnt commented out and I remember hearing that its meant to be when the drivers are installed. Should i comment that out?

---

### Post by kassetra on 2005-02-20
yes, you should comment out the load dri.
 
 Let me see what else I can find out by poking my computer...

---

### Post by brk3 on 2005-02-20
Ok Ive done that. Thanks let me know if you find anything

---

### Post by kassetra on 2005-02-20
Let's try a little testing here...
 Have you tried running any of your games with sudo from the command line ...?

---

### Post by brk3 on 2005-02-21
Yup tried that

---

### Post by brk3 on 2005-04-29
This problem has been solved since I upgraded to hoary  :smile:

---

