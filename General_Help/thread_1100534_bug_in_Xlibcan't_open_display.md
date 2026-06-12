---
title: "bug in Xlib/can't open display"
date: 2009-03-19
forum: General Help
---

### Post by bwm71 on 2009-03-19
Just got the desktop version of 8.04.2 running and within gnome-terminal I'm getting (seems at random times) the following:

$ xterm
No protocol specified
xterm Xt error: Can't open display: :0.0

This seems to come and go with no pattern which makes me think it's a bug.  At least I haven't been able to reproduce it at will.

I didn't immediately find anything in my searches and thought I would check to see if it's a known issue.

Thanks,
Brandon

---

### Post by bwm71 on 2009-03-19
A little more information on this.  If I ssh to another host and send an X application back to my X server over the secure channel, it works.  I just can't launch X applications locally from command line or the tool bar.

Logging out and back in always fixes the problem until what ever it is that triggers it causes it to occur again.

Brandon

---

### Post by schaile on 2009-03-31
Hi all,

"No protocol specified
xterm Xt error: Can't open display: :0"

same happens to me with:
Ubuntu 8.10, X.Org X Server 1.5.2, 

xorg:
Version: 1:7.4~5ubuntu3

kde-nightly-kdebase:
Architecture: amd64
Version: 20090304+svn934897-0neon1

As in previous post:
It happens from time to time (e.g. with xterm but not only)
sometimes it is fixed by itself, logout/login fixes it.

Cheers
Otto

---

### Post by bwm71 on 2009-04-02
I haven't solved the problem, but I've found when the problem occurs, if I do

  ssh myhost xterm

then I can launch X applications locally again.  It's as if ssh'ing back into my host and send X traffic over the secure channel wakes up the X server, so to speak.

Any luck on finding a solution?  If not, I'm thinking of submitting a bug report.

Brandon

---

### Post by bwm71 on 2009-05-12
I believe I have figured out this problem.  It rarely happens and I finally thought to run strace(1) against xterm when it does.  The problem is

  access("/home/brandon/.Xauthority", R_OK) = -1 ESTALE (Stale NFS file handle)

Obviously, my home directory is NFS mounted and accessing it clears up the problem until it happens again.  So, now I need to figure out why I'm getting the stale handle error.

---

### Post by bwm71 on 2009-05-12
Looks like a kernel bug in the NFS support:

  [http://bugzilla.kernel.org/show_bug.cgi?id=12557](http://bugzilla.kernel.org/show_bug.cgi?id=12557)

---

