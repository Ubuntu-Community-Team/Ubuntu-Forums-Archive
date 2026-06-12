---
title: "Trying to install AWN (Ubuntu n00b help!)"
date: 2009-03-09
forum: General Help
---

### Post by Grynch108 on 2009-03-09
Hello!

I'm trying to get AWN to run on my Dell Mini 9 netbook. I think I'm almost there, I have AWN and I think I have Compiz installed (I see Advance Desktop Effect Settings under preferences which opens CompizConfig).

When I try and run AWN, I get a dialog box which says "Warning: Screen isn't composited. Please run compiz (-fusion) or another compositing manager".

How do I do this? Please can anyone help me get further?

Cheers!

---

### Post by erebus314 on 2009-03-09
What graphics card are you using? I know this happens with ati (it happened to me). Make sure you have the right driver installed by going to System->Administration->Hardware Drivers.  Also right click on your desktop and go to change desktop background and then visual effects, make sure basic is not selected.

Beware that if you are like me using an ATI graphics card then there is a bug in their driver which for me at least stops me switching user (you can still log out). I don't think there is a fix for this yet as the bug is with ATI.


I've only been using ubuntu myself for a few days so I'm not sure if I can be of much more help. Still I hope this helps...

---

### Post by Grynch108 on 2009-03-10
Thanks for the reply.

I'm using a Dell Mini 9, so I'm guessing it's the Intel integrated graphics chip (I'm not expecting great visual effects, but I've heard it at least works).

If I go to Hardware drivers there is only one device driver called 'wl' (I have no idea what this is) and it's enabled, however, I do not have a visual effects tab under Appearance Preferences. Am I missing something?

Cheers.

---

### Post by Grynch108 on 2009-03-10
I finally got this working. If I open Terminal and type "Compiz", Awn will start running. However, if I reboot, it will not run again until I type "Compiz" in the Terminal again.

I think I'm doing something wrong here? Please can anyone give me advice?

Also, I seem to lose the title bar to all the windows once I've run Compiz. Not sure why this is happening.

I'm not sure either whether this is a decent thing to do on a Netbook. It seems to run ok, but scrolling in web browsers has become slightly jerky.

Thanks in advance.

---

### Post by erebus314 on 2009-03-10
So basically compiz just isn't running? Check if you have simple-ccsm installed, if not install it. Now right click on your desktop on your desktop and go to change desktop background and you should see visual effects. Select normal, extra, or custom (and customize) and that should make compiz run in the background.

---

### Post by Grynch108 on 2009-03-10
Nice one. Thanks for your help.

I'll get the hang of this at some point!

---

### Post by detroit/zero on 2009-03-10
You should also install the Fusion icon```
sudo apt-get install fusion-icon
``` and set it in your system tray. I think it'll load automagically whenever you reboot and it should maintain your settings from the previous session.

---

