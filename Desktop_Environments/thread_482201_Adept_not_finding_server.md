---
title: "Adept not finding server"
date: 2007-06-23
forum: Desktop Environments
---

### Post by asearle on 2007-06-23
We have installed Kubuntu 6.06 and everything works fine.  However, now we would like to install some other software packages and find that, although Adept opens and requests the admin (sudo) password and displays the installed packages, it seems to be unable to list the uninstalled packages and to supply an option to download/install them.

I have checked the environment and the correct boxes seem to be ticked (e.g. display uninstalled).

Adept displays a whole range of ftp/server sites where software is available but they all seem to be greyed out.

We are using an ADSL connection so our link to the internet is very smooth and fast.

Any tips on this one because, with other installations (of Ubuntu and of Knoppix) the remote software installation options (Adept in this case) always worked without a hitch.

Maybe it is something simple that I have overlooked or an option that I have not set.

Many thanks for any tips that you can give us.

Cheers,
Alan Searle

PS: Adept is requesting the admin password so it is not likely to be permissions, I believe.

---

### Post by raul_ on 2007-06-23
Try opening a terminal and do a 

sudo aptitude update

and see if it fetches all the information.

Also, did you enable extra repositories since you finished the installation from the CD?

---

### Post by asearle on 2007-06-24
Hi Raul,

Thanks very much for the tips.

I tried sudo aptitude update but got ...

# Unable to lock /var/lib/dpkg/lock - open (resource temporarily unavailable)
# Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
... then it rebuilds the packets but at the end says ...
# Couldn't rebuild package cache

Indeed, this seems very similar to what happens when I click 'refresh' in Adept:  It tries but it can't get the package listings.

And regarding your second tip:  How do I enable repositories?

Anyway, maybe this information will help and you can give me a further tip?

Many thanks for the help.

Cheers,
Alan

---

### Post by asearle on 2007-06-24
I have been googling on this and find that others have had the same problem and one guy seems to suggest that synaptic (required for the original Ubuntu installation?) is still active somewhere in the background and therefore blocking adept.

I did a #ps -A  but couldn't see anything that looked suspicious enough to try killing.

I feel that I am moving forward on this problem but I just need to know how to kill/remove/reset whatever is blocking the operation of adept.

Many thanks for any tips that you can give me.

Cheers,
Alan.

---

### Post by asearle on 2007-06-24
Maybe the problem is because the sources in /etc/apt/sources.lst are commented out?

Why is this?

Anyway, I wanted to remove some of the commenting to see if that helped but the file has root privileges and I couldn't edit it.

Under Knoppix I could always do 'open as root' but I'm not sure how this works with sudo.  I tried '#sudo kate' but that didn't work.

Maybe someone can point me towards a HOWTO?

Cheers,
Alan.

---

### Post by raul_ on 2007-06-24
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by asearle on 2007-06-24
Hi Raul, hi everyone,

I solved my problems:   I needed to right-click and enable the repositories.  It was my error but it wasn't so clear in the screen.

I also found that I can right-click on a file and select open as root (with sudo).

Anyway, thanks for your help.

Cheers,
Alan.

---

### Post by asearle on 2007-06-24
I managed to sort out my problems with editing root files and with declaring repositories but somehow it still gives me some problems:

Under adept I can run an update and the system brings me lists of available files/applications from the source that I have activated ...

[http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/)

(two declarations have been activated)

I can also click on 'request install' for the item I want (the entry switches to 'BREAK (install)'.

However, when I click on Apply I am shown that the connection to the server was OK:  done (100%) but I still get the message ...

There was a failure carrying out the changes.   Maybe a problem with downloading some packages or the some packages were damaged.

This has happened with various attempts with different software.

Maybe there is some problem with my installation?  Indeed I googled on apt-get and checked the MAN pages but couldn't find an option 'repair'.  Does this exist?

Anyway, maybe this is a simple problem and someone out there has an idea how I can get these packages installing?

Regards and thanks,
Alan Searle

---

