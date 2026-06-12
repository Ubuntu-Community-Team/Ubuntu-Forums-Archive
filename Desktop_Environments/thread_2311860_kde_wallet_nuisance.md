---
title: "kde wallet nuisance"
date: 2016-01-30
forum: Desktop Environments
---

### Post by yonnie on 2016-01-30
This KDE Wallet seems to pop-up for just about any reason.  Sometimes the window gets behind another window and blocks work.  I've tried removing it via the package manager, but it still is here and causing trouble.  It supposedly is to pop-up for passwords?  Then why does it seem to pop-up for everything?  First off, what is it asking for when no passwords were used or altered when it pops-up?  Next, how do I get rid of it?

---

### Post by buzzingrobot on 2016-01-31
If/when you see a dialogue asking you to created a password for Kwallet (you will see a choice of GPG encryption or Blowfish encryption)  choose Blowfish and *do not enter a password*.  Leave the password field blank and click 'OK".  You'll be warned that this is insecure.  But, it is the widely-used way of taming Kwallet.

It's KDE's password manager. Most KDE apps depend on it to store their password. For example, the mail servers you set up in a Kmail account have passwords.  KWallet stores them and automatically supplies them to Kmail when it logs on to those servers.  Without that, Kmail would prompt for a password every time it accesses a mail server.(That's equivalent to the mail check interval you set, not just when Kmail is launched.)

Kwallet itself is protected by its own password.  It will prompt for its password when KDE is restarted.  If you don't provide one then, and you later launch an app that uses a password maintained by kwallet, you'll be prompted by kwallet for its own password.
It's almost impossible to successfully remove the kwallet packages.

In the "Account Details" panel in System Settings, you can access Kwallet's controls. (Also available via kwalletmanager.) 

KWallet irritates and frustrates most users.

---

### Post by yonnie on 2016-02-07
I was waiting for an email telling me there was a response that either never came or was missed, sorry for the delay.  I will try the above and get back.  The wallet is a damned nuisance when on a scratch-pad and I need it gone!

---

### Post by mr-tin-man on 2016-02-09
I found this link, don't know if it is still valid, seems to be mixed opinions.  Hope it helps.

[http://askubuntu.com/questions/47216/how-to-disable-kde-wallet](http://askubuntu.com/questions/47216/how-to-disable-kde-wallet)

mr tin man

---

### Post by montag dp on 2016-02-11
Just to add to buzzingrobot's response, in kwalletmanager there is the option to change kwallet's password. If you have already set a password and it asks you for it all the time, go there and change it, leaving both the new password field and confirmation field blank. It will warn you that it is a weak password, but that's okay.

I'm not sure why kwallet works the way it does. It's a major nuance if you actually have a password set. It seems like if it really needs to have a password for security reasons, it shouldn't need to ask your for it every time a known service starts. Maybe just for new services to ensure they are not malicious. But then, I don't think I fully understand the concept behind it in the first place, so maybe that wouldn't work.

---

### Post by wandalalakers on 2016-02-28
I disable kwallet.  I don't use kmail.

---

### Post by yonnie on 2016-04-07
Can't find it when looking for it, but it still pops-up when I don't want it and forces to be dealt with.  Not in system settings.

---

### Post by buzzingrobot on 2016-04-07
It's in, or should be, System Settings->Account Details in both KDE4 and KDE5.   You can also launch "kwalletmanager".

KWallet is the way KDE remembers passwords. If it's removed (difficult and risky) then most applications won't be able to store their passwords. The problem seems to be that 
Kwallet also has a password and it will prompt you for it. I.e., it doesn't store its own password. Until Kwallet is provided with its password, it will not provide stored passwords to other applications. 

Working correctly, KWallet should prompt for a password once a session.

Whatever is going on here has been happening for years. Many, many users never seem to get it to stop being so annoyoing.

The most effective way to deal with it, as mentioned, is to use a blank password for your KWallet password.

Until all KDE4 components have moved to KDE5, distributions typically ship a mix of both KDE4 and KDE5 packages. Those distributions, then, have to also ship two Kwallet versions, one that works in KDE4 and one the works in KDE5.

---

