---
title: "rc.local &quot;after upgrade to 9.04&quot; NFS mount help"
date: 2009-05-06
forum: General Help
---

### Post by blueorder on 2009-05-06
Hi y'all...

I recently upgraded to 9.04 from 8.04. I have a server with RAID 1 where I keep all our pictures and videos and such. I have a script that is run in rc.local that first checks to see if the server is there via ping and if the server is there, the script goes ahead and mounts via NFS (this script has worked perfectly fine since 7.04, when I wrote it).

The issue that I am having is that during boot, when rc.local is run, the shares are not mounting. If I run the script after login via sudo, it mounts the shares fine.

The script resides in "/usr/username/bin" and is owned by root.

The command I use in the script to mount is: "mount -v -t nfs server:/mnt/raid1/Video /media/Video"

I use the -v flag because I am logging the script to see what's going on. When looking at the logs when it doesn't mount, the output from the "mount" command is not there. It is there when I run it manually.

/scratches head
//By the way, I know enough scripting/programming to get in trouble ;)

**EDIT:** Just wanted to mention that my "upgrade" was not an upgrade. I clean installed.

---

### Post by blueorder on 2009-05-07
Yep, still searching and not finding much info.

---

### Post by atfrase on 2009-05-14
I'm having the same problem, and it looks like it's caused by rc.local running before networking is initialized.  I added some logging to the mount commands in my rc.local ("mount ... >log 2>&1") and the error it gets is:

  mount error: could not resolve address for srv99: Name or service not known
  No ip address specified and hostname not found

So it looks like the DNS setting (which I configured in NetworkManager) has not yet been applied when rc.local runs, so it can't resolve the name of the server to mount.

---

### Post by blueorder on 2009-05-14
Hmm, interesting. Gonna have to do more testing when I get home. Thanks

---

### Post by blueorder on 2009-05-15
> **atfrase said:**
> the error it gets is:

  mount error: could not resolve address for srv99: Name or service not known
  No ip address specified and hostname not found

So it looks like the DNS setting (which I configured in NetworkManager) has not yet been applied when rc.local runs, so it can't resolve the name of the server to mount.

I changed my script to mount by IP address instead of name and it works now.

---

### Post by atfrase on 2009-05-28
Unfortunately mounting by IP doesn't work for me; the error just changes to "mount error(101): Network is unreachable".  So for me, networking is in fact completely unavailable when rc.local runs.

---

### Post by mk4 on 2009-06-02
What fixed the problem for me was:

sudo apt-get install nfs-common

EDIT: Sorry, my problem didn't involve startup script. A script that I used to run manually, stopped working after new install (hardy to jaunty "upgrade"). Still, Google returned this post with highest ranking, so this comment might help someone.

---

### Post by blueorder on 2009-06-15
Well, had to restart my desktop, after being off for the weekend, and no mounting joy.

Added a "sleep 10" in my script to see if waiting a bit will do anything.

Will report once I reboot.

---

### Post by Saltee on 2009-07-01
Although adding a /bin/mount foo:/bah /bah/foo into the rc.local should work, why not add the mounts directly into the fstab?

So, you could add into your /etc/fstab something like this:

foo:/bah	/data/foobah	nfs defaults 0 0

instead of, $mount foo:/bah /data/foobah

This will mount the volumes as you initially describe.

---

### Post by blueorder on 2009-07-01
> **Saltee said:**
> Although adding a /bin/mount foo:/bah /bah/foo into the rc.local should work, why not add the mounts directly into the fstab?

At first I had it like that but I wanted to check make sure the server was there before mounting. When I had the mount just on fstab and the server was off or unreachable, there was wait for the mount to time out, This way I check if the server is there. If it's there mount; if not, don't mount.

---

### Post by Saltee on 2009-07-01
You have a point there (I think).  Maybe a perl script called from rc.local to do the job ...  Should be easy enough.

(I may try this later, but the weather here in UK Ltd. is too nice at the moment and I have only a few days off work)

---

### Post by greggster on 2009-07-20
I had this error upon install using the package manager installation gui - also had issues at the command line with apt-get install nfs-common

E: nfs-common: subprocess post-installation script returned error exit status 1

E: nfs-common: subprocess post-installation script returned error exit status 1
E: nfs-kernel-server: dependency problems - leaving unconfigured

I have not put more than 20 into figuring this out - its nice but not needed - been using FTP to get files locally I need, but would like to see this working eventually..

---

### Post by Wally Gator on 2009-12-02
Ok... the 'right' way to do this would be to create a script in /etc/init.d which takes as arguments at least the keywords 'start' and 'stop', and possibly 'restart', since it's easy to construct from the other two, and do the ping testing and the mounting there.
Then you should set up symbolic links to this script from all of the /etc/rc?.d/ directories.
Redhat-based distros, such as Fedora or CentOS, have the chkconfig command to simplify the linking of this script to those directories. Since I'm new to Ubuntu, I don't know what would be the 'standard' way to do that in this distro, but anyhow, you should link at least to rc0.d, rc5.d (or rc3.d, if you don't use X11), and rc6.d, with names starting with S?? in rc{35}.d and starting with K?? in rc{06}.d, where the ?? are two numbers, giving the execution order of the scripts in those directories.

For more information on this, see 'man boot', specifically the sections 'Boot Scripts' and 'Sequencing Directories'.

If you think this is too much trouble, you could always say, in rc.local:
at +1min do_the_stuff
where do_the_stuff would be the script you'd like to execute when networking is on. This gives the system 1 minute to start up everything that's needed before you can run your script.

Hope this solves the problem.
[]s.

---

