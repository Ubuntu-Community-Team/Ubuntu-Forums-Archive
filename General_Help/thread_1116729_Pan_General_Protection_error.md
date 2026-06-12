---
title: "Pan General Protection error"
date: 2009-04-05
forum: General Help
---

### Post by etlpkby on 2009-04-05
I keep getting the following when loading a newsgroup with a large amount of posts via Pan:-

> Apr  5 12:01:23 serverwuss kernel: [ 4754.368566] pan[7253]: segfault at 8 ip 000000000048120f sp 00007fff0fb361d0 error 4 in pan[400000+1fb000]

Apr  5 12:23:39 serverwuss kernel: [ 6089.911802] pan[8423] general protection ip:7fd565c807b0 sp:7fff714c4ce8 error:0 in libc-2.8.90.so[7fd565bfe000+169000]

Apr  5 12:24:53 serverwuss kernel: [ 6164.631196] pan[8795] general protection ip:4fea1f sp:7fff765d3b10 error:0 in pan[400000+1fb000]

Apr  5 12:48:50 serverwuss kernel: [ 7601.163567] pan[9271]: segfault at db ip 00007f3abb603498 sp 00007fffc66b3a78 error 4 in libstdc++.so.6.0.10[7f3abb594000+f1000]

Apr  5 12:49:06 serverwuss kernel: [ 7617.226198] pan[9286] general protection ip:7fd538ce47d0 sp:7fff44526608 error:0 in libc-2.8.90.so[7fd538c62000+169000]

I'm running Pan 0.132 on my Ubuntu x64_86 (8.10) (AMD cpu) distro 

> Linux serverwuss 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

Does anyone else get these? I've googled around and there appears to be no posts out there...so I thought I would at least post this in the hope someone is also getting similar and in the hope someone has ideas. Seems to be a memory management issue with either Pan or (worse) kernel libs

---

### Post by imhotep_ on 2009-08-18
sorry for the lateness of this reply...

i get almost the same error (@ downloading, randomly appearing)

> [ 4760.263302] pan[5218] general protection ip:523d1a sp:7fff977990d0 error:0 in pan[400000+1fb000]
[ 7165.183483] pan[6121] general protection ip:523d1a sp:7fff357f8280 error:0 in pan[400000+1fb000]
[ 7373.147746] pan[6523] general protection ip:523d1a sp:7fffc114abd0 error:0 in pan[400000+1fb000]i'll try to build pan and investigate this with valgrind or gdb if i have the time :)

btw, you could try to upgrade to pan 0.133 via svn

update:
edited this

```
gboolean
GIOChannelSocket :: gio_func (GIOChannel   * channel,
                              GIOCondition   cond)
{
  debug ("gio_func: sock " << this << ", channel " << channel << ", cond " << cond);

  set_watch_mode (IGNORE_NOW);

  if (_abort_flag)
  {
    _listener->on_socket_abort (this);
  }
  else if (!(cond & (G_IO_IN | G_IO_OUT)))
  {
    _listener->on_socket_error (this);
  }
  else // G_IO_IN or G_IO_OUT
  {
    const DoResult result = (cond & G_IO_IN) ? do_read () : do_write ();#
    /*     if (_abort_flag)        _listener->on_socket_abort (this);
    else*/ if (result == IO_ERR)   _listener->on_socket_error (this);
    else if (result == IO_READ)  set_watch_mode (READ_NOW);
    else if (result == IO_WRITE) set_watch_mode (WRITE_NOW);
```looks good for now ...

---

### Post by dcstar on 2009-08-19
> **imhotep_ said:**
> sorry for the lateness of this reply...

i get almost the same error (@ downloading, randomly appearing)

i'll try to build pan and investigate this with valgrind or gdb if i have the time :)

btw, you could try to upgrade to pan 0.133 via svn
......

Or simply get it here:

[http://packages.ubuntu.com/karmic/pan](http://packages.ubuntu.com/karmic/pan)

---

### Post by imhotep_ on 2009-08-19
> **dcstar said:**
> Or simply get it here:

[http://packages.ubuntu.com/karmic/pan](http://packages.ubuntu.com/karmic/pan)

thanks for the link. unfortunately even with 0.133 from the svn the error was there,
so the commenting of the line mentioned above seems to help for me :P

---

