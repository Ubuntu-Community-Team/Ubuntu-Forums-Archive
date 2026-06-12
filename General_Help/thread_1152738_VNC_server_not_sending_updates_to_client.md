---
title: "VNC server not sending updates to client"
date: 2009-05-08
forum: General Help
---

### Post by yang on 2009-05-08
I recently upgraded to 9.04.  After upgrading, it seems I was able to use VNC for a bit OK, but then it stopped working.  Screen updates were no longer being sent from the server to the client.  Input was still being sent from the client to the server - I could see the effects of the mouse and keyboard working on the at the actual server machine.

I can kill vino-servre then run /usr/lib/vino/vino-server.  When I reconnect from a client I can see the updated screen.  On the client side I'm just using Linux vncviewer.

This never happened in 8.10.  If it matters I have compiz enabled.  Let me know what other information would be helpful.

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

$ uname -a
Linux yang-xps410 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by roberthr on 2009-05-08
If you are using Compiz (Desktop effects) on server side, it will not send screen refresh to client due to a bug. The only currently known workaround is to disable desktop effects.

---

### Post by yang on 2009-05-08
Things seem to be working OK on my other Ubuntu 9.04 box with Compiz enabled, though....

---

### Post by jackmetal on 2009-05-08
I'm having the same problem..   This is killing me, as I use remote connectivity to my servers every day.  It's a huge hassle at the moment, hopefully they fix it soon.  In the meantime, I'm trying to find other options for my remote connectivity (but haven't had much luck yet)..

Compiz has no effect on mine either.  It works when I connect to my 8.10 system and it even works on 1 of my 9.04 systems (one that doesn't have an nvidia card).  It 'seems' to be a problem only on my systems that have nvidia.

---

### Post by yang on 2009-05-08
Good point - I also have an nvidia on the problematic machine, but not my other machine.  lspci says:

```

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1)

```

---

### Post by jackmetal on 2009-05-12
Well....I'm still looking for a fix for it, but haven't been able to find one yet.

I've begun looking at FreeNX, but I'm having a strange issue with it scaling the display on the client side (so it shows a crunched up screen on the client that is my 2 monitor screens from the server)..  If I could get that fixed, there would no longer be any need for the built-in Remote Desktop that has the bug.

Plus - FreeNX looks like it has a lot of really cool features that 'may' come in handy.

---

### Post by jackmetal on 2009-05-12
Forgot to mention earlier...

No fix is available yet, but there is a workaround:
[http://ubuntuforums.org/showpost.php?p=7214210&postcount=5](http://ubuntuforums.org/showpost.php?p=7214210&postcount=5)

---

### Post by jackmetal on 2009-07-30
Hi All,

Just checking in to see if there is any 'real' fix available for this that anyone knows about?

It would be nice to be able to enable compiz again and still have remote desktop work.  :-)

---

### Post by XCan on 2009-07-30
Nope. [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126) It doesn't have any high priority it seems, kind of sucks.

---

### Post by jackmetal on 2009-07-31
That's a shame..  A known issue since it was released for a lot of users and still no fix.  

I don't know why I didn't think about it before, but I think I may look into running metacity instead.

Now I just need to do some searching and see how to enable it.  :-)

---

### Post by XCan on 2009-07-31
You are using metacity as you turn off the visual effects. Or you could type 
```
metacity --replace
``` to switch quickly. However, your windows will be all messed up and end up on the same workspace.

---

### Post by v1nsai on 2009-08-02
Bumping this thread cuz I'm having the same problem.  I'm using an nvidia geforce 6600 card with compiz.  Disabling compiz is not an option! :mad:

Someone suggested using x11vnc in the bug report on launchpad.  It's not very friendly and it runs in console, I currently can't even get it to accept my password even though it tells me it does (its still unsecured atm) but it DOES send updates even with compiz and nvidia.  Just a thought, I'm looking around for more info on how to use it, I'll post a link back if I work out my problems.

----
Well, I found the website for x11vnc and it doesn't look like much has been updated since 2006.  The site is very difficult to read and unclear, I was able to figure out how to set up a password using the x11vnc -storepassword option, then by starting x11vnc by 'x11vnc -rfbauth path/to/passwd/file but when I tried to view it, the whole screen was grey and blank, except for a very ugly terminal screen.  I've gone through tightvnc, vnc4server, linuxvnc and will be trying anything else that comes up from 'apt-cache search vnc server' but none of them have worked either.  I'm gonna go lay down for a while, I'll post back if I come up with anything else.

---

### Post by krunge on 2009-08-02
> **v1nsai said:**
> 
but when I tried to view it, the whole screen was grey and blank, except for a very ugly terminal screen.  I've gone through tightvnc, vnc4server, linuxvnc and will be trying anything else that comes up from 'apt-cache search vnc server' but none of them have worked either.
Sounds like you don't know what you are doing and/or flailing.

Once you get x11vnc exporting the physical X server's display (i.e. not vncserver's X server), be sure to use x11vnc's```
-noxdamage
``` option to work around the compiz bug.

---

### Post by v1nsai on 2009-08-02
I've never written a vnc server so no, I don't exactly know what's going on.  So I guess thanks for the "help" but with the -rfbauth option to protect with password and your -noxdamage option enabled I got the grey background with a white terminal off to the side.

---

### Post by krunge on 2009-08-02
> **v1nsai said:**
> I've never written a vnc server so no, I don't exactly know what's going on.  So I guess thanks for the "help" but with the -rfbauth option to protect with password and your -noxdamage option enabled I got the grey background with a white terminal off to the side.

Do you know what happens to be displaying on the physical screen (monitor etc.) at the time you connect via x11vnc?

From your description I'm guessing:

1) Somehow the physical display is logged into a "Failsafe-Terminal" session (and x11vnc is simply showing it to you.)  Or,

2) You started a virtual (RAM-only) X server with "vncserver" and somehow, don't ask me how, you pointed x11vnc to it (instead of to the physical display.) You see, the default Desktop for "vncserver" is very minimal, and fits your description, grey bg, etc.

If I had to guess, I'd say you are doing 1)

---

### Post by krunge on 2009-08-02
> 
2) You started a virtual (RAM-only) X server with "vncserver" and somehow, don't ask me how, you pointed x11vnc to it (instead of to the physical display.)
Oh, another way for this to happen is your viewer is connected to the "vncserver" you started and **not** to x11vnc.  So you see the default grey bg + terminal of vncserver.

x11vnc will print out info when the viewer connects, so you can tell that way if you are connecting to x11vnc or not.

---

### Post by v1nsai on 2009-08-04
Thanks, I'm able to see the remote screen I'm just trying to log into my computer from different parts of the house haha, it sounds like I'm probably logging into a RAM session, I'll sit down with it and get it figured out, like I said I tried all the vnc servers I could find in the repositories and x11vnc was the only one that actually worked with (minor) tweaking.

Eventually I'll sit and play with it, sometimes when you get on the computer you need to do actual WORK lol

---

### Post by v1nsai on 2009-08-11
anyone know of a good alternative that will let us keep compiz running?

---

### Post by krunge on 2009-08-11
> **v1nsai said:**
> anyone know of a good alternative that will let us keep compiz running?
In a previous post you mentioned you got x11vnc working. Did you run it via ```
x11vnc -noxdamage ...
```?  That should allow you to keep compiz running.

Maybe you actually never connected to x11vnc but to something else instead.  Run x11vnc with "-o somefilename" in addition to the other cmdline options, then try connecting with a VNC viewer to it, and then upload the "somefilename" logfile to this thread and I will have a look.

---

### Post by v1nsai on 2009-08-14
I have no problem at all connecting to x11vnc, it's a little hard to follow since its a console app but everything works fine except trying to get a password set up, I forget what the author said to use but I couldn't figure out how to do it properly.  If you can figure out that part and tell me, me and everyone else who refuse to lose compiz would really appreciate it!

---

### Post by krunge on 2009-08-14
> **v1nsai said:**
> I have no problem at all connecting to x11vnc, it's a little hard to follow since its a console app but everything works fine except trying to get a password set up, I forget what the author said to use but I couldn't figure out how to do it properly.
Tell me the full command line you are using to run x11vnc.

---

### Post by v1nsai on 2009-08-16
The way I understood the website of the author, you were to use the '-storepasswd path/to/passwd' command to store a password to a file, and then '-rfbauth path/to/passwdfile' to run it with the password.  When I connected to the server I ran with -rfbauth I got the grey screen with weird shell.

So to answer your question, I'm running x11vnc as such:
```
x11vnc -rfbauth .vnc/passwd
```


Thanks for all the help, it'd be great to get this running with a password, I don't need remote access bad enough to allow the rest of the world remote access as well.

---

### Post by krunge on 2009-08-16
> **v1nsai said:**
>  When I connected to the server I ran with -rfbauth I got the grey screen with weird shell.
Oh yes, I remember now.

Try running it this way as a test:```
x11vnc -passwd test99
```
Then try connecting to it with a VNC viewer.  If you connect without having to supply "test99" as a password you obviously have not connected to that x11vnc process (and we need to troubleshoot that.)

After we see that is working we will move on to the -rfbauth and other stuff.

---

### Post by v1nsai on 2009-08-16
Hot damn!  That did it!  Thanks a million, I've been stumbling around trying to figure out how to work it for a while now.

I also just figured out your name, thanks for the great program man!  It's the only one that I've seen that will send updates even with compiz running.

Just one other question though, the server exits after I connect to it once then disconnect, is there a way to keep it running after the last client disconnects?

---

### Post by krunge on 2009-08-16
> Hot damn!  That did it!  Thanks a million, I've been stumbling around trying to figure out how to work it for a while now.

Great, glad it is working for you.

> 
I also just figured out your name, thanks for the great program man!  It's the only one that I've seen that will send updates even with compiz running.

Thanks.  However I am confused compiz is working for you since you didn't say  you were using the "-noxdamage" x11vnc option.  Just to be sure, I show it below.
> 
Just one other question though, the server exits after I connect to it once then disconnect, is there a way to keep it running after the last client disconnects?
Sure, it is the -forever option described in the FAQ:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-forever-shared](http://www.karlrunge.com/x11vnc/faq.html#faq-forever-shared)[/INDENT]
So your command line should look something like this:
```
x11vnc -passwd test99 -noxdamage -forever
```
Be sure to use -noxdamage or compiz might stop updating some day. (I wish Xorg/compiz would fix this bug!)

---

### Post by v1nsai on 2009-08-17
Thanks a bunch man, I donated some moneys your way.

Hooray for x11vnc we all have a working vnc server again!

---

### Post by jackmetal on 2009-10-11
Has anyone heard if this has actually been fixed?  I've gotten around it (by disabling compiz and using metacity for the moment), but it's still broken in Ubuntu 9.10 beta also.  

I would have thought they would have fixed it by now.

---

### Post by XCan on 2009-10-11
It hasn't been fixed in Ubuntu, however, there are patches for xorg out that fixes it. It just, unfortunately, seem that the Ubuntu devs don't consider this an important issue at this time. :(

---

### Post by jackmetal on 2009-10-12
> **XCan said:**
> It hasn't been fixed in Ubuntu, however, there are patches for xorg out that fixes it. It just, unfortunately, seem that the Ubuntu devs don't consider this an important issue at this time. :(

That's definitely disappointing isn't it!!  It's amazing that they're letting this bug make it through yet another release (9.10).  At least thus far (hopefully they'll fix it before 9.10 goes live!

Did you apply the xorg patches, how will that affect future ubuntu updates of xorg?  Also, Where did you get them?

Thanks!!

---

### Post by XCan on 2009-10-12
I didn't apply any patches. I just have to cope with the less than ideal experience atm killing stuff on my workstation and running them through ssh -X (which kind of blows for my graphical intensive java guis). :( There are, however, more info [http://ubuntuforums.org/showthread.php?t=1270527](http://ubuntuforums.org/showthread.php?t=1270527) [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126/comments/124](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/353126/comments/124)

---

### Post by Justcameron on 2009-11-17
A simple workaround for this is to set the disable_xdamage flag to true.

Apparently this uses more bandwidth but as I am only using it over a home network this is not a problem for me.

Easiest way to set this flag:
[LIST=1]
[*]ALT+F2 to run a command
[*]gconftool --type boolean --set /desktop/gnome/remote_access/disable_xdamage true
[*]Click Run
[*]...PROFIT!
[/LIST]

Works for me in Karmic with a NVidia GFX card, Compiz enabled and connecting using Ultr@VNC

---

