---
title: "help I deleted pam.d I can't log in"
date: 2010-10-16
forum: Desktop Environments
---

### Post by farchumbre on 2010-10-16
Hi,
I deleted the whole pam.d directory.
unfortunately I logged out and now I can't log in again, not even via the console.
I can't not even recover my data because is encrypted.
any ideas?

---

### Post by ankspo71 on 2010-10-16
Hi.
How did you delete the directory? I mean did you send the directory to trash or did you permanently delete it? If the directory got moved to the trash then it is probably in the Root's trash folder, but if not then maybe in your own trash folder (but that isn't likely, and you cant access it anyways - since it is encrypted). 

You can use the live cd to browse to the trash folders on the hard drive and then copy and paste the pam.d directory back to where it belongs. 

When you boot into the live cd, the hard drive will appear in the Places menu and it will appear as "96 GB Filesystem" (the size is only an example, of course). Click on that to mount your hard drive and browse around.

Root's trash is located at:
/root/.local/share/Trash/ 

And if you can  possibly access it, your own trash folder is at:
/home/your-username/.local/share/Trash/

Hope this helps.

---

### Post by farchumbre on 2010-10-16
Dear ankspo71


It worked !!!!!
thanks a lot.

do you know how to remove the encrypted thing? so next time will be simpler?

---

### Post by ankspo71 on 2010-10-16
Hi,
I'm glad it worked out for you. 

Before attempting anything, try to back up everything you have to an external source... for just in case things go wrong.

I don't know if the encryption during the installation will encrypt every future user's home folder, or just the user that installed Ubuntu. Actually, now that I think about it, I would probably backup everything I need and install Ubuntu fresh since that would only take me about 45 minutes to do everything. You'll see why when you read the links below. 

Here are some links on encrypting/decrypting the home folder:
[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)
[https://answers.launchpad.net/ubuntu/+source/ecryptfs-utils/+question/48636](https://answers.launchpad.net/ubuntu/+source/ecryptfs-utils/+question/48636)
[http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reinst](http://serverfault.com/questions/160277/ubuntu-how-to-decrypt-home-directory-swap-basically-everything-without-reinst).

Hope this helps.

---

