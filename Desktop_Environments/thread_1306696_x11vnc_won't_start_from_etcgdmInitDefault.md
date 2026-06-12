---
title: "x11vnc won't start from /etc/gdm/Init/Default"
date: 2009-10-30
forum: Desktop Environments
---

### Post by heltoupee on 2009-10-30
Problem started after upgrade from 9.04 to 9.10.

On 9.04, I started x11vnc by executing it from /etc/gdm/Init/Default.  The command I use is below (personal info replaced with '~':

/usr/bin/x11vnc -o /var/log/x11vnc -noxdamage -verbose -auth /var/lib/gdm/:1.Xauth -rfbauth /etc/.vncpasswd -rfbport 5900 -shared -forever -bg -scale 3/4 -users ~~~~~ -solid \#003399 -afteraccept "gconftool-2 --type bool --set /desktop/gnome/background/draw_background false" -gone "gconftool-2 --type bool --set /desktop/gnome/background/draw_background true"

This worked fine, and allowed me to see the GDM login screen from a VNC session on bootup.  I later set GDM to auto-login.

After upgrading to 9.10, x11vnc is not executed, despite that line being in /etc/gdm/Init/Default.  The -o option indicates the file to log to, and that file is not changed upon restart of gdm.  Placing that line in /etc/gdm/PreSession/Default causes x11vnc to run without error, when autologin is enabled, but I would like x11vnc to be available with the login screen.

Any ideas why gdm is ignoring /etc/gdm/Init/Default now?

---

### Post by krunge on 2009-10-30
I've heard that GDM is much changed in 9.10 and has significantly less functionality.

However, I suspect /etc/gdm/Init/Default should still be honored.  Maybe a mis-configuration from your upgrade?

BTW, the new GDM no longer support KillInitClients=false:
[INDENT][http://ubuntuforums.org/showthread.php?t=1296156](http://ubuntuforums.org/showthread.php?t=1296156)[/INDENT]
and this requires additional workarounds, but I don't think you are at that point yet.

---

### Post by heltoupee on 2009-11-02
Thanks!

I've read your posts in that thread and am grateful for your help.  I have compiled and installed the updated version you have there.  I was under the impression that x11vnc would manage to log something to the specified logfile before GDM gives it the axe due to KillInitClients no longer being respected.  If that is not the case, then maybe I should try the "x11vnc -env X11VNC_AVOID_WINDOWS=120" trick and see if it will write anything to the logfile.  At that point I would know that it's doing something.  I read somewhere that someone threw a "touch /var/some-file-that-doesnt-exist" into the Init/Default script, and it didn't seem to execute that, either.  That's what I'll do if the first idea fails.

Thanks again!

---

### Post by krunge on 2009-11-02
> **heltoupee said:**
>  I have compiled and installed the updated version you have there.  I was under the impression that x11vnc would manage to log something to the specified logfile before GDM gives it the axe due to KillInitClients no longer being respected.  If that is not the case, then maybe I should try the "x11vnc -env X11VNC_AVOID_WINDOWS=120" trick and see if it will write anything to the logfile.
As it dies it should log the XIO error and a bit more, e.g:
```

caught XIO error:
15/04/2008 14:12:17 deleted 50 tile_row polling images.

```
The I/O error should be obvious: the X server closed its socket with x11vnc. Is this logging not happening for you?

I am very curious to see how this works on ubuntu 9.10, but don't have the time to set one up right now.

For the touching a filename, putting this in Init/Default should work:
```
(x11vnc -whatever ...; touch /var/tmp/foofile) &
```

Thanks,

Karl

---

### Post by krunge on 2009-11-03
Well, I set up ubuntu 9.10 in a Virtualbox instance and now I see more what is going on.

In the new GDM, for the Login Greeter they start up gnome-session, dbus-launch, and metacity!  So x11vnc's heuristics to try to guess that the display manager login window is still up and the window manager hasn't started are foiled (because the gdm login greeter looks like a full session.)

No wonder GDM got rid of KillInitClients=false, they want all of their doo-dad windows to be destroyed after the user logs in!

I've uploaded a new x11vnc 0.9.9 tarball today that tries to detect this as well (it looks for windows with names like 'gdm-simple-greeter'.)  Please try it out when you get the chance.

Thanks.

---

### Post by tixetsal on 2009-11-03
Krunge,

I apologize that I have not had time to get back to you on this, and I sincerely appreciate your reply.  I have been deep in some AD stuff at work, and I have had to put my true love, *nix, on the shelf and travel off to "AD Land."  

I discovered something similar, somewhat accidentally.  I disabled visual effects last night while logged in via x11vnc (i use your s/w to control all of the machines at my home from my laptop), as I was leting an avi play and the visual effects were jerking the image around.  GDM crashed and restarted.  After that, I noticed that I was able to login w/o gdm killing the x11vnc process.  I meant to post back, but I wanted to wait until I had time to pursue the different options that you presented.

All of that to say: I believe that you are on the right track, sir!

I will post back more, when I can dig out of M$ hole that I am in.

Thank you, Krunge.

---

### Post by heltoupee on 2009-11-03
Here is a little information from my testing methodology.

```

pjones@pkjones:/tmp$ tail /etc/gdm/Init/Default
      fi
    fi
  fi
fi

touch /var/doesinitwork

/usr/bin/x11vnc -o /var/log/x11vnc -noxdamage -verbose -auth /var/lib/gdm/:1.Xauth -rfbauth /etc/.vncpasswd -rfbport 5900 -shared -forever -bg -scale 3/4 -users pjones -solid \#003399 -afteraccept "gconftool-2 --type bool --set /desktop/gnome/background/draw_background false" -gone "gconftool-2 --type bool --set /desktop/gnome/background/draw_background true"

exit 0

```

Here I show the last couple commands in /etc/gdm/Init/Default.  Both of these commands should be run, and indeed do run successfully when I manually run /etc/gdm/Init/Default as root (like gdm should do).

```

pjones@pkjones:/tmp$ ls /var
backups  crash  lib    lock  mail  run    tmp
cache    games  local  log   opt   spool  www

```

you can see that /var/doesinitwork is not created.

```

pjones@pkjones:/tmp$ sudo ps -aef | grep x11vnc
[sudo] password for pjones:
pjones    3276  3228  0 11:01 pts/1    00:00:00 grep x11vnc

```

and that x11vnc is not running

```

pjones@pkjones:/tmp$ tail /var/log/x11vnc
03/11/2009 08:10:09  PointerEvent        :   4164 |     24984/    24984 (  0.0%)
03/11/2009 08:10:09  FramebufferUpdate   :    825 |      8250/     8250 (  0.0%)
03/11/2009 08:10:09  SetEncodings        :      1 |        72/       72 (  0.0%)
03/11/2009 08:10:09  SetPixelFormat      :      1 |        20/       20 (  0.0%)
03/11/2009 08:10:09  TOTALS              :   5187 |     34894/    34894 (  0.0%)
caught signal: 15
03/11/2009 08:10:32 deleted 105 tile_row polling images.
extra[1] signal: -1
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 2116201 requests (2116200 known processed) with 0 events remaining.

```

The machine was rebooted at 8:10, so the final line in the log was the running x11vnc process dieing. There are no more lines logged to the file from an x11vnc instance starting up after reboot.

Thank you again for your help on this.  Sorry if I'm being dense, but the link in the other thread, [http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz) , should be the new version your previous post spoke about?  If so, I'll give that a try and see if that works any better.  Is it correct that the 'touch /var/doesinitwork' should get executed, and I should see that file in /var?

Thanks!

---

### Post by krunge on 2009-11-03
> 
touch /var/doesinitwork

Yes, that file not appearing is a problem.  However why not use /var/tmp/doesinitwork to be sure write permission exists? (i.e. perhaps the script is being run as non-root user...)
> 
Thank you again for your help on this.  Sorry if I'm being dense, but the link in the other thread,[http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz](http://x11vnc.sourceforge.net/dev/x11vnc-0.9.9.tar.gz) , should be the new version your previous post spoke about?  If so, I'll give that a try and see if that works any better.  Is it correct that the 'touch /var/doesinitwork' should get executed, and I should see that file in /var?
Yes, 0.9.9 is the development version and I update that tarball regularly.

Try /var/tmp/something just to be sure. However, from your other statements it appears you are correct in that the script is not being run.  I will try on my ubuntu 9.10 test image.

---

### Post by krunge on 2009-11-03
On my ubuntu 9.10 test machine I put this line in the /etc/gdm/Init/Default  script:
```

/home/fred/x11vnc.new -o /var/tmp/x11vnc_test.log -forever -bg

```
near the bottom right before the "exit 0" line in the script. /home/fred/x11vnc.new is the x11vnc built from the latest x11vnc-0.9.9 tarball link above.  I then restarted GDM.

It works great for me.  I can connect with a VNC viewer and get the GDM login panel, then login and get a desktop session.  x11vnc is not disconnected; it works as we want it to. It flies in under the radar of the GDM kill initial clients and survives.

Let me know if it works for you.

BTW, for others reading this thread, also note that the heuristics I put in for this GDM problem also work around the following Xorg server crash bug:
[INDENT][http://bugs.freedesktop.org/show_bug.cgi?id=18451](http://bugs.freedesktop.org/show_bug.cgi?id=18451)[/INDENT]
[indent][http://ubuntuforums.org/showpost.php?p=6132263&postcount=13](http://ubuntuforums.org/showpost.php?p=6132263&postcount=13)[/indent]
which, sadly, still happens in ubuntu 9.10 and has been there since 8.10.

---

### Post by heltoupee on 2009-11-04
Cool.  Thanks.  I will give that new version a try.  According to GDM documentation ([http://projects.gnome.org/gdm/docs/2.24/configuration.html](http://projects.gnome.org/gdm/docs/2.24/configuration.html)) , Init/Default is supposed to get run as root.  Searching google for 'GDM Init/Default' turns up several others having problems with init scripts not running, but it seems to be hit-and-miss, like we have here, and the solutions I'm finding (switch to kdm) aren't really that acceptable ;).

I get the feeling that this is due to me having run the upgrade from 9.04 to 9.10, and I assume you just installed 9.10 straight away.  I wonder if something went wrong in the upgrade.

---

### Post by krunge on 2009-11-04
> 
I get the feeling that this is due to me having run the upgrade from 9.04 to 9.10, and I assume you just installed 9.10 straight away.  I wonder if something went wrong in the upgrade.
Yes, mine was a fresh install.

If you want to attach your Init/Default as a file for this thread I will take a look at it for differences.  Also look for other files and permissions in the Init directory. I just have the file "Default".

---

### Post by heltoupee on 2009-11-04
I've got it.  It had to do with the autologin.  I was certain that the Init/Default script was not getting executed, so I knew that it was a problem with gdm, and not with x11vnc.

I figured that the only other difference between our setups was that I'd enabled autologin, and you had not.  Once I'd disabled autologin, everything works exactly as you described, so, there's something to learn here:

1.) If you enable autologin using gdm's 'custom.conf' file, the Init/Default script does not execute.  This is true for Ubuntu 9.10, but not for 9.04 and before.  ***If you want to use x11vnc with gdm autologin in Ubuntu 9.10 (and possibly later versions), you should execute it from PreSession/Default instead of Init/Default.

2.) Your dev version of x11vnc gets around gdm's killinitclients perfectly (For Ubuntu 9.10, patched to the date of this post).

***I noticed something else, too, and it may have to do with my setup, or it may be farther-reaching. If you have autologin enabled, and do a logout, you cannot log back in.  The greeter just re-appears every time you enter your credentials.  This was verified over x11vnc, not at the local machine, but I don't see any reason it would be any different sitting at the console. Again, this may be caused by my stupidity, and not an inherent problem in gdm.

At any rate, it now works for me again.  Thanks for all your help!

---

### Post by irvin on 2009-11-04
krunge, many thanks for all the help.

I was trying to compile your latest raball on ubuntu but it never worked. I'm not very good at this but I tried a long time and was getting crazy why it is so hard to
compile it and get it run :-(

But with your lates help I finally get it running on a virtualbox 32-bit Version.

+++

For all others, here's a quick how to x11vnc (0.9.9) with Ubuntu 9.10 (32 und 64-bit Version)
Test with Ubuntu 9.10 32-bit in Virtualbox

I kept the original File names and did a different logfile name.

Download here:

[http://www.karlrunge.com/x11vnc/bins/](http://www.karlrunge.com/x11vnc/bins/)

Choose

x11vnc-0.9.9_TEST_i686-Linux (32-bit)

or

x11vnc-0.9.9_TEST_amd64-Linux (64-bit)

download and copy to this directory /usr/bin/

right mouseclick on file and go to permissions, activate run as program (hope I translated good enough)

Install via Synaptic:

openssh-server

Now set the password

sudo x11vnc-0.9.9_TEST_i686-Linux -storepasswd yourpasswordhere /etc/x11vnc.pass

replace “yourpasswordhere” with your password

config GDM to run x11vnc before login screen:

sudo gedit /etc/gdm/Init/Default

/usr/bin/x11vnc-0.9.9_TEST_i686-Linux -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc_0.9.9_32.log -forever -bg -rfbport 5900
- if you have 64-bit replace it in the line

Reboot and you have x11vnc before login without any crash :-)
Thanks again !

---

### Post by Sappox on 2009-11-25
Hi, I've compiled your 0.9.9 x11vnc and added the following line to /etc/gdm/Init/Default on a new 9.10 installation

> 
/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg -rfbport 5900


it still quits after loggin in.

Ideas?

---

### Post by krunge on 2009-11-25
> **Sappox said:**
> it still quits after loggin in.

Ideas?
Put /tmp/x11vnc.log in as an attachment to this thread.

---

### Post by Sappox on 2009-11-27
Sorry for the delay.

After a reboot it worked. No idea why it was giving the problem before...

Thank you.

---

### Post by Lothsahn on 2009-12-05
Krunge:

I can confirm that I'm seeing this same problem after upgrading from Ubuntu 9.04.  Namely, I login via ssh and then manually start x11vnc, and then I use RealVNC to connect to the box and do the login from there.  When I click login, I x11vnc terminates and the login never processes (I'm back at the GDM login page when I restart x11vnc and connect).

Will this fix eventually be merged into the 9.10 Ubuntu repositories so that x11vnc will work, or do I need to get your test version?  Any idea (rough guess) on how long until it's fixed?

Thanks for ALL of your work on x11vnc.  Great product.

Also, I get the following line on login:
caught XIO error:
05/12/2009 21:15:03 deleted 32 tile_row polling images.

I realize that caught XIO error is supposed to give information, but why is there no error message after that line?

Lothsahn

---

### Post by krunge on 2009-12-06
> **Lothsahn said:**
> 
Will this fix eventually be merged into the 9.10 Ubuntu repositories so that x11vnc will work, or do I need to get your test version?  Any idea (rough guess) on how long until it's fixed?

I would like to release this x11vnc 0.9.9 sometime this month.  Then it is up to when debian picks it up and then when ubuntu picks up what debian has delivered.

Until this year, x11vnc was orphaned by debian, and so updates would sometimes take years; but this year a nice fellow, a debian maintainer, has 'adopted' x11vnc along with some other packages.  So I am optimistic that x11vnc 0.9.9 will be in debian/testing a month or so after after I release it.

---

### Post by Lothsahn on 2009-12-06
> **krunge said:**
> I would like to release this x11vnc 0.9.9 sometime this month.  Then it is up to when debian picks it up and then when ubuntu picks up what debian has delivered.

Until this year, x11vnc was orphaned by debian, and so updates would sometimes take years; but this year a nice fellow, a debian maintainer, has 'adopted' x11vnc along with some other packages.  So I am optimistic that x11vnc 0.9.9 will be in debian/testing a month or so after after I release it.

Awesome, look forward to the official fix.

---

### Post by Vladimir_S on 2009-12-07
Krunge, please can you help, i've compiled 0.9.9 x11vnc and added "/home/vladimir/x11vnc -o /var/tmp/x11vnc_test.log -forever -bg" to /etc/gdm/Init/Default on a 9.10, but even after reboot it still quits after loggin in. Attached x11vnc_test.log P.S. The biggest thank you for your work on x11vnc!! :-)

---

### Post by krunge on 2009-12-07
> **Vladimir_S said:**
> Krunge, please can you help, i've compiled 0.9.9 x11vnc and added "/home/vladimir/x11vnc -o /var/tmp/x11vnc_test.log -forever -bg" to /etc/gdm/Init/Default on a 9.10, but even after reboot it still quits after loggin in.
Is this really the end of it?
```

07/12/2009 17:46:10 check_xrandr_event: no change detected.
07/12/2009 17:46:10 check_xrandr_event: updating config...
07/12/2009 17:46:10 check_xrandr_event: current  WxH: 1440x900
07/12/2009 17:46:10 check_xrandr_event(): returning control to caller...

```
I don't see any messages indicating that a client has connected, but you say it it fails after you log in.

Also, please examine /var/log/Xorg.0.log and /var/log/Xorg.0.log.old for any indication that your X server is crashing.

Perhaps use "-oa /var/tmp/x11vnc_test.log" instead of "-o" to have the log append (i.e. maybe what you sent was for a restarted X server and it overwrote the log for the actual failure.)

---

### Post by Vladimir_S on 2009-12-08
> **krunge said:**
> Is this really the end of it?
```

07/12/2009 17:46:10 check_xrandr_event: no change detected.
07/12/2009 17:46:10 check_xrandr_event: updating config...
07/12/2009 17:46:10 check_xrandr_event: current  WxH: 1440x900
07/12/2009 17:46:10 check_xrandr_event(): returning control to caller...

```
I don't see any messages indicating that a client has connected, but you say it it fails after you log in.

Also, please examine /var/log/Xorg.0.log and /var/log/Xorg.0.log.old for any indication that your X server is crashing.

Perhaps use "-oa /var/tmp/x11vnc_test.log" instead of "-o" to have the log append (i.e. maybe what you sent was for a restarted X server and it overwrote the log for the actual failure.)


OK, i've added "-oa" and i saw next message at x11vnc_test.log:

"08/12/2009 11:33:50 copy_tiles: allocating first_line at size 46
caught XIO error:
08/12/2009 11:33:57 deleted 45 tile_row polling images."

And there is an error in Xorg.0.log: 

"(II) Dec 08 11:33:56 NVIDIA(0): Setting mode "1440x900"

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xb6e400]
3: /usr/bin/X [0x80f99f0]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x5d46267]
Saw signal 11.  Server aborting."   

P.S. Before and after i installed x11vnc it was a problem with local logging into xfce. 2-3 times of putting in my password before I get into the desktop. Only in Karmic i get this problem. Maybe this issue cause the problem with loggin into vnc server?  

P.S.S Sorry for my english.

---

### Post by krunge on 2009-12-08
> **Vladimir_S said:**
> 
And there is an error in Xorg.0.log: 

"(II) Dec 08 11:33:56 NVIDIA(0): Setting mode "1440x900"

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xb6e400]
3: /usr/bin/X [0x80f99f0]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x5d46267]
Saw signal 11.  Server aborting."   

P.S. Before and after i installed x11vnc it was a problem with local logging into xfce. 2-3 times of putting in my password before I get into the desktop. Only in Karmic i get this problem. Maybe this issue cause the problem with loggin into vnc server?  

Well, if the X server is crashing that is pretty serious.  I suspect buggy nvidia video drivers.

To be clear, x11vnc is not part of the X server, it is just an X client (application) that asks the X server for 'screenshots' of regions of the screen and asks to inject mouse and keystroke events.  The X server (+h/w drivers) must be able to handle those requests w/o crashing.

Did you say sometimes it crashed and restarted when you tried to log into xfce while sitting at the physical display? (i.e. no VNC/x11vnc)  If so, I suspect buggy video drivers or failing hardware and somehow x11vnc pushes it through a more likely failure path....

Try it with the non-proprietary driver 'nv' and see if the problem goes away.  Or check nvidia's site for changes/bugs WRT the driver for your graphics h/w. ubuntu 9.10, etc..

---

### Post by Vladimir_S on 2009-12-09
> **krunge said:**
> Well, if the X server is crashing that is pretty serious.  I suspect buggy nvidia video drivers.

To be clear, x11vnc is not part of the X server, it is just an X client (application) that asks the X server for 'screenshots' of regions of the screen and asks to inject mouse and keystroke events.  The X server (+h/w drivers) must be able to handle those requests w/o crashing.

Did you say sometimes it crashed and restarted when you tried to log into xfce while sitting at the physical display? (i.e. no VNC/x11vnc)  If so, I suspect buggy video drivers or failing hardware and somehow x11vnc pushes it through a more likely failure path....

Try it with the non-proprietary driver 'nv' and see if the problem goes away.  Or check nvidia's site for changes/bugs WRT the driver for your graphics h/w. ubuntu 9.10, etc..

Thank you very much, Krunge! I solved problem with loggin in into xfce (my monitor did't correctly detected, but after uninstall old drivers of videocard and installed the newest and generating modeline, edited xorg.conf - it's all right and i'm logging w/o any trouble) So now i'm logging in to x11vnc, but it is issue with mouse cursor - it is like "black crossroads".

---

### Post by krunge on 2009-12-09
> So now i'm logging in to x11vnc, but it is issue with mouse cursor - it is like "black crossroads".
I'm not sure what you mean by this.

---

### Post by Vladimir_S on 2009-12-09
> **krunge said:**
> I'm not sure what you mean by this.

Mouse cursor: **[SIZE="6"]X[/SIZE]**

---

### Post by krunge on 2009-12-09
> **Vladimir_S said:**
> Mouse cursor: **[SIZE="6"]X[/SIZE]**
That is my favorite cursor, BTW.  (I built it by hand to match the X server's default cursor; it gives me a warm feeling every time I see it.)

Are you supplying the '-noxfixes' cmdline to x11vnc by any chance?  

If not, when you compiled did you have the libXfixes build package (aka dev) installed?  I.e. configure saying 'checking for XFixesGetCursorImage in -lXfixes' saying 'yes' or 'no'?

libXfixes support should give you your cursors.  If you can't get that to work (the older x11vnc's in the repositories should have that support) you can supply '-cursor arrow' to get a single arrow everywhere (see also -arrow n in the docs for how to choose from some styles.)

---

### Post by Vladimir_S on 2009-12-09
> **krunge said:**
> That is my favorite cursor, BTW.  (I built it by hand to match the X server's default cursor; it gives me a warm feeling every time I see it.)

Are you supplying the '-noxfixes' cmdline to x11vnc by any chance?  

If not, when you compiled did you have the libXfixes build package (aka dev) installed?  I.e. configure saying 'checking for XFixesGetCursorImage in -lXfixes' saying 'yes' or 'no'?

libXfixes support should give you your cursors.  If you can't get that to work (the older x11vnc's in the repositories should have that support) you can supply '-cursor arrow' to get a single arrow everywhere (see also -arrow n in the docs for how to choose from some styles.)

Thank you very much, Krunge! I decided to use your favourite cursor too :-) It is very useful, i will not forget that i'm on VNC server now :-)) Thank you very much for your help and work on the x11vnc project!

---

### Post by docjay on 2010-05-23
Hi,

  I have a similar problem.  I am using Lucid 10.04 and also x11vnc-0.9.10_i686-Linux which lives in /usr/bin and I have this in /etc/gdm/Init/Default just before exit...

"/usr/bin/x11vnc-0.9.10_i686-Linux -rfbauth -usepw -oa /tmp/x11vnc_0.9.10_32.log -forever -bg -rfbport 5900 -httpdir /usr/share/vnc-java/"

--also I do not have auto log on configured at all.
  
At first I had errors in /var/log/Xorg.0.log about my Nvidia display driver so I did what was suggested in this thread:  [http://ubuntuforums.org/showthread.php?t=1480714&highlight=x11vnc+Xorg]("http://ubuntuforums.org/showthread.php?t=1480714&highlight=x11vnc+Xorg") which was to do this:

Code:
open the terminal and type
gksudo gedit /etc/default/grub

change the line 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

save file 
close
and then
sudo update-grub 

...after this I didn't have any more errors in Xorg.0.log, but my command would execute in my Default file because I could see a log created in /tmp but then x11vnc would crash and I would not see it running with a "ps wwaux" command.

Is there any way to give Default a delay in executing maybe?   After x11vnc crashes, I can then run the same command in putty and it starts up just fine and does not crash.  Maybe there is another approach to take to this?

Thanks for your help on this  :)

--docjay

---

### Post by krunge on 2010-05-23
> **docjay said:**
> 
...after this I didn't have any more errors in Xorg.0.log, but my command would execute in my Default file because I could see a log created in /tmp but then x11vnc would crash and I would not see it running with a "ps wwaux" command.

Please attach to this thread as a file your entire /tmp/x11vnc_0.9.10_32.log showing the failure.

---

### Post by docjay on 2010-05-23
the log file - thanks for looking.

I just restarted my ubuntu box and then tried to get to vnc and it wasn't running.  I then copied over this log file to upload here.

--docjay

---

### Post by krunge on 2010-05-23
> **docjay said:**
> the log file - thanks for looking.

Looks like you forgot to specify the vnc passwd file argument after '-rfbauth':
```

23/05/2010 17:50:23 passing arg to libvncserver: -rfbauth
23/05/2010 17:50:23 passing arg to libvncserver: -rfbport
23/05/2010 17:50:23 passing arg to libvncserver: 5900
...
23/05/2010 17:50:23 *** unrecognized option(s) ***
23/05/2010 17:50:23     [1]  5900

```
So it took '-rfbport' as the vnc passwd file and then didn't recognize '5900' standing in isolation.

---

### Post by docjay on 2010-05-24
Krunge,

  Thanks for responding so quick -- it works :)  Like you said, all I needed to do was give it the path for the password file and it executed just fine from /Default!

Thank you!

---

