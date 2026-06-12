---
title: "Permissions broken from changing user's group"
date: 2006-05-18
forum: Desktop Environments
---

### Post by a_guerere on 2006-05-18
Hello, i've unfortunately changed my ubutu's primary user group and now i can't view nor modify any files beyond the user's home directory. Not even sudo works any more and the root account was never "activated" on this machine, so it has no password and can't login.

Any ideas or clues on how to fix this?

Thanks!

---

### Post by tonyr on 2006-05-18
You can fix this if you have an install cd (or even a Live CD, but I don't know
how to use that).  You will need to be familiar with using the command line.
If you aren't, (there is no gui for this kind of recovery), say so, and I'll
post a list of commands.   

I'm describing this from memory, and I use Dapper instead of Breezy, so
what you see on the screen may be slightly different word-wise, but
I think the general flow of things is the same.

Boot from the install cd and choose **[COLOR="Red"]rescue[/COLOR]** mode.
Let the process go on.  If it tries to establish a network connection and can't,
don't worry, it doesn't matter.  It should eventually offer you a list of partitions,
asking you which one to mount on "/" (root).  You will need to know which ione this
is for your system.  After that it should offer you a list of things to do.  Choose
"Enter shell on root partition".  

At that point you should get a shell prompt, and you are root user.  
Change directory to /etc and edit the file **group**.  Find the line
starting with **admin:** and add your user name after the last ':'
(no spaces).  

That should be enough to get **sudo** back for you.  Remove the install CD and reboot.  You will need to add yourself to some other groups as well, but
I'll have to get that list and post it later on.

---

### Post by a_guerere on 2006-05-18
Thanks tonyr for your very fast reply. I am doing it in a moment, i'll let you know if it worked.

Thanks again.

---

### Post by tonyr on 2006-05-18
Well, I just discovered that if you are using the Breezy release instead of
the Dapper release, my instructions are all wrong because the Breezy
installation startup is completely different.  I put in my old Breezy 5.10
install CD, and I haven't yet figured out the way to do the same thing there.

---

### Post by a_guerere on 2006-05-18
Tonyr, i couldn't edit the file from breezy's rescue shell, but instead started a breezy live cd, mounted the partition and edited /etc/group file as you said. It worked flawlessly that way, and now i can use sudo :D :D :D 

Thanks for your expertise.

I will not hesitate to write here when i need help again.

Thank you all.

---

### Post by tonyr on 2006-05-18
You are most welcome, and I am glad to provide a good experience for you
in these forums.

In my earlier post I said that there were other groups that you needed also,.
When you first installed Breezy, the installation process added you to a lot
of groups so that you could be the administrator of your system.  Here is
a list of groups that show up on my Dapper installation:
> 
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin


You should add yourself back to these groups also, either with an editor as
you did before, or with **System->Administration->Users and Groups**. Under the
**Groups** tab, select a group, select your userid from the **All users:** list,
and select **+Add**.

Don't worry if not all of the groups show up in the group list.

---

