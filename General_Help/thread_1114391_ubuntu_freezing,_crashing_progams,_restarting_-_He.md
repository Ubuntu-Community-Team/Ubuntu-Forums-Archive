---
title: "ubuntu freezing, crashing progams, restarting - Help!"
date: 2009-04-02
forum: General Help
---

### Post by jensenguy on 2009-04-02
Im having some serious issues with my computer and/or ubuntu and I need some assistance. Ive had 2 previous threads open dealing with just firefox crashing, but now my problems have become more severe.

Ive had many different things happen to me, it started just firefox crashing every now and again, now Ive had other programs start crashing, like amarok, and synaptic manager. One particular time firefox crashed, and ubuntu would not allow me to start any application up, giving me this error:

[I]terminate called after throwing an instance of 'std::bad_alloc'
  what():  std::bad_alloc
Aborted
[/I]

After a restart, all was good again. Then last night I had ubuntu completely crash twice on me. The first time just going to a black screen, and having to restart manually, the second time kicking back to the login screen, but not letting me log in. I managed to pull error details from syslog:

[I]Apr  1 21:31:59 jim-desktop gdm[4814]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr  1 21:31:59 jim-desktop bonobo-activation-server (jim-7688): could not associate with desktop session: Failed to connect to socket /tmp/dbus-eoB16nGFyY: Connection refused

Apr  1 21:50:52 jim-desktop gdm[4808]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Apr  1 21:50:52 jim-desktop kernel: [ 1028.161162] fast-user-switc[5237]: segfault at 0 ip b77daf0b sp 00000000 error 4 in libglib-2.0.so.0.1800.2[b77aa000+b5000][/I]

I am not sure if this is a hardware issue or a major software issue, I am willing to try anything! please help!

---

