---
title: "Accidental chmod permissions of File System to user name"
date: 2009-03-16
forum: General Help
---

### Post by Daft Apeth on 2009-03-16
I've had a read through the forums and have found quite a few similar threads (which mostly seem to suggest a full reinstall), but nothing quite the same.

Basically it's another variation on the "I've accidentally changed all the permissions" problem.

I was in the directory "username@computername:~Desktop/a_folder$" and all the permissions of and within "a_folder" were set wrong. What I was trying to do was to set all the subfolder permissions to my username.

Thinking I was "already in that directory", so it would only apply from that point onwards, what I've actually done is something along the lines of a :

sudo chown USERNAME /*/* 

I meant "within this folder that I'm already in". It didn't realise this, of course. It went by what I actually told it to do, rather than what I was thinking. I also realise since that I should have been using the -R to adjust the subfolders etc (I was half thinking in DOS terms, where * would cover everything within). Thankfully I only realised this after making the error.

It doesn't seem to have done the whole system, it's literally done the "second layer" of all the folders. All files and folders beyond that are as normal. There's a pattern of things belonging to me and belonging to root, which is something like :

/folders(root)/files and folders(me)/files and folders(root)

For example, "boot/grub/menu.lst" is alternately owned by "root/me/root".

Most notably so far is that sudo responds with the line :

"/etc/sudoers is owned by uid 1000, should be 0"

The permissions for "sudoers" is currently :

Owner : USERNAME (cannot change)
Access : Read only (can change)
Group : Root (can change)
Access : Read-only (can change)
Others Access : None

In short form, everything which lays two directories deep is owned by my username. I can't change them back because sudo doesn't work. My username is the only account on the system at present.

So, the question is whether I can :

a) Boot into recovery console as root, reset "sudoers" to root, then reset all those second layer permissions to root again?
b) No I can't. I have to reinstall everything from scratch.
c) No. Just give up and use Windows. You're so poor at this that you got the command wrong and couldn't even manage to ruin your whole file system properly.

Any advice would be very welcome.

---

