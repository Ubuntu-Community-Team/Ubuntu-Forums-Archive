---
title: "Login does not work"
date: 2009-01-07
forum: General Help
---

### Post by Oracle_The_Blind on 2009-01-07
Hi

I am having an issue with logging into Ubuntu 8.10 kernel 2.6.27-11. 
Neither the GDM nor the tty will let any of my user accounts log in.
When I enter my username and password into the GDM, the GDM simply restarts, and when I enter my username and password into a tty, it will not give any errors, but rather just prompt again for a login.

However, when I enter a username and INCORRECT password into either the GDM or a tty, it will say login incorrect.
I therefore do NOT think that it is an authentication problem.

Incidentally, when I boot into the recovery mode, the recovery mode works just as it always has, except that when I try to change passwords for my user accounts, I get a "Segmentation fault"

Any help on this will be greatly appreciated, as I currently am unable to log in to my computer.

---

### Post by Oracle_The_Blind on 2009-01-08
Bump.
So long as this problem persists, my computer is unusable.

---

### Post by Demosthenes on 2009-01-18
Got exactly the same issue.

Can't log in, gdm just restarts, Segmentation Fault on trying to use passwd in recovery prompt.

---

### Post by mssever on 2009-01-18
First, look in /var/log/Xorg.0.log and post any relevant info (or the whole thing if you don't know what's relevant). You can also try going to recovery mode, then: ```
su yourusername -
startx
```Let us know if you are successfully able to get into your X environment, or if you get errors, post them.

---

### Post by adamlau on 2009-01-18
2.6.27-11 from proposed? kernels.org? git source tree? Fall back to to 2.6.27-9-generic (or your previously working kernel).

---

### Post by Demosthenes on 2009-01-18
Kernel is from proposed (adding proposed repository was only real change from working system, so it must be something from there) however selecting the old kernel at grub prompt doesn't result in a working system. (If you've got a link to a known bug relating to this I would be interested, as would any others like myself who find this thread when having the same problem.)

Sadly the system isn't mine and in order to restore a working sytem I've just done a quick reinstall on another partition and copy across of settings before I have to leave it. Thus I won't be able to delve any further into this problem, but it might be of interest to Oracle_The_Blind that others are having the same issue. Especially if one of you kind fellows already has the solution.

---

### Post by metlhead05 on 2009-01-25
I am having the exact same problem as described here.

I cannot login with any users accounts. If I use the root terminal from the restore option I get a segmentation fault if I try to change a user password

I have tried running dpkg-reconfigure on all the gnome desktop packages. 


I can startx, but it locks up saying "User Switcher" has quit unexpectedly

The only thing that I have done is run standard updates and I installed SciTE.

---

### Post by mssever on 2009-01-25
> **metlhead05 said:**
> I am having the exact same problem as described here.

I cannot login with any users accounts. If I use the root terminal from the restore option I get a segmentation fault if I try to change a user password

I have tried running dpkg-reconfigure on all the gnome desktop packages. 


I can startx, but it locks up saying "User Switcher" has quit unexpectedly

The only thing that I have done is run standard updates and I installed SciTE.
Have you tried reinstalling passwd and all the pam stuff?

---

### Post by metlhead05 on 2009-01-25
> **mssever said:**
> Have you tried reinstalling passwd and all the pam stuff?

right now I am backing up all my files that I want to keep as I'm no expert so usually a reinstall is the fastest way to get back up and running. ( I still have my 8.04 install on a different drive just for this type of thing.)

I'm not sure exactly which packages are included in the 'pam stuff'. but I will try and remove and re add them as soon as the tar is done packaging all my files.


I guess it could have had something to do with me trying to setup printers through samba on a couple of laptops tonight, but I don't really see how that would affect anything. I was trying to look at cups, and it stopped responding, so I went to restart that service and my password didn't work. That was when I rebooted and I was locked out.

---

### Post by mssever on 2009-01-25
> **metlhead05 said:**
> I guess it could have had something to do with me trying to setup printers through samba on a couple of laptops tonight, but I don't really see how that would affect anything. I was trying to look at cups, and it stopped responding, so I went to restart that service and my password didn't work. That was when I rebooted and I was locked out.
This is certainly an odd problem. I'm very tempted to say that it has nothing to do with your printers, but I have no alternate explanation.

Here's a list of the PAM packages installed on my Intrepid machine. Your list, or course, may vary slightly.```
libpam0g libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-runtime python-pam
```

---

### Post by metlhead05 on 2009-01-27
I don't know if this helps anyone, I am probabaly going to reinstall tonight once I finish downloading the OS cd again (I gave my latest CD to a girl at work).

```
I was digging in the user.log, and I found these entries that looked pretty suspect.

Jan 20 21:25:18 waldorf hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 21:25:19 waldorf python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 21:25:24 waldorf hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 20 21:25:25 waldorf python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 24 15:54:14 waldorf bonobo-activation-server (patrick-12983): could not associate with desktop session: Failed to connect to socket /tmp/dbus-EZdu5imHmJ: Connection refused
Jan 24 15:54:19 waldorf bonobo-activation-server (patrick-13218): could not associate with desktop session: Failed to connect to socket /tmp/dbus-EZdu5imHmJ: Connection refused
Jan 24 15:55:51 waldorf pulseaudio[6071]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 24 15:55:51 waldorf pulseaudio[6073]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 24 15:55:51 waldorf pulseaudio[6073]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 24 15:55:51 waldorf pulseaudio[6073]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jan 24 15:55:51 waldorf pulseaudio[6073]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Jan 24 15:55:51 waldorf pulseaudio[6073]: alsa-util.c: Cannot find fallback mixer control "PCM".
Jan 24 15:55:51 waldorf pulseaudio[6073]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
Jan 24 15:56:06 waldorf pulseaudio[6073]: module-x11-xsmp.c: X11 session manager not running.
Jan 24 15:56:06 waldorf pulseaudio[6073]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Jan 24 15:57:15 waldorf hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 24 15:57:16 waldorf python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 25 20:41:25 waldorf hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 25 20:41:26 waldorf python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Jan 25 21:03:39 waldorf bonobo-activation-server (patrick-23299): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Ru4P3kugAb: Connection refused
Jan 25 21:03:43 waldorf bonobo-activation-server (patrick-23532): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Ru4P3kugAb: Connection refused

```

---

### Post by mould on 2009-01-29
> **metlhead05 said:**
> I was trying to look at cups, and it stopped responding, so I went to restart that service and my password didn't work. That was when I rebooted and I was locked out.

Same problem here. I logged in fine and started the CUPS web interface. I tried to cancel a job, entered the root password, CUPS stopped responding. So I did a "sudo /etc/init.d/cups restart", and got a segfault. 
Now, sudo, su and passwd all segfault after I enter the password. 
 
After rebooting, I can't log in at all. Trying to login to a tty just gives the login prompt again. 
If I boot to single user mode, running "passwd" gives a segfault, but only when setting a user password, not root. I can use passwd to set a root password, and then trying to login as root gives "Login incorrect". I have to boot from a LiveCD to reset the root password. 

One thing that might be relevant - I think I originally never set a root password on this system, although I tried to tell CUPS I had one. Maybe this confused it? 

This happens with 2.6.29-9-generic and 2.6.29-7-generic. It also happens if I boot a LiveCD and chroot to my usual filesystem.

---

### Post by mould on 2009-01-29
Hooray, I can log in again now :) 
dmesg showed that the segfault was in pam_smbpass.so. 
Removing the libpam-smbpass package fixed the problem for me.

---

### Post by metlhead05 on 2009-01-30
> **mould said:**
> Hooray, I can log in again now :) 
dmesg showed that the segfault was in pam_smbpass.so. 
Removing the libpam-smbpass package fixed the problem for me.

I'm glad that you figured that out. I'm sure that you will help someone that has this problem. I just backed up all my stuff and reformatted.

Thanks for everyone that posted some help messages!

---

### Post by spaetz on 2009-02-13
So how do you remove a package when you cannot become root anymore? I have exactly the same problem, but as sudo/su doesn't work anymore and I never set a root passwd (stupid ubuntu policy BTW), I cannot login as root and remove packages...

---

### Post by mould on 2009-02-13
So you have this login problem too? Someone should file a bug report I guess.
If you had set a root password it wouldn't help you because you can't log in as root either. 

To remove the package, you have to boot into recovery mode. If you have set a root password though, this won't work - you have to boot a LiveCD and chroot to your filesystem instead.

---

### Post by grambo on 2009-03-09
another dead one here...  ASUS EEE box, failed trying to manage (rename) a CUPS printer...  (The EEE box has no cd rom drive, I did a network install from a USB stick 2 months back)

same seg fault on successful password entry, proper access denied on bad password, ssh'ing in doesn't work, su seg faults, sudo's password challenge seg faults, but my automatic GDM login does work...  but I cant apt-get remove/install/upgrade anything since the su and sudo seg faults are there.  any thoughts/recommendations?

I don't really want to go back to FreeBSD, but...
](*,)

oh yah, I lost the cool Ubuntu skin to the GDM, it's fallen back to the basic blue Gnome skin, not sure if that is a clue to anyone.

---

### Post by grambo on 2009-03-17
got it, hit 'esc' during boot, fired up a recovery console, "apt-get remove libpam-smbpass" and it's all good.
\\:D/

...should this be bug reported to libpam-smbpass, or to cups?

---

### Post by Feanor's Curse on 2009-04-07
Thanks, the workaround really was helpful. Anyway, I filed a bug report at [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/356851](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/356851)

---

