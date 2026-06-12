---
title: "ssh deamon configuration, I dont want users out of their directory"
date: 2005-12-24
forum: General Help
---

### Post by danf_1979 on 2005-12-24
Hi folks.
Thats right, when you loggin via ssh to a host, normally you can do a "cd .." and get out of your directory and if you are curious enough go and check some other users directory and files. I want to completely disable this capability in ssh.
Somebody knows how to do it?
Many thanks.

---

### Post by briancurtin on 2005-12-24
you could set every users's home directory to have the following permissions set, denying everyone else 
```
chmod -R o-rwx /home/danf_1979
```

that would deny all others read, write, and executable access to any files in or under the home directory

---

### Post by zoiks on 2005-12-24
[QUOTE=danf_1979]Hi folks.
Thats right, when you loggin via ssh to a host, normally you can do a "cd .." and get out of your directory and if you are curious enough go and check some other users directory and files. I want to completely disable this capability in ssh.
Somebody knows how to do it?
Many thanks.[/QUOTE]

I could be wrong, but there may be no easy way to do this.  The problem is that ssh normally gives a user all their normal permissions as if they had logged in with a physical terminal.  There are a lot of files in the system that are readable, writable, and/or executable by any of the system's users, and normal ssh connections just give you the normal user's rights.

I have managed to run sshd in what is called a "chroot jail" which has this capability, but doing this is *not* for the faint of heart.

Theoretically, you could also set up groups and group permissions on the system that might get you what you want, but this could mess up the way your system works and take a long time to get right.

If you could list the specific reasons or resources that you want protected, it might help; there might be some simpler workaround for what you need.  For example, if you are just worried about one user accessing another user's files, you can use "chmod -R go-rwx" on the individual users' home directories to take away the loose permissions.  Then, change each user's umask to 0700 to ensure that any new files that the users create are not accessible to other users.

---

### Post by danf_1979 on 2005-12-24
Ok, I'm configuring a web hosting server, and I dont want my clients seeing other clients directory and files... they could see each others database passwords! (i.e. config.php in php-nuke or postnuke, etc)
I think I'll go with the chroot stuff.
Any useful links?
I'll check google and post results in here.
Thanks.

---

### Post by danf_1979 on 2005-12-24
I can't take out read permissions to group "others"... then the web would be not available.  :(
"home" directories are in /var/www/

---

### Post by zoiks on 2005-12-24
[QUOTE=danf_1979]Ok, I'm configuring a web hosting server, and I dont want my clients seeing other clients directory and files... they could see each others database passwords! (i.e. config.php in php-nuke or postnuke, etc)
I think I'll go with the chroot stuff.
Any useful links?
I'll check google and post results in here.
Thanks.[/QUOTE]

Ikes!  Doing a chroot ssh isn't as easy as it sounds.  I did it about 1 1/2 years ago, but it's a challenge.  One of the things you'll have to do is copy over all the binaries, libs, config files, etc. that the user's going to need into the user's home directory.  You'll also need to make sure the sshd is compiled with chroot support.  I didn't take good notes on how I did it, but you can google around for some good information on this.  But again, it's not for the faint of heart, so...

Also, it still doesn't necessarily solve the problem of users accessing each other's files.  You may be able to set it up so that you are chrooted into a users home when they log in, but normally sshd will just sit there and run in a chroot environment waiting for someone to log in.  That's a little different.

I am not recommending you actually do this now.  I don't think it'll really solve your issue, and it's a lot of work.  I think you should just manage the permissions on the files you're worried about.

If you are simply worried about people looking at other's php passwords, you could just make sure that those files are chmodded "go-rwx".  You can also have a directory in the user's home directory that is chmodded the same way, so that any file that's in there remains private.

---

