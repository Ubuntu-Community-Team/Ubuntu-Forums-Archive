---
title: "Trying to install SNES9x, help!"
date: 2009-09-05
forum: Gaming &amp; Leisure
---

### Post by Jerfo on 2009-09-05
Hello there! I've been trying to install snes9x and I don't know if it's because I'm plainly dumb or if I'm missing something here but I keep getting an error message when I attempt to do the key thing. This is the error message I get (some parts roughly translated from french, sorry if it's not exactly as it'd be in English, I underlined those parts so that you can identify them):


jerfo@jerfo:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6CF5CE97
[sudo] password for jerfo: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 6CF5CE97
gpg: _request for key 6CF5CE97 from server_hkp keyserver.ubuntu.com
gpgkeys: HTTP fetch error 7: couldn't connect to host
gpg: _no valid OpenPGP address(?) has been found_
gpg: _Total number of attempts: 0_Quantité totale traitée: 0

---

### Post by scragar on 2009-09-05
You don't need to do that, it just get's rid of a warning about untrusted downloads.
```
sudo apt-get install snes9x
```That should work on it's own.

---

### Post by Jerfo on 2009-09-05
Nope, didn't work, it tells me the file couldn't be found :( (And I would have felt even dumber, if relieved, had that worked lol)

---

### Post by scragar on 2009-09-05
Sorry, 
[enable multiverse first.](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Repositories%20in%20Ubuntu)
Then run that command again.


Or you could install it from the .debs
[http://packages.ubuntu.com/search?searchon=names&keywords=snes9x](http://packages.ubuntu.com/search?searchon=names&keywords=snes9x)
Scroll down to the end and click your architecture, download the .deb, then run it to launch the installer. I think you'll also need to download the zsnes package as well if you choose to do it this way.

---

### Post by Jerfo on 2009-09-05
The multiverse was already enabled and I tried to get it from the .deb, it asked to reinstall and I said yes, apparently it installed correctly but nothing happened, I searched for the program in the apps menu and there's nothing there, searched in hte /bin folder and found the 'snes9x' but if I try to run it with alt + f2 nothing happens, not even an error message :S

---

### Post by Grishka on 2009-09-05
use [this ppa](https://launchpad.net/~bearoso/+archive/ppa).

---

### Post by Jerfo on 2009-09-05
That's the PPA I've been trying to use all along.

---

### Post by RabidWeezle on 2009-09-06
can't test since I'm not home, but try:

```

cd /path/to/snes/roms
snes9x name-of-romfile.smc
```

I believe the linux version doesn't have a pretty gui frontend, you just launch it like that.

But check out their manpage to see all the available commands:

```
man snes9x
```

---

### Post by Grishka on 2009-09-06
> **Jerfo said:**
> That's the PPA I've been trying to use all along.

ah, right. you have a problem with importing the PGP key. I do it like this:
clicking the 'signing key' of this PPA (1024R/6CF5CE97) will bring you [here](http://keyserver.ubuntu.com:11371/pks/lookup?search=0xDCEF94F365801075ECBB7353C71839136CF5CE97&op=index). on this page, clicking the key/ID (6CF5CE97) will get you the [key itself](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xC71839136CF5CE97). now, just copy paste the key (from '-----BEGIN PGP PUBLIC KEY BLOCK-----' to '-----END PGP PUBLIC KEY BLOCK-----' into your favourite text editor, save as whetever.pgp, fire up System/Administration/Software Sources, and import the PGP key you've just saved. this'll do it.

---

### Post by Jerfo on 2009-09-06
Well that worked wonders, for the key at least as it no longer tells me there's an invalid key but now the problem is it doesn't do a thing. When I run 'sudo apt-get update' I don't get any new files, it does all the usual stuff but doesn't ask to install anything, same with Update Manager, I update and nothing.

---

### Post by Jerfo on 2009-09-06
Oh never mind, I figured it out myself thanks a lot for the help with the key guys, I would have never been able to get it myself! Now, off to do some classic gaming :D

---

