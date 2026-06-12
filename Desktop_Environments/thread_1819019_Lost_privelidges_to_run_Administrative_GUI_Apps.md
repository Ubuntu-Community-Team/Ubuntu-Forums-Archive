---
title: "Lost privelidges to run Administrative GUI Apps"
date: 2011-08-05
forum: Desktop Environments
---

### Post by johansson on 2011-08-05
Hey All,

Not too long ago I upgraded to 10.10 and after doing so, many of my Administrative GUI apps wouldn't work properly.  For example, I can open the Update Manager, it will display all of the available updates but when I click "Install", the button "clicks" but nothing happens.  The same behavior is displayed when trying to use the GUI to add a new user.  I click the "Add" button but nothing happens.  Similarly, if I try to change my graphics driver to the old version (not that I would necessarily want to) it tells me I don't have permission to do so.  And Lastly, if I try to enable Visual Effects I get an error message saying that my graphics card does not support them. 

All of this worked just fine in 10.04.  And I'm not sure where something went wrong.  

I realized I can use gksudo for any of these applications and they work fine, however this is not really a solution for me because any time I log off, or restart, I would need to re-execute the commands to enable compiz and all that, and honestly, that's not how I want my box to work.

I thought maybe I had lost admin privileges, but I checked and I am in the "admin" group.  

I thought maybe somehow root took ownership of some of my configuration settings in my /home/<user> so I: 

```
<user>@<user>-desktop:~$ ls -lar .*/* | grep root
-rw-r--r--  1 root    root        12288 2011-03-15 20:32 .rpmdb/Providename
-rw-r--r--  1 root    root        12288 2011-03-15 20:32 .rpmdb/Packages
-rw-r--r--  1 root    root        12288 2011-03-15 20:32 .rpmdb/Name
-rw-r--r--  1 root    root        12288 2011-03-15 20:32 .rpmdb/Basenames
-rwxr-xr-x 1 <user> root      179552 2010-06-02 17:48 nppdf.so
drwxr-xr-x  2 root    root         4096 2011-08-04 19:47 .rpmdb
drwxr-xr-x  3 root    root         4096 2009-08-26 23:27 ..
-rwxrwxrwx  1 root    root         394 2010-06-02 17:48 AdobeReader.desktop
```I don't know who should own that .rpmdb directory, so I rebuilt it (sudo rpmdb --rebuild).  No effect.

So now I'm stuck.  I have limited understanding of how the persmissions for the GUI apps work (clearly).    I hope I was clear enough, I would appreciate any ideas, or even just resources I could check out, because googling and searching this forum haven't landed me any solutions yet

Thanks much!

---

### Post by johansson on 2011-08-09
Messing around last night I realized a few things.  Not sure how helpful they are, but running the users-admin application I realized none of the buttons work except for "Properties" to add groups to the user.  Also the "Help" button brought up the help window.  

I noticed a similar behavior with Synaptic Software Manager, in that I couldn't use the buttons to remove software but clicking "help" brought up the help menu.  

This coupled with the fact that when I gksduo certain applications, they work fine, makes me think that the app itself thinks it's doing what I tell it but is being denied permissions.  Does anybody know where the logs are for applications like this?  I wonder if errors are being recorded but not displayed to the screen.   I did a little looking but haven't found anything yet.  

I also realized that alt + F2: gksudo users-admin brings up the application but then it stays greyed out and with the "processing" mouse icon.  

Thinking about resetting Gnome to the default but not sure if that would only cause more headaches.  At this point any input would be really helpful.  Thanks much

---

