---
title: "Can't figure out this error."
date: 2006-07-21
forum: Desktop Environments
---

### Post by Roasted on 2006-07-21
I'm having some trouble. I posted in another section but I'm not getting very many leads. I'm on Ubuntu, just installed it a few days ago, and I been trying to install the mp3 codecs for totem and amarok to run. Can anyone help with this problem? 

Maybe my repositories are off, I don't know. I don't know how to determine whether I changed them right or not. Maybe someone can shed some light on this?

Anyway, I get this error anytime I try to reload synaptic. I also get it in the software manager when I try to reload my repositories.

Error:

W: GPG error: [ftp://cipherfunk.org](ftp://cipherfunk.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4CF19C3233BAC1B3

](*,) :(

---

### Post by ciscosurfer on 2006-07-21
You need to add the GPG key to your keychain by issuing these commands, replacing 'KEY' with '33BAC1B3'```
gpg --keyserver subkeys.pgp.net --recv KEY
gpg --export --armor KEY | sudo apt-key add -
```

---

### Post by Roasted on 2006-07-21
Is this a good thing?


jason@Linux:~$ gpg --keyserver subkeys.pgp.net --recv 33BAC1B3 gpg --export --armor 33BAC1B3 | sudo apt-key add -
Password:gpg: "--armor" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "gpg" not a key ID: skipping
gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: key 33BAC1B3: "cipherfunk.org packages <packages@cipherfunk.org>" not changed
gpg: key 33BAC1B3: "cipherfunk.org packages <packages@cipherfunk.org>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

---

### Post by Roasted on 2006-07-21
Also I just realized during flash videos I have no sound. ](*,)

---

### Post by ciscosurfer on 2006-07-21
> **Roasted said:**
> Is this a good thing?


jason@Linux:~$ gpg --keyserver subkeys.pgp.net --recv 33BAC1B3 gpg --export --armor 33BAC1B3 | sudo apt-key add -
Password:gpg: "--armor" not a key ID: skipping
gpg: "--export" not a key ID: skipping
gpg: "gpg" not a key ID: skipping
gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: key 33BAC1B3: "cipherfunk.org packages <packages@cipherfunk.org>" not changed
gpg: key 33BAC1B3: "cipherfunk.org packages <packages@cipherfunk.org>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
You need to enter each command separately: first issue```
gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
```then hit enter. (sometimes this hangs as the server tries to obtain the key...keep trying if nothing happens after a minute or so {CTRL-C to quit, then try again} Then enter the next line in the terminal:```
gpg --export --armor 33BAC1B3 | sudo apt-key add -
```at which point a password prompt will appear--go ahead and enter your user's password. You want your output to look like this:```
snoopy@myhome:~$ gpg --keyserver subkeys.pgp.net --recv 33BAC1B3
gpg: requesting key 33BAC1B3 from hkp server subkeys.pgp.net
gpg: key 33BAC1B3: "cipherfunk.org packages <packages@cipherfunk.org>" not changed
gpg: Total number processed: 1
gpg:                    unchanged: 1
snoopy@myhome:~$ gpg --export --armor 33BAC1B3 | sudo apt-key add -
Password: *ENTER YOUR PASSWORD HERE*
gpg: no ultimately trusted keys found
OK
```

---

### Post by ciscosurfer on 2006-07-21
Search Ubuntu forums for threads on Flash and Sound issues, Flash and Firefox issues--they are varied and many...choose the one that best suits you. :D

---

### Post by Roasted on 2006-07-21
Okay. My output looks directly like that. Am I in the clear now? 


Also - I noticed in your example you have the key plugged in to snoopy, your username. What exactly is that? I mean... I didn't just give out my social security number or anything, did I? :mrgreen: :confused: 

So, trying to figure out my next step. I guess I should make sure all of my repositories are right where I need them, THEN continue on getting whatever codecs or plugins I may need. I want to get Totem and Amarok working completely, just so I have other players to tinker with and see what I like most. Then I need to get the sound working on flash and mozilla. I also think I need to get the media player plugin so I can watch imbedded media player movie clips on web sites. This sound like a good plan? Or would you do something in a different order?

---

### Post by bruenig on 2006-07-21
> **Roasted said:**
> Also I just realized during flash videos I have no sound. ](*,)
If you have any other sound making thing going while there is flash going, flash sound will be disabled. The only way I have found to get around this is to reboot the computer. I have tried restarting x, but it doesn't seem to work.

---

### Post by ciscosurfer on 2006-07-21
You're good to go!  You are basically just importing the GPG key from cipherfunk and then importing that key to your GPG keychain--you're username@hostname are not transmitted \\:D/

There are GUIs for GPG if you'd rather go that route.  If you use KDE then use 'kgpg' (download via aptitude, apt-get, synaptic, or whatever you use--they are all apt-based).  If you use GNOME you should check out 'seahorse' (again download via whichever means you use) and will then be located in GNOME menus as Encryption Key Manager.

Yes, you should make sure all the repos you want to use are setup fully before you start trying to download apps (not all repos require GPG signatures, some do, some don't...)

If you want an absolutely awesome way of getting all your needs met, then try out Automatix.  Go to Getautomatix.com and follow the instructions on the home page.  It's a streamlined way of obtaining everything you need.  I use the Automatix scripts and I love it--you probably will too! :D

---

### Post by tewest99 on 2007-08-29
This might not be the answer you're looking for but I've been using XMMS for mp3's and it's a great utility  :-)

---

