---
title: "Ubuntu login screen with ecryptfs (Emergency)"
date: 2012-04-01
forum: Desktop Environments
---

### Post by djreplay1234 on 2012-04-01
Hello everyone,
I am having a big problem here. I converted an old IBM computer to be a server, running ubuntu 11.10. I have the computer set up to duel boot with a version on Win XP. Don't ask me why, I have been meaning to scrap it. Though just now, I had to shutdown and restart to get into it to copy over some old files. Though when I reboot back into ubuntu and prompted with the normal login screen. I enter my credentials and it kind of flashes for a moment and returns back to the login screen.
After a little bit of research, I have found that this is a common problem and I need to delete a file in my home directory. Though when I press (contol+alt+F1) at the login screen and get a shell, I log in fine with my credentials, though I am greated by an encrypted home folder. Why? All I did was reboot the machine, not install any new programs or anything. Nonetheless, I try and run the command advised to be from the README, (ecryptfs-mount-private) though, it is telling me my login is incorrect. How can that be?
I know I am not making any mistakes, but I just entered the same password to get access to my shell.
My entire server is on hold because of this, I have had to login to my FTP host account, to bring some of the services online.
This is a emergency, please help.
Thanks in advance!

EDIT: I'd though that I would mention, when I check syslog after I get an authentication failure. This is what shows up.
> Apr  1 01:13:24 h4xb0x ecryptfs-insert-wrapped-passphrase-into-keyring: Error attempting to unwrap passphrase from file [/home/will/.ecryptfs/wrapped-passphrase]; rc = [-5]
Apr  1 01:13:44 h4xb0x sudo: pam_ecryptfs: Passphrase file wrapped
Apr  1 01:13:45 h4xb0x sudo: Incorrect wrapping key for file [/home/will/.ecryptfs/wrapped-passphrase]
Apr  1 01:13:45 h4xb0x sudo: Error attempting to unwrap passphrase from file [/home/will/.ecryptfs/wrapped-passphrase]; rc = [-5]
Apr  1 01:13:45 h4xb0x sudo: pam_ecryptfs: Error adding passphrase key token to user session keyring; rc = [-5]
Apr  1 01:15:29 h4xb0x ecryptfs-insert-wrapped-passphrase-into-keyring: Incorrect wrapping key for file [/home/will/.ecryptfs/wrapped-passphrase]
Apr  1 01:15:29 h4xb0x ecryptfs-insert-wrapped-passphrase-into-keyring: Error attempting to unwrap passphrase from file [/home/will/.ecryptfs/wrapped-passphrase]; rc = [-5]


---

