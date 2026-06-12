---
title: "Unable to cd to '/home/user'"
date: 2013-07-12
forum: Desktop Environments
---

### Post by wind_clouds on 2013-07-12
Hi Everybody,

I have an user in Ubuntu while su - user getting error Unable to cd to '/home/user'

root@fox:~# su - user
Unable to cd to '/home/user'
root@fox:~#

Where Could be the problem please suggest me

---

### Post by 1clue on 2013-07-12
sudo chown user:user /home/user

---

### Post by wind_clouds on 2013-07-12
I have tried already but still the same 

sudo chown user:user /home/user

root@fox:~# su - user
Unable to cd to '/home/user'
root@fox:~#

Is it user profile related issue or any user authentication issue

---

### Post by 1clue on 2013-07-12
ls -al /home /home/user

---

### Post by wind_clouds on 2013-07-12
Hi,

When i execute ls -la under /home

my . directory is root and .. directory was other user that's what, we got this problem.

so now i have executed the below one

# cd /home
# ls -la
drwxr-x--- 22 root   root     4096 Jul 11 03:01 .
drwxr-xr-x 30 test   test     4096 Apr 22 08:07 ..
drwxr-xr-x 30 user   user     4096 Apr 22 08:07 user
drwxr-xr-x 30 test   test     4096 Apr 22 08:07 test

# chown -R root.root ".."

# ls -la
drwxr-x--- 22 root   root     4096 Jul 11 03:01 .
drwxr-xr-x 30 root   root     4096 Apr 22 08:07 ..
drwxr-xr-x 30 user   user     4096 Apr 22 08:07 user
drwxr-xr-x 30 test   test     4096 Apr 22 08:07 test

# cd /
# chown -R root.root usr

After restarted the system the problem has been resolved.

---

### Post by 1clue on 2013-07-12
Um.

There's so much wrong here I don't know if I should even say anything.

Sorry for the rant, but as somebody who has been there and done that -- and been owned for it -- on more than one occasion, take some words of wisdom:

First, the presence of this problem is an extremely good argument toward never having a root shell open.  The fact that Ubuntu goes through all the trouble to eliminate the need to log in as root, ever, moves it from maybe my 6th favorite distro to my favorite.  You were obviously running as root in these examples, and to accidentally change ownership of your /home directory is more proof.

Second thing, you're using two of the easiest to guess account names there are.  The whole point of having security is to prevent people from getting access, and 'test' is about as bad as it can possibly get with that.

This is pure speculation, but I suspect your passwords are the same as your usernames.  Or something equally easy to guess like "secret".

---

### Post by 1clue on 2013-07-12
BTW, your /usr permissions are wrong now.  Easiest thing is to reinstall.

---

### Post by 1clue on 2013-07-12
Actually, go ahead and ls -al / as well, you don't have to tell me but I'm thinking your entire hard drive was owned by test.  So your system is hosed and won't be right again until you reinstall it.

---

### Post by 1clue on 2013-07-12
I'm truly sorry but I just can't let this alone.  This is not a rant at you as much as it's a rant at a younger me, and everyone like us.

There's almost nothing you need to be root for to run Ubuntu, or any other Linux.  System updates, major configuration changes, that's about it.  In fact if you look into the /etc/group file and research some of the groups there, there's no need to be root for updates or config changes either.  It's pure laziness that prompts us to run as root.

There is NO reason to change ownership of a directory or file which was installed by Ubuntu.

There is NO reason to change permissions on a directory or file which was installed by Ubuntu.

If you need to be a privileged user more than once or twice a week on your Linux box, you're doing it wrong.

---

