---
title: "kdewallet configuration with ProtonVPN question"
date: 2021-12-31
forum: Desktop Environments
---

### Post by jwoodruff on 2021-12-31
I am using Ubuntu 20.04 as the sole operating system on my desktop home computer. I previously installed the Plasma desktop environment and have become used to it and prefer it over the standard Ubuntu desktop environment. I recently purchased ProtonVPN and installed the client app. I found I was unable to connect using the ProtonVPN program, (it would just hang) unless I logged into the Ubuntu desktop environment - where it works just fine. Discussions with protonvpn help services eventually directed me to follow instructions to configure KWallet as per this wiki article: ([https://wiki.archlinux.org/title/KDE_Wallet](https://wiki.archlinux.org/title/KDE_Wallet)). The article instructs to install kwallet-pam then mentions "kwallet-pam is not compatible with GnuPG keys, the KDE Wallet must use the standard blowfish encryption". I tried temporarily disabling KWallet, but protonvpn still wouldn't connect, (apparently ProtonVPN requires KWallet to be running).  I have generated a GPG key previously, but do not use it, so I'd like to "disable GPG. That doesn't seem possible as I understand that it is used for things like software updates etc. by the linux system. 
So, can anyone please tell me how to set KWallet encription to "blowfish encryption"? Or possibly point me to an article, - I haven't been able to locate instructions.
Alternatively, if anyone has any other solutions, I would appreciate hearing them.
Please inform me if/what further information regarding system details are required.
Thank-you in advance
Joe

---

