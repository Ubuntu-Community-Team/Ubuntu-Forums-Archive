---
title: "Changing schools PCs from Windows domain to Ubuntu?"
date: 2007-05-14
forum: Education &amp; Science
---

### Post by daniel_szollosi-nagy on 2007-05-14
Hi there!

I'm a sysadmin for a small high school in Budapest, Hungary, with about 200 students. Being a recent convert to Ubuntu, I'm now looking at rolling out Ubuntu to run parallel with our currently used Windows XP installations, with a view of eventually replacing them. The latter is going to be the hard bit, so at first let's go for dual booting and see how that turns out. We're running an Active Directory domain and the Ubuntu users would either need to authenticate to that or have some other means of using the same login across multiple machines.

As we are talking about 50 PCs in total, I would not much like to tweak every single one of those machines by hand, so my first question is about mass deployments - is there something similar to Symantec Ghost for Ubuntu, where I can take a single machine and just clone it to the other fifty? Then again, I'm sure they'd break Ubuntu less often than Windows, so a complete reinstall would not be required that often. 

Are there any tools for centrally managing software installs, system upgrades and users? There are some applications that the teachers would be allowed to access, but not the students. I have no doubt that the Group Policies would not work in Ubuntu, but is there something similar? I'm not much for restrictions, but we've got to have a few. I'm looking at Wine for running legacy Windows apps, so my other concern would be restricting what Wine would run.

The second question is about logins. When I was in college we used AIX and could log in to all Unix machines with the same login. I'm sure such a facility exists in Ubuntu, I just don't know how to get it done. I've seen that it is possible to join an Ubuntu machine to an AD domain, so I'm not worried about that, but if I don't have to use AD then I'd rather not. I also noted that file and directory access with SMB is pretty straightforward, so that's not an issue for me either. 

Come to think of it, these are pretty much the same questions that would be applicable to a small business transitioning from a Windows environment to Ubuntu, so I'm not even sure if this is the right forum. Pointers to other threads with similar information would be much appreciated, there is no need to replicate all that info here if it exists elsewhere. Right now I don't even know where to start looking, or what for.

Thanks,

Daniel

---

### Post by calraith on 2007-05-14
Hello Daniel,

For a Linux equivalent to Norton Ghost, have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=405796").  Clonezilla is probably your best bet.

For software deployment, I don't have any first-hand experience with any software in particular, but [OCS Inventory NG]("http://www.ocsinventory-ng.org/") looks promising.

I'll be highly interested to watch this thread and see how it develops.  I think other people's answers to your questions will benefit me as well.

---

### Post by daniel_szollosi-nagy on 2007-05-14
Thanks calraith, Clonezilla and OCS Inventory do look quite promising. I'll poke around with them for some.

---

### Post by calraith on 2007-06-01
I'm kind of disappointed nobody else has offered any suggestions for this thread.  Hey Daniel, how have your experiences with Clonezilla and OCS Inventory NG been?  Any interesting stories about the switch from Windows to Linux?  Any bureaucratic obstacles with the switch?  I work at a state university, and... well, apparently Microsoft's sales reps have done their jobs well at my school, to say the least.

---

### Post by calraith on 2007-06-12
[IMG]http://imgred.com/http://fotofon.cathexes.net/archives/bump02.jpg[/IMG]

---

### Post by jviscosi on 2007-06-12
Hi Daniel,

Maybe you'd want to have a look at Edubuntu ([http://www.edubuntu.org/Home](http://www.edubuntu.org/Home)).  It's supposed to include centralized management of the type you suggest.  I haven't actually used it but I'm sure someone on the Edubuntu list could help you out.  It also seems to come with a lot of applications that may be geared to younger students than yours, but you don't have to use them.  

I have a small Mandriva network set up in my wife's classroom (I used to use Mandriva ... sorry!), three old laptops and an old desktop "server" doing directory sharing with NFS (Samba didn't want to work for this) and printer sharing with Samba.  The students all share a single "student" login, while the teachers use a "teacher" login.  After fussing around with various desktops and window managers I ended up using Fluxbox on all the machines, because it's a simple matter to copy the .fluxbox directory to each one and then all the settings are identical.  Also, it's relatively easy to lock down something like Fluxbox, vs. a desktop like KDE or even some of the more complex window managers.  The students have a custom Fluxbox menu, with no access to the terminal or "run" command, that keeps them from executing anything they shouldn't.  Of course, crafty students could access one of the other sessions with ALT-F1, F2, etc. (or whatever the key combo is), but that hasn't happened.  They're little kids and not all that sneaky, and besides, they wouldn't have much fun with just a command line.  High schoolers may be a little more ingenious.

I don't do frequent updates to the computers, mainly because my wife doesn't want me messing with them during the school year lest they break (they never do, unlike the Windows 98 machines in other classrooms), but when I do I run rpmdrake on them individually.  Obviously this wouldn't scale well.  It would probably be possible to schedule updates on the machines using cron or something, but it sounds like you want a centralized push, which I don't know how to do.  Perhaps Edubuntu has something.

Well, this probably hasn't been overly helpful, but anyway, that's my two cents or Euros or whatever.  Good luck!

Jim
[http://www.jamesviscosi.com](http://www.jamesviscosi.com)

---

### Post by elst on 2007-06-12
Cloning isn't really necessary on Linux - you simply set up a central package repository on a server, and use the "answer file" functionality to automate the installation so that it pulls the correct packages and configures the system as you like (Ubuntu supports Red Hat-style Kickstart answer files, and you can install a graphical tool to generate them). With PXE boot you don't even need a boot disk.

The big deployments either use thin client technologies to avoid needing to manage client configurations, or a management system (cfengine, Puppet etc.). These can handle software packages and configurations, but require you to spend a bit of time setting them up. Some places install applications into directories on servers, and then use NFS to mount those directories on clients.

For Group Policy-style user settings management, there's Kiosk for KDE and Sabayon for GNOME (not yet mature). They don't provide a configuration server and aren't as powerful as AD - they just let the desktop environment configure itself from files made by administrators.

If there is already an Active Directory on-site then you can use Winbind to let the Linux systems join the AD domain as members.

I think that WINE is an important project, but I wouldn't yet rely on it to provide for non-technical users - even small glitches that a technical user would shrug off can be show-stoppers for ordinary folks. Some people run Windows applications on a Windows Server using Terminal Services, and then configure the Linux desktops to access them with rdesktop etc.

Basically, you have to assemble your own solution from several different products - unfortunately there is no all-in-one answer, or cookbook that tells you how to do it (yet).

---

