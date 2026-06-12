---
title: "Of smbfs, nfs, permissions, masks, and OOo"
date: 2006-02-15
forum: Desktop Environments
---

### Post by dgermann on 2006-02-15
Hi all--

> 
The time has come the Walrus said
To speak of many things
Of shoes and ships and sealing wax,
Of cabbages and kings


This question is as much about achieving an understanding of what is going on as it is about getting how to ideas. So please help.

Background: We have a small office network with 4 users. Most are currently on Win95, one is on WinXP, and we are moving everyone to a linux desktop with OOo as the word processor and spreadsheet components. We need to be able to have common document files, common templates and common AutoText. The server has been in place for close to 3 years. It is a Red Hat 9.0 box, serving up files under Samba.

Most of the problems I have been having with OOo Writer have turned out to be rights/permissions issues. I have been frustrated most recently trying to put together the diverse elements of smbfs, nfs (if necessary), rights and masks and such.

So on to the questions--

1. What are the optimal rights/permissions I need and want in this setting? For instance, smb.conf has a createmask of 0775; here is my entry in /etc/fstab on a linux workstation:

```

//samba1/vol22        /sam/vol22  smbfs    rw,user,credentials=/root/.smbcredentials,dmask=777,fmask=777       0       0

```

2. Now that you have told me the optimal rights I need, how do I achieve them? What is the interplay I need between smb.conf, dmask, fmask, fstab, and who knows what else, to make it work?

3. Should I stick to just one way of serving up files, that is smbfs or nfs, rather than have both available? It seems to me that it is more secure that way--there is only one door open to my server.

4. Which is better for my use--samba or nfs? I am thinking samba is better because it has password protected access, limits access to certain users, and has file locking to keep 2 users from editing the same document at the same time, but perhaps I do not understand well enough yet to make that call. 

5. How do I get these all to play nice with each other?

OK, all you people who have a clue, help someone here who has little. Please. <sob>  :wink: 

Thanks!

---

### Post by dgermann on 2006-02-19
OK, folks, here's what's up:

I decided to try to just do this via nfs. I suspect the problems I have are that the userids and groupids on the server and the client machines are not in sync.

So after much tribulation I managed to install ypserv on the server (which is a red hat 9.0 machine).

Now I cannot get ypserv started.

I have portmap running on the server and have done rpcinfo -u localhost ypserv and /etc/init.d/ypserv start and service ypserv start, but service ypserv status reports that ypserv is stopped. ypserv -d hangs.

What am I doing wrong please?

Thanks!

---

