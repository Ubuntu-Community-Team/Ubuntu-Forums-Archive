---
title: "Ubuntu shell doesn't fully load; compiz config corrupted?"
date: 2011-10-14
forum: Desktop Environments
---

### Post by jlebar on 2011-10-14
I just upgraded to 11.10 from 11.04.

I opened the compiz config app and clicked "preferences".  Before I could even do anything, my shell crashed.

Now when I try to log in using the Ubuntu shell, it doesn't fully load.  I get my desktop icons and a file menu at the top of the screen, which appears to be for nautilus.  But that's it.

I can log in with Ubuntu 2D without issue.

It appears that some configuration file may have been corrupted.  When I load the compiz config program from the Ubuntu 2D shell, click on "preferences", and click the "Profile" drop-down-list, I see two entries: "Default", and garbage characters.  When I remove the profile with the garbage name, another one comes to take its place.

How can I fix this or get more information on how the Ubuntu shell is failing?

---

### Post by mjmeyer@ on 2011-10-14
Sorry no fix but same thing happened to me. Go into preference and it crashes. Ended up starting from scratch and reloading 11.10. Definately its the preferences from compiz that crashes it because tried it again and crashed again. Starting from reload of 11.10 again. Not clicking on preferences again. Desktop just ends up blank.

---

### Post by thewaffler100 on 2011-10-14
This happened to me a couple times today. First off, make sure you are using Unity 2D at the moment. go to the Ubuntu Software Center and search and install the Compiz Settings Manager. When it finally installs, open it, and check the "Enable Ubuntu Unity Plugin" to enable it. It will tell you that there are some conflicts. No biggie, just click to allow to fix these conflicts. You will see a series of dialog boxes. Click the first option (usually the one with an orange border) on any dialog box you see. After all the dialog boxes are gone, either log out or restart your computer. Then try to login using the normal session (Unity 3D) Hope this works. :P

---

### Post by g30rg3 on 2011-10-15
Same problem here. Compiz crashed and then the Dash disappeared. Now I can't do anything!

---

### Post by jlebar on 2011-10-15
> **thewaffler100 said:**
> This happened to me a couple times today. First off, make sure you are using Unity 2D at the moment. (snip) Then try to login using the normal session (Unity 3D) Hope this works. :P

The Unity plugin was disabled, but unfortunately these steps didn't work for me.

---

### Post by jlebar on 2011-10-15
I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875400](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875400)

---

### Post by veroslav on 2011-10-17
I would like to confirm that I also experienced the exactly the same bug yesterday. I've tried unity --reset and other reset commands, but nothing helped.

I've confirmed the bug report you created.

---

### Post by kaliban on 2011-10-17
I had the same problem numerous times, found a solution for repairing Unity on the net.

Leave the corrupted unity session (ctrl+alt+suppr)
Enter a new session of either recovery console, or Gnome Classic 

You have to delete the following folders in your home folder :
.compiz
.config/.compiz-1
.gconf/apps/compizconfig-1
.gconf/apps/compiz-1

Unity will be fully restored next time you open a session with it.
It also works for the Gnome shell (seems the compiz corruption damages both Unity and Gnome shell).

---

### Post by areeda on 2011-10-17
I've had this happen multiple times.  It seems that compiz config is my problem.  Whenever I set even the most innocuous things I loose the launcher bar, dash and the top menu bar.  Only the background displays.

Sometimes Ctl-Alt-Del works to get the logout prompt other times not.

What has worked at least 3 times is:

[LIST]
[*]Ctl-Alt-F2 to get to a text login prompt
[*]Log in
[*]unity --reset
[*]sudo shutdown -r now
[/LIST]
This gets Unity 3D running with default configuration, which I guess I'm stuck with until this is fixed.

Joe

Edit:
I added a comment to the bug filed by Jlebar [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875400](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/875400)
I also filed a full apport bug report and marked it as a duplicate so my configuration could be compared.  To do this type:
ubuntu-bug compiz
and follow the prompts.

One thing I saw is that we both have nVidia display cards and are using the proprietary drivers.  If that is a common thread it may help developers find the problem.

---

### Post by wildjiji on 2011-10-17
[QUOTE=jlebar]When I load the compiz config program from the Ubuntu 2D shell, click on  "preferences", and click the "Profile" drop-down-list, I see two  entries: "Default", and garbage characters.  When I remove the profile  with the garbage name, another one comes to take its place.[/QUOTE]
This part is a bug in compizconfig-python.  
[https://bugs.launchpad.net/ubuntu/+source/compizconfig-python/+bug/874799](https://bugs.launchpad.net/ubuntu/+source/compizconfig-python/+bug/874799)

---

### Post by jlebar on 2011-10-22
> **kaliban said:**
> You have to delete the following folders in your home folder :
.compiz
.config/.compiz-1
.gconf/apps/compizconfig-1
.gconf/apps/compiz-1


This works for me.  Thanks!

---

