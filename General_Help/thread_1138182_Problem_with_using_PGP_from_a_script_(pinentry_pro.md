---
title: "Problem with using PGP from a script (pinentry problem)"
date: 2009-04-26
forum: General Help
---

### Post by linuxxor on 2009-04-26
After installing ubuntu, I'm having problems with my "diary" scripts which use GPG to encrypt files. It's quite simple: it just reads passphrase from console and uses it to decrypt and encrypt files. Now GPG does not work as wanted, but it actually asks password 3 times using something called PINENTRY. I want to disable this pinentry, but no idea how...

Here are some relevent lines from my scripts:

```
read -s -e pass

gpg --passphrase $pass -o $filu --decrypt $filu.gpg   &&   wipe -f $filu.gpg

gpg -c --passphrase $pass $filu   &&   wipe -f $filu
```

---

### Post by linuxxor on 2009-04-29
Does anyone else use command line GPG on ubuntu? Why it does not accept the passphrase from command line - it should be perfectly fine command line option... 

This does not work as wanted: 
```

gpg --passphrase pass  -o text.txt --decrypt text.txt.gpg

```

---

