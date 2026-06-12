---
title: "sudo problem with kubuntu"
date: 2005-09-04
forum: Desktop Environments
---

### Post by carlos1 on 2005-09-04
I just started using kubuntu, and most things work fine (at least my network card is recognized which it wasn't in FC4).
However, when I try to run synaptic, or configure network settings, it asks for the root password. 
For some reason it will not accept the root password and says that it is the wrong one. No matter what I try to sudo it is the same. 
I can log into the shell as "su" and the password works, but I can't launch synaptic as root from the shell, and I can't sudo. 
Literally if I just launch synaptic from the menu, I am prompted for the password, which it won't accept. 
Am I missing something about what I need to type in? 
Many thanks for any suggestions. 
BTW I am running it on Dell Inspiron 4100 if that makes any difference.

---

### Post by one_ro on 2005-09-04
If you said you use Kubuntu, then it should be kynaptic (instead of synaptic as in Gnome).
At my box it works w/o any problems:
$ sudo kynaptic
password: (this is where I type in [COLOR=Blue]**my**[/COLOR] password, as there is [COLOR=Blue]no root password[/COLOR] by default in Kubuntu)
And it should work like magic.
Please do that and tell us what you get.
hth

---

### Post by carlos1 on 2005-09-04
Thanks. 
I tried that with kynaptic and it said that I am not in the sudoers file.
Then I tried launching it from the menu, and typed in my user password, and it said it didn't recognize the password, then again, and it said 'conversation with su failed'. 
As a not when I set up the installation I did set up a root password separately, but I don't know if that makes any difference.

---

### Post by one_ro on 2005-09-04
[QUOTE=carlos1]Thanks. 
I tried that with kynaptic and it said that I am not in the sudoers file.
Then I tried launching it from the menu, and typed in my user password, and it said it didn't recognize the password, then again, and it said 'conversation with su failed'. 
As a not when I set up the installation I did set up a root password separately, but I don't know if that makes any difference.[/QUOTE]

That shouldn't happen with Kubuntu. AFAIK, the installation process does not ask for a root password and the regular user that you create IS by default a sudoer. I don't know what to say, have you installed your Kubuntu properly? Try installing it again, and btw what version you have?

---

### Post by carlos1 on 2005-09-07
Thanks. I have tried re-installing, and when I do a default install, it just has me set up myself as a normal user, as you say, but then when I log on and try to sudo I get the same message. 

i check the /etc/sudoers file and indeed I am not in it. It also won't let me edit the file, but I can view it (I don't know what to put in there, as the file is currently empty, but I tried entering something in, and it wouldn't save any changes). 

I even tried installing ubuntu instead of kubuntu, but have exactly the same problem. 

It's strange as can access internet, etc. Everything else works great, except for anything requiring root access. 

Can anyone shed light on this or point me in the right direction? I've tried everything I can think of at this point. 

Thanks.

---

### Post by carlos1 on 2005-09-09
bump...
I'm still trying to tackle this problem - can anyone advise?
Thanks.

---

### Post by shakin on 2005-09-09
It's quite weird that you're not in the sudoers file, but there is hope!

Easiest way is when you boot, go into the grup menu and highlight the kernel you want to boot into (the default is fine). Now press 'e' to edit that line. Add the word 'single' to the end of it, then continue the boot process.

This will dump you into single user mode, where you are root. Now edit /etc/sudoers with the 'visudo' command.

At the very bottom of the file you'll see where it says "Members of the admin group may gain root privileges." Below that it should real "admin  ALL=(ALL) ALL"

So, you need to be part of the admin group. Edit /etc/group and scroll down until you see the line that reads "admin:x:109:" (or something very similar... it starts with "admin"). Now add your name to the end so it looks like this: "admin:x:109:carlos1". Save the file, reboot, make sure "single" has been removed from grub, and when you get back to your desktop see if you can use sudo.

---

### Post by carlos1 on 2005-09-10
Thanks.
I tried this - in the sudoers file at the bottom it doesn't say "admin ALL=(ALL) ALL", but rather "root ALL=(ALL) ALL".
Also in /etc/group there isn't a user called "admin" but there is one called "admn". 
So, I changed the entry in sudoers from "root" to "admn". 
My user ID was already entered after "admn" in /etc/group. 
Unfortunately this didn't work. 
Maybe I should leave "root" in the sudoers file and add myself to the "root" group in /etc/group? 
Also what program should I use in single user mode to edit /etc/group? I used vim.

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=carlos1]bump...
I'm still trying to tackle this problem - can anyone advise?
Thanks.[/QUOTE]
Well, it is really weird it didn't set up your user in the /etc/sudoers file.  The best thing would probably be to boot into recovery mode (see [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) ), and add your user to the /etc/sudoers file.  If that doesn't work, maybe you could boot up with the live CD, mount your Ubuntu filesystem, and edit the file that way.

---

### Post by Gezzer on 2005-09-10
have u tried using

kdesu program name

in a konsole ...

---

### Post by agm642 on 2005-09-11
Edit /etc/sudoers using the visudo command. Under the line where it says "root ALL=(ALL) ALL", add "(username or group) ALL=(ALL) ALL"

---

### Post by carlos1 on 2005-09-12
Sweet! 
After adding my username under the "root" line in the sudoers file, I am up and running. 
Thanks to all who helped in this thread. Hopefully I can return the favour for others when I become more proficient with the distro. 
Now I just have to figure out how to configure apt (i skipped it during the install as it crashes the install for some reason). So, off to browse the online guides for that. 
carlos

---

### Post by snowjunkie on 2005-09-14
[QUOTE=carlos1]
Now I just have to figure out how to configure apt (i skipped it during the install as it crashes the install for some reason). So, off to browse the online guides for that. 
carlos[/QUOTE]

Hi Carlos,
The apt configuration was crashing my install as well.  It turned out to be a dodgey burn of the cd image.  I burned another cd and it worked smoothly.

---

### Post by bsussman on 2005-09-19
I think you might consider slowing down and approaching initial problems with more suspicion.
 
Install problems that are fixed by hand modifying files are very likely to indicate a serious problem with the installation process. The designers and implementers have not released a system that requires bit-fiddling.
 
 modifying security related files can result in unintended consequences.
 
 Now, OTOH, if you want to learn a great deal in a waaay to short time, be my guest :D

---

### Post by craig3612 on 2005-09-24
I don't know if you've given up and moved onto another distro or what, but this happened to me tonight as well.  There are a couple reviews of kubuntu that also complain of this happening.  

Fortunately, I did find a solution here:
[http://kudos.berlios.de/kf/kisimlar/useradmin.html#sudomore](http://kudos.berlios.de/kf/kisimlar/useradmin.html#sudomore)

Essentially, as root (using whatever means you have available to do so), you run visudo.  Then, assuming your username is craig (as is mine), you would append the following line to the file:

craig    ALL=(ALL) ALL

save the file, reboot and you should be good to go.

---

### Post by carlos1 on 2005-10-02
The fix that i mentioned above did work perfectly and I've had no sudo problems since then.
Since I couldn't access root normally, I just rebooted into recovery mode, then used the visudo command to edit /etc/sudoers, added "(my username) ALL=(ALL) ALL" at the bottom, saved and rebooted. 
Hope this works for others as well.

---

### Post by kikinovak on 2005-10-02
Hi,

I'm a Slackware veteran new to Kubuntu. Been giving it a try since this morning, and I like it. I had this sudo problem too, maybe because I chose an "expert" mode install. Anyway, my main user (kikinovak) wasn't automagically added to /etc/sudoers.

I just wonder: how's the above described hack, e. g. adding the user with visudo, in terms of security?

Cheers,

Niki Kovacs

---

### Post by bigredjew on 2005-10-13
I'm getting a strange error after attempting this fix... Now I can't access the /etc/sudoers file at all to edit it, even in recovery mode. It says something about a parse error in line 23 or something and goes back to the command prompt. Any advice, or should I just reinstall...? Is there a way to "upgrade" or reinstall without losing everything?

---

### Post by Chxta on 2006-10-24
Simple, go to the terminal, log in as root and type synaptic.

---

