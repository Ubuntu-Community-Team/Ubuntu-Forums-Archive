---
title: "&quot;Xlib: Invalid MIT-MAGIC-COOKIE-1 key&quot; on gksu/gksudo"
date: 2006-08-31
forum: Desktop Environments
---

### Post by 3370318 on 2006-08-31
Hello, I'm a new poster running Dapper.  Recently (I have no idea how or why) any app typically requiring root access via gksu/gksudo has failed to launch successfully.  However, simply sudoing works without a hitch.  For example, if I run disks-admin by going through System->Administration->Disks, I will be prompted for my password and, after entering my password, the application will immediately fail to launch.  I've also tried this through the command line as follows (with some debug output):

#I have run this as “gksu -d disks-admin” with the same result
gksudo -d disks-admin

xauth: /tmp/libgksu1.2-n2Oyrf/.Xauthority
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: disks-admin
buffer: -GNOME_SUDO_PASS-
Yeah, we're in...
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

(disks-admin:9244): Gtk-WARNING **: cannot open display:
xauth: /tmp/libgksu1.2-n2Oyrf/.Xauthority
xauth_env: /home/glyle/.Xauthority
dir: /tmp/libgksu1.2-n2Oyrf

As I mentioned, simply running “sudo disks-admin” works without any problem; thus, I'm convinced that my problem resides somewhere with a gksu config file or a bug in gksu (or a library).  Also, just to be clear, disks-admin is just an example...  every app that requires root access fails with gksu.  So far, I have tried reinstalling gksu (not a clean reinstall), removing .Xauthority, and removing/reinstalling scim (as some people with the hoary and I think breezy releases had a similar problem due to scim).

Any help would be much appreciated.
Thanks

---

### Post by mlind on 2006-08-31
MIT-MAGIC-COOKIE(s) are stored in ~/.Xauthority, but you said that removing this file (and restart of Xserver) didn't help. Did you try to remove ~/.ICEauthotity too?

Try to remove */tmp/libgksu1.2-n2Oyrf* directory if it exists.

What's the output of
```

sudo echo $DISPLAY

```

---

### Post by 3370318 on 2006-09-01
Thanks for the quick response.  I just tried removing .ICEauthority (and .Xauthority) along with restarting X but without any success.  Also, there was no directory /tmp/libgksu1.2-n2Oyrf.  Also, the output of "sudo echo $DISPLAY:" is simply ":0.0"

Thanks again for the response.

---

### Post by mlind on 2006-09-01
Everything looks normal to me so far. Try reverting to default gksu gconf keys (settings)

```

gconftool-2 --recursive-unset /apps/gksu

```
then restart Xserver again.

I don't know how gksu works, but there's something weird happenin when it's attempting to find a DISPLAY where to open the window. Authorization part seems to work okay.

---

### Post by 3370318 on 2006-09-01
Unfortunately running ```
gconftool-2 --recursive-unset /apps/gksu
``` along with restarting X didn't work either.

Seriously though, thanks for the help.

---

### Post by mlind on 2006-09-01
Try creating a temporary user with sudoing permissions (user is in admin group) using System > Administration > Users and Groups. Then log in as this new user. 

If same error persists, then the problem is with gksu package, and you should purge it and reinstall back. If there's no errors, then it's something in your $HOME directory that's confusing gksu..

---

### Post by 3370318 on 2006-09-01
The user that I added had the exact same problem.  I therefore completely removed gksu (along with associated packages) and reinstalled everything.  However, the problem still persists.  This is beginning to look more bizarre than I originally imagined.

Thanks for your help

---

### Post by mlind on 2006-09-01
> **3370318 said:**
> The user that I added had the exact same problem.  I therefore completely removed gksu (along with associated packages) and reinstalled everything.  However, the problem still persists.  This is beginning to look more bizarre than I originally imagined.

Thanks for your help

Hmm.. I wonder what is the root cause for all this..

Try purging gksu without removing any other packages, then install it right back
```

sudo dpkg -P --force-depends gksu
sudo aptitude install gksu

```
Any changes?

---

### Post by 3370318 on 2006-09-01
Sorry for the long delay.  I tried what you suggested, but still no changes.

---

### Post by 3370318 on 2006-09-01
Also, I probably should have mentioned this earlier, but when I added a new user, gnome's menus curiously displayed none of the gksu apps as choices.  However, under the menu editor, all of the gksu apps were checked to appear as menu choices.  I don't know if that is significant in any way, but I just figured I'd mention it.

Thanks

---

### Post by mlind on 2006-09-01
> **3370318 said:**
> Also, I probably should have mentioned this earlier, but when I added a new user, gnome's menus curiously displayed none of the gksu apps as choices.  However, under the menu editor, all of the gksu apps were checked to appear as menu choices.  I don't know if that is significant in any way, but I just figured I'd mention it.

Thanks

Did you add this user to **admin** group? Otherwise these menu entries you describe are not visible.
To do this from GNOME: System > Administration > Users and Groups > (select new user) > Properties > User Privileges > tick "Executing system administration tasks" checkbox.

Or from command-line
```

sudo adduser *user* **admin**

```

---

### Post by 3370318 on 2006-09-01
Indeed, I added the user to the admin group.

---

### Post by mlind on 2006-09-02
> **3370318 said:**
> Indeed, I added the user to the admin group.

And? Still same error with another using gksudo?

---

### Post by 3370318 on 2006-09-02
> And? Still same error with another using gksudo?
Yes, the new user still had the same gksudo problems

---

### Post by mlind on 2006-09-02
I'm out of ideas then.. You should probably post a bug against gksu package (and search for similar existing bug report).
[https://launchpad.net/distros/ubuntu/+source/gksu/+bugs](https://launchpad.net/distros/ubuntu/+source/gksu/+bugs)

---

### Post by 3370318 on 2006-09-02
Sure thing, thanks for all the help

---

### Post by Alessandro Allegri on 2006-10-10
I'm getting the same problem. Found any solutions yet?
Thanks!

---

### Post by TomG on 2006-10-29
Just had the same problem. I was even not able to change date and time.
After running a  "xhost +" command it works. I don't know why although...
I will consider to run it automatically on boot from now.
Hope this helps.
TomG

---

### Post by Alessandro Allegri on 2006-11-04
Well, that worked for me too... I wonder what caused this weirdness.

---

### Post by Muiske on 2007-03-22
It seems I have the exact same problem. It's VERY annoying! Even more annoying is the fact that there is no solution as of yet. Changing ownership of authority files doesn't solve the problem, neither does reinstalling gksu.

I have the feeling the solution to this is within reach... but who will make the discovery?

Damnit, I want my menu access back! :(

---

### Post by Muiske on 2007-03-23
Ok, the solution is on top of this page:

[http://www.ubuntuforums.org/showthread.php?t=166863&page=2&highlight=MIT-MAGIC-COOKIE](http://www.ubuntuforums.org/showthread.php?t=166863&page=2&highlight=MIT-MAGIC-COOKIE)

---

### Post by Muiske on 2007-03-27
Er. Correction. It worked for as long as I was logged in. When I restarted the PC again, it was broken again. 

Doesn't anyone have a solution for this? :(

---

