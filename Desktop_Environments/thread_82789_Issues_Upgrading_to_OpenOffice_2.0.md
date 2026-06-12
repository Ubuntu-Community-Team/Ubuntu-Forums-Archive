---
title: "Issues Upgrading to OpenOffice 2.0"
date: 2005-10-27
forum: Desktop Environments
---

### Post by ronmarley1 on 2005-10-27
Hi Everybody,
I am running Breezy on an IBM R51.  I have upgraded to OpenOffice 2.0 from 1.9X.  When I try to open a file from a Windows share (a file on a Windows server) I get a window that says, "Can't Display Location" in the window title bar and in the window, the message, *Couldn't display "smb://polaris.edu%3Brgoodwin...oodwin/Presentations/OSBA.ppt".*If I go in and change the Open With... back to OpenOffice 1.9X, I am able to open the files on the Windows share again.  If I COPY the files from the Windows share to my laptop, they open fine.  I just can't seem to open them from the Windows share by double clicking with OO 2.0.  Before upgrading from 1.9X to 2.0, I did not have issues.
Thanks,
rg
PS, I hope I posted this in the right forum.  If I did not, I'll delete and move.
Thanks,
New Linux User

---

### Post by ronmarley1 on 2005-10-27
[QUOTE=ronmarley1]Hi Everybody,
I am running Breezy on an IBM R51.  I have upgraded to OpenOffice 2.0 from 1.9X.  When I try to open a file from a Windows share (a file on a Windows server) I get the message, *Couldn't display "smb://polaris.edu%3Brgoodwin...oodwin/Presentations/OSBA.ppt".*If I go in and change the Open With... back to OpenOffice 1.9X, I am able to open the files on the Windows share again.  If I COPY the files from the Windows share to my laptop, they open fine.  I just can't seem to open them from the Windows share by double clicking with OO 2.0.  Before upgrading from 1.9X to 2.0, I did not have issues.
Thanks,
rg
PS, I hope I posted this in the right forum.  If I did not, I'll delete and move.
Thanks,
New Linux User[/QUOTE]

Hi Again,
If I can't fix this issue, is it really worth the upgrade to 2.0?  I have not really noticed a difference between 1.9X and 2.0.  Reverting back would not be hard.  I'm just wondering if this is worth the trouble to upgrade.
Thanks,
rg

---

### Post by drigloi on 2005-10-27
I think this is not an OO.o bug.

E.g you won't start movies with mplayer from a Samba share. And the problem you've described is there with OO.o 1.1.x and 1.9.x too.

I think this is a Nautilus issue - it somehow forward bad URL syntax to the applications.

You can fix this if you doesn't connect to your shares through the Nautilus-smb:// way. You should "sudo apt-get install smbfs" and mount your shares from your fstab/terminal. This way opening things will work.

---

### Post by djjuice on 2005-10-27
i uninstalled openoffice 1.9 before installing 2.0 and it worked.. uninstalling 1.9 removes some files not required in 2.0 like the debian-files. uninstall every open office you have installed.. and try again

---

### Post by ronmarley1 on 2005-10-27
[QUOTE=drigloi]I think this is not an OO.o bug.

E.g you won't start movies with mplayer from a Samba share. And the problem you've described is there with OO.o 1.1.x and 1.9.x too.

I think this is a Nautilus issue - it somehow forward bad URL syntax to the applications.

You can fix this if you doesn't connect to your shares through the Nautilus-smb:// way. You should "sudo apt-get install smbfs" and mount your shares from your fstab/terminal. This way opening things will work.[/QUOTE]

Hi drigloi,
I thought it would be a Nautilus issue also, but it does seem to work if I open the files with OO 1.9X.  Thanks for the reply.  I'll give it a whirl and see what happens.
rg

---

### Post by ronmarley1 on 2005-10-27
[QUOTE=djjuice]i uninstalled openoffice 1.9 before installing 2.0 and it worked.. uninstalling 1.9 removes some files not required in 2.0 like the debian-files. uninstall every open office you have installed.. and try again[/QUOTE]

Hi djjuice,
I'm gonna give this a try and see what happens.  I'm just afraid that if I remove 1.9X and it does not fix the issue, I'd then nned to remove 2.0 and reload 1.9X.
Thanks for the reply.
rg

---

### Post by ronmarley1 on 2005-10-27
[QUOTE=ronmarley1]Hi djjuice,
I'm gonna give this a try and see what happens.  I'm just afraid that if I remove 1.9X and it does not fix the issue, I'd then nned to remove 2.0 and reload 1.9X.
Thanks for the reply.
rg[/QUOTE]

Hey djjuice,
You are the man!  Somtimes I don't see the forest for the trees.  I uninstalled 1.9X and reinstalled 2.0 and everything works great!  Thanks so much for helping a new linux user.
rg

---

