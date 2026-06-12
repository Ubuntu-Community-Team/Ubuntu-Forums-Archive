---
title: "$HOME/.dmrc isn't working"
date: 2009-03-02
forum: General Help
---

### Post by Sugi on 2009-03-02
I keep getting this error message at the beginning of my Ubuntu Startup.  Something about my HOME/.dmrc is being ignored.  How do I fix it?  I have also noticed some issuies with giving out premission to directories and files. 

"User's $HOME/.dmrc file is being igonred.  This prevents the default session and language from being saved.  File Should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Ubuntu Hardy Heron
[B]
My Fix[/B]:
sudo chown username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username /home/username 	
chmod 755 /home/username

Log out of your current session and back in. 
Rebooting is not necessary but will accomplish the same thing.

Sugi

---

### Post by sisco311 on 2009-03-02
[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by Sugi on 2009-03-02
Thank you, the link help me.

My Fix:
sudo chown username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username /home/username 	
chmod 755 /home/username

Log out of your current session and back in. 
Rebooting is not necessary but will accomplish the same thing.

Sugi

---

### Post by ScarySquirrel on 2009-03-03
I have tried the tutorial mentioned here, but my system still gives me this error.
My current setup is a bit eccentric, since I am mounting a ntfs partition as home.  However, when I copied system or hidden files to it, I made sure that their permissions were preserved by using the -a, -v, and -u tags in the cp command.

---

### Post by sisco311 on 2009-03-04
NTFS does not have unix-like ownership and permission systems. You can not change the permissions and owner/group of the files.

You set the ("fake") permissions at mount time with the umask, fmask and dmask and the owner and group with the uid and gid mount options. Once the partition is mounted you can not change the permissions of individual files.

So, it's not advised to mount an NTFS partition as /home. 

You can mount the partition in your home directory: /home/user/data or in the /media/data directory and symlink the content to /home/user:

e.g.:
/home/user/movies -> /media/data/movies
/home/user/music -> /media/data/music
...

```
ln -s -T /media/data/movies /home/user/movies
...

```

---

