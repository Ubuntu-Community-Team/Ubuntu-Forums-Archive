---
title: "Problem with encrypted file system and Kubuntu"
date: 2010-01-29
forum: Desktop Environments
---

### Post by dnunes on 2010-01-29
. . Hi there, everybody.

. . I'm a Kubuntu user (9.10, fully updated) and I was using my system normally. Yesterday I changed my password for security reasons and suddenly my system started to give erros whenever I log in ("Configuration file '/home/dnunes/.kde/share/config/knotifyrc' not writable. Please contact your system administrator.", "Configuration file '/home/dnunes/.kde/share/config/foorc' not writable. Please contact your system administrator.", "kstartupconfig4 does not exist or fails. The error code is 3. Check your installation").
. . Some people are saying that you have problem with encryption + auto-login, but that is not my case. I couldn't stop the problem until I logged in with console and tried to decrypt the home folder data. I noticed that my "login passphrase" wasn't working with the new login, so I tried to "unwrap" the passphrase file and could do it with the old password.
. . [Googling a little]("http://www.google.com/search?client=opera&rls=en&q=change+ecryptfs+login+password&sourceid=opera&ie=utf-8&oe=utf-8") (actually, in the first try), I found a [document about ecryptfs]("http://bodhizazen.net/Tutorials/Ecryptfs/") that clearly stated that after changing the login from the system you must change the login passphrase manually as well:

> The first is your log in password. This allows your private directory to be automatically decrypted when you log in. When you change your log in password, however, the ecrypts password is not updated. You unfortunately need to manually the Ecryptfs password (...).

. . The problem is that the documentation on that page is also wrong and will make your original mounting passphrase (that giant random one) be PERMANENTLY LOST. They tell you to use "ecryptfs-wrap-passphrase", but this command will expect you to provide the mounting passphrase (which you obviously don't know :P), bot the old login passphrase, as the doc says. So, to whom it may concern, the command to change the "login passphrase" (the password that decrypts the encrypted "mount passphrase file" [usually "~/.ecryptfs/wrapped-passphrase"]) is actually:

```
ecryptfs-rewrap-passphrase ~/.ecryptfs/wrapped-passphrase
```
. . It will ask you the old login passphrase (your old login password) and the new one (that should be the new login password).

. . Amplexos.

---

