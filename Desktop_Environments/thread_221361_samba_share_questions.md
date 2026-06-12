---
title: "samba share questions"
date: 2006-07-23
forum: Desktop Environments
---

### Post by fatsheldon on 2006-07-23
I'm trying to use [THESE]("https://wiki.ubuntu.com/MountWindowsSharesPermanently?highlight=%28windows%29") instructions to... well, do exactly what it says (mount windows shares permanently).  When i edit fstab and set up a ~/.smbcredentials as indicated  i receive the following message when trying to mount the share:

 ERROR: Unable to open credentials file!

now, if i change fstab to read /home/username/.smbcredentials (instead of ~/.smbcredentials) then it works fine.  but i don't want to hardcode the username.  you know... sometimes another user will login.  Has anyone else had this issue?  Anyone have any idea what the problem is or how to fix it?

this whole issue comes about from not being able to authenticate as the logged in user when accessing these samba shares (on a Slackware box).  what i mean is:  from windows if i access the shares as the user 'sheldon' it allows me write access as that user is on the "write list."  Ubuntu constantly uses the guest user if i use the "places" menu to connect to the share.  i can't seem to consistently force it to use my username.  guest access is allowed, but then i don't have write access.  does anyone have a suggestion on this one?

i appreciate any suggestions.

fatsheldon

---

### Post by gerbman on 2006-07-23
> **fatsheldon said:**
> but i don't want to hardcode the username.  you know... sometimes another user will login.You could place the credentials file somewhere other than your home directory (e.g., in /etc) Just make sure that the permissions are set correctly on the file to protect your password information from being read by others. Do this with```
sudo chown username:username credentials_file
sudo chmod 600 credentials_file
```where username is your account name.

---

### Post by der_joachim on 2006-07-23
When the mount script is loaded, nobody is logged in yet, so ~ in an fstab file will never work. Put somewhere safe, give the full path to your credentails file and you should be set.

---

### Post by fatsheldon on 2006-07-23
I have two problems with the suggestion provided.

1.  why is it listed in the wiki page that the credentials page can be put into the home directory and the ~ can be used in the fstab?  i've seen that page linked in two or three other threads and i seem to be the only loser with a problem with it.

2.  putting the credentials file in any other directory giving the full path doesn't sovle the main issue.  i was wanting the share to be mounted with different permissions depending on the user that was logged in.  you know... the way it works in Windows (stupid thing to say, i know).  You just login, access the share and it allows you permissions based on what user is logged in.

i suppose the way to do this is use ONE credentials file and set the uid or guid options...  right?  that way the owner can have different permissions than the others... right?

sheldon

---

### Post by Thund3rstruck on 2006-07-23
Truthfully, I feel this is a real weakness as well. I'd like to use the $USER env variable to dictate share logins as well but since no user is actually logged in when fstab mounting occurs, this appears inpossible. 

At the moment we're using gnome login scripts that mount the windows shares based on the user who has logged into the machine.

---

### Post by fatsheldon on 2006-07-23
> **Thund3rstruck said:**
> At the moment we're using gnome login scripts that mount the windows shares based on the user who has logged into the machine.

that's a pretty good idea...  that'd be great for the user specific shares.  ones that only ONE user has access to.

for the shares where everyone can see them and only the owner needs write access i'm using the uid option in the fstab and it's working fine.  i still can't see why there isn't a way to do this from the "places" menu though!

anyway, i'll look a little more at gnome login scripts too.  thanks for the reply!

fatsheldon

---

### Post by fatsheldon on 2006-07-24
> **fatsheldon said:**
> for the shares where everyone can see them and only the owner needs write access i'm using the uid option in the fstab and it's working fine.  

i take that back.  it's not working fine.  i booted up today (one day later) and as soon as i login i receive the nice:

FAILED TO INITIALIZE HAL!

and it locks.  boot into gentoo, mount the root ubuntu partition and set the "noauto" option in fstab, reboot and all is fine (but no mounted samba shares...)

anyone seen this before?

sheldon

---

