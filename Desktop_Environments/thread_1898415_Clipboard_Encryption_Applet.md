---
title: "Clipboard Encryption Applet?"
date: 2011-12-21
forum: Desktop Environments
---

### Post by StewartM on 2011-12-21
I'm used to using the Seahorse encryption-applet in GNOME 2, which was a handy-dandy way to encrypt and/or sign anything on the clipboard, no matter what application it was in. (I preferred using that for GnuPG use rather than email plugins, which usually seem to act as 'black boxes'). Now, it seems to be gone in GNOME/Unity. Or at least I can't find it.

a) Am I wrong, is it really still there in Unity/GNOME, just hidden somewhere?

b) Is there a corersponding app in KDE or Xubuntu that one can add to a panel or as an icon?

Thanks for any replies.

StewartM

---

### Post by vintermann on 2012-01-14
I'm not aware of any, but I am on the lookout for a feature like this too. Something to quickly encrypt and sign the clipboard, selected text, files in Nautilus etc.

---

### Post by Telengard C64 on 2012-01-14
Not really what you asked for, but related: 
[Encryption support for Emacs](http://www.emacswiki.org/emacs/EasyPG).

---

### Post by StewartM on 2012-01-14
> **Telengard C64 said:**
> Not really what you asked for, but related: 
[Encryption support for Emacs](http://www.emacswiki.org/emacs/EasyPG).

Thanks. 

On my laptop, which runs 11.10 with a combination of Unity/GNOME 3/Classic GNOME/KDE/Lubuntu, I have KGPG. It has the native ability to encrypt OR sign clipboard text, but not the ability to do both. However, a user can encorporate custom commands for it. 

I know the GNUPG command for encrypting and signing into ascii format:

gpg --armor --recipient [recipient] --encrypt --sign my-file.txt 

but do not know the command for doing that with clipboard text to add that to KGP's menu.

Has anyone done this with KGPG?

The word is that GNOME will re-introduce the Seahorse sign and encrypt applet with 12.04 and that there just wasn't enough time to develop it for the current GNOME release.

StewartM

---

### Post by StewartM on 2012-01-14
> **Telengard C64 said:**
> Not really what you asked for, but related: 
[Encryption support for Emacs](http://www.emacswiki.org/emacs/EasyPG).

I see that EasyPG is included by default in Emacs 23. I'll look in the repositories to see if that's in 11.10 (I'm typing this from a 10.04 box, and GNOME Emacs is in the 10.04 repositories).

Thanks again.

StewartM

---

### Post by Telengard C64 on 2012-01-14
[Emacs 23 in 10.04 Lucid](http://packages.ubuntu.com/lucid/emacs)

[Emacs 23 in 11.10 Oneric](http://packages.ubuntu.com/oneiric/emacs)

I don't know Damien Cassou, and have not tried it, so decide for yourself whether this is trustworthy:

[Emacs-snapshot versions : Damien Cassou: PPA](https://launchpad.net/~cassou/+archive/emacs)

---

