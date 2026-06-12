---
title: "Evolution decryption problem."
date: 2005-04-24
forum: Desktop Environments
---

### Post by rudoe on 2005-04-24
I use Evolution 2.2.1.1

I imported my keys to gpg that was no problem.
Evolution also automaticaly signs and encrypts my emails.

But if i get a email like this:

X-Mailer: JMailer/2  V1.7 010131  by JaeCOM
X-EUMEL-Scanner: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
X-EUMEL-Cfg: 20010621-112806, Modus 4
MIME-Version: 1.0
Content-Type: text/plain; charset="iso-8859-1"
Content-Transfer-Encoding: 8bit
Message-ID: <20040103-05542079@sv11>
X-EUMEL-EKA: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
X-Auto-PGP: MustEncrypt  <xxxxxxxxxxxxxxxxx>
Status:   

-----BEGIN PGP MESSAGE-----
MessageID: jUf403apYNCg+8+L/jNelw/Ya0W4zSet
Comment: PGP 5.0 for OS/2

qANQR1DBw04DtaNpkaCjzv0QD/92mz7Wr+PByLVQ8JTIras+/9+5kndZLEy/iRtM
...
2yxCUgS0ncbGMkQXDHF90x83oFSq9ZuYSwQYgMzINjHnalv2+vpVJPTgpsz2CgzH
Wxy/b6E=
=u5tc
-----END PGP MESSAGE-----

Evolution does not decrypt it. And there is also no button to decrypt it manual.

I think it is coz of Content-Type: text/plain; charset="iso-8859-1", but i am not able to change this in the emails i get. So i need to change something in Evolution. 

But i dont know  what and how.

Thanks Folks!

---

### Post by rudoe on 2005-04-26
hmm if nobody has a idea here then i better try thunderbird

---

### Post by wolovids on 2005-04-26
Evolution refuses to encrypt/decrypt inline PGP messages.  The inline method is depreciated but is still used by people using email clients such as PINE.  The new standard is S/MIME and evolution does it this way. 

This is why I am using Mozilla Thunderbird with the Enigmail extension.  It can handle inline and S/MIME PGP messages.  I love it.

---

