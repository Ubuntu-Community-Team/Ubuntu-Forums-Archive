---
title: "3D Beryl VNC"
date: 2007-03-02
forum: Desktop Effects &amp; Customization
---

### Post by youthforlinux on 2007-03-02
I would like to show off Beryl on my desktop to my friends via remote desktop, but VNC wont work.  I've heard that VirtualGL and TurboVNC could do the trick but I googled and could not find any Ubuntu packages.  Any ideas????

---

### Post by clarknova on 2007-08-20
I grabbed the rpms off virtualgl.org and used alien to create .debs, which installed fine. I then followed the instructions in their documentation but it doesn't seem to be working in ltsp yet, which is what I'm using. Who knows, maybe it would work with vnc.

At least it didn't crash me. I'll have to tinker some more to figure out how to adapt their instructions to work on my thin clients.

db

---

### Post by kwandar on 2007-10-05
Please keep us up to date on how Beryl runs with Virtualgl and TurboVNC.  I would like to know if its possible to do thi!!

Now that quad cores are coming down in price I'm hoping that I can put in a couple of video cards and have a wonderful Ubuntu desktop to show off anywhere, and add virtualized XP on the server as well, to run all my legacy software.

Before I start buying, I'd like to know if there is any hope for this working.

---

### Post by JayTee on 2007-10-07
I used X11VNC to remote to my computer with Beryl running. The default VNC won't work with Beryl. X11VNC allows you to connect to session 0 running Beryl. Depending on your internet connection speed it may seem sluggish.

---

### Post by kwandar on 2007-10-14
Okay, I got the latest version of VirtualGL and TurboVNCL, and converted with Alien.  Converted, but didn't work.  Then I noticed that for Ubuntu _**you need to install a dependency called TurboJPEG.**_.  This is also on the VirtualGL website.

Now it seems to work (brings up a menu at least) but I have yet to get further.  Learning lots trying to get this up on a test basis,  but it is slow as I'm not network literate.

---

### Post by wonk-o-matic on 2008-03-06
kwandar, how has VirtualGL worked out with ltsp?  Any updates?

---

### Post by clarknova on 2008-03-11
Yeah, I would love to hear from anybody having success here. I'm about to create another ltsp/edubuntu network and 3D on the clients would be sweet.

db

---

### Post by khaije1 on 2008-05-25
i'm curious about this too. VirtualGL seems like a great tech to make openGL net-transparent, which is an awesome point of convergence for openGL enablement of virtual machines and thin-clients.

Very significant tech imo. There is vmgl as well but I think virtualGL's approach has broader applications. This project is owned, or at least sponsored by Sun (it's gpl'd though so not a super big deal) and seems to make regular and recent progress since  I first noticed it 1.5+ yrs ago.

I'm going to start trying to get this running for vm_guest acceleration on Hardy Server x64. Is there a place where ubuntu users can collaborate on this directly? Perhaps a wiki page at community docs? 

I'm not sure the best way to go about this, please let the suggestions roll in since i'll probably need some help to make sense of this! :-)

Thanks!

---

### Post by clarknova on 2008-05-27
I'm starting to think that GL on ltsp is perhaps a different problem than GL on VNC, so rather than hijack this thread any further I've started another.

[http://ubuntuforums.org/showthread.php?t=809982](http://ubuntuforums.org/showthread.php?t=809982)

db

---

### Post by wonk-o-matic on 2008-06-08
I got VirtualGL working.  I'll start posting the method on the new GL thread: 

[http://ubuntuforums.org/showthread.php?t=809982](http://ubuntuforums.org/showthread.php?t=809982)

---

### Post by Debuggern on 2008-06-11
> I got VirtualGL working. I'll start posting the method on the new GL thread:

[http://ubuntuforums.org/showthread.php?t=809982](http://ubuntuforums.org/showthread.php?t=809982)

Sounds great, looking forward to see your HOW TO, wonk-o-matic! It would be great to actually be able to run heavy openGL appllications by remote. Also it is a easy way to work with openGL projects and program by remote.

cheers! :)

---

### Post by Debuggern on 2008-06-11
Nice! I got virtualGL working with nxserver! :) Still have problems with getting turboVNC installed. I will try the real thing at work, however, I am not totally satisfied with the rendering speed. Seems like nxserver is not the the best VNC server to test things out, I have tryed the virtualGL commands for better rendering speed, none of them has helped. 

Going to try out the real deal later at work by playing Jedi Knight II: Jedi Outcast by true remote. Later folks! :)

---

### Post by wonk-o-matic on 2008-06-11
I typed in a lot of details for that new thread, but somehow my post didn't show up.  Rats.  Probably user error.  

One down-side: keyboard input is terribly slow within one of the apps I've tested.  Don't know how serious it will be, in general.  But it sure is nice to see the zippy grapics.

Basically, I got the latest source from the project cvs site.  Then  I compiled and noted the missing modules.  I looked for the Ubuntu packages that had what I needed, and installed them, then compiled again.  There were some modules that I moved from the tarball into my local include directory.  

When you're done, google on "Configuring a Linux or Solaris machine as a VirtualGL Server" for the way to set it up.  Considering that VirtualGL toasts security on the PC architecture, I just set it up with the lax settings.  My internal network doesn't have the kind of users that make me worry.

---

### Post by Debuggern on 2008-06-12
Hmm, I cannot execuite the command /usr/bin/vglrun on my applications at work, it says it can't connect to my X Display 0.0.

wonk-o-matic, could you please explain in detail how you installed TurboVNC and virtualGL? I really appreciate your effort in explaining in detail how you did it, thanks.

---

### Post by Debuggern on 2008-06-13
ok, the command > xhost + should do it. I could not connect to the X display 0.0, since it was created by another user, so this command should do it. Will try it later at DreamHack!

Cheers!

---

### Post by pegasus123 on 2008-06-30
I couldn't get virtualGL installed correctly. During installation it complained:
"cannot stat ./linux/dbg/bin/vglclient: No such file or directory".

I didn't install openSSL or TurboJPEG. The config file had the following:
DEBUG = yes
JPEGLIB = libjpeg
M32 = yes
CC = gcc
USESSL = no

I will appreciate if someone can tell us how to  install virtualGL and TurboVNC stepbystep for Ubuntu.

Thanks!

---

