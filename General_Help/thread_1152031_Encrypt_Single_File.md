---
title: "Encrypt Single File"
date: 2009-05-07
forum: General Help
---

### Post by Michelexub on 2009-05-07
Hi.
At the moment I have a dual boot laptop Xubuntu/WinXP.

I have a couple of files which contains sensitive data and I want to encrypt them, but they must be encryptable/decryptable from Xubuntu and Win Xp at the same time.

Obviously they are saved in a NTFS partition, which is accessible by both OSes.

Is there any software that can be run by either WIN or XUBUNTU which can encrypt/decrypt those few files?

Note that another request of mine would be to be able to copy those files to an external HD in their encrypted form for backup purposes and being able to decrypt them easily, possibly like a self-extracting archive, so that I can simply attach my HD to any computer and decrypt them.


Hopefully my post it's not too confusing.

Thanks.
Michele

---

### Post by jakupl on 2009-05-07
you can use truecrypt, but that might be overkill. Truecrypt makes an encrypted container, in which you can put the files into. and it is cross platform. Truecrypt is not in the repositories, so you need to download it from here [http://www.truecrypt.org/](http://www.truecrypt.org/)

---

### Post by sloggerkhan on 2009-05-07
encfs is another option. I think there's even gnome applet for working with encfs dirs.

---

### Post by Michelexub on 2009-05-08
> **jakupl said:**
> you can use truecrypt, but that might be overkill. Truecrypt makes an encrypted container, in which you can put the files into. and it is cross platform. Truecrypt is not in the repositories, so you need to download it from here [http://www.truecrypt.org/](http://www.truecrypt.org/)

Yes, that's exactly my issue.
I thought about it, but it seems a bit too "complex" for my scope.
But it seems tat tehre are not many other options around.

Once I found a small win program which was an executable (no need to install) and you could run it and encrypt/decrypt files.
It would be greta to have the same software as an .exe for Win and as a .sh for *nix.

---

### Post by Michelexub on 2009-05-08
> **sloggerkhan said:**
> encfs is another option. I think there's even gnome applet for working with encfs dirs.

I think that you missed my point: if I encrypt a file using encfs, can I then decrypt it booting from Windows?

Michele

---

### Post by sloggerkhan on 2009-05-08
> **Michelexub said:**
> I think that you missed my point: if I encrypt a file using encfs, can I then decrypt it booting from Windows?

Michele

Oh, didn't notice that for some reason. I guess you could try compiling on cygwin or something.

---

### Post by tornadof3 on 2009-05-08
GNU PG would do this fine, although you'd need to store your secret key on both windows and linux partitions.

---

### Post by darthmob on 2009-05-08
personally I'm using truecrypt as well. I have got some text documents encrypted with it on my usb stick.

there seems to be an option to run it from a stick as well:
[http://www.uniyatra.com/docs/truecrypt/](http://www.uniyatra.com/docs/truecrypt/) (step 12)

// edit: I just saw that with the windows installer you can simply select 'extract files' to put it on a stick. it's just about 3mb and you can mount encrypted containers / partitions without having to install it on the windows machine. that does not seem like overkill to me! ;-)

---

### Post by jakupl on 2009-05-08
I feel somewhat obliged to tell you that truecrypt has some serious issues. I try not to encourage people to use it.
This is what wikipedia has to say about truecrypt:

> The TrueCrypt Collective License does not meet the Open Source Definition, and thus has not been approved by the Open Source Initiative. It is considered "non-free" by all the major GNU/Linux distributions (Debian[12], Ubuntu[13], Fedora[14], openSUSE[15], Gentoo[16]). The Fedora project explains[17] that

    The TrueCrypt software is under an **extremely poor license**, which is not only non-free, but actively **dangerous** to end users who agree to it, opening them to possible **legal action** even if they abide by all of the licensing terms. Fedora made extensive efforts to try to work with the TrueCrypt upstream to fix these mistakes in their license, but was unsuccessful. Fedora Suggests: **Avoid this software entirely.**


---

