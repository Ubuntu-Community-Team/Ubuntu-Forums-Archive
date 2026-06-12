---
title: "No desktop after password change"
date: 2014-12-29
forum: Desktop Environments
---

### Post by gpgp on 2014-12-29
Hello

So i changed my password on a pretty normal 14.04 installation aside from having gnome desktop installed. after a reboot i get a login screen, login with new password but then am sitting in black. i can see my mouse but thats it. no key combinations work, like launching a terminal or the like.
I am away from that computer now but thought i would ask if any one has seen this. I can tell it has something do with file system encryption. it seems i missed a step in the password change; let me explain.

This is a desktop computer in a secure location, i like a short password on it. i did this via terminal with sudo passwd USERNAME as you cannot with the gnome tool as the password i wanted is too short.

if i switch to a shell and login, i am prompted with something about run ecryptfs-mount-private, if i do that i get a file not found, i have no files that i can see etc just a readme and something else. whats most curious here is that it asks for login passphrase. my old password is the answer it is looking for here. this is an encrypted home folder also.
trying a recovery boot with failsafe graphics fails at mounting some filesystems. trying to do a normal boot and choosing a different window manager gives the same result, black screen with mouse.

Anyone have any ideas ? i was thinking my next steps are trying to figure out the difference between a login passphrase and a password. the way i use this computer i may just go to a live cd move the files i want to keep and reinstall, but i would love to be able to reinstall some packages instead.

thank you for your time.

GPGP

---

### Post by gpgp on 2014-12-29
Not sure why i didnt think of this but i was able to get everything back by reverting to the original password.

I would still like to change the password but must now research the proper steps when an encrypted file system is concerned.

[http://askubuntu.com/questions/33730/will-changing-password-re-encrypt-my-home-directory](http://askubuntu.com/questions/33730/will-changing-password-re-encrypt-my-home-directory)

found my answer here in case it happens to you.

GP

---

### Post by mcduck on 2015-01-01
So for anyone having the same problem, the short answer is that using "passwd" to change the password is fine, but you shouldn't run it with "sudo" but instead as your own user.

If you however run it with sudo, or your system admin changes your password, you need to mount your encrypted home with *ecryptfs-mount-private* and then execute *ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase* to re-encode the the passphrase used to de-encypt your home directory using your new password.

---

