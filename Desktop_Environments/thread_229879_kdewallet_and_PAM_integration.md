---
title: "kdewallet and PAM integration?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by MerZo on 2006-08-05
Hello!

My problem is that I have to enter a password twice when I am using the kwallet for storing my password for the knetwork manager. First one time at login, which is perfectly fine. And the second when the desktop has loaded, this time for the wallet.

Now my question is that if it is possible to integrate so that the account login password, feeds the wallet with the same password and in that way I will just have to enter one password for logging in.

I searched the net and someone talked about PAM but I don't really have any clues. 

The problem is almost the same as the keyring-problem in gnome when using the nm-applet.

And yes, I can use the wallet without password, but it would be fun to be able to use the wallet for more than just the knetworkmanager.

---

### Post by Jucato on 2006-08-05
I'm not really sure. I think the purpose of KWallet is to be a KDE Wallet Manager, meaning it keeps your different passwords from different applications/sites for safekeeping in one accessible place, not for having one pasword "to rule them all" (so to speak).

I'm not sure about KNetworkManager, but for other apps, you can set them not to notify you anymore when they're going to access passwords from KWallet **as long as KWallet is already opened**, which means you still have to enter your password for KWallet at least once.

---

### Post by MerZo on 2006-08-05
> **Fenyx said:**
> I'm not really sure. I think the purpose of KWallet is to be a KDE Wallet Manager, meaning it keeps your different passwords from different applications/sites for safekeeping in one accessible place, not for having one pasword "to rule them all" (so to speak).

I'm not sure about KNetworkManager, but for other apps, you can set them not to notify you anymore when they're going to access passwords from KWallet **as long as KWallet is already opened**, which means you still have to enter your password for KWallet at least once.

But because all programs are storing the password in kwallet, I think the purpose is to be one to rule them all. The one password would be nice to set when it logins in, KDE that is.

Anyone else? :/

---

### Post by Jucato on 2006-08-05
It's actually "one wallet to contain them all".

You can emulate a "one password to rule them all" by setting KWallet not to inform you anymore that it's being accessed by a program. With the exception of KNetworkManager, you don't have to enter your passwords again and again once KWallet is already opened. You just have to run KWallet in the beginning and you're set to go.

---

