---
title: "drive encryption error"
date: 2009-04-21
forum: General Help
---

### Post by Pollywoggy on 2009-04-21
I installed Jaunty (release candidate) two days ago and when I did so, I enabled encryption of my home directory (during the installation process).  I was not asked for a password or passphrase for this at that time.  This morning, a light bulb icon appeared on the task bar and when I clicked it, it told me I should enter a passphrase to encrypt the drive, but it did not seem to accept all of my input and it closed and did not ask me to reenter the passphrase for verification.  Now I am afraid to reboot the machine for fear of being locked out.  encryptfs-unwrap-passphrase does not even seem to be a command on my system.  The light bulb mentioned this as a command.

Should I reinstall Ubuntu?

---

### Post by DGortze380 on 2009-04-21
> **Pollywoggy said:**
> I installed Jaunty (release candidate) two days ago and when I did so, I enabled encryption of my home directory (during the installation process).  I was not asked for a password or passphrase for this at that time.  This morning, a light bulb icon appeared on the task bar and when I clicked it, it told me I should enter a passphrase to encrypt the drive, but it did not seem to accept all of my input and it closed and did not ask me to reenter the passphrase for verification.  Now I am afraid to reboot the machine for fear of being locked out.  encryptfs-unwrap-passphrase does not even seem to be a command on my system.  The light bulb mentioned this as a command.

Should I reinstall Ubuntu?

If you have important information in your home directory I suggest that you immediately copy it to an external device!

If you lose, forget, can't figure out the passphrase for the encryption, you are correct, any data is essentially lost for ever.

---

### Post by Pollywoggy on 2009-04-21
> **DGortze380 said:**
> If you have important information in your home directory I suggest that you immediately copy it to an external device!

If you lose, forget, can't figure out the passphrase for the encryption, you are correct, any data is essentially lost for ever.

I am going to copy the most important files before I reboot, but I believe I found the solution to the problem.  I will know soon enough.

I entered the command "ecryptfs-manager" and this brought up a dialog where I added a passphrase (option #1) and then exited.   I will make backups in case I am wrong.

thanks

---

### Post by Pollywoggy on 2009-04-21
I backed up the most important files and then logged out of the system and I then connected to it with ssh and I was (as expected) unable to see my home directory.  Then I entered ecryptfs-mount-private and was prompted for my *passphrase* but the passphrase I had entered earlier did not work.  My normal password DID work and then I did a cd /home/mydirectory and I could see my files.  I rebooted my machine and everything still works.

I have to install a third Jaunty system today but I am not going to use ecryptfs until I understand it.  I will go with LVM for the remaining install since it is a netbook.

---

