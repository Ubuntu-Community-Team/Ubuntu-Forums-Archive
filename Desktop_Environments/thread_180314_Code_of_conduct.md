---
title: "Code of conduct"
date: 2006-05-22
forum: Desktop Environments
---

### Post by Rhapsody on 2006-05-22
Note: I actually felt the need to vent in an unrelated chatroom prior to typing this since on top of this problem, Firefox is acting up. The problem with Firefox will probably always remain a mystery though.

So, I wanted to [sign the code of conduct](https://launchpad.net/codeofconduct/1.0/+sign) (which I'm pretty sure I can adhere to, as long as I'm still allowed to yell and swear at my PC) but, as I was half-expecting, I hit a problem.

```
gpg: directory `/home/rhapsody/.gnupg' created
gpg: new configuration file `/home/rhapsody/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/rhapsody/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/rhapsody/.gnupg/secring.gpg' created
gpg: keyring `/home/rhapsody/.gnupg/pubring.gpg' created
gpg: no default secret key: secret key not available
gpg: /home/rhapsody/coc.txt: clearsign failed: secret key not available
```
This is a fairly standard problem. It's a common operation, with step-by-step instructions that don't even mention the possibility of problems.

I'm beginning to think that there is something fundamentally wrong with this install...

---

### Post by nocturn on 2006-05-22
[QUOTE=Rhapsody]
This is a fairly standard problem. It's a common operation, with step-by-step instructions that don't even mention the possibility of problems.

I'm beginning to think that there is something fundamentally wrong with this install...[/QUOTE]

The problem is that you do not have a keypair yet, so there's nothing to sign the CoC with.

If you look into gpg --gen-key or use a frontend like seahorse, you can generate the needed keys.

---

### Post by Rhapsody on 2006-05-22
Now the sign form is complaining about the lack of a public key. You people really want to make sure people are dedicated before they sign this thing, don't you? I am on the verge of giving up on this one.

---

### Post by nocturn on 2006-05-22
[QUOTE=Rhapsody]Now the sign form is complaining about the lack of a public key. You people really want to make sure people are dedicated before they sign this thing, don't you? I am on the verge of giving up on this one.[/QUOTE]

I'm not one of the developers, nor am I involved in the creation of the launchpad software.

If you do not want to go the PGP venue, you could always send in a hardcopy with a signature.  
For many of us that went the PGP route, it wasn't that hard because we routinely use it (therefor already have a keypair).

That said, if you go into your launchpad account, there is an option in the right menu 'OpenPGP keys', there, you need to upload the public part of your key to link your key to your account (otherwise anyone could create a key in your name).

---

### Post by Rhapsody on 2006-05-23
[QUOTE=nocturn]I'm not one of the developers, nor am I involved in the creation of the launchpad software.[/QUOTE]
Yeah, I'm sorry about that. It wasn't directed at you.

[QUOTE=nocturn]If you do not want to go the PGP venue, you could always send in a hardcopy with a signature.  
For many of us that went the PGP route, it wasn't that hard because we routinely use it (therefor already have a keypair).[/QUOTE]
Well the instructions seem to assume that *only* people who already routinely use the software would be following them, and I see no good reason why that would be the case. I certainly aren't a routine user.

[QUOTE=nocturn]That said, if you go into your launchpad account, there is an option in the right menu 'OpenPGP keys', there, you need to upload the public part of your key to link your key to your account (otherwise anyone could create a key in your name).[/QUOTE]
With a combination of help from the GnuPG website (mainly clarifying what is meant by a 'key ID'), I think I'm almost done with this. I think this will end up as something productive.

Edit: Yep, finally got it. This encryption stuff may come in handy later.

---

### Post by az on 2006-05-23
[QUOTE=Rhapsody]Now the sign form is complaining about the lack of a public key. You people really want to make sure people are dedicated before they sign this thing, don't you? I am on the verge of giving up on this one.[/QUOTE]
[https://wiki.ubuntu.com/GnuPrivacyGuardHowto](https://wiki.ubuntu.com/GnuPrivacyGuardHowto)

It's all there.

---

