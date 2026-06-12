---
title: "Installing Tor"
date: 2006-07-25
forum: Desktop Environments
---

### Post by SpongeBob SquarePants on 2006-07-25
I've had Tor running on Ubuntu many a time and with no problems at all. For some reason however, when I try to install it after a recent OS reinstall I get the following.......

Jul 25 15:05:59.086 [notice] Tor v0.1.0.16. This is experimental software. Do no t rely on it for strong anonymity.
Jul 25 15:05:59.087 [warn] /var/lib/tor is not owned by this UID (113). You must  fix this to proceed.
Jul 25 15:05:59.088 [err] options_act(): Couldn't access/create private data dir ectory /var/lib/tor
Jul 25 15:05:59.088 [err] init_from_config(): Acting on config options left us i n a broken state. Dying.

Anyone know how I fix the problem?


Cheers chaps.....Bob

---

### Post by SpongeBob SquarePants on 2006-07-25
bump

---

### Post by SpongeBob SquarePants on 2006-07-26
Just in case anyone's interested in solving the above problem I found that........

sudo chown yourusername /var/lib/tor

.....before rerunning Tor worked.

---

### Post by j-strap2 on 2006-07-26
Bob, which version of Tor are you running and who is the packager? Ideally, Tor should be run as a service in its own user account.

---

### Post by SpongeBob SquarePants on 2006-07-26
> **j-strap2 said:**
> Bob, which version of Tor are you running and who is the packager? Ideally, Tor should be run as a service in its own user account.

I'm running version 0.1.0.16-lubuntu2 from synaptic

---

### Post by j-strap2 on 2006-07-30
> **SpongeBob SquarePants said:**
> I'm running version 0.1.0.16-lubuntu2 from synaptic

I recommend that you upgrade to the latest stable release. Many people have reported problems with the standard repo version of Tor. Follow the instructions on the Tor website here:

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")

---

