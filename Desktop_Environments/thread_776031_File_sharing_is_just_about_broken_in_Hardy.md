---
title: "File sharing is just about broken in Hardy"
date: 2008-04-30
forum: Desktop Environments
---

### Post by randysparks on 2008-04-30
Sharing a folder from within Ubuntu Hardy isn't working very well.

I've figured out that you need to log out and back in again after being prompted to install the Samba software, but guest access results in files placed in the shared folder being owned by 'nobody' and with permissions that mean you can't even read them.

So the only way to do it is to have people log in via your username and password. But this involves giving other people your password!

If you try and change the smb password at the prompt, by typing smbpasswd. it actually changes your LOGIN password as well. I don't know how or why it does this, but it's crazy. Especially considering this is an LTS release. 

Any work around much appreciated. NFS is out of the question because I'm in an office with Windows machines.

---

### Post by gobbledigook on 2008-04-30
hi! surely you would just set up a guest acc. for "everyone" to log into and share the files within this?

---

### Post by randysparks on 2008-04-30
> **gobbledigook said:**
> hi! surely you would just set up a guest acc. for "everyone" to log into and share the files within this?

No, because the shared folder is shared using my username. There's no way to assign it to a different user apart from at the command-line.

---

### Post by gobbledigook on 2008-04-30
well you just need to abolish the share in your user account.

I assume it is a root acc. which means that only root users can access it, which is why you cannot have filesharing like in windows... its a security thing:)

set up a second acc and re-establish the share in that acc. with limited access to your files/read only abilities or whatever access rights you find necesary.

---

### Post by randysparks on 2008-04-30
> **gobbledigook said:**
> well you just need to abolish the share in your user account.

I assume it is a root acc. which means that only root users can access it, which is why you cannot have filesharing like in windows... its a security thing:)

set up a second acc and re-establish the share in that acc. with limited access to your files/read only abilities or whatever access rights you find necesary.

Well, I should be able to use the smbpasswd command to assign a specific password for Samba sharing. This is what I've done in the past. Then I can share folders from my user account, and have people login to the share using my username and the Samba password.

But in Hardy if I use the smbpasswd command, it CHANGES MY LOGIN PASSWORD!!!! Not the Samba password. It changes the actual Ubuntu password I use to login to the computer. I don't know how, but I suspect that really shouldn't be happening. There's your "security thing" right there. 

What you're describing re: setting up a new account solely for sharing is too convoluted. I'm not going to keep switching users to created shared folders and share files. That's crazy.

---

