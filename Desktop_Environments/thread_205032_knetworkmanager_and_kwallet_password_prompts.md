---
title: "knetworkmanager and kwallet password prompts"
date: 2006-06-27
forum: Desktop Environments
---

### Post by LazyBoy on 2006-06-27
Everytime I use knetworkmanager to connect to a different network, I'm prompted for the password to kwallet.

Any way to stop that?  Any way to stop knetworkmanager from using kwallet or let kwallet be accessed without a password?

LB

---

### Post by Jucato on 2006-06-27
Two possible ways:

1. When you are prompted by KDE Wallet Manager when trying to connect to a Network, choose "Allow Always". This will only affect knetworkmanager

2. Open up KWalletManager and go to Settings > Configure Wallet. Go to the Access Control tab and uncheck "Prompt when an application accesses an open wallet". This is will stop KWalletManager from asking you for confirmation everytime any application needs to access the Wallet, only if the wallet is already opened. So it will still ask you for your password the first time you run it.

---

### Post by LazyBoy on 2006-06-27
Thanks!

LB

---

