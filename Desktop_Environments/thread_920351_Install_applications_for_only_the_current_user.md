---
title: "Install applications for only the current user"
date: 2008-09-15
forum: Desktop Environments
---

### Post by Moezzie on 2008-09-15
Im trying to learn a little about how to administer a linux box with a couple of different users. One of the first things i ran into was installation of software only for the user running the install.

I could not find any options to specify the user on eather apt-get nor dpkg.
Is there an easy way to give a user privileges to install software which does not affect the other users on the system?

Thanks for you help!

---

### Post by skullmunky on 2008-09-16
AFAIK the answer is unfortunately, no, there isn't a way to do that built into Apt.  It is certainly possible to install software only for yourself, not system-wide, but I don't think you can in through apt.  

I think the reason is that a software package is frequently a pretty complicated bunch of files, spread throughout the system.  it wouldn't be uncommon to have one "application" put files in /usr/bin, /etc/, /usr/share, /usr/lib, and perhaps a few other places too.  this is different from Windows, where everything's mostly in the application folder plus some DLL's that get put in the system folder, secret registry black magic, and some other stuff; or OSX, where mostly everything goes into the "Application" which is actually a gigantic fat directory that just looks like a single file in the Finder through a mind-boggling bit of legerdemain.

So you could install a binary within your own home directory, but all the rest of the stuff - libraries, configs, docs, all of that - is still supposed to go into the system-wide directories.

There are ways around this, too, but the problem is that the whole system starts to get messier and harder to maintain.  Instability and security holes start to creep in.  Package dependency is already tricky in linux, so letting users have divergent and conflicting installs of packages could get really really messy.  So i think that Debian just decided to make the package management system clean, fast, and stable.

You can install things to your home directory when you compile from source.  Also some apps are distributed using their own installer method, but not most in the Ubuntu repositories.

I think this also goes way back in unix admin philosophy...

---

### Post by Moezzie on 2008-09-16
Thanks scullmonkey. You really seem to know a lot about this.

The thing is, im trying to set up a small network of one host and a bonch of thin clients, kind of like in schools or workplaces. The clients are connected whith Nomachine(remote desktop software) though ssh.

I thought there could be some easy way to handle which application a user/group has access to. I know this can be done with permissions and ownership, but would'nt i have to set the permissions for every single group on every single application? That would be alot of work.

I really don't like to draw parallels with Windows here, but there seems to be a bunch of software for customizing users/groups access to applications/startmenu items/file and folder access. Doesn't something like this exist for any debianbased systems?

Cheers

---

