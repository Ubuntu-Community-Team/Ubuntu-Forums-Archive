---
title: "Problem installing True Combat Elite"
date: 2007-02-15
forum: Gaming &amp; Leisure
---

### Post by Fyrzen_ on 2007-02-15
I just did a fresh install of edgy and installed enemy-territory. But when i try to install the latest tce this happens:
```
$ sudo sh true*
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.49b-english-2 Installer...............................
./search.sh: 36: Syntax error: Bad substitution

```

Im thinking of downloading the regular 0.49 and the the patch to 0.49b, but is there a quick fix for this problem?

---

### Post by Kelnoky on 2007-02-15
Same thing happened to me. You can either extract the contents of the *.run file and then extract the contents of the tcetest archive into your ET folder or you could just download the install archive from the TCE homepage and follow the alternative instructions there.

---

### Post by Fyrzen_ on 2007-02-16
How do you extract a .run script? Google offered me no answers.

I just moved the tcetest archive from an unpatched .zip version to the et folder and copied the patch files onto that. It works, but it lacks the launcher script the installer would have created.

Just a heads up though, if you're downloading the 0.49 Full Version from truecombatelite.net, I'd advise to steer clear of the first mirror "Eclipse Sports - TC:Elite Full Install Linux" and go with one of the "All OS" ones, I'm not sure this is because the file mirrored is corrupt, but the one i downloaded from eclipse failed to extract.

---

### Post by el_itur on 2007-03-14
TCE doesn't like dash (ubuntu default's CLI). 
try this:
sudo dpkg-reconfigure dash

and select no

then run the script again.

After that I guess you could reconfigure dash as default cli again

---

### Post by Lystrodom on 2007-03-15
So, um, is there really only one server? From the amount of people I'd seen supporting this game, I had expected more than one server. As it is, that's all my client's finding.

Also, I can't connect to that server. It gets to a point where it's going to download a sound, and then just starts over, reconnecting to the server.

---

### Post by el_itur on 2007-03-15
Last version of enemy territory just broke the server browser on TCE. The only ones who suffer this problem are the linux gamers because there are (and TCE devs encourage to you to try) better server browsers for windows.

So, play enemy territory until its fixed, or start crying out loud on tce forums.

---

### Post by Arcadian on 2007-03-23
> **el_itur said:**
> TCE doesn't like dash (ubuntu default's CLI). 
try this:
sudo fkg-reconfigure dash

and select no

then run the script again.

After that I guess you could reconfigure dash as default cli again

Hi All,

Just wanted to say that this worked for me, however, it should be 'sudo dpkg-reconfigure dash' as the command line, must be a typo. Cheers for sharing this guys, really keen to give it a bash! :twisted: 

Cheers!

---

### Post by hikaricore on 2007-03-23
So you gave dash a bash?

Sounds like some kinda weird abstract pun if you ask me.

---

### Post by spartan777 on 2007-05-27
uh, i try to reconfigure dash, and it just says 

```
calvin@calvin-desktop:~$ sudo fkg-reconfigure dash
sudo: fkg-reconfigure: command not found
```

is dash important?

---

### Post by el_itur on 2007-05-27
> **spartan777 said:**
> uh, i try to reconfigure dash, and it just says 

```
calvin@calvin-desktop:~$ sudo fkg-reconfigure dash
sudo: fkg-reconfigure: command not found
```

is dash important?

fkg!!!. I can't believe I've wrote that... I meat dpkg-reconfigure....


I will edit the post to avoid confusions. Cheers

---

### Post by merlyn on 2007-05-27
> **el_itur said:**
> fkg!!!. I can't believe I've wrote that... I meat dpkg-reconfigure....


I will edit the post to avoid confusions. Cheers

Hi this is horribly off topic, but I didn't realise that Ubuntu used Dash. 

Why not Bash I wonder? Is there any documentation on this, I'd like to learn more.

Cheers

---

### Post by spartan777 on 2007-05-28
thanks!

---

### Post by Rafty on 2007-05-29
```
sudo ln -sf /bin/bash /bin/sh
```
works too ;)

and to this "only-one-server" thing: that bug was fixed in tc:e 0.49b full (what is the latest version, btw!) and the servers should pop up. at first try switching the in-game server browser options. if you still get no or not enough servers install XQF (available in "add software - games")

TC:E 0.49b Fullversion: [http://liflg.org/?catid=6&gameid=52](http://liflg.org/?catid=6&gameid=52) (true.combat.elite_0.49b-english-3.run click on "[direct]"!)

good luck:D

---

### Post by Anthony T. on 2008-08-02
Worked for me, thanks bud

---

