---
title: "corrupted /etc/X11 file ....HELP"
date: 2011-07-07
forum: Desktop Environments
---

### Post by MentatGhola on 2011-07-07
For the love of God why didn't I read the top of the read only thread:

 "Hello, MentatGhola You are browsing a READ only archive of the main  support categories pre 4/21/2008. You will not be able to post or reply  any threads in this section.[B] Be aware that some of the information is outdated and may cause problems  to a current installation."  

[/B]Then I might have thought twice about jumping right in and following these instructions:

> 
                                  **Re: Running without GUI**             
                                                                Its Very Simple. Just remove all the entries in 
**/etc/X11/default-display-manager** file

Now, reboot your machine, it automatically  boots without GUI(Without starting X server).
If you want to start the X server, just give 
     Code:
     #gdm 
regards,
zoobave
[http://zoobave.blogspot.com]("http://zoobave.blogspot.com/")

When I saved the hacked file I got a series of error messages (that I should have copied somewhere but I guess I needed to learn that hard way) then on restart I couldn't boot into ubuntu and got hung up on the loading screen that has the orange dot sequence.  So I booted with recovery mode in the grub loader and was able to amend:  /etc/X11/default-display-manager, to include the original contents.  Now I can boot ubuntu and get the login menu but after I enter my password and the log screen drops away the system just hangs indefinately.  I can however log into low graphic mode, as I said.

Please help me so I don't have to re-install.

---

### Post by MentatGhola on 2011-07-07
I ended up reinstalling.

---

