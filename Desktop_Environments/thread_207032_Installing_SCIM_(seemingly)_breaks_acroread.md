---
title: "Installing SCIM (seemingly) breaks acroread"
date: 2006-07-01
forum: Desktop Environments
---

### Post by mtpadilla on 2006-07-01
Hello...possibly useful info for those using scim for foreign languages and who also like to use acroread. If anyone knows a solution for this, that would be great...

THE PROBLEM
-------------
I just did a fresh install of Ubuntu 6.06 and noticed that when I followed the instructions in the following page

[https://help.ubuntu.com/community/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6.06_Dapper_Drake](https://help.ubuntu.com/community/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6.06_Dapper_Drake)

that this caused acroread 7.0 to no longer load. I know that it is scim that caused acroread to fail since I carefully monitored each step of my installation, trying acroread after each thing that I did (I knew there was a problem with acroread from previous installations and wanted to find the source). In order to be able to use Japanese, I did the following (as outlined in the link above):

0) I enabled Japanese language support via System->admin->Language Support and clicking on Japanese. I then rebooted the system.
1) Upon the completion of the reboot, I typed in the terminal
"locale | grep LANG="
and the result was "LANG=en_US.UTF-8"
2) I then typed in the terminal "im-switch -z en_US -s scim".
3) Then if I tried to run acroead, nothing happens (I see that the diskdrive is doing something, but I never even see an acroread entry in the system monitor. Reinstalling acroread doesn't help.

I'm using kpdf now, but there is less functionality than acroread...

---

### Post by leeyee on 2006-07-01
Okay, you are there! If I recall, you might not run RealPlayer any more either, eh? Here is the solution, just add this line into your acroread script "/usr/bin/acroread" and "/usr/bin/realplay"
```

export GTK_IM_MODULE=xim

```
Note that you should place this after the "#!/bin/sh".

---

### Post by mtpadilla on 2006-07-02
[QUOTE=leeyee]Okay, you are there! If I recall, you might not run RealPlayer any more either, eh? Here is the solution, just add this line into your acroread script "/usr/bin/acroread" and "/usr/bin/realplay"
```

export GTK_IM_MODULE=xim

```
Note that you should place this after the "#!/bin/sh".[/QUOTE]


Leeyee...nice work! :p  Indeed, my realplayer was broken also, although I hadn't realized it. I tried the fix you mentioned and both work now....thank you very much!!!

Incidentally, would you happen to understand what the deal is here? It would be cool to understand why SCIM breaks these and what the fix you suggested does to correct it....

Thanks again!!

---

