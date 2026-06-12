---
title: "Nautilus won't start"
date: 2005-06-03
forum: Desktop Environments
---

### Post by dabear on 2005-06-03
I have no idea how it happened, but I cannot start nautilus as my own user anymore.
As root I can start nautilus in a terminal, but as my own user, it just blinks. I can't open folders as my own user anymore , neither the desktop and its icons- it just shows one color.
How to fix this?

---

### Post by ola on 2005-06-03
One thing I have done some thimes when I'm starting to have problems with "GNOME" is removing the gnome dot-files in your home folder.. 

I usualy start with the ".gnome, .gnome2 and eventually .gnome2_private" folders.. NOTE! That your settings will be lost on this action so a backup of the folders you remove could be useful..

It's not pretty, but it might work..

---

### Post by toxidator on 2007-12-22
i'm having the exact same problem and the removal of all the .gnome* dir's in my home dir did not solv the problem.

Other symptms are:
- no wallpaper
- if you press for example the button of your home dir in the locations menu nautilus tells you he is opening it but then he stops and nothing.....

this is an old tread but hopefuly sombody replys.

---

### Post by kathryn on 2008-01-16
I've had the same problem with Nautilus today (ctrl-h to show hidden files would crash it, then Nautilus failed to open at all under my user login).  A more experienced Linux friend of mine hypothesised that the permissions for my Home folder had changed.

Accessing Nautilus as root, i.e. via

gksudo nautilus

allowed Nautilus to function normally, and sure enough the permissions for my Home folder (including my username folder) had changed to root.

We changed the permissions back to my user name and rebooted.  Things seem to be okay at the moment (fingers crossed).  As for the cause, we're baffled.  I can't even remember the last time I used root/super-user access, and I certainly didn't change the permissions!

Hopefully my post will contribute to the diagnosis of this problem. :)




> **toxidator said:**
> i'm having the exact same problem and the removal of all the .gnome* dir's in my home dir did not solv the problem.

Other symptms are:
- no wallpaper
- if you press for example the button of your home dir in the locations menu nautilus tells you he is opening it but then he stops and nothing.....

this is an old tread but hopefuly sombody replys.

---

### Post by kathryn on 2008-01-16
Strike that.  Nautilus is still playing up for me, even though the permissions appear okay.

For the time being I've switched to the Thunar file manager.  I used these instructions to change my default file manager from Nautilus to Thunar:
[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

EDIT: The problem resurfaced again, and the symptoms worsened.  For example, desktop was not refreshing when new content was added (new icons missing), right-click functionality lost [on desktop only], then all icons disappeared from desktop (still in the actual folder).  Desktop background vanished to black, and power/log off button stopped working.  Relied on ctrl-alt-backspace to log out or shut down.
The only reliable 'work around' thus far has been to create a new user account (for safety, non-admin) and work from there until I have time to reinstall Gnome (or Ubuntu altogether).  Talk about a snow-balling problem!


> **kathryn said:**
> I've had the same problem with Nautilus today (ctrl-h to show hidden files would crash it, then Nautilus failed to open at all under my user login).  A more experienced Linux friend of mine hypothesised that the permissions for my Home folder had changed.

Accessing Nautilus as root, i.e. via

gksudo nautilus

allowed Nautilus to function normally, and sure enough the permissions for my Home folder (including my username folder) had changed to root.

We changed the permissions back to my user name and rebooted.  Things seem to be okay at the moment (fingers crossed).  As for the cause, we're baffled.  I can't even remember the last time I used root/super-user access, and I certainly didn't change the permissions!

Hopefully my post will contribute to the diagnosis of this problem. :)

---

### Post by UofLSpeed on 2008-01-16
Similar problem here.  Nautilus seems to be crashing if I try to browse root.  Any other directory works as it should, but as soon as I redirect it to root, it locks and needs to be killed.

Running "sudo nautilus" lets be browse without problem.  I'm assuming that it's a permissions issue.  Which permissions should I look at to determine if there is a problem?

EDIT:  I just tried switching to another non-root user.  There were no problems.  This is very confusing.

EDIT:  Found the problem.  I had setup a directory in root for a remote net boot installation.  The owner was set to nobody and group to nogroup.  I deleted this folder and it fixed the problem.

---

### Post by ofir_k on 2008-01-23
Same problem here.

I opened a bug in here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/185483](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/185483)

Please add your problems there too.

---

### Post by PaganBlasphemy on 2008-02-01
I also find Nautilus won't start.  I'm not sure why.  It seems that rebooting my laptop will allow it to work again, logging out and and back in is hit or miss.  'gksudo nautilus' always works.  None of the suggestions in this thread seemed applicable (permissions were fine, no scripts, and so on).

---

### Post by snanand on 2008-02-01
i had the same problem and the following solution worked for me. nautilus is back working and the desktop looks fine now. solution:
 
   delete .gnome .gnome2 .gnome2_private and .nautilus directories
   logout and login 

a previous suggestion was to delete the .gnome directories. that didn't work. i had to remove the .nautilus one as well.

---

### Post by kathryn on 2008-02-14
I never resolved this issue properly, and still not sure what caused it in the first place.  I did nevertheless fix it entirely by performing a re-install of Ubuntu!  It wasn't too painful because I had an external hard drive to back up my data to.

Don't know if it's worth noting, but I haven't fiddled with compiz at all the second time round, and retained nautilus as the file manager.  No problems as of yet, thank goodness. :)

---

