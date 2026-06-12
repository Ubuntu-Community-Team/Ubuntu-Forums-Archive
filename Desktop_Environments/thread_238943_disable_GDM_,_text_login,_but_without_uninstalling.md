---
title: "disable GDM , text login, but without uninstalling X"
date: 2006-08-18
forum: Desktop Environments
---

### Post by xenon2000 on 2006-08-18
I tied this:

Changed to runlevel 3

Removed the sym link from the relevant /etc/rcX.d to gdm. ie for init 3 (made back version of course)

rm -f /etc/rc3.d/S13gdm

... and while it did give me a text login prompt after reboot like I wanted. When I logged in as my normal user and then did

startx

it started my XFce4 desktop and everything looked right. But when I try to do anything that needs the password, it says

[B]Failed to run Services-Admin
Unable to copy the user's Xauthorization file.[/B]

And doesn't work. So I went back to runlevel 2 for now. But I still want to disable gdm and have a text login without uninstalling X. Otherwise I would have just installed the Server install CD. Any ideas?

---

### Post by bensexson on 2006-08-18
startx is not being run with root permissions.  try sudo startx.

---

### Post by xenon2000 on 2006-08-18
> **bensexson said:**
> startx is not being run with root permissions.  try sudo startx.

Isn't startx normally not run with root permissions? Are you saying that when I login as my normal user via GDM, that X is being started with root permissions? That makes no sense.

And already ahead of you. I had alread tried sudo startx and also just logging in as root (account enabled). Both result in the same thing. I get root's X session. Which has completely different sessions settings than my normal user account. So that is not the solution. Also, if you sudo startx or use the root account, it never asks for the password for admin functions since it already had it from sudo startx. This is less secure and is the whole reason you log in as a normal user in the first place.

So, I still need help with a solution. In other distros I would just use runlevel 1, but that causing Ubuntu to freeze at the text boot up section when loading all the services. Gets to network setup and freezes. So I stopped trying runlevel 1.

I have a hard time believing I am the first person to want a text login while still having normal access to my X session.

---

### Post by ifishfortorque on 2006-08-18
```

cd /etc/init.d/
sudo update-rc.d -f gdm remove
```

This is what I always use.  Then just type

```
startx
```

whenever; no root permissions needed.

---

### Post by xenon2000 on 2006-08-18
> **ifishfortorque said:**
> ```

cd /etc/init.d/
sudo update-rc.d -f gdm remove
```

This is what I always use.  Then just type

```
startx
```

whenever; no root permissions needed.

Tried your steps and that accomplishes the exact same thing as the steps I did in my original post. Startx works, but then if I go to NETWORKING where it would normally ask for a password, it gives the error I stated above.

Sorry that I forgot to post my details. I am using Xubuntu 6.06 with XFce and Gnome desktop is not installed. So if those methods work in Gnome Ubuntu, they don't in Xubuntu. There is an .Xauthority problem in Xubuntu using the steps listed so far for disabling GDM and still keeping X.

---

### Post by xenon2000 on 2006-08-19
I solved the Xauthority issue and now have a text boot up and login. And can start X with my regular user X session AND all the Xauthority features work.

Though I tried a lot of things, so hopefully the details I give are all that are needed to complete the above steps.

ls /home/yourfolder/.X* -l

to see if it's root:root , if it is like it was for me, then:

sudo chown you:you /home/yourfolder/.Xauthority

ls /home/yourfolder/.ICE* -l

mine was already owned by my user, but if not:

sudo chown you:you /home/yourfolder/.ICEauthority

Now, I didn't test at this point, so maybe it was fixed at this point. I then used

sudo mc

to open both those files for editing. Didn't make any changes and exited. mc is Midnight Commander and I often use mcedit from the command line and within mc. It's not default in Ubuntu or Xbuntu or the normal repositories. It's in the universal repositories and I highly recommend it for commandline and SSH file browsing and file editing.

Anyways, now

startx

works and it asks for the password when accessing secure items. If I find anything that doesn't work as I expect it, I will post again. But looks like I now have exactly what I want. Thanks everyone.

---

