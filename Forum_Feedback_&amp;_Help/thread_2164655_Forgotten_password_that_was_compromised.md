---
title: "Forgotten password that was compromised"
date: 2013-08-01
forum: Forum Feedback &amp; Help
---

### Post by haifisch27 on 2013-08-01
Dear community,

I have not used the Ubuntu Forum much in the last years and thus forgotten the/which password I used for it. Now that the site was hacked and the passwords stolen, I was wondering if there is a procedure for me to find out which password I used for the forum (don't want to change the passwords for every internet service I use). I would be very grateful if anyone has helpful suggestions here...

---

### Post by TheFu on 2013-08-01
Not going to help you now, but a password manager can prevent this issue in the future.  After about a week of use, KeePassX changed my life.  Accounts are remember, extremely complex, random, different passwords used everywhere, and because KeePassX DBs are v1 compatible, Windows, Linux, Android programs can read the same DB without issue.

I know only 3-4 passwords now - but the most important one is to access the AES encrypted KeePassX DB. A few articles about KeePassX:
* [http://www.jdpfu.com/2010/04/24/keepassx-password-manager](http://www.jdpfu.com/2010/04/24/keepassx-password-manager)
* [http://www.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](http://www.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)

As you can see - I'm crazy about password managers and have learned there are many, many, many uses for those DBs, not just for passwords.

A few family and friends have started using KeePass or KeePassX - they all agree - it takes about a week, but after that, they are 100% hooked.

---

### Post by oldos2er on 2013-08-01
Moved to FF&H.

See [http://ubuntuforums.org/showthread.php?t=2164064](http://ubuntuforums.org/showthread.php?t=2164064)
All the old forum passwords were randomized, so your old password is gone.

---

### Post by cariboo on 2013-08-01
> **haifisch27 said:**
> Dear community,

I have not used the Ubuntu Forum much in the last years and thus forgotten the/which password I used for it. Now that the site was hacked and the passwords stolen, I was wondering if there is a procedure for me to find out which password I used for the forum (don't want to change the passwords for every internet service I use). I would be very grateful if anyone has helpful suggestions here...

There is no way for us to tell what your password was, as all the password were randomized, and we no longer store passwords in our database. I'd suggest you use something like apg or pwgen to generate new passwords for the services you are worried about.

---

### Post by CharlesA on 2013-08-01
> **TheFu said:**
> Not going to help you now, but a password manager can prevent this issue in the future.  After about a week of use, KeePassX changed my life.  Accounts are remember, extremely complex, random, different passwords used everywhere, and because KeePassX DBs are v1 compatible, Windows, Linux, Android programs can read the same DB without issue.

I know only 3-4 passwords now - but the most important one is to access the AES encrypted KeePassX DB. A few articles about KeePassX:
* [http://www.jdpfu.com/2010/04/24/keepassx-password-manager](http://www.jdpfu.com/2010/04/24/keepassx-password-manager)
* [http://www.jdpfu.com/2011/03/25/101-uses-for-a-password-manager](http://www.jdpfu.com/2011/03/25/101-uses-for-a-password-manager)

As you can see - I'm crazy about password managers and have learned there are many, many, many uses for those DBs, not just for passwords.

A few family and friends have started using KeePass or KeePassX - they all agree - it takes about a week, but after that, they are 100% hooked.

Just chiming in with a +1 here. I've been using Keepass for a long time now and it just rocks. I even got my mum to start using it so she would stop using weak passwords and/or reusing passwords.

---

### Post by Dave_L on 2013-08-01
I see that both keepass2 and keepassx are available in the 12.04 repositories. Which is preferable?

---

### Post by CharlesA on 2013-08-01
> **Dave_L said:**
> I see that both keepass2 and keepassx are available in the 12.04 repositories. Which is preferable?

I use keepassx on *nix and [KeePass]("http://keepass.info/") on Windows.

---

### Post by TheFu on 2013-08-01
> **Dave_L said:**
> I see that both keepass2 and keepassx are available in the 12.04 repositories. Which is preferable?

I haven't researched this in some time, but when I was looking for a password manager, I wanted:
* F/LOSS - GPL/BSD license
* Strong, standard encryption
* Trust no external websites or services
* Cross-platform DB support - copy the same DB to any platform - 100% binary compatible.
* Cross-platform Application support
* Avoid Mono and .NET libraries.
* auto-type for userid and passwords - I haven't typed logins in a few years for the things inside my keepassX db.

At the time, KeePassX on Linux, KeePass v1.x on Windows and KeePassDroid all used the v1.xx DB format.

Things may have changed since then. I dunno.

Your requirements are probably different than mine.  Just do the research on all the platforms you want covered and take your best choice.

Be certain that you back up the DB file religiously.  I have it on 6 different machines and on an internet server located 1,000 miles away. It gets pushed to most of these automatically, nightly.  I use 1 system for updates - all the others are considered "read-only" copies.

---

### Post by sandyd on 2013-08-01
Best thing to do.

Get a YubiKey.
Generate an super long PW, and use it on keepassx. Store the keepassx database anywhere you like.
Store password on YubiKey.

Now, you dont even need to remember any passwords....

Basically a YubiKey emulates a keyboard, and on a press of the key, it inserts the password in. Ive found it useful for securing LUKS lvm setups as well.

---

### Post by CharlesA on 2013-08-01
> **sandyd said:**
> Best thing to do.

Get a YubiKey.
Generate an super long PW, and use it on keepassx. Store the keepassx database anywhere you like.
Store password on YubiKey.

Now, you dont even need to remember any passwords....

Basically a YubiKey emulates a keyboard, and on a press of the key, it inserts the password in. Ive found it useful for securing LUKS lvm setups as well.

That would be awesome, especially if you don't have to actually remember the damn encryption key.

---

### Post by TheFu on 2013-08-01
> **sandyd said:**
> Best thing to do.

Get a YubiKey.
Generate an super long PW, and use it on keepassx. Store the keepassx database anywhere you like.
Store password on YubiKey.

Now, you dont even need to remember any passwords....

Basically a YubiKey emulates a keyboard, and on a press of the key, it inserts the password in. Ive found it useful for securing LUKS lvm setups as well.

I had considered that, but how to access passwords from Android or locations that don't have any USB ports available (some places hot-glue USB ports).  There are other smartcard systems too - these suffer the same concern.

Plus, I need to be able to login to a few different PCs directly - those are the passwords I must memorize.

Still, Yubikey is very interesting for many uses.  I see it mainly used for Truecrypt volume access with a short pre/post-pended phrase so that "something you know" part is still involved.

---

### Post by sandyd on 2013-08-02
> **TheFu said:**
> I had considered that, but how to access passwords from Android or locations that don't have any USB ports available (some places hot-glue USB ports).  There are other smartcard systems too - these suffer the same concern.

Plus, I need to be able to login to a few different PCs directly - those are the passwords I must memorize.

Still, Yubikey is very interesting for many uses.  I see it mainly used for Truecrypt volume access with a short pre/post-pended phrase so that "something you know" part is still involved.

[NFC version.]("http://www.yubico.com/products/yubikey-hardware/yubikey-neo/") Works perfectly on the Note II

---

### Post by CharlesA on 2013-08-02
> **sandyd said:**
> [NFC version.]("http://www.yubico.com/products/yubikey-hardware/yubikey-neo/") Works perfectly on the Note II

I so want to add that to my toolbox. I'd probably use it for encrypted partitions or something...

---

### Post by sandyd on 2013-08-02
> **CharlesA said:**
> I so want to add that to my toolbox. I'd probably use it for encrypted partitions or something...

The VIP edition is nice too, I have a whole bunch of these Yubikeys I keep.

---

### Post by TheFu on 2013-08-02
> **sandyd said:**
> [NFC version.]("http://www.yubico.com/products/yubikey-hardware/yubikey-neo/") Works perfectly on the Note II

I have an NFC capable device, the there is NO WAY IN THE WORLD that I'd enable that - especially for a security device. NO WAY.  Call me paranoid, if you like.

My DefCon friends have showed NFC hacking techniques at DefCon. I'll avoid it for now and the foreseeable future. Each individual needs to determine where their personal security needs lies.

---

### Post by pc-athome on 2013-08-02
Once I reach the 25 mark can I change my username back to what it was?  I thought that I would be 'reinstated' after rejoining, but instead it picks up part of my 'address' which I don't want!

RE YubiKey - advisable to have more than one key - if main key becomes broken (assume this is some sort of flash key) you are screwed. Linux Magazine did a very good tutorial on how to make a system secure - would not boot without a thumb drive with encrypted password!;)

---

### Post by Elfy on 2013-08-02
> **pc-athome said:**
> Once I reach the 25 mark can I change my username back to what it was?  I thought that I would be 'reinstated' after rejoining, but instead it picks up part of my 'address' which I don't want!

RE YubiKey - advisable to have more than one key - if main key becomes broken (assume this is some sort of flash key) you are screwed. Linux Magazine did a very good tutorial on how to make a system secure - would not boot without a thumb drive with encrypted password!;)

No - you won't be able to change username - you never would have been able to. 

It will pick part of the e-mail if you've not done as everything says and make sure that addresses match.

IF you want us to look at this for you - please post in resolution centre - as has been mentioned more than once in threads.

We will not deal with it in a thread with multiple people posting.

---

