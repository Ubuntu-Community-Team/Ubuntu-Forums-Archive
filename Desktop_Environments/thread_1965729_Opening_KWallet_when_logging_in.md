---
title: "Opening KWallet when logging in"
date: 2012-04-26
forum: Desktop Environments
---

### Post by kristianz on 2012-04-26
Hey! I wonder if the following is possible in KDE/Kubuntu. I think it's the ideal behavior of an DE for me as far as password handling goes.

I want the action of logging in or unlocking the screen to also unlock all the passwords stored in KWallet.

As it is now, I fist log in from kdm, then a few seconds later have to enter a passphrase to unlock KWallet for the networking to get the the WIFI-passphrase (stored in KWallet). Then later, when sending an email, I have to enter the KWallet passphrase once more for KMail to access the GPG encryption keys to sign the email.

I want proper security, but I don't want to be prompted for a passphrase several times in one active computer session. I'm diligent about locking the screen/suspending the computer when leaving it unattented, so that's all the security I need. The act of unlocking the screen would ideally also unlock KWallet for the remainder of the active session.

So my question is: Can I do this in Kubuntu?

---

### Post by kelpdip on 2012-04-27
This only addresses one symptom, but setting wifi connections as "system connections" disconnects wifi security from individual users' wallets.

Also, it seems the next step from kwallet is ksecretservice, which is almost done? more info here:
[http://www.kubuntuforums.net/showthread.php?57081-KSecretService-in-KDE-Wallet-4-8](http://www.kubuntuforums.net/showthread.php?57081-KSecretService-in-KDE-Wallet-4-8)

/\ There's a link to a ppa which includes ksecretservice if you are feeling adventurous.

---

