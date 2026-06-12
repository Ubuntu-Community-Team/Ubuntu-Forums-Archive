---
title: "Allowing access to single folder"
date: 2009-03-25
forum: General Help
---

### Post by cchase88 on 2009-03-25
Hey everyone, I have a friend that I would like to let access a certain folder on my system through the use of ssh.

I have installed openssh and it seems to be working fine when I try ```
ssh localhost
```

Here is where I'm getting stumped.

The folder that I would like to let my friend access is a on a drive that is in the NTFS format. I've tried setting permissions to this folder, but I'm guessing that since the drive is NTFS, that's why it keeps reverting back to it's original state.

What I have done to counter this is create a symbolic link in his home directory that points to that folder on the NTFS drive.

What I would like to know is how can I make it so my friend cannot escape his home folder and only have access to the folder that I have specified.

---

