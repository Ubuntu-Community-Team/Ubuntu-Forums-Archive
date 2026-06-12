---
title: "KDE4 Won't Start"
date: 2008-01-11
forum: Desktop Environments
---

### Post by wersdaluv on 2008-01-11
I am on Ubuntu (GNOME) Gutsy. I didn't install KDE 3 but I had some KDE packages installed because I installed some KDE applications.

I installed KDE4 by following this
> # Remove previous KDE 4 packages, they are not compatible (apt-get remove kdelibs5 kde4base-data kde4libs-data)
# Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main to your /etc/apt/sources.list
# Install kde4-core, note that PPAs aren't authenticated so you will likely get a warning when installing
# KDE 4 apps should appear in your KDE 3 K-menu or you can run a full session by selecting "KDE 4" from your login manager.

When I logged in KDE4, after the splash screen, GDM just came out again. I tried rebooting. When I logged in, the splash screen came out and I came back to GDM again.

Any idea?

:KS

---

### Post by sports fan Matt on 2008-01-11
wers,

I have excactly the same issue ..im glad its not just me..When it reboots, does it look like a tv with snow on it/knocked off air..etc?

---

### Post by wersdaluv on 2008-01-11
> **sox fan Matt said:**
> wers,

I have excactly the same issue ..im glad its not just me..When it reboots, does it look like a tv with snow on it/knocked off air..etc?

Ah.. Nope. I don't et that.

---

### Post by sports fan Matt on 2008-01-11
Wierd, thats what i get when i try kde then it restarts to login screen...

---

### Post by wersdaluv on 2008-01-11
> **sox fan Matt said:**
> Wierd, thats what i get when i try kde then it restarts to login screen...

Oh! Yah! I get that too! I thought, you were talking about rebooting. Whenever I get back to GDM!

---

### Post by [z]ephyr on 2008-01-11
I've got the same issue - Login with KDE4 selected, and the little loader with the disk icon comes up, then *poof*, back to the Nvidia logo and then to KDM.

---

### Post by sports fan Matt on 2008-01-11
yeah, it reboots with that garbled screen then returns to the login where you can select options..etc

---

### Post by wersdaluv on 2008-01-11
We need help!!! 

:KS

---

### Post by sports fan Matt on 2008-01-11
HHHHHHHHHHHHHHEEEEEEEEEEEEEEEEEEELLLLLLLLLLLLLLLLLPPPPPPPPPPPPPPPPPPPPPPPP!!!!!!!!!!!!!!!!!!!!!!!! Maybe that will work?

---

### Post by sports fan Matt on 2008-01-11
Could it be possible that KDE4 was prematurely released cause it sure seems like alot are having issues with it...?

---

### Post by kugn on 2008-01-11
try checking how much disk space there is. getting back to the login screen happens when there isn't space.

---

### Post by [z]ephyr on 2008-01-11
I can't speak for everyone else, but I have plenty of disk space available.

---

### Post by smartboyathome on 2008-01-11
I am having a similar problem with trying to start KDE with Xephyr. It just quits. I have plenty of space (I haven't even filled up my drive halfway and it is 320 GB!).

---

### Post by jmedina on 2008-01-11
I'm having the same problems. Oh well, it was worth a shot.

---

### Post by [z]ephyr on 2008-01-11
Update: It works just fine in Xephyr, but not as a full session.  I have a dual-head monitor setup, if that matters at all.

---

### Post by smartboyathome on 2008-01-11
weird... why would it work fine for you in xephyr, but not for me? By the way, did you follow the instructions from Kubuntu to install it?

EDIT: Could it be that I am using gtk-xephyr and that is why it isn't working? Also, here is the output from the terminal which is what I get when kde4 crashes:

```
kdeinit4: preparing to launch /usr/lib/kde4/lib/kde4/libexec/klauncher
kdeinit4: Launched KLauncher, pid = 22649 result = 0
kdeinit4: Can't connect to the X Server.
kdeinit4: Might not terminate at end of session.
kdeinit4: preparing to launch /usr/lib/kde4/bin/kded4
kdeinit4: Launched KDED, pid = 22650 result = 0
kded4: cannot connect to X server :2
kded(22650): Communication problem with  "kded" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message did not receive a reply (timeout by message bus)" " 

kdeinit4: PID 22650 terminated.
kdeinit4: preparing to launch /usr/lib/kde4/bin/kcminit_startup
kdeinit4: Launched 'kcminit_startup', pid = 22652 result = 0
kcminit_startup: cannot connect to X server :2
kdeinit4: PID 22652 terminated.
kdeinit4: Got KWRAPPER 'ksmserver' from socket.
kdeinit4: preparing to launch /usr/lib/kde4/bin/ksmserver
<unknown program name>(22655)/ KStartupInfo::createNewStartupId: creating:  "aabbott-laptop;1200111377;710597;22655_TIME0" : "unnamed app"
kdeinit4: PID 22655 terminated.
ksmserver: cannot connect to X server :2
startkde: Shutting down...
kdeinit4: terminate KDE.
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
```

Looks like for some odd reason it couldn't connect to the xserver... oh well, I can try starting it manually from terminal.

---

### Post by wersdaluv on 2008-01-11
It's better if we don't need to run xephy. 

Got plenty of space here too.

---

### Post by [z]ephyr on 2008-01-11
Yeah, I followed the Kubuntu guide to install it and to run the Xephyr session.  I just decided to try it with Xephyr to see if it would work - I know that's definitely not a solution to the problem.

---

### Post by smartboyathome on 2008-01-11
I don't want to restart x, that is why I run xephyr. I always have several apps up and it is rarely convenient for me to restart. Anyway, the same happens when trying to start KDE from a terminal (xephyr quits and kde spits out the same errors).

EDIT: XFCE works with it, so it is a problem with KDE4.

---

### Post by jmedina on 2008-01-11
I'm going to try the opensuse KDE 4 Live CD and see if that works.

---

### Post by sports fan Matt on 2008-01-11
i have 23.9 gb available so im most likely not  out of space....how wierd!

---

### Post by smartboyathome on 2008-01-12
I logged out and am in it now as a full session.

---

### Post by sports fan Matt on 2008-01-12
i'm hoping to be there in about 5, 10 mins:)

---

### Post by jacksaff on 2008-01-12
Those of you having this problem might have a near-full root partition.
I did - I had all of the downloaded kde4 packages plus all the rc2 packages in apt-cache and my root partition was over 90% full.
I removed kde3 apps where I had both kde3 and 4 versions, ran 'sudo apt-get clean' and presto, cleared out well over a gig-and-a-half of cruft. 
I can log into kde4 fine now.
We really need a more graceful way of failing when this happens though.

---

### Post by tanari on 2008-01-12
kde 4 say that my temp dir is full, and I can't start kde4.
but my temp dir is empty!!!!

how to start kde 4???

---

### Post by SunnyRabbiera on 2008-01-12
> **sox fan Matt said:**
> Could it be possible that KDE4 was prematurely released cause it sure seems like alot are having issues with it...?

yup....

---

### Post by nevercome on 2008-01-14
> **tanari said:**
> kde 4 say that my temp dir is full, and I can't start kde4.
but my temp dir is empty!!!!

how to start kde 4???

SOLVED removing the directories .kde and .kde4 in my homedirectory.

---

### Post by lavid on 2008-01-14
I'm having the same issue "kdeinit4 cannot start check installation" and I think it's due to constantly trying out the latest alpha versions. I'm running hardy unstable and I think that perhaps uninstalling debs at some point didn't get rid of something that is now preventing kde4 from starting.

---

### Post by GeneralZod on 2008-01-14
> **nevercome said:**
> SOLVED removing the directories .kde and .kde4 in my homedirectory.

Just in case someone here reads this and doesn't know: **This will erase *all* of your KDE3 and KDE4 configuration and data** (including e-mail if you use KMail/ Kontact), so don't do it unless you have backups and know precisely what you are doing!

---

### Post by borris.morris on 2008-01-27
I too am having this problem. I noticed it when I updated some packages, but I'm not sure if this was the cause or not... I did some installing of packages too...

---

### Post by mawdryn on 2008-01-28
I had the same issue, but found it was caused by the lack of Direct Rendering in X Windows. Once I reconfigured X with the glx module, it worked fine.

---

### Post by borris.morris on 2008-01-29
> **mawdryn said:**
> I had the same issue, but found it was caused by the lack of Direct Rendering in X Windows. Once I reconfigured X with the glx module, it worked fine.

How would one go about that? Reconfiguring X? I'll try...

---

### Post by FlipJones on 2008-02-06
I have the same problem...How do i clean out the kde3 stuff exactly?

---

### Post by borris.morris on 2008-02-06
stop! wait, no dont do that! if you're using nvidia, go get the newest drivers and reinstall them. that worked for me. (it was the glx module..)

---

### Post by FlipJones on 2008-02-06
nope i dont have nvidia...i cleaned out my root dir and removed the .kde folder....
i am a gnome guy mostly and rarely use kde but i want to try to run 4...

Any help on what to do from here?

---

### Post by borris.morris on 2008-02-06
Well, try reconfigureing X while using the Vesa driver. If it works, then yes, it is the lack of Glx that is killing you.

---

### Post by travist120 on 2008-02-09
I've been having the same issue. On my laptop, I get into the boot screen, and it just stays there, no going back to the gdm or anything. Let me mention though that I got KDE4 RC working with a CHMOD of something -- can't remember what, but on my desktop I'm having the same problem as you where it will show the splash screen, then WHAM! back to the gdm menu for me. Honeslty, I've always hated KDE, but I figure that kde4 would be better. I've hated kde because I always have a problem with it, whether it be hardware or some random broken thing. Though I have to admit, kde4 is pretty sexy, and it looks like they've gotten their qt4 themes sexy looking too. Anyhow, Is there a way I can get it to work? I'll look into deleting .kde4 and .kde

*EDIT*
Deleted .kde .kde4, nothing new. Still not working.

---

### Post by wersdaluv on 2008-02-09
> **travist120 said:**
> 
*EDIT*
Deleted .kde .kde4, nothing new. Still not working.

To those who are not aware, deleting .kde will remove the settings of all your kde apps including kontact, Amarok, etc.

---

### Post by inportb on 2008-02-24
Hm, this seems to be a problem still. I tried launching KDE4 using the failsafe terminal, and got the following:

Fatal error: you need to have a KComponentData object before you do anything that requires it! Examples of this are config objects, standard directories or translations.

---

### Post by ekrey on 2008-02-29
You could try delete the /etc/kde4rc file 

refer to this bug report :
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/193498]("https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/193498")

---

