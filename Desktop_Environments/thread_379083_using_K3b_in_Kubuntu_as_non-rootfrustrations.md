---
title: "using K3b in Kubuntu as non-root/frustrations"
date: 2007-03-08
forum: Desktop Environments
---

### Post by CareySchug on 2007-03-08
Note: my background is Unix servers, I am at home in command line and mostly use vi as my editor.  I am ignorant in desktops, when we did have gui desktops on Unix serves, we did very little other than create terminsl sessions to access OTHER unix servers.

I first used Ubuntu and loved it.  I messed up by mixing apt-get, dpkg, and gui, so decided to try starting over with kubuntu on a specialized machine, I liked some stuff, especially the system monitor, so when my primary machine had a hard disk crash, I installed Kubuntu there also.  I am getting very frustrated, both with things that seem to not work right (and did work in Ubuntu), and it being much harder to find solutions.  When I wanted to revert to firefox, the gui said I could make that my default brouser, but that did not work, and I had to find an ugly command line option to do that (and I don't like konquerer for web browsing, though it is the best file manage I have  yet tried in Kubuntu).

The manual says just bring up K3b.  It doesn't work, no access to cd writer drive (unless you are root).  OK, searching for KDE found something that made sense, change permissions on /dev/hdb.  Great, I could burn a CD, but that gets reset when you reboot, and lets everybody write (which is actually OK for me, but not good in general).  I didn't try changing its group, that would probably get reset also.

I found another set of instructions, which I *MAY* be able to figure out the details on, but this seems awfully ugly, and I know somebody with only a background in windows would have not clue on (see below).  I think before I did this, I would set up commands in rc.local to change the file permissions (actually, since learning about rc.local for another issue, I just took a break from writing this to go do that).  Still it would be nice to have some more obvious way to make K3b useable. 

Actuallly, on a whim, I looked for the "camcontrol" used in the procedure below.  Nothing found by either "which" or "apt-cache search", so I guess I couldn't do following procedure anyway.  Nothing found by "find / -name camcontro*" either.

quote:
3. k3b has to be started from a root console, which is not recommended.
   Alternatively do the following:
3a. set the suid flag on cdrecord and cdrdao. The 'Notes' the chapter of
    'man cdrecord' discusses this.
3b. - install sudo (security/sudo) and add the following line or similar to
      sudoers (usually in /usr/local/etc/sudoers):
      ALL             ALL = NOPASSWD: /sbin/camcontrol devlist
    - or execute 'camcontrol devlist' For every user who should be able to use 
      k3b. Resolve all errors e.g by giving him/her access rights to /dev/xpt0.
      'camcontrol devlist' must run without error for all these users!
      Note that giving access rights to /dev/xpt* might be a security leak!
    - or give camcontrol the suid flag, which is a security leak as well.
3c. - For every user who should be able to use k3b and for every CD or DVD
      device add a directory in the users home directory. These directories
      must be owned by the corresponding user. For each such directory add a
      line in /ect/fstab (see remark 2), like:
        /dev/cd0c  /usr/home/XXX/cdrom  cd9660  ro,noauto,nodev,nosuid  0  0
      Furthermore allow user mounts as described in topic 9.22 of the FAQ:
      [http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/disks.html#USER-FLOPPYMOUNT](http://www.freebsd.org/doc/en_US.ISO8859-1/books/faq/disks.html#USER-FLOPPYMOUNT)
    - or just give mount and umount the sudo flag, which is a security leak.
3d. - Every user who should be able to use k3b must have read and write access
      to all pass through devices connected with CD and DVD drives. Run
      'camcontrol devlist' to identify those devices (seek string 'passX' at
      the end of each line and modify the rights of /dev/passX). Note, that
      this is a security leak as well but that there is no alternative!

---

