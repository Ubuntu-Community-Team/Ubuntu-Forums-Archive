---
title: "$HOME/.ecryptfs - CORRUPTED"
date: 2011-03-29
forum: Desktop Environments
---

### Post by nicolasdiogo on 2011-03-29
HI,

I had my $HOME full at one point and there was no error warning about it.

after deleting some files to make room.
and rebooting. i can no longer login using KDE.

i have run:

find $HOME/.Private/ -size 0c -exec ls '{}' \; | wc -l

and got:

203


which means that i have all these many ZERO size files in my private folder

i also noticed that my $HOME/.ecryptfs is corrupted.
but i am able to access all my files still.


i have no idea how to proceed here.

does anyone REALLY know what to do here?

as you can guess i am a little stressed out with this error. and hoping that i do not need to rebuild my $HOME from my previous backups.

thanks

Nicolas

---

### Post by nicolasdiogo on 2011-03-30
found the guilt part

nepomuk

here
[http://ubuntuforums.org/showthread.php?p=10617413](http://ubuntuforums.org/showthread.php?p=10617413)


i have recreated my 
$HOME/.ecryptfs

as a symbolic link to 
/home/.ecryptfs/$USER/ecryptfs

---

