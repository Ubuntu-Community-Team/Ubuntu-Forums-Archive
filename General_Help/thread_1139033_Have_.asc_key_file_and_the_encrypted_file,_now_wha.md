---
title: "Have .asc key file and the encrypted file, now what?"
date: 2009-04-26
forum: General Help
---

### Post by rbhkamal on 2009-04-26
Today ,for the first time, I used the file encryption option and now I can't decrypt the file. I get the error:
Dycrption failed. You probably don't have the decryption key.


Here is what I did:
1- I opened the "Passwords and Encryption keys" application and created/signed a new key using a good password.
2- I right clicked on the new key and exported it to an myTestKey.asc file
3- Encrypted my data file by right clicking on it and choosing the encrypt option
4- Opened "Passwords and Encryption keys" and deleted the key that I just generated
5- Reboot

After reboot:
1- I double clicked on the myTestKey.asc and get a message saying that it was imported
2- Double clicked on my encrypted file.

Now I get a progress bar for the decryption process which lasts about a minute. Then when its done, I get an error message saying that I don't have the key.


What should I do? I really need that file... it has my openvpn certs :(

Here is the output of gpg -k and gpg -K:
```
kuku@kuku-desktop:~$ gpg -k
/home/kuku/.gnupg/pubring.gpg
------------------------------
pub   1024D/4B07D612 2009-04-26
uid                  kuku <kuku@gmail.com>
sub   2048g/A2DCF8C5 2009-04-26

kuku@kuku-desktop:~$ gpg -K
kuku@kuku-desktop:~$
kuku@kuku-desktop:~$ gpg --list-keys
/home/kuku/.gnupg/pubring.gpg
------------------------------
pub   1024D/4B07D612 2009-04-26
uid                  kuku <kuku@gmail.com>
sub   2048g/A2DCF8C5 2009-04-26

kuku@kuku-desktop:~$ 

```


Ooboontoo 9.04

---

### Post by rbhkamal on 2009-04-27
Please help...

---

### Post by rbhkamal on 2009-04-29
help please [-o<

---

### Post by spiderbatdad on 2009-04-29
not sure what is going on...sounds like you deleted one of the keys...you need a pair. Check out this link, and install seahorse or use terminal. Generally you can't decrypt your own encryptions unless you have the private key.
[http://www.ubuntu-unleashed.com/2008/02/beginners-guide-for-gnupg-in-ubuntu.html](http://www.ubuntu-unleashed.com/2008/02/beginners-guide-for-gnupg-in-ubuntu.html)

---

### Post by rbhkamal on 2009-04-29
Oh... damn!

The public key (.asc) is used for encrypting files and the private key is used for decryption... :( :(

I only have the stupid public key... which cant's decrypt the file.

I'm dead

---

