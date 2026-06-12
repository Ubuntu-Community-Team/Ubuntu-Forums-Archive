---
title: "Help me with a crashed system"
date: 2009-01-15
forum: General Help
---

### Post by Dakillakan on 2009-01-15
Alright, I have used Ubuntu for a little bit, and my computer has just crashed hard.  I was fiddling around with packages in the terminal and I am worried I did something bad.  Did a recovery boot and it was able to load the command promp but when it got to the login screen It would cycle between loading that and going back to the boot text with no progress.  Thanks you in advance, I have a Dell inspiron e1505

---

### Post by blazemore on 2009-01-15
If you go to recovery mode, go to a root prompt, and type
```
startx
```
what happens?

---

### Post by mssever on 2009-01-15
> **blazemore said:**
> If you go to recovery mode, go to a root prompt, and type
```
startx
```what happens?
That's bad advice. Don't follow it. There's no reason to run X as root. Instead, look at the file ~/.xsession-errors for error messages. (You can use less to do this.)

---

### Post by blazemore on 2009-01-15
Excuse me!
That is NOT bad advice.
If it drops back to the terminal with errors, which I expect it will, he can tell us what the errors are, which can help diagnose the problem.
If it works, well don't use it! You'll be running in "Windows Mode" where any program can do anything to any part of your system.

---

### Post by Dakillakan on 2009-01-15
Sorry for following all lines of advice but startx yields 
(EE) intel (0): I830 Vblank Pipe Setup Failed 0
(EE) intel (0): I830 Vblank Pipe Setup Failed 0
.FreefFontPath: FPE "/usr/shar/fonts/x11/misc" refcount is 2, should be 1; fixing.

As for the other sugestion, how does one navigate to that file? cd ~?

---

### Post by blazemore on 2009-01-15
> **Dakillakan said:**
> how does one navigate to that file? cd ~?

msserver, I rest my case.

However, there's a bug on launchpad, and a possible solution seems to be turning off gnome screensaver.
So if this is the right package name:
```
apt-get remove gnome-screensaver
``` from the recovery terminal.

Someone correct me if I'm wrong.

---

### Post by mssever on 2009-01-15
> **blazemore said:**
> Excuse me!
That is NOT bad advice.
If it drops back to the terminal with errors, which I expect it will, he can tell us what the errors are, which can help diagnose the problem.
But that can be done as a normal user, not as root. In fact, some errors are caused by user settings and so would not be reproducible by root. In any case, it's never necessary to run X as root.
> **Dakillakan said:**
> As for the other sugestion, how does one navigate to that file? cd ~?
~ is an abbreviation for your home directory. So you can do ```
less ~/.xsession-errors
## Or, if you're running as root in recovery mode:
less ~yourusername/.xsession-errors
```> **blazemore said:**
> msserver, I rest my case.How does the fact that the OP didn't understand my command line suggestion prove that running X as root is a good idea?

> However, there's a bug on launchpad, and a possible solution seems to be turning off gnome screensaver.
So if this is the right package name:
```
apt-get remove gnome-screensaver
``` from the recovery terminal.

Someone correct me if I'm wrong.What makes you think that gnome-screensaver is at fault? There are lots of things that can cause the symptoms described. It's best to do some troubleshooting before recommending that the OP uninstall random packages that they just might find useful. We don't have enough information yet to diagnose the problem.

---

### Post by blazemore on 2009-01-15
> **mssever said:**
> some errors are caused by user settings

Exactly, so if it worked as root, we would have known it was that.

> **mssever said:**
> What makes you think that gnome-screensaver is at fault?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/160309/comments/3](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/160309/comments/3)

---

### Post by Dakillakan on 2009-01-15
Did the apt-get remove and returned with this error
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_set_translation_domain 
dpkg: error processing gnome-screensaver (--remove):
  subprocess pre-removal script returned error exit status 127 
Errors were encountered while processing:
  gnome-screensaver
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Dakillakan on 2009-01-15
The  ~/.xsession returns this error
x-session-manager: symbol lookup error: /usr/lib/libgdk-x11-2.0.so.0: undefined symbol: g_once_init_enter_impl
/root/.xsession-errors (END)

---

### Post by blazemore on 2009-01-15
Wow what did you DO to get it like this?

---

### Post by mssever on 2009-01-15
> **blazemore said:**
> Exactly, so if it worked as root, we would have known it was that.I'd rather diagnose that through error messages than through running X as root.

> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/160309/comments/3](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/160309/comments/3)
OK. I somehow missed the OP's earlier post containing error messages.
> **Dakillakan said:**
> Did the apt-get remove and returned with this error
gconftool-2: symbol lookup error: gconftool-2: undefined symbol: g_option_context_set_translation_domain 
dpkg: error processing gnome-screensaver (--remove):
  subprocess pre-removal script returned error exit status 127 
Errors were encountered while processing:
  gnome-screensaver
E: Sub-process /usr/bin/dpkg returned an error code (1)
Looks like the package manager is broken, as well (the two problems could easily be correlated). I don't know how to fix that, though.

---

### Post by Dakillakan on 2009-01-15
I hope I did not scare you guys away

---

### Post by mssever on 2009-01-15
> **Dakillakan said:**
> I hope I did not scare you guys away
Nope. I'm just stumped.

Oh, here's a wild idea that might be worth a try. I noticed that some of your error messages have to do with translation. Is your system set up for some language other than US English? If so, try typing ```
export LANG=en_us.UTF-8
```then re-trying apt. The first thing to try would be something like ```
sudo aptitude update
``` Then try other stuff as relevant. It might be that some of your language settings or gettext is hosed. Whether that explains your X problems I don't know. And even this suggestion is a bit of a long shot.

---

### Post by PartickThistle on 2009-01-15
mssever,  don't be a tool all your life.

Dakillakan,  it appears you've either been playing about with VMWare or have removed some X and/or Gnome libs.

Are you getting into your desktop environment?

I'm assuming no due to the error.

I recommend re-installing these packages (assuming 8.10)

libx11-6
libgtk2.0-0

Good luck.

---

### Post by Dakillakan on 2009-01-15
I tried all of these things to no avail.  The sudo apt update worked but did not accomplish anything.  Please help.  And no I can not get into the x environment,  I get to the spinny loading button that usually pops up before the login, and then it cuts out again to the boot screen and from then on it cycles.

---

### Post by mssever on 2009-01-15
> **Dakillakan said:**
> I tried all of these things to no avail.  The sudo apt update worked but did not accomplish anything.  Please help.  And no I can not get into the x environment,  I get to the spinny loading button that usually pops up before the login, and then it cuts out again to the boot screen and from then on it cycles.
So you successfuly uninstalled gnome-screensaver as you started to try? Also, please post the contents of /var/log/Xorg.0.log. I'm hoping to find something else to try, although the information you've posted already might point to the problem (in which case, I don't know how to solve it).

---

### Post by blazemore on 2009-01-16
So you can get to the login window?
If you click Sessions, then choose Failsafe Gnome (or similar) does that let you log in? If so it might be a problem with user settings.

If you CAN log in, I'd recommend making a new user, and copying all your files across. It's the only *sure* way to be rid of user settings problems.

---

### Post by Dakillakan on 2009-01-16
When I /var/log/Xorg.0.log I get permission denied even though I am root.  If it helps I was unpakaging gtk and ran this string  
R CMD INSTALL gtk_0.3-0.tar.gz   That seemed to be when everything stoped working.

And no I can not get to the login screen, just the few seconds before and then it crashes.
I did not unistall the screensaver, that came with an error but the
libx11-6
libgtk2.0-0 
both replied that they were already installed.

---

### Post by mssever on 2009-01-16
> **Dakillakan said:**
> When I /var/log/Xorg.0.log I get permission denied even though I am root.
That's because you have to use some program to open a file. Try ```
less /var/log/Xorg.0.log
```
> If it helps I was unpakaging gtk and ran this string  
R CMD INSTALL gtk_0.3-0.tar.gz   That seemed to be when everything stoped working.
That's probably relevant information, but what command did you run? You didn't run the command you just gave, because that's an invalid command and just would have given you an error (unless you have R installed, in which case I have no idea what would happen--though I presume you'd still get an error).

In the future, you should install stuff from .debs whenever possible. Plus, you already have GTK, so there's no need to install it from source. Plus, the current version of GTK is 2.14, or maybe higher. So GTK 0.3 is really outdated.
> I did not unistall the screensaver, that came with an errorThe same error you reported earlier, even after setting $LANG?
> but the
libx11-6
libgtk2.0-0 
both replied that they were already installed.
We already knew they were installed. You were asked to to **re**install them. ```
sudo aptitude reinstall libx11-6 libgtk2.0-0
```

---

### Post by Dakillakan on 2009-01-16
I tried the less and there is pages of details, do you want me to copy it all or were you looking for something specific.  Also when I attemept to reinstal the libx11-6 I get this error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libx11-6 2:1.1.1-1ubuntu4
   Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxll/libx11-6_1.1.1-ubuntu4_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxll/libx11-6_1.1.1-ubuntu4_i386.deb:) COuld not resolve 'us.archive.ubuntu.com?'
E: Internal Error, ordering was unable to handle the media swap
then it runs the recover stuff   
Also the same error occurs when apt-get removing the screensaver

---

### Post by mssever on 2009-01-17
> **Dakillakan said:**
> I tried the less and there is pages of details, do you want me to copy it all or were you looking for something specific.It's just a stab in the dark, so I don't know what I'm looking for. Better post it all.  Be sure to paste it in [noparse]```

```[/noparse] tags to that it stays readable.> Also when I attemept to reinstal the libx11-6 I get this error
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libx11-6 2:1.1.1-1ubuntu4
   Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxll/libx11-6_1.1.1-ubuntu4_i386.deb:](http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxll/libx11-6_1.1.1-ubuntu4_i386.deb:) COuld not resolve 'us.archive.ubuntu.com?'
E: Internal Error, ordering was unable to handle the media swap
then it runs the recover stuff   
Also the same error occurs when apt-get removing the screensaverTwo separate errors here. First, apparently you aren't connected to the Internet. If you're running wirelessly, you might have to plug into a wired connection for now.

The second error is a bit of a mystery. I Googled it anddidn't come up with much of value, except that it appears to have something to do with the CD.

It seems that your machine has some deep problems indeed.

EDIT: By the way, what do you mean by "recover stuff"?

---

### Post by Dakillakan on 2009-01-17
Hey, I dont know if this helps but i could boot from the cd

---

### Post by upchucky on 2009-01-17
if u can boot from the cd, and you do not have data that u care about then delete the ubuntu partiton, and reinstall.

if u have data u want to save then back up the /home directory, say to a usb or cd rom, delete the partition and reinstall. see knoppix below, it can save and back up u data from its live cd tools.

if u want to troubleshoot the installed system as is then get advanced supergrub to fix the mbr, (just in case u hose it during experiments).

also get knoppix to be able to edit, delete, create partitions, xorg and menu.lst files on the unresponsive system. the reason i suggest knoppix is cause there are rare instances where both partition editors are needed so it is best to have both on hand. and knoppix can fix windows system too.

i suspect that the repositories were set to wrong dist and sites, and the original problem was the xorg file. if my suspicions are true the above will fix it.

and the biggest error was in running x as root and uninstalling gnome. the additional errors just added to the confusion which is why that advice was bad.

I am surprised that the learned posters did not ask to confirm the pc specs, the dist, the xorg settings and did not even ask for the repository settings. when the failures came up.

the op did not post machine specs or distribution, this is important troubleshooting info.

there is a good possibility now that the pc is badly borked enough now that a clean install is a faster choice. u will notice i said faster not better, although personally i would troubleshoot it to learn more. i suspect the op wants to get this working as fast as possible. it is up to the op to decide which way to go. every linux install can be repaired without a reinstall, but it can be a time consuming task. so in this case faster may be the better way to go.

---

