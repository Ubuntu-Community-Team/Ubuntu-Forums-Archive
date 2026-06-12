---
title: "sudo works in BASH but not KDE GUI"
date: 2005-12-02
forum: Desktop Environments
---

### Post by beama on 2005-12-02
expert install on Compaq laptop Presario 700 so that I may dual boot with XP Pro.
I can use sudo in BASH sucessfully but if I try and go into administrator Mode in KDE I get a comincation error.

I noticed that in expert install mode Root account is enabled, compared to using the default install Mode (press enter on the boot screen) in which the root account is disabled.

I have tried using the "sudo passwd -l root" which disabled the root account but did not change the behavoir of the KDE GUI administration utilities so I have since re-enabled root.

Any ideas this is annoying me but not a problem because I can use Bash if I have to.

The reason I installed Kubuntu is because Ubuntu (Ghome version) did the same but worse

---

### Post by codejunkie on 2005-12-02
[quote=beama]expert install on Compaq laptop Presario 700 so that I may dual boot with XP Pro.
I can use sudo in BASH sucessfully but if I try and go into administrator Mode in KDE I get a comincation error.

I noticed that in expert install mode Root account is enabled, compared to using the default install Mode (press enter on the boot screen) in which the root account is disabled.

I have tried using the "sudo passwd -l root" which disabled the root account but did not change the behavoir of the KDE GUI administration utilities so I have since re-enabled root.

Any ideas this is annoying me but not a problem because I can use Bash if I have to.

The reason I installed Kubuntu is because Ubuntu (Ghome version) did the same but worse[/quote] you have to add your name to the sudoers file. you can do that like this, in a terminal gain root acess with su
and enter this command
```
export EDITOR=kate && visudo
``` and add this to the bottm of the file
yourusername ALL=(ALL) ALL
save and exit kate hope this helps.

---

### Post by beama on 2005-12-02
thanks Ill give it  a shot
I use vi so ill export to that
That got rid of the error messages but
It still does not give me sufficent privalages to adjust the settings ie
if I go into the administrator mode to adjust clock settings even though my password is now accpeted im still denied rights to change settings ( everything still greyed out).

---

### Post by codejunkie on 2005-12-03
[quote=beama]thanks Ill give it  a shot
I use vi so ill export to that
That got rid of the error messages but
It still does not give me sufficent privalages to adjust the settings ie
if I go into the administrator mode to adjust clock settings even though my password is now accpeted im still denied rights to change settings ( everything still greyed out).[/quote]
you could try creating a new link to an application and use this as the command 
```
kdesu kcontrol
``` this will let you change system settings as root.

---

### Post by beama on 2005-12-03
that kdesu is handy thank you codejunkie for your help.
 I think I've found the problem with sudo, while in kcontrol I noticed that the sudo service was not running but was tagged to start on startup. Investerigating that now. Oh btw the kdesu kcontrol wouldnt run from a shell so I used the run applet in kde worked great not only on kcontrol but also other areas I was having trouble with (adept) Looks like Im in for hours of fun here:D

---

### Post by beama on 2005-12-03
I had trouble with sudo. I was provided a workable work a round, but during my ventures around kcontrol  I noticed that the Sudo service is marked to start  on system boot but  was not running. Attempts at  starting this service seems to hang ie looking endlessly at start service dailog.

I believe that because this service is not running, is proberly the root of my earlier problem.

Any ideas on why and how to solve this.

---

