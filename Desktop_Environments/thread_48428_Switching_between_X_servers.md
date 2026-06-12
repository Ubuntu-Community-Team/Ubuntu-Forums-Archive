---
title: "Switching between X servers?"
date: 2005-07-12
forum: Desktop Environments
---

### Post by Dogmeat on 2005-07-12
I'm trying to start another server in the same machine. I edited .Xauthority and stuff and I can run apps there, etc.

The plan is to use that X server with a vnc client so I can have two full screen desktops on one computer and easily switch between them. 

Now thats where my problem is. I don't know how to switch between the X servers! I read somewhere it was Ctrl+Alt+F7/F8 or just Ctrl+F7/F8 but neither of these work, if I want to switch I have to kill it, so please let me know what could be wrong? I start the X server like this:

```
sudo X :1.0  & xterm -display :1.0 &
```

And after I kill it I get this output (I dont know if it's related but just in case...):

```
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 root@terranova.warthogs.hbd.com)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux OMEGA 2.6.10-5-686 #1 Fri Jun 24 17:33:34 UTC 2005 i686
Build Date: 05 April 2005
        Before reporting problems, check http://wiki.X.Org
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-686 (buildd@vernadsky) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Fri Jun 24 17:33:34 UTC 2005 T
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.0.log", Time: Tue Jul 12 13:02:11 2005
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Error:            No Symbols named "abnt2" in the include file "pc/us_intl"
>                   Exiting
>                   Abandoning symbols file "default"
Errors from xkbcomp are not fatal to the X server
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
xterm:  fatal IO error 32 (Pipe quebrado) or KillClient on X server ":1.0"
```

Thanks in advance!

---

### Post by Dogmeat on 2005-07-12
Well it turns out I had to comment out a few lines of my keyboard n xorg.conf, now it works with ctrl+alt+f7/f8, I can switch to my other consoles but now when I come back  to the new x server all I get is a black screen  ](*,) 

I discovered you cant use X shortcuts in full screen apps so that kind of defeats the ideas I had in mind (changing between full screen apps on the fly)

I guess I'll just keep using a single X server. :neutral:

---

### Post by Dogmeat on 2005-08-04
Sorry to reply to this old post, but I had to finish it. Today I fixed my newbie problem, thing is, my :1 x server went to the F2 display (i have removed all but one virtual consoles). Now everything works great, I can run full screen apps on several X servers!

New solutions bring in new questions, so I wonder if someone can give me a hint on these:

1 - How do I select the virtual console I want :1 to go to?
2 - How do I change :0 from the default F7 VC?

---

