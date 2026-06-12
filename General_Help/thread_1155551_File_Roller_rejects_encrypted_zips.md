---
title: "File Roller rejects encrypted zips"
date: 2009-05-10
forum: General Help
---

### Post by Billko on 2009-05-10
I need to be able to open files compressed and encrypted in WinZip. File Roller will open unencrypted zipped files and files encrypted with Zip 2.0 compatible encryption but not with AES encryption. Is there any way I can overcome this?

---

### Post by sgosnell on 2009-05-10
Do the zip files have to be encrypted with Winzip?  It's possible to encrypt them with PGP, then unencrypt them in Linux and then unzip them with archive manager or tar.  If they absolutely have to be encrypted with Winzip, then running it in wine is about all I can think of.

On second thought, gpg might be able to do the unencrypting before the extraction.  I haven't tried it, but it might be worth a shot.

---

### Post by Billko on 2009-05-11
Thanks for that. The files are sent to me by Windows users who would not take kindly to being asked to use anything but WinZip which has the undeniable virtue of being very user-friendly.

I myself am new to Linux and cannot see how I would use gpg in the way you suggest. It seems to be geared to the use of public and private keys rather than passwords- or am I confused?

---

### Post by sgosnell on 2009-05-11
It does both.  It can be used to encrypt local files as well as being used with public and private keys to encrypt files and also to sign messages so they can be verified as coming from the proper person.  It's a very versatile system.  

If the files are encrypted by Winzip, how do you decrypt them?  Do they send you the password?  This would be an ideal use for gpg/pgp, since they could get your public key, encrypt the files using that, and then you would decrypt them using your private key, without anyone having to know that key or send a password by any means.  Most Windows users would probably be incapable of doing that, though.

---

### Post by TrombaMarina on 2009-10-05
I just tried PeaZip and it works great.  It's not obvious where to enter your password (Tools -> Enter password / keyfile), but once you figure that out, it can decrypt and extract files created and encrypted with WinZip just fine.  I'm about to try the reverse (create/encrypt in PeaZip, decrypt/extract in WinZip 10).  Wish me luck!

It's not in the Ubuntu repositories, so you have to download it from [http://peazip.sourceforge.net/index.html](http://peazip.sourceforge.net/index.html)
Once downloaded, I just had to click on the .deb package and it converted and installed without a hitch and showed up in my Applications -> System Tools menu.

(An hour or two later)
Just zipped up 500MB of files in PeaZip with encryption, then unzipped/decrypted them in Windows XP with WinZip 11.  Worked like a charm (though PeaZip is noticeably faster than WinZip)!

---

