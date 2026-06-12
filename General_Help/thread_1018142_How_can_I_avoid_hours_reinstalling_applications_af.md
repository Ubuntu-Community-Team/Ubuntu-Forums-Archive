---
title: "How can I avoid hours reinstalling applications after"
date: 2008-12-21
forum: General Help
---

### Post by 3pinner on 2008-12-21
How can I avoid hours reinstalling applications after I do a clean install of version 8.10?

I am currently running version 7.10, and have dowloaded lots of stuff using Synaptic. I think I can use AptonCD to back those up, but I also have several other applications that run on WINE, and Crossover; plus a couple of others that I paid for (yeah.......I know!!! but I LIKE these applications!). i'm really interested in not having to reinstall Opera, Thunderbird, etc; stuff I use on a daily basis.

My hard disk had 3 partitions, /, /home, and /swap. I am planning on installing in the / partition, and just let it overwrite 7.10. I assume all my stuff in the /home partition will be safe (will back it up using QuickStart anyway)

Any suggestions on re-installing the other applications will be helpful
THANKS!

---

### Post by tuxxy on 2008-12-21
As you have a seperate /home partition all the files in your /home will be safe and your correct fresh install it to / partition this doesnt have to be very large around 6-8 GB.

Once you clean install all your application settings will be safe in /home partition you will just have to reinstall the apps you did have from synaptic, which shouldnt take long and dont forget new versions of your apps are available with Intrepid so you dont want to save the old anyway.  The new apps should be able to read your old settings though so you wont have to do much reconfiguring.  

Any apps you have not available from repos you could just put in your /home and reinstall them once you are on 8.10

---

### Post by mdurham on 2008-12-21
I'm not sure if the following will help, but take a look anyway.
> # Create a text list of an existing installation of all apt-get installed packages
# in order to re-install on a newly installed distro

# make the list
[old distro] sudo dpkg --get-selections >packages

# Now put them back on the new distro
[new distro] sudo dpkg --set-selections <packages

[new distro] sudo apt-get dselect-upgrade

# that's it!

I got this from the forum some time ago.
Cheers, Mike

---

### Post by lovinglinux on 2008-12-21
> **mdurham said:**
> I'm not sure if the following will help, but take a look anyway.

I got this from the forum some time ago.
Cheers, Mike

Yep, this will do the trick to re-install most of your repository applications automatically. It's really a nice feature. 

I guess Wine applications will still be there after installing Wine too, because they are installed in the home partition, under .wine folder.

If you installed applications from deb files, tar balls or something else, then I think you have to install them manually.

---

### Post by IEKnight on 2008-12-21
If you're worried about downloads, almost all the packages you install are cached in /var/cache/apt/archives , so if you back that up and run a recursive installation (*dpkg -i -R <directory>*) or use apt on cd with them, that should save you some downloads. 

A better option would be that many ISPs will have unmetered or local content though, which downloads faster, and isn't included with your standard downloads - all you have to do is find a repo that is included in your isp's local/unmetered content, and that way, you can get the latest versions.

hope that helps

---

