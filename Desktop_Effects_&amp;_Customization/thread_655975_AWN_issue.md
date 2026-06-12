---
title: "AWN issue"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by Chapeen on 2008-01-02
I'm trying to install AWN on my Gutsy and when I add this 2 lines in software sources
- deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
- deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

It gives me this error:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

Help please Thanks!

---

### Post by Mr Greencastle on 2008-01-02
The repostories you added need to be authenticated by whats known as an 'apt-key'. This is to prevent harm to your system and verify that you are the one adding the repository. 

Enter these lines into the terminal one at a time:
```
wget http://download.tuxfamily.org/syzygy42/reacocard.asc
sudo apt-key add reacocard.asc
rm reacocard.asc
```
~In-depth look at what you are doing so you can learn~
-The first line downloads the key from the internet, hence the 'wget' command (Which is essentially telling the computer to download THIS file please).
-The second line adds the adds the key you just downloaded to the 'list of keys'.
-And the third line removes the key from where you downloaded it to. It has already been added to 'the list', so the computer doesn't need to have the actual file anymore. You don't HAVE to do this, but it is recommended.

That should do it, hope it helped!

Mr Green

---

### Post by overdrank on 2008-01-02
> **Chapeen said:**
> I'm trying to install AWN on my Gutsy and when I add this 2 lines in software sources
- deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
- deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

It gives me this error:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181

Help please Thanks!

HI this may help
[http://www.peter-v.com/88/ubuntu-gutsy-update-manager-gpg-public-key-error-awm/](http://www.peter-v.com/88/ubuntu-gutsy-update-manager-gpg-public-key-error-awm/)
Edit to slow :) and a much better explanation by Mr Green

---

