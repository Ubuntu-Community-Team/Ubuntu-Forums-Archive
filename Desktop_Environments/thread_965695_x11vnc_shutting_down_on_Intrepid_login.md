---
title: "x11vnc shutting down on Intrepid login"
date: 2008-10-31
forum: Desktop Environments
---

### Post by Underpants on 2008-10-31
Running Intrepid Ibex
Installed x11vnc package
This process has worked on pretty much all previous Ubuntu versions.

This line goes into /etc/gdm/Init/Default
```

/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg

```

This option is set in /etc/gdm/gdm.conf
```

KillInitClients=false

```


With all previous versions of Ubuntu this works perfectly. I can connect to GDM and stay connected after a login to the desktop. Very easy "set it and forget it" configuration.

After a clean install of Intrepid Ibex 8.10 I can connect to the login screen, but get disconnected after entering the password and then GDM restarts and brings the computer right back to a login screen!

After the machine gets logged in I can open the console and manually run this command
```

/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg

```
and x11vnc starts up on port 5900 and I can reconnect with VNC viewer. 


Anyone have some ideas about what's changed with Intrepid that makes this quit working?

---

### Post by Underpants on 2008-10-31
I've also added ```
KillInitClients=false
``` to the gdm.conf-custom file. 

This is even worse. GDM restarts itself after entering the password. Brings ya right back to the login prompt.

So I comment out the KillInitClients line in both gdm.conf and gdm.conf-custom which brings me to some interesting results.

*I boot the computer. 
*I connect with SSH and try to connect VNC. 
*VNC connects. I type the username and password through the VNC session, and GDM blows up and restarts like you've pressed CTRL+ALT+BACKSPACE

If I boot the computer, connect SSH and VNC; ***and then type my username and password at the physical computer VNC will stay connected to the desktop and act normal.***

---

### Post by krunge on 2008-11-01
> **Underpants said:**
> 
*I boot the computer. 
*I connect with SSH and try to connect VNC. 
*VNC connects. I type the username and password through the VNC session, and GDM blows up and restarts like you've pressed CTRL+ALT+BACKSPACE


Do any messages appear in the various logs (syslog, messages, gdm, Xorg, etc, etc.)?

BTW, you put the 'KillInitClients=false' in the [daemon] section, right?

---

### Post by Underpants on 2008-11-01
It is in the daemon section, yes. 

I'll have to check the logs on Monday or Tuesday. The laptop I use (Thinkpad x60) is getting a new LCD and it's in 50 pieces on my workbench right now. :)

---

### Post by krunge on 2008-11-02
> **Underpants said:**
> 
I'll have to check the logs on Monday or Tuesday. The laptop I use (Thinkpad x60) is getting a new LCD and it's in 50 pieces on my workbench right now. :)
This person seems to have the same problem:

[http://ubuntuforums.org/showthread.php?t=968044&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=968044&highlight=x11vnc)

---

### Post by MisterB on 2008-11-04
I am seeing the same behavior.  To troubleshoot, I reinstalled Intrepid (AMD64) with the default configuration.  I then installed X11Vnc and making to the edits to /etc/gdm/gdm.conf, /etc/gdm/gdm.conf-custom, and /etc/gdm/Init/Default.  After I submit my password, GDM restarts, VNC is killed, and I find myself back on the login screen.

It looks like this is an out-of-the box issue w/ Intrepid, and I'm surprised there are only a couple of reports of this.  So, I figured I'd better chime in as another affected user.

Is anyone able to get this working on Intrepid?  Maybe it's only a 64-bit issue.

---

### Post by beowulfshaeffer on 2008-11-04
I am indeed seeing the same problem. I'll go post a link here from my other thread.

---

### Post by Underpants on 2008-11-04
> **MisterB said:**
> Maybe it's only a 64-bit issue.

Mine is happening on more than one 32bit machine. :/

Anyone have thoughts? Anyone? Anyone? :confused:

---

### Post by krunge on 2008-11-04
> **Underpants said:**
> 
Anyone have thoughts? Anyone? Anyone? :confused:

How did the search for clues in the messages, syslog, Xorg, gdm, etc, etc, log files go?

Please verify the following for me:  with a clean install of intrepid and **NO** edits to gdm.conf and gdm.conf-custom, does the Xserver/GDM still crash after you login to the X session using x11vnc?

I want to take the gdm.conf edits out of the picture if they play no role.

---

### Post by Underpants on 2008-11-04
> **krunge said:**
> How did the search for clues in the messages, syslog, Xorg, gdm, etc, etc, log files go?

Please verify the following for me:  with a clean install of intrepid and **NO** edits to gdm.conf and gdm.conf-custom, does the Xserver/GDM still crash after you login to the X session using x11vnc?

I want to take the gdm.conf edits out of the picture if they play no role.

My laptop will normal install is still out of order. I built an Intrepid system in vmware a few minutes ago. Clean install, installed only openssh-server and x11vnc.

* I power on the system and it comes to the GDM logon screen.
* Connect with SSH and open tunnel
* I run (/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg)

And I cannot connect to GDM. I logon to the vmware machine via GDM and then rerun the command. I can connect, but when I 'logoff' x11vnc dies.


I don't see "x11vnc" anywhere in the syslog, xorg log, or gdm log.

---

### Post by krunge on 2008-11-05
> **Underpants said:**
> 
* I run (/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg)

And I cannot connect to GDM. I logon to the vmware machine via GDM and then rerun the command. I can connect, but when I 'logoff' x11vnc dies.

You will need to run x11vnc as root and also supply the mit-magic-cookie file via -auth option.

I.e. maybe '-auth /var/lib/gdm/:0.Xauth', but I am not sure of the exact location on your distro, use 'ps wwwwwaux | grep auth' to find it.

Also add '-display :0'

So try something like that and see what gdm (or X server) does.
> 
I don't see "x11vnc" anywhere in the syslog, xorg log, or gdm log.
There won't be any.  We're looking for messages from gdm why it is exiting/crashing.

---

### Post by MisterB on 2008-11-07
I tried adding the auth and display options without success.  However, I did find this error in the syslog:

gdm[8748]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

Not sure where else I can look to get more information about this error.

---

### Post by krunge on 2008-11-08
> **MisterB said:**
> I did find this error in the syslog:

gdm[8748]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

Not sure where else I can look to get more information about this error.

I have a test machine in my basement with ubuntu on it and I upgraded it to 8.10.  I was able to reproduce this problem.

It is the X server itself that is crashing.  From /var/log/Xorg.0 (actually Xorg.0.old):

```

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f89400]
2: /usr/X11R6/bin/X [0x8158279]
3: /usr/X11R6/bin/X(CallCallbacks+0x4e) [0x80909ae]
4: /usr/X11R6/bin/X(XaceHook+0x7e) [0x815702e]
5: /usr/X11R6/bin/X(ProcXFixesGetCursorImageAndName+0x8b) [0x8147e9b]
6: /usr/X11R6/bin/X [0x814639c]
7: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
8: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b93685]
10: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

```

Please verify that all of you get the same X server crash.

It is pretty serious that a simple X application like x11vnc can make the X server (running as root) have a segmentation violation and crash. Potentially a security issue as well.

Note by the 'ProcXFixesGetCursorImageAndName' above, x11vnc was trying to retrieve the mouse cursor shape and image at the time.

So a workaround is to apply the '-noxfixes' option to the x11vnc command line.

Please verify that -noxfixes avoids the crash for all of you.

If you don't like the few fixed mouse cursors under -noxfixes, you will have to log in twice via the VNC viewer, e.g.:

1) Put KillInitClients=true   (not false) in gdm.conf-custom
2) Put the x11vnc start line in **BOTH** /etc/gdm/Init/Default and /etc/gdm/PreSession/Default
3) Restart everything

This way when you connect via VNC and login at the GDM greeter x11vnc will be disconnected after you log in.  Then the x11vnc in PreSession/Default will be running and you connect to it with your VNC viewer a 2nd time.  Then you will have all the xfixes mouse cursors.

---

### Post by bearda on 2008-11-08
I experienced the same problem trying to set up a headless Via Artigo system.  I've even got the exact same backtrack in my X server logs.  On the plus side, the -noxfixes switch seems bypass the problem completely with x11vnc executing out of xinetd (no changing the gdm startup script).

Thanks!

---

### Post by krunge on 2008-11-09
> **bearda said:**
> I experienced the same problem trying to set up a headless Via Artigo system.  I've even got the exact same backtrack in my X server logs.  On the plus side, the -noxfixes switch seems bypass the problem completely with x11vnc executing out of xinetd (no changing the gdm startup script).

I reported the problem to Xorg: [http://bugs.freedesktop.org/show_bug.cgi?id=18451](http://bugs.freedesktop.org/show_bug.cgi?id=18451)


BTW, if a person is willing to build x11vnc version 0.9.6 from the upstream source tarball, it has an option "-reopen" that works around this problem fairly well.

When using x11vnc's "-reopen" one does **not** specify KillInitClients=false to GDM, you either leave GDM in its default configuration or set to "true".

Then, when you login with GDM through x11vnc, GDM tries to kill x11vnc, but instead x11vnc just waits a few seconds and then tries to reopen the X display.  It seems to work around this problem pretty well, and gives the full cursor shape (no need for -noxfixes).

Going forward, "-reopen" will probably become the preferred way to work around GDM's KillInitClients behavior.

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen)

---

### Post by MisterB on 2008-11-11
I can confirm that the -noxfixes option is working as described.  I have to connect twice, but the login persists.

I haven't tried the -reopen option yet, but may try later this week.

Thanks!

---

### Post by krunge on 2008-11-11
> **MisterB said:**
> I can confirm that the -noxfixes option is working as described.  I have to connect twice, but the login persists.

Thanks.

BTW for x11vnc -noxfixes when using GDM with KillInitClients=false properly configured (gdm.conf-custom, or where ever) you should only need to connect *once*. Check if that works.

---

### Post by GenPFault on 2008-11-12
> **MisterB said:**
> I can confirm that the -noxfixes option is working as described.  I have to connect twice, but the login persists.

I haven't tried the -reopen option yet, but may try later this week.

Thanks!
-reopen seems to work (stock gdm.conf) with a self-compiled 0.9.6.  [checkinstall](http://asic-linux.com.mx/~izto/checkinstall/) is your friend!

---

### Post by hatmancan on 2008-11-12
i am asking the following question?i tried to install kubuntu 8.10 to my hard drive..i waited for almost 5 hrs to download and when it did i now cannot log into my system..
i was reading this thread and thought maybe i have the same problem.
to give you some idea of my problems here they are.
dave@dave-desktop;~fglrxinfo
display: :0.0 screen:0
Opengl vendor string:S3 Graphic Inc
Opengl renderer string:Mesa dri pro savageDDR 20061110 AGP1x x86/MMX/SSE2
Opengl version string:1.2 Mesa 7.0.3-RC2
Segmentation Fault
dave@dave-desktop~$

i then ran sudo dpkg-reconfigure -phigh xserver-xorg
error message
xserver-xorg postinst warning:overwriting possibly-customised configuration file;backup in /etc/x11/xorg.conf.20081108214244

so i ran sudo dpkg --configure-a
after that i have a list of errors as well if you need.

i have to switch from windows and this drive to get some answers..
i do have a ubuntu cd as well
2 hard drives one with ubuntu and one with windows
ps..i have also tried many other things to no avail
one being where i get to a screen with options to repair 4 different items,but neither will work

could someone please help me with this post

---

### Post by krunge on 2008-11-12
> **hatmancan said:**
> i am asking the following question?i tried to install kubuntu 8.10 to my hard drive... i now cannot log into my system..
i was reading this thread and thought maybe i have the same problem.

From what you have said, I don't think it is the same problem.  You might want to start a separate thread.

---

### Post by MisterB on 2008-11-14
I set the KillInitClients back to false and all is well.  I no longer get kicked out.  Losing the custom mouse cursor with -noxfixes is no big deal to me.  Thanks again for the help!

---

### Post by Underpants on 2008-12-05
> **krunge said:**
> I reported the problem to Xorg: [http://bugs.freedesktop.org/show_bug.cgi?id=18451](http://bugs.freedesktop.org/show_bug.cgi?id=18451)


BTW, if a person is willing to build x11vnc version 0.9.6 from the upstream source tarball, it has an option "-reopen" that works around this problem fairly well.

When using x11vnc's "-reopen" one does **not** specify KillInitClients=false to GDM, you either leave GDM in its default configuration or set to "true".

Then, when you login with GDM through x11vnc, GDM tries to kill x11vnc, but instead x11vnc just waits a few seconds and then tries to reopen the X display.  It seems to work around this problem pretty well, and gives the full cursor shape (no need for -noxfixes).

Going forward, "-reopen" will probably become the preferred way to work around GDM's KillInitClients behavior.

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen)

Hey Karl, thanks for all of your help on this one! I got things working using the -noxfixes option. 

I've got one small annoyance and I don't know if it's related or not. The cursor in the VNC viewer window shows as a big X instead of the cursor... is that because of something in x11vnc?

---

### Post by krunge on 2008-12-05
> **Underpants said:**
> Hey Karl, thanks for all of your help on this one! I got things working using the -noxfixes option. 

I've got one small annoyance and I don't know if it's related or not. The cursor in the VNC viewer window shows as a big X instead of the cursor... is that because of something in x11vnc?

Yes, it is precisely because you turned off xfixes:

[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-cursor](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-cursor)

---

### Post by Underpants on 2008-12-05
Excellent! 

This has been a pretty productive thread. I'm going to construct a nice howto for headless systems and folks that just want control of the console session.

If you are a Bourbon drinker, send me an address and I'll make sure you get a nice little bottle of something good from Kentucky for the holidays.

x11vnc is giftware, right? ):P

---

### Post by Skip Da Shu on 2009-01-05
> **krunge said:**
> Thanks.

BTW for x11vnc -noxfixes when using GDM with KillInitClients=false properly configured (gdm.conf-custom, or where ever) you should only need to connect *once*. Check if that works.

It does. Thanx much.

No SSH, just VNC... added only "-noxfixes" 

On the local client I get the big ugly "**[SIZE="4"]X[/SIZE]**" cursor and don't see the remote server's pretty little red arrow but that's nit picking.  

Lines at end of /etc/gdm/Init/Default:

```
#
# Setup x11vnc for remote resumable session within LAN - SRG 12/2007
#
/usr/bin/x11vnc -forever -nolookup -bg -sb 11 -noxfixes -usepw -rfbauth /home/skip/.vnc/passwd -rfbport 5923 -allow 192.168.218. -o /var/log/xvnclog -auth /var/lib/gdm/:0.Xauth

exit 0
```

Entry in /etc/gdm/gdm.conf-custom (no changes to gdm.conf):

```
[daemon]
#
# Added KillInitClients=false - SRG
#
KillInitClients=false
```

---

### Post by Underpants on 2009-01-05
add "-cursor normal" to the end of your line and you'll get a regular looking black arrow. I think that's the correct option, seek the help doc on Karl's site, but I think that's correct.

---

### Post by Skip Da Shu on 2009-01-05
> **Underpants said:**
> Excellent! 

This has been a pretty productive thread. I'm going to construct a nice howto for headless systems and folks that just want control of the console session.

If you are a Bourbon drinker, send me an address and I'll make sure you get a nice little bottle of something good from Kentucky for the holidays.

x11vnc is giftware, right? ):P

There's a how-to for x11vnc grafted into this how-to on setting up headless machines on Xubnutu to run BOINC [**HERE**]("http://www.skipsjunk.net/how-to/xubuntu04.html") or [**HERE**]("http://dcteam.guru-mountain.com/howto/xubuntu04.html").

At this moment it doesn't contain this fix but it will shortly.

---

### Post by Skip Da Shu on 2009-01-05
> **Underpants said:**
> add "-cursor normal" to the end of your line and you'll get a regular looking black arrow. I think that's the correct option, seek the help doc on Karl's site, but I think that's correct.

That didn't work for me... but you got me to look at Karl's doc and what did work was "-cursor arrow" w/ the "-noxfixes" parm.  I also added "-cursor n". 

I didn't see, but may have missed, what the arrow pointer options give you.  I tried -arrow 2|3|4|5|6 all of which worked for me.  Here's what the options give:

1 = stubby black arrow, default w/o this command
2 = stubby white arrow
3 = thin tailed black arrow
4 = thin tailed white arrow
5 = smaller head, longer tail, thin black arrow
6 = smaller head, longer tail, thin white arrow

I liked the 5 & 6 options but 3 was easier for my old eyes to spot so I went back to that.

So on the v8.10 headless number cruncher the end of my /etc/gdm/Init/Default now looks like:

```
#
# Setup x11vnc for remote resumable session within LAN - SRG 12/2007
#
/usr/bin/x11vnc -forever -nolookup -bg -sb 11 -noxfixes -cursor arrow -arrow 3 -usepw -rfbauth /home/skip/.vnc/passwd -rfbport 5923 -allow 192.168.218. -o /var/log/xvnclog -auth /var/lib/gdm/:0.Xauth 
 
```

---

### Post by Underpants on 2009-01-05
Sorry, this is the line I use in /etc/gdm/Init/Default

```
/usr/bin/x11vnc -localhost -o /var/log/x11vnc.log -forever -bg -noxfixes -ultrafilexfer -cursor arrow
```

---

### Post by excbuntu on 2009-02-20
i thought i'd contribute to make things clear to fix this problem. you need to add the "-nofixes" option to fix the crash and the "-auth /var/lib/gdm/:0.Xauth" option to view the login screen. also, find out if your GDM uses /etc/gdm/gdm.conf or /etc/gdm/gdm.conf-custom (the emptier one is the unused one!) and edit the used one to include "KillInitClients=false" under the [daemon] section.

the command i use is this:

```
sudo x11vnc -WhateverOptionsYouWant -noxfixes -auth /var/lib/gdm/:0.Xauth -display :0 
```

with KillInitClients=true in my /etc/gdm/gdm.conf file. i only need to start x11vnc once. i don't care about the "X" cursor.

thanks guys.

---

### Post by Skip Da Shu on 2009-02-20
> **excbuntu said:**
> i thought i'd contribute to make things clear to fix this problem. you need to add the "-nofixes" option to fix the crash and the "-auth /var/lib/gdm/:0.Xauth" option to view the login screen. also, find out if your GDM uses /etc/gdm/gdm.conf or /etc/gdm/gdm.conf-custom (the emptier one is the unused one!) and edit the used one to include "KillInitClients=false" under the [daemon] section.

the command i use is this:

```
sudo x11vnc -WhateverOptionsYouWant -noxfixes -auth /var/lib/gdm/:0.Xauth -display :0 
```

with KillInitClients=true in my /etc/gdm/gdm.conf file. i only need to start x11vnc once. i don't care about the "X" cursor.

thanks guys.

Actually... I THINK... They are both used.  The gdm.conf-custom is supposed to contain additions and overrides to the gdm.conf file and is the one that should probably be updated.  I believe this will avoid any possible re-configs of gdm.conf by dpkg wiping out your settings also.

Cursor arrow options posted earlier.

---

### Post by Wiley99 on 2009-04-08
> **krunge said:**
> I have a test machine in my basement with ubuntu on it and I upgraded it to 8.10.  I was able to reproduce this problem.

It is the X server itself that is crashing.  From /var/log/Xorg.0 (actually Xorg.0.old):

```

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f89400]
2: /usr/X11R6/bin/X [0x8158279]
3: /usr/X11R6/bin/X(CallCallbacks+0x4e) [0x80909ae]
4: /usr/X11R6/bin/X(XaceHook+0x7e) [0x815702e]
5: /usr/X11R6/bin/X(ProcXFixesGetCursorImageAndName+0x8b) [0x8147e9b]
6: /usr/X11R6/bin/X [0x814639c]
7: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
8: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b93685]
10: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

```

Please verify that all of you get the same X server crash.

It is pretty serious that a simple X application like x11vnc can make the X server (running as root) have a segmentation violation and crash. Potentially a security issue as well.

Note by the 'ProcXFixesGetCursorImageAndName' above, x11vnc was trying to retrieve the mouse cursor shape and image at the time.

So a workaround is to apply the '-noxfixes' option to the x11vnc command line.

Please verify that -noxfixes avoids the crash for all of you.



This works for me on Intrepid! Thanks for the workaround.

---

### Post by michalre on 2009-07-25
> **krunge said:**
> I have a test machine in my basement with ubuntu on it and I upgraded it to 8.10.  I was able to reproduce this problem.

It is the X server itself that is crashing.  From /var/log/Xorg.0 (actually Xorg.0.old):

```

:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f89400]
2: /usr/X11R6/bin/X [0x8158279]
3: /usr/X11R6/bin/X(CallCallbacks+0x4e) [0x80909ae]
4: /usr/X11R6/bin/X(XaceHook+0x7e) [0x815702e]
5: /usr/X11R6/bin/X(+0x8b) [0x8147e9b]
6: /usr/X11R6/bin/X [0x814639c]
7: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
8: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b93685]
10: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

```

Please verify that all of you get the same X server crash.

It is pretty serious that a simple X application like x11vnc can make the X server (running as root) have a segmentation violation and crash. Potentially a security issue as well.

Note by the 'ProcXFixesGetCursorImageAndName' above, x11vnc was trying to retrieve the mouse cursor shape and image at the time.

So a workaround is to apply the '-noxfixes' option to the x11vnc command line.

Please verify that -noxfixes avoids the crash for all of you.

If you don't like the few fixed mouse cursors under -noxfixes, you will have to log in twice via the VNC viewer, e.g.:

1) Put KillInitClients=true   (not false) in gdm.conf-custom
2) Put the x11vnc start line in **BOTH** /etc/gdm/Init/Default and /etc/gdm/PreSession/Default
3) Restart everything

This way when you connect via VNC and login at the GDM greeter x11vnc will be disconnected after you log in.  Then the x11vnc in PreSession/Default will be running and you connect to it with your VNC viewer a 2nd time.  Then you will have all the xfixes mouse cursors.

To make things little more complicated ;-) :

I have the same problem but there is no sign of the crash in Xorg.0, Xorg.0.old nor the whole /var/log

But -noxfixes option works!

I am on jaunty with:

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux mic 2.6.28-14-generic #46-Ubuntu SMP Wed Jul 8 07:21:34 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)

starting x11vnc from /etc/gdm/Init/Default as:

/usr/bin/x11vnc -v -clear_keys -repeat -rfbauth /etc/x11vnc.pass -v -o /var/log/x11vnc.log -noxdamage -forever -bg -rfbport 5900 -ncache 12

In x11vnc.log is:

caught XIO error:
25/07/2009 20:36:33 deleted 40 tile_row polling images.

The whole x11vnc.log is in the attachment.

---

### Post by krunge on 2009-07-25
> **michalre said:**
> To make things little more complicated ;-) :

I have the same problem but there is no sign of the crash in Xorg.0, Xorg.0.old nor the whole /var/log

Can you use ps(1) to see if the X server process (either named "X" or "Xorg") restarts when you see the problem?  Or are you saying the X server does a clean shutdown and exit (and is then restarted by gdm) when you connect via x11vnc?

---

### Post by michalre on 2009-07-26
> **krunge said:**
> Can you use ps(1) to see if the X server process (either named "X" or "Xorg") restarts when you see the problem?  Or are you saying the X server does a clean shutdown and exit (and is then restarted by gdm) when you connect via x11vnc?

No crash or restart of the X, PID does not change at all.

---

### Post by michalre on 2009-07-26
> **michalre said:**
> No crash or restart of the X, PID does not change at all.

I have also noticed that unlike the #1 poster in this thread I will stay logged in and can connect to the session if I manually start the x11vnc after it has crashed. So no repeating login screen for me.

---

### Post by krunge on 2009-07-26
> **michalre said:**
> No crash or restart of the X, PID does not change at all.

Are you sure you have:
```
KillInitClients=false
```
in the [daemon] section the various "gdm.conf", "gdm.conf-custom" files?  (And you have verified that it makes an effect.)

Note that it should be set to "false".  The suggestion to use "true" above was a workaround (-reopen) for the ProcXFixesGetCursorImageAndName X server crash.

More info on GDM setup for x11vnc connections here (see the section labeled 'Continously'):
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

---

### Post by michalre on 2009-07-26
> **krunge said:**
> Are you sure you have:
```
KillInitClients=false
```
in the [daemon] section the various "gdm.conf", "gdm.conf-custom" files?  (And you have verified that it makes an effect.)

Note that it should be set to "false".  The suggestion to use "true" above was a workaround (-reopen) for the ProcXFixesGetCursorImageAndName X server crash.

More info on GDM setup for x11vnc connections here (see the section labeled 'Continously'):
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

You are right when I add 
KillInitClients=false
to the gdm.conf-custom
login screen keeps repeating itself and my X server is crashing with the message:
```

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x3b) [0x813518b]
1: /usr/X11R6/bin/X(xf86SigHandler+0x55) [0x80c7be5]
2: [0xb7fe0400]
3: /usr/X11R6/bin/X [0x8161a55]
4: /usr/X11R6/bin/X(CallCallbacks+0x4e) [0x80916be]
5: /usr/X11R6/bin/X(XaceHook+0x7e) [0x815ff5e]
6: /usr/X11R6/bin/X(ProcXFixesGetCursorImageAndName+0x8b) [0x814cb3b]
7: /usr/X11R6/bin/X [0x814af7c]
8: /usr/X11R6/bin/X(Dispatch+0x33f) [0x808d57f]
9: /usr/X11R6/bin/X(main+0x3bd) [0x80722ed]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7ba7775]
11: /usr/X11R6/bin/X [0x80717a1]
Saw signal 11.  Server aborting.

```

So I guess I have exactly the same problem as described in this thread.

Thanks for your assistance.

---

### Post by krunge on 2009-07-26
> **michalre said:**
> So I guess I have exactly the same problem as described in this thread.

That's too bad.

Wouldn't it be nice if they fixed this X server bug... going on one year this fall.  I guess it is a low priority bug. Hmm, it's not clear that freedesktop/Xorg even acknowledge this bug, what is your take?  Is it a dup of another bug?

---

### Post by michalre on 2009-07-27
> **krunge said:**
> That's too bad.

Wouldn't it be nice if they fixed this X server bug... going on one year this fall.  I guess it is a low priority bug. Hmm, it's not clear that freedesktop/Xorg even acknowledge this bug, what is your take?  Is it a dup of another bug?

Can't find any similar bug for xorg but there is a bug in ubuntu
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/217892](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/217892)

I have updated it with the upstream bug. Maybe this will help to at least get some attention for the upstream bug.

---

### Post by backlinks on 2009-07-27
This is such an awesome forum, thanks for your help everyone!

---

### Post by krunge on 2009-10-21
An update:  I found a way to have x11vnc avoid the xfixes crash and also to avoid the need for KillInitClients=false (and still not be killed):

[INDENT][http://ubuntuforums.org/showthread.php?p=8138368#post8138368](http://ubuntuforums.org/showthread.php?p=8138368#post8138368)[/INDENT]

So it should all work nicely w/o having to add KillInitClients=false to gdm.conf or "-noxfixes" to x11vnc cmdline.

It is in the dev tarball:
[INDENT][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz)[/INDENT]
If anyone tests that it works in their environment to avoid the problems I would appreciate it. Thanks.

More info:

[INDENT][http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-reopen)[/INDENT]

From: [http://www.karlrunge.com/x11vnc/#beta-test](http://www.karlrunge.com/x11vnc/#beta-test) 
> 
Heuristics are applied to try to determine if the X display is currently in a Display Manager Greeter Login panel (e.g. GDM) If so, x11vnc's creation of any windows and use of XFIXES are delayed. This is to try to avoid x11vnc being killed after the user logs in if the GDM KillInitClients=true is in effect. So one does not need to set KillInitClients=false. Note that in recent GDM the KillInitClients option has been removed. Also delayed is the use of the XFIXES cursor fetching functionality; this avoids an Xorg bug that causes Xorg to crash right after the user logs in.


---

### Post by Skip Da Shu on 2009-10-21
> **krunge said:**
> 
If anyone tests that it works in their environment to avoid the problems I would appreciate it. Thanks.
]

Will test this weekend on a couple different machines (Xubuntu, Ubuntu, Dotsch/UX).

---

### Post by krunge on 2009-10-21
> **Skip Da Shu said:**
> Will test this weekend on a couple different machines (Xubuntu, Ubuntu, Dotsch/UX).

Thanks a bunch.  Any of them 9.10 by any chance?  That will be the acid test because GDM KillInitClients is evidently removed in that release.  I don't have a box with 9.10 on it here..

---

### Post by Skip Da Shu on 2009-10-25
> **krunge said:**
> Thanks a bunch.  Any of them 9.10 by any chance?  That will be the acid test because GDM KillInitClients is evidently removed in that release.  I don't have a box with 9.10 on it here..

Sorry, I didn't look at what the link was to before saying I would test it.  I was thinking it was an executable or better a .deb as opposed to source. My apologies for raising my hand too quick.

---

### Post by krunge on 2009-10-26
> **Skip Da Shu said:**
> Sorry, I didn't look at what the link was to before saying I would test it.  I was thinking it was an executable or better a .deb as opposed to source. My apologies for raising my hand too quick.
What!?  Skip, please say it not so that you cannot do source... or I will never be able to look at SkipsJunk the same way again ;-)

It is true that it is very sad that the distro maintainers make it very difficult for one to build from source (why they don't install the -dev packages by default boggles my mind...)  In any event, this binary should probably work on debian:

[INDENT][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_i686-Linux](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_i686-Linux)[/INDENT]

---

### Post by Skip Da Shu on 2009-10-26
> **krunge said:**
> What!?  Skip, please say it not so that you cannot do source... or I will never be able to look at SkipsJunk the same way again ;-)

It is true that it is very sad that the distro maintainers make it very difficult for one to build from source (why they don't install the -dev packages by default boggles my mind...)  In any event, this binary should probably work on debian:

[INDENT][http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_i686-Linux](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9_TEST_i686-Linux)[/INDENT]

It's mostly so... I'm an old mainframe assembler programmer.  I know it's not that hard but I just haven't spent the time yet to figure it out.

Will this executable run off of the ia32 libs in my 64b install?

---

### Post by krunge on 2009-10-26
> **Skip Da Shu said:**
> 
Will this executable run off of the ia32 libs in my 64b install?
Yes, it should.  Run ldd on it to see if all of the libs are present.  Let me know if there are any problems, thanks.

---

### Post by tixetsal on 2009-11-01
Krunge,

In amd 64 Karmic, I am suffering from the same inability to login to Gnome, due to the now-ineffective nature of KillInitClients=false, which I use on all of my </= 9.04 machines.  

I can't seem to get the source from your tarball to compile on Karmic either, even after trying to install the Debian dependencies listed on your site.  I assume that this is due to the new version of gdm.  (If an assembly programmer can't compile the code, I fear that I am in trouble.)  Do you have any suggestions as to how to determine what libs, etc are needed to compile?  I tried pointing to /lib64 .

ERROR BELOW:

==========================================================================
*** A working X window system build environment is required to build *** x11vnc.  Make sure any required X development packages are installed.
If they are installed in non-standard locations, one can use the
--x-includes=DIR and --x-libraries=DIR configure options or set the
CPPFLAGS and LDFLAGS environment variables to indicate where the X
window system header files and libraries may be found.  On 64+32 bit machines you may need to point to lib64 or lib32 directories to pick up the correct word size.

If you want to build x11vnc without X support (e.g. for -rawfb use only or for native Mac OS X), specify the --without-x configure option.
==========================================================================


I also tried the link for the binary, but when I run ldd on it, it echoes "not a dynamic executable."  I'm confused on that front as well.

I realize that the root problem is an issue with gdm, not x11vnc.  Any suggestions that you might have (or if anyone else has figured out another workaround) are appreciated.

*EDIT

I realized that the -noxfixes switch still keeps gdm from crashing, even in Karmic.  So i throw that switch on, login, gdm kills x11vnc, and then I fire it up again without the noxfixes, which gives me a nice-looking mouse pointer.  If anyone has a better workaround, I am open to suggestion.

Thanks for the great s/w, Krunge!

---

### Post by krunge on 2009-11-01
> **tixetsal said:**
> 
In amd 64 Karmic, I am suffering from the same inability to login to Gnome, due to the now-ineffective nature of KillInitClients=false, which I use on all of my </= 9.04 machines.  

I can't seem to get the source from your tarball to compile on Karmic either, even after trying to install the Debian dependencies listed on your site.

Your build problem looks normal; I don't think it is related to 9.10.

I honestly can't believe how difficult debian/ubuntu and most all other Linux distros make it to build a simple package like x11vnc.  This stuff was **so** easy 10-15 years ago, and now it is **so** difficult... maybe I am the only one who does not view this as "progress"?

Anyway, a few weeks ago I had the displeasure of building x11vnc on a vanilla installed ubuntu 9.04 machine.  Looking at my apt-get cache directory, it looks like these packages were installed to build x11vnc:
```

      libxau-dev
      x11proto-core-dev
      libjpeg62-dev
      libpthread-stubs0-dev
      libx11-dev
      libxcb1-dev
      libxdmcp-dev
      x11proto-input-dev
      x11proto-kb-dev
      x11proto-xext-dev
      xtrans-dev
      libxext-dev
      libxi-dev
      libxtst-dev
      x11proto-record-dev
      x11proto-fixes-dev
      libxfixes-dev
      x11proto-damage-dev
      x11proto-xinerama-dev
      libxdamage-dev
      libxinerama-dev
      libxrandr-dev
      libxrender-dev
      x11proto-randr-dev
      x11proto-render-dev

```
(boy, the above really reminds me of: 'A foolish consistency is the hobgoblin of little minds')

I think there might be more in that list than are needed. But if you apt-get every one of those it should work. I am sure there are dependencies among those packages so it is really a smaller number I apt-get'd but I don't have my shell history available.

One thing I don't see on that list is libz, i.e. zlib1g-dev (maybe it was already on the system) so you might need that too.

If that doesn't work please report back here with the error messages.

---

### Post by krunge on 2009-11-01
> **tixetsal said:**
> 
I also tried the link for the binary, but when I run ldd on it, it echoes "not a dynamic executable."  I'm confused on that front as well.

I think you need to install the 32bit runtime on your amd64 machine (that's another pet peeve of mine, but I've already over-ranted in this thread.)

---

### Post by Skip Da Shu on 2009-11-01
> **krunge said:**
> Yes, it should.  Run ldd on it to see if all of the libs are present.  Let me know if there are any problems, thanks.

So far no luck with it moved to /usr/bin/x11vnc, chown'd to root: and chmod'd to a+x.  Will look at the changes I made in Default and gdm.conf-custom to see if I boogered one of those up.

---

### Post by Skip Da Shu on 2009-11-01
> **Skip Da Shu said:**
> So far no luck with it moved to /usr/bin/x11vnc, chown'd to root: and chmod'd to a+x.  Will look at the changes I made in Default and gdm.conf-custom to see if I boogered one of those up.

Using "Remote Desktop Viewer" from my v9.04 desktop it works like a champ... once you take out the extraneous "3" in the command line at the bottom of Default.  

Server (remote client) was an Ubuntu v9.04 64b with the following Default entries (old commented out, new below it):

```
#
# Setup x11vnc for remote resumable session within LAN - SRG 12/2007
#
#/usr/bin/x11vnc -forever -nolookup -bg -sb 11 -noxfixes -cursor arrow -arrow 3 -usepw -rfbauth /home/skip/.vnc/passwd -rfbport 5924 -allow 192.168.218. -o /var/log/xvnclog -auth /var/lib/gdm/:0.Xauth 

/usr/bin/x11vnc -forever -nolookup -bg -sb 11 -usepw -rfbauth /home/skip/.vnc/passwd -rfbport 5924 -allow 192.168.218. -o /var/log/xvnclog -auth /var/lib/gdm/:0.Xauth
```
Also commented out the following in /etc/gdm/gdm.conf-custom:
```
[daemon]
#
# Set KillInitClients = false for X11vnc access to login screen - SRG
#
#KillInitClients=false
```

The only other boxes I have with any variation right now are an Xubuntu v8.04 system that doesn't have the -noxfixes but it does have the "killinitclients" in it's gdm.conf-custom (where overrides to gdm.conf are really supposed to go).  Any value in trying it there?

And then I've got a Dotsch/UX server (a Ubuntu v8.10 derivative) that I never got around to installing it on.  Wouldn't kill me to install x11vnc on it but it'd pretty much be a test of Ubuntu v8.10.  Any value?  

I had v9.10 on an old Sempron box but I sold it Saturday.  This week I'll be refurbishing some old P4 Dell machines and I can install v9.10 32b on one of those and try it there.

---

### Post by krunge on 2009-11-03
I posted an update to the ubuntu 9.10 GDM killing x11vnc in post #5 here:
[INDENT][http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)[/INDENT]
it seems to work fine now.

---

### Post by Skip Da Shu on 2009-11-03
> **krunge said:**
> I posted an update to the ubuntu 9.10 GDM killing x11vnc in post #5 here:
[INDENT][http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)[/INDENT]
it seems to work fine now.  I can do a little 'regression' testing on 8.04 / 9.04 if ya wanna shoot me a binary.

---

### Post by krunge on 2009-11-03
> **Skip Da Shu said:**
> I can do a little 'regression' testing on 8.04 / 9.04 if ya wanna shoot me a binary.
Thanks for helping out with testing.

I cut some new binaries with the latest x11vnc-0.9.9 dev tarball and uploaded them:
[INDENT][http://www.karlrunge.com/x11vnc/bins/](http://www.karlrunge.com/x11vnc/bins/)[/INDENT]
I also bit the bullet and created an amd64 one (x11vnc-0.9.9_TEST_amd64-Linux) that I have lazily avoided doing all this time. I'd appreciated knowing if that works for anyone.

So anyway, I claim the binaries at the above link should avoid the GDM KillInitClients **completely** (no need to specify it in gdm.conf) on all releases of debian and ubuntu (i.e. x.y to 9.10).

I also claim it will automatically work around this Xorg server crash bug:
[INDENT][http://bugs.freedesktop.org/show_bug.cgi?id=18451](http://bugs.freedesktop.org/show_bug.cgi?id=18451)[/INDENT]
(which is the original topic of this thread in case anyone remembers.)  I believe it works around the bug on all releases and it **does not** require that you specify "-noxfixes".

Any testing of the above claims would be greatly appreciated.  Thanks.

---

### Post by damdam76 on 2009-11-04
Hi Karl,
Happy to see you there !
Do you recognize me ? ;-)

> **krunge said:**
> Thanks for helping out with testing.

I also bit the bullet and created an amd64 one (x11vnc-0.9.9_TEST_amd64-Linux) that I have lazily avoided doing all this time. I'd appreciated knowing if that works for anyone.

So anyway, I claim the binaries at the above link should avoid the GDM KillInitClients **completely** (no need to specify it in gdm.conf) on all releases of debian and ubuntu (i.e. x.y to 9.10).

.../...

Any testing of the above claims would be greatly appreciated.  Thanks.

Like many people, i also switched to Ubuntu 9.10.
I have to admit that I had some issues even when I was using a binary compiled from source 0.9.9. Especially the KillInit/reopen issue discussed here.But since your last changes, and using your 64 bits binaries, x11vnc now works well after login/logout/login from GDM. (All this on a 64 bit version)
Anyway, I'm not sure this the right place to talk about that, but i'm really sad to tell you that the feature we debugged together, and the nice trick you coded about the -solid feature does not work anymore.
Did some researches and saw that x11vnc process does not switch from root to the specified user following the -user option.Launched manualy from a console as the logged user, the feature works well.
Might this be due to the fact these options are not included in the 64 bit binary ( like you told before in this thread ? )
Anyway, i'm there if you need more explanations or testing.
If you think it's better to talk about somewhere else, you got my email !

See you.

---

### Post by krunge on 2009-11-04
> **damdam76 said:**
> 
Anyway, I'm not sure this the right place to talk about that, but i'm really sad to tell you that the feature we debugged together, and the nice trick you coded about the -solid feature does not work anymore.
Did some researches and saw that x11vnc process does not switch from root to the specified user following the -user option.Launched manualy from a console as the logged user, the feature works well.
Might this be due to the fact these options are not included in the 64 bit binary ( like you told before in this thread ? )

Hi, yes, I remember you now that you mentioned the -solid option.

I don't think it is a 64-bit issue, but I don't have a 64-bit ubuntu 9.10 to test with right now.

Since I had my little 9.10 image in virtualbox, I did some more testing last night, including the -solid option.  I found it interesting with the new GDM (that I describe above) it creates its own gnome-session/dbus-session.  And  even when the user logs in it remains so there are now **TWO** dbus-launch sessions!  So, regarding our hack to divine DBUS_SESSION_BUS_ADDRESS there is now an ambiguity as to which one to use.  In the 0.9.9 tarball (and corresponding uploaded binaries) I have x11vnc apply a simple 'voting scheme' to try to decide.  It seems to work fine.

Regarding the root user running x11vnc from Init/Default, wasn't this always the case for -solid on gnome?  I.e. it has to run gconf2-tool.  Are you saying this worked as root on ubuntu 9.04 and earlier?

For testing -solid on 9.10 I simply did this in /etc/gdm/Init/Default:
```

/var/tmp/x11vnc.new -users +fred -nopw -o /var/tmp/x11vnc_test.log -forever -bg

``` 
where 'fred' is my almost-famous testing user.  Anyway, -solid (including the  dbus env. var. voting trick ) works fine as above for fred. It is not a general solution, but I can't think of any besides a more general usage of -users and/or -unixpw.   Remind me if there is some other method I have forgotten...

---

### Post by damdam76 on 2009-11-04
> **krunge said:**
> Hi, yes, I remember you now that you mentioned the -solid option.

You're right, I just realized I was not emailing you with my 'damdam76' nickname ! Anyway you identified me :)

> 
Regarding the root user running x11vnc from Init/Default, wasn't this always the case for -solid on gnome?  I.e. it has to run gconf2-tool.  Are you saying this worked as root on ubuntu 9.04 and earlier?

In fact on 9.04 and earlier versions, x11vnc was running as root on GDM until user was login in, and switched to user specified when session was opened ( maybe the -reopen switch was doing this stuff ?) thus allowwing the wallpaper to be removed.

> For testing -solid on 9.10 I simply did this in /etc/gdm/Init/Default:
```

/var/tmp/x11vnc.new -users +fred -nopw -o /var/tmp/x11vnc_test.log -forever -bg

``` 
Seeing you had added a + before your username, I tried to do the same.
"Funny" result, x11vnc directly runs as 'damdam' user (my login user) and as soon that I connect via VNC client, wallpaper of the GDM login screen disapears ! But wallpaper remains on "damdam's" desktop when connected.

---

### Post by krunge on 2009-11-04
> **damdam76 said:**
> 
In fact on 9.04 and earlier versions, x11vnc was running as root on GDM until user was login in, and switched to user specified when session was opened ( maybe the -reopen switch was doing this stuff ?) thus allowwing the wallpaper to be removed.

Could you show me the x11vnc command you use on 9.04?
> 
Seeing you had added a + before your username, I tried to do the same.
"Funny" result, x11vnc directly runs as 'damdam' user (my login user) and as soon that I connect via VNC client, wallpaper of the GDM login screen disapears!
Oh boy!  I think there will be a lot of "funny" things with the extra dbus-session for GDM...

I'm not sure how best to handle this... I already have x11vnc 'guessing' that GDM is still up for a number of activities that it delays.  It will be easy to workaround by the user setting a, say, environment variable, but I am not sure I should do it automatically.

---

### Post by Skip Da Shu on 2009-11-04
> **krunge said:**
> Thanks for helping out with testing.

I cut some new binaries with the latest x11vnc-0.9.9 dev tarball and uploaded them:
[INDENT][http://www.karlrunge.com/x11vnc/bins/](http://www.karlrunge.com/x11vnc/bins/)[/INDENT]
I also bit the bullet and created an amd64 one (x11vnc-0.9.9_TEST_amd64-Linux) that I have lazily avoided doing all this time. I'd appreciated knowing if that works for anyone.

So anyway, I claim the binaries at the above link should avoid the GDM KillInitClients **completely** (no need to specify it in gdm.conf) on all releases of debian and ubuntu (i.e. x.y to 9.10).

I also claim it will automatically work around this Xorg server crash bug:
[INDENT][http://bugs.freedesktop.org/show_bug.cgi?id=18451](http://bugs.freedesktop.org/show_bug.cgi?id=18451)[/INDENT]
(which is the original topic of this thread in case anyone remembers.)  I believe it works around the bug on all releases and it **does not** require that you specify "-noxfixes".

Any testing of the above claims would be greatly appreciated.  Thanks.
Now have x64 version on four v9.04 boxes and one Xubuntu v8.04 w/o problems.

Performance leaves something to be desired on SOME of them (a pre-existing condition) but since it's not across the board I have to think that is something else since my x11vnc set up is uniform on all 5.  As soon as I get some time I'll have to read the doc and see what I can do to speed things up a bit... (removing wallpaper huh... will have to look for that one).

PS: turns out the really slow ones had some "effects" turned on in the Ubuntu preferences menu... how, I don't know.

---

### Post by krunge on 2009-11-05
> **Skip Da Shu said:**
> 
Performance leaves something to be desired on SOME of them (a pre-existing condition) but since it's not across the board I have to think that is something else since my x11vnc set up is uniform on all 5.  As soon as I get some time I'll have to read the doc and see what I can do to speed things up a bit... (removing wallpaper huh... will have to look for that one).

What does x11vnc print out for the framebuffer read rate?
```

05/11/2009 00:24:24 Autoprobing TCP port 
05/11/2009 00:24:24 Autoprobing selected port 5901
05/11/2009 00:24:24 
05/11/2009 00:24:24 Xinerama is present and active (e.g. multi-head).
05/11/2009 00:24:24 fb read rate: 146 MB/sec
05/11/2009 00:24:24 fast read: reset wait  ms to: 10
05/11/2009 00:24:24 fast read: reset defer ms to: 10
05/11/2009 00:24:24 screen setup finished.

```
That is for nvidia proprietary drivers.  Using Xorg drivers it is sometimes  only 5 to 10MB/sec.  This means, for that low rate, when a big window (i.e. taking up most of screen) is iconified or deiconified it takes 0.5-1.0 sec just to read in the pixels (this is before the bits even hit the network.)

---

### Post by Skip Da Shu on 2009-11-05
> **krunge said:**
> What does x11vnc print out for the framebuffer read rate?
```

05/11/2009 00:11:08 X FBPM extension not supported.
05/11/2009 00:11:08 X display is capable of DPMS.
05/11/2009 00:11:08 --------------------------------------------------------
05/11/2009 00:11:08 
05/11/2009 00:11:08 Default visual ID: 0x21
05/11/2009 00:11:08 Read initial data from X display into framebuffer.
05/11/2009 00:11:08 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5120
05/11/2009 00:11:08 
05/11/2009 00:11:08 X display :0.0 is 32bpp depth=24 true color
05/11/2009 00:11:08 
05/11/2009 00:11:08 Listening for VNC connections on TCP port 5928
05/11/2009 00:11:08 
05/11/2009 00:11:08 Xinerama is present and active (e.g. multi-head).
05/11/2009 00:11:08 Xinerama: enabling -xwarppointer mode to try to correct
05/11/2009 00:11:08 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
05/11/2009 00:11:08 Xinerama: Use -noxwarppointer to force XTEST.
05/11/2009 00:11:08 fb read rate: 735 MB/sec
05/11/2009 00:11:08 screen setup finished.
```
This is the one that had 3D effects turned on... don't know how... much better now.  

Why is Xinerama "present and active"?  This machine right now actually has no monitor, keyboard or mouse on it.

```
05/11/2009 00:26:57 Got connection from client 192.168.218.17
05/11/2009 00:26:57   other clients:
05/11/2009 00:26:57 check_access: client 192.168.218.17 matches pattern 192.168.218.
05/11/2009 00:26:57 Disabled X server key autorepeat.
05/11/2009 00:26:57   to force back on run: 'xset r on' (3 times)
05/11/2009 00:26:57 created xdamage object: 0x40002c
05/11/2009 00:26:58 Client Protocol Version 3.8
05/11/2009 00:26:58 Protocol version sent 3.8, using 3.8
05/11/2009 00:26:58 rfbProcessClientSecurityType: executing handler for type 2
05/11/2009 00:26:59 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFE)
05/11/2009 00:26:59 Enabling NewFBSize protocol extension for client 192.168.218.17
05/11/2009 00:26:59 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x574D5669)
05/11/2009 00:26:59 Enabling full-color cursor updates for client 192.168.218.17
05/11/2009 00:26:59 Enabling X-style cursor updates for client 192.168.218.17
05/11/2009 00:26:59 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFF)
05/11/2009 00:26:59 Using tight encoding for client 192.168.218.17
05/11/2009 00:27:00 client 1 network rate 663.0 KB/sec (29750.9 eff KB/sec)
05/11/2009 00:27:00 client 1 latency:  0.5 ms
05/11/2009 00:27:00 dt1: 0.0833, dt2: 0.0931 dt3: 0.0005 bytes: 116843
05/11/2009 00:27:00 link_rate: LR_LAN - 1 ms, 662 KB/s
05/11/2009 00:27:14 Battling with something for -norepeat!! (1 resets left)
05/11/2009 00:27:14 Disabled X server key autorepeat.
05/11/2009 00:27:14   to force back on run: 'xset r on' (2 times)
```

I also copied over my xorg.conf from my Xubuntu machine and the screen size is now correct when the remote machine doesn't have a monitor hooked to it as they rarely do.

---

### Post by damdam76 on 2009-11-06
Hi Karl,

> **krunge said:**
> Could you show me the x11vnc command you use on 9.04?

Here is the command I use:
```

x11vnc-0.9.9 -noxdamage -chatwindow -reopen -rfbport 5900 -rfbauth /etc/x11vnc/passwd -forever -shared -users damdam -solid '#DAB082' -ultrafilexfer -skip_lockkeys -nodpms -bg -o /tmp/x11vnc.log
```


> Oh boy!  I think there will be a lot of "funny" things with the extra dbus-session for GDM...

I'm not sure how best to handle this... I already have x11vnc 'guessing' that GDM is still up for a number of activities that it delays.  It will be easy to workaround by the user setting a, say, environment variable, but I am not sure I should do it automatically.

...can't be the one that could give you any advise on how to handle this,anyway if you need me for any kind of testing, you just have to ask !

Another question : Has someone experienced problems with the autorepeat function disabled when hitting things from the VNC client ?

Thanks again for your support.

---

### Post by krunge on 2009-11-06
> **Skip Da Shu said:**
> 
Why is Xinerama "present and active"?  This machine right now actually has no monitor, keyboard or mouse on it.

The Xorg server sometimes does this even with only 1 or no monitor.  I don't know why...  I guess an xorg.conf setting could be used to force the issue.

Add '-v' to x11vnc cmdline it will tell you how many sub-screens (heads) the X server reports there are:
```

06/11/2009 12:29:28 Xinerama is present and active (e.g. multi-head).
06/11/2009 12:29:28 Xinerama: number of sub-screens: 1
06/11/2009 12:29:28 Xinerama: no blackouts needed (only one sub-screen)

```

---

### Post by damdam76 on 2009-11-09
Hi,

> **damdam76 said:**
> 
Another question : Has someone experienced problems with the autorepeat function disabled when hitting things from the VNC client ?

In case anyone was also affected by this problem, I found a solution, adding -repeat to the x11vnc command line seems to solve the issue.
Don't know why this parameter was not necessary before Ubuntu 9.04

See you.

---

### Post by damdam76 on 2009-12-02
> **damdam76 said:**
> Hi,



In case anyone was also affected by this problem, I found a solution, adding -repeat to the x11vnc command line seems to solve the issue.
Don't know why this parameter was not necessary before Ubuntu 9.04

See you.

Made some recent tests since GDM was recently updated in Karmic, and found that repeat problem is more weird than what I thought !
Behavior is different whenever i connect from another Linux computer or from Windows.
I tried many clients RealVNC viewer, ultraVNC, SSVNC and even the java client, and i must admit I did not found why everything is working well on any client when it's run from Linux and not when it's run from Windows.Even the same java applet behaves differently when it's run from the same version of firefox on Linux and on Windows.
I've tried the latest version of x11vnc-0.9.9 on a Hardy system, and everything's OK wherever I connect.

I understand this might not be the right topic to discuss about this, so tell me Karl if you prefer me to start a new thread, or discuss of this directy via your mail.

Thanks

---

### Post by krunge on 2009-12-02
> **damdam76 said:**
> 
I understand this might not be the right topic to discuss about this, so tell me Karl if you prefer me to start a new thread, or discuss of this directy via your mail.
Please start a new thread, and please include many details (I can't say I understand how the problem manifests itself.)  Thanks.

---

### Post by damdam76 on 2009-12-03
Hi Karl, and thanks for your reply.

> **krunge said:**
> Please start a new thread, and please include many details (I can't say I understand how the problem manifests itself.)  Thanks.

Here is the link to the new thread is started:
[http://ubuntuforums.org/showthread.php?t=1344610]("http://ubuntuforums.org/showthread.php?t=1344610")

---

### Post by irvin on 2009-12-03
One question about the Test Version 0.9.9.

When I install 0.9.3 and all other older Versions of x11vnc with the ubuntu synaptic i see that there will be install other libaries like libvncserver ... which probably are needed for x11vnc to run. But with the new TEST 0.9.9 Version I don't do this and it works. Should I install the or why are they installed with the older Versions ?

---

### Post by krunge on 2009-12-03
> **irvin said:**
> When I install 0.9.3 and all other older Versions of x11vnc with the ubuntu synaptic i see that there will be install other libaries like libvncserver ... which probably are needed for x11vnc to run. But with the new TEST 0.9.9 Version I don't do this and it works. Should I install the or why are they installed with the older Versions ?

The x11vnc source tarball ships with the most recent version of libvncserver included.  By default the x11vnc built from the tarball (./configure; make) will statically link in its libvncserver; the TEST ones at the website are built this way.

libvncserver has grown in usage over the years and it makes sense for a distro maintainer to have a single libvncserver dynamically shared library for all of them.  In this case they configure x11vnc via: ./configure --with-system-libvncserver

So for the TEST x11vnc you are using it doesn't need and won't use your system libvncserver.

BTW, to see which libraries a binary needs run the "ldd" command on the binary (e.g. "ldd /path/to/my/x11vnc")

---

