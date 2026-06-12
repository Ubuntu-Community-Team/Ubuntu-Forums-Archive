---
title: "Same-gnome / Sweel foop"
date: 2010-05-01
forum: Gaming &amp; Leisure
---

### Post by hype on 2010-05-01
Ok, so this would not look like a big change for most of us, but my parents were used to play "same-gnome"

 Since Lucid, same-gnome has been replaced by Sweep foop and it is probably linked to the fact that it has become totally slow, CPU consuming, and finally just totally unplayable.

 I cant understand how such a basic game (that used to work perfectly with same hardware) now takes like 5 seconds to refresh the display.

 So, here is my question: is it possible to have Same-gnome back?

  Or Is it possible to disabled totally useless and pointless 3d effects used by default? (no options found in gconf-editor neither)
 

 Did anyone ever play that game? I didnt exept a few minutes ago after my mum complaint after Lucid upgrade, but how could anyone seriously need any fancy visual effexts for such a basic game really??

---

### Post by zebbers on 2010-05-01
Same Gnome was fine as it was. This was just another thing to change(like the buttons) for the sake of change. This swill poop game is horrendously unplayable and should never have made it into lucid.:-k

---

### Post by AnRa on 2010-05-03
You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb) ;-)

---

### Post by hype on 2010-05-04
You got a big thank from my parents. :p

---

### Post by scorptig on 2010-05-05
> **AnRa said:**
> You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb) ;-)

One major problem Swell foop needs to be removed, when you do so, your asked to remove gnome-games.

So request to Ubuntu to drop Swell foop, and re-introduce same-gnome game.

I have two computers running in Bar, this game same-gnome is very popular in this new release Lucid Lynx it was omitted.

---

### Post by hikaricore on 2010-05-06
Probably best to report it on launchpad.  Then some ignorant dev can tell you that it was done for "a good reason".

---

### Post by basementwall on 2010-05-06
> **AnRa said:**
> You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb) ;-)

Is there a package out there for the whole gnome-games package from Karmic? Like someone else said, we have to remove gnome-games to install the old Same Gnome, but I want the other games too--but I'm happy to have Karmic versions!

(Sorry to be such a noob. I browsed to the folder [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb") but couldn't figure out which one to get.)

---

### Post by djchandler on 2010-05-07
> **hikaricore said:**
> Probably best to report it on launchpad....

Yes, please, everybody post your problems with this package to launchpad. I'm getting segfaults almost every time I try to play this game. Even if you don't post a comment, click where the question is asked if the bug affects you and answer "yes, this bug affects me."

If apport isn't catching the crash (it doesn't on two of my intallations), check in /var/log/messages and see if you are getting anything like this:

May  6 22:31:01 tobuntu kernel: [21279.514692] seed[6827]: segfault at 20 ip 00007f7de5894fd0 sp 00007fff41d773e8 error 4 in libclutter-glx-1.0.so.0.200.4[7f7de5868000+f0000]

[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/574876](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/574876)

In the meantime, here's the link for the AMD64 version too:

[http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu3_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu3_amd64.deb)

---

### Post by djchandler on 2010-05-07
> **basementwall said:**
> Is there a package out there for the whole gnome-games package from Karmic? Like someone else said, we have to remove gnome-games to install the old Same Gnome, but I want the other games too--but I'm happy to have Karmic versions!

(Sorry to be such a noob. I browsed to the folder [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb") but couldn't figure out which one to get.)

At your own risk, you may want to try this:

[http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/gnome-games_2.28.0-0ubuntu3_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/gnome-games_2.28.0-0ubuntu3_all.deb)

Let us know how/if it works for you. It looks like it's a metapackage .deb file to me. It's built for Gnome 2.28 (as in Karmic), not 2.30. That's the very latest package, from February, but that is *not* the Lucid package. That package is 2.30.0-0ubuntu6.

BTW, uninstalling swell-foop just uninstalls swell-foop and the metapackage gnome-games. All the other games are left intact. The message synaptic gives about uninstalling gnome-games is a bit misleading, especially to some of us who have tried removing a certain package only to see a cascade effect on dependencies. That's not the case in this instance.
:guitar:

---

### Post by basementwall on 2010-05-07
Ok, it finally worked for me. Here's how:

[LIST=1]
[*]Used Synaptic to uninstall gnome-games, which to my surprise didn't uninstall all the games! (Is that something worth reporting in launchpad--that as a Ubuntu newbie, this didn't function the way I expected?)
[*]Tried installing the old gnome-games .deb that djchandler recommended, but got a package installation error--something about Blackjack.
[*]But now that gnome-games was uninstalled, I tried installing the older same-gnome .deb that AnRa suggested--and it said it conflicted with the currently installed swell-foop. (This surprised me, since I thought uninstalling gnome-games would make swell-foop go away too.)
[*]Used Synaptic to uninstall swell-foop.
[*]Tried installing the older same-gnome .deb again, and it works!
[/LIST]

---

### Post by markweaver on 2010-05-10
Thank you for showing me how to easily change swell foop to same gnome. I clicked on the "this effects me" in the swell foop bug. I also noticed the undo last move didn't work in swell foop. And, it didn't save any scores. But then, same gnome says my scores aren't in the top ten, though the scores are blank. I'm off to look into that.

---

### Post by Kilarin on 2010-05-12
Uninstalling Swell Foop, and gnome-games allowed me to re-install same gnome (which my wife loves)
BUT, I DID lose several games.  
Four-In-a-Row
Iagno
Klotski
Tali
Tetravex
Gnometris
Nibbles
Robots
Black Jack
Freecell

Is there any way to reinstall the gnome games package without swell foop so I can get the rest of these back?

thanks.

---

### Post by djchandler on 2010-05-18
> **markweaver said:**
> Thank you for showing me how to easily change swell foop to same gnome. I clicked on the "this effects me" in the swell foop bug. I also noticed the undo last move didn't work in swell foop. And, it didn't save any scores. But then, same gnome says my scores aren't in the top ten, though the scores are blank. I'm off to look into that.

When swell foop installs, it changes your same-gnome scores file name if you upgraded. On a fresh installation, you need to create these files to keep your scores for same-gnome or change the swell-foop scores data file name.

Note: *Follow the example for the small layout then repeat the instructions for medium and large layouts.*

Here's the names of the files that need to be created:

/var/games/same-gnome.Small.scores
/var/games/same-gnome.Medium.scores
/var/games/same-gnome.Large.scores

You can use gedit and save an empty file with the right file name to your home directory, then copy it to the /var/games directory.

After creating the empty files, open a terminal window and enter:

**sudo cp same-gnome.Small.scores /var/games**

If you upgraded from a previous version of Ubuntu and want to keep your old same-gnome high scores, change the file name back to the  appropriate one for same-gnome.

**sudo mv /var/games/swell-foop.Small.scores /var/games/same-gnome.Small.scores**

Disclaimer: I may not be remembering the actual swell-foop scores data file name correctly--use nautilus to make sure you have the right file name for swell-foop. The file names for the same-gnome scores are correct.
:popcorn:

You people have gotten me hooked on playing this game. I had not even tried it until this thread got started.

---

### Post by scratchr on 2010-05-21
> **AnRa said:**
> You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb) ;-)

Thank you!!!!!!!!!!

I love this game!

---

### Post by poliltimmy on 2010-05-25
I would like to know how to get the old gnome-games package in full. My 5 year old granddaughter is devastated! removing the most popular game native to Ubuntu was not a smart move by what is supposed to be intelligent people.

---

### Post by poliltimmy on 2010-05-26
> **Kilarin said:**
> Uninstalling Swell Foop, and gnome-games allowed me to re-install same gnome (which my wife loves)
BUT, I DID lose several games.  
Four-In-a-Row
Iagno
Klotski
Tali
Tetravex
Gnometris
Nibbles
Robots
Black Jack
Freecell

Is there any way to reinstall the gnome games package without swell foop so I can get the rest of these back?

thanks.

Nope and they do not care either. Linux has never cared about gamers. They are becoming MS light. Forcing programs like Evolution and Empathy and the disaster Pulse, that can not be removed, without causing problems, meaning forced bloat. Sound familiar?. So much for 'freedom'. I know have to do a fresh install (read regression). Pain the ***, so my wife and my granddaughter can both have their games. Gee thanks!

---

### Post by khansolo on 2010-06-10
I have my favorite game back. Thank you kind people.

---

### Post by Kilarin on 2010-07-09
A recent upgrade wiped out same-gnome again.  how odd.  I reinstalled and it works fine again.

I really don't understand why I can't have same gnome AND the rest of the games package at the same time.  It seems VERY strange to tie them all together so tightly that it's an all or nothing deal.

Anyway, one small note.  My wife has been complaining about the scores for same-gnome being gone.  After reading djchandler's very informative post, I just did a sudo cp for each of the swell-foop score files to the same-gnome score files.

BUT, another step was required to make the scores work.  I had to change the permissions on each of the same gnome score files so that group games had read-write access.

I did this by doing a sudo nautilus and then browse into /var/games.  Right click a score file.  Go to the "Permissions" tab.  Click the GROUP and change to GAMES.  change the   access under groups to READ AND WRITE.  Do that for each score file.

---

### Post by michaelc.nash on 2010-08-06
> **basementwall said:**
> Ok, it finally worked for me. Here's how:

[LIST=1]
[*]Used Synaptic to uninstall gnome-games, which to my surprise didn't uninstall all the games! (Is that something worth reporting in launchpad--that as a Ubuntu newbie, this didn't function the way I expected?)
[*]Tried installing the old gnome-games .deb that djchandler recommended, but got a package installation error--something about Blackjack.
[*]But now that gnome-games was uninstalled, I tried installing the older same-gnome .deb that AnRa suggested--and it said it conflicted with the currently installed swell-foop. (This surprised me, since I thought uninstalling gnome-games would make swell-foop go away too.)
[*]Used Synaptic to uninstall swell-foop.
[*]Tried installing the older same-gnome .deb again, and it works!
[/LIST]

Thank you very much for your instructions, but I have hit a snag. I used the Synaptic package manager and 'completely removed' both gnome-games and swell-foop at the same time, then clicked the link to the older gnome-games package.

That opened it with the GDebi Package installer, and I got the error message:
Error: Dependency is not satisfiable: gnome-blackjack

Does anyone have any ideas? My mum loves to play this game, and if I had known that some idiot developper would remove a perfectly good game and replace it with a crippled and vastly inferior version, I would never have 'upgraded' to 10.04!

---

### Post by michaelc.nash on 2010-08-06
A-ha! I have cured my own problem, and it is simple :D (still should not have to be necessary, though, but that's another matter).

Having tried to install the older gnome-games .deb package and failed, I started looking in its web directory, and lo and behold, there were two .deb packages specifically for same-gnome.

I installed one of those, and it works. Not tested any of the scoreboard things yet, but I presume all your fixes will work.

The web directory is [here]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/"), and the specific package I used is [here]("http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu3_i386.deb").

It won't restore all the other removed games, but it seems pretty foolproof for restoring SAME Gnome.

---

### Post by Kilarin on 2010-10-08
I just installed Maverick, and it uninstalled same gnome.
Installing from the the above link: [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb)
worked fine and now I've got same gnome back.

But then I got to wondering, did they make any changes that would let me get my OLD games back?  So I pulled up the software center and tried to install Robots.   

IT WORKED!

Now my wife can play Same Gnome and I can play Robots on the same machine!!!!  (Yeah, it doesn't take much to get me excited) :)

---

### Post by basementwall on 2011-04-30
At the risk of showing my absolute ignorance of these things, I have a question about same-gnome in 11.04. (I'm still running Lucid.)

Since the desktop interface is new, is it possible that if I upgrade to 11.04, same-gnome won't work anymore, as a Gnome-based game?

Thanks for your help, pals.

---

### Post by Patsfriend on 2011-12-02
Hello AnRa-

I have been having the same problem... However, the link given in your post ( and others) is no longer available.
Is htere another way I can get the older version of Gnome games?

Thanks in advance,
I also posted the qustion to Irvine on another thead... Sorry I am very new at this.

Patsfriend 

> **AnRa said:**
> You can install the package from Karmic: [http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/same-gnome_2.28.0-0ubuntu1_i386.deb) ;-)

---

### Post by poliltimmy on 2011-12-03
This is the package I have running in 10.04. I have no idea if it will work in any others. All the dependencies are there also. It does mess with updates though, asking me to do a partial upgrade in Update manager. I just update through synaptic now. I had to wipe out all references to the installed gnome-games version to install it.

[http://pkgs.org/debian-lenny/debian-main-i386/gnome-games_2.22.3-3_i386.deb.html](http://pkgs.org/debian-lenny/debian-main-i386/gnome-games_2.22.3-3_i386.deb.html)

Actual package i used was.....

mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.22.3-0ubuntu2_all.deb

I got the dependencies there also. Make sure all the version numbers match.Why they can not just give us our game back is anyones guess. Good luck!

---

### Post by Patsfriend on 2011-12-03
[SIZE=2]Hello All- Thanks for all of the good info.

However, After finding Two apparenty good download packages. 
I ran into an installation problem with each one:

Using the GDebi Package Installer for .deb files the error message reads:

 <message title bar> [/SIZE][SIZE=2] " gdebi-gtk
  Could not open ' same-gnome_2.28.0-0ubuntu1_i386.deb' The package  might be corrupted or you are not allowed to open the file. Check the  permissions of the file"[/SIZE]

[SIZE=2].... and the other package with the same results....

 [/SIZE][SIZE=2] <message title bar>[/SIZE][SIZE=2] " gdebi-gtk
  Could not open ' same-gnome_2.28.0-0ubuntu3_i386.deb' The package might be corrupted or you are not allowed to open the file. Check the permissions of the file"

I have logged in as administrator and changed all of the .deb files permissions to read/write.
Still get the same message.

Maybe someone could let me know if there is another installation method. [/SIZE]
[SIZE=2]Thanks in advance.[/SIZE]
- Patsfriend

---

### Post by poliltimmy on 2011-12-04
Try this package. As I remember I had a bunch of problems too. This might be the package I used. My memory ain't what it used to be.

[http://pkgs.org/debian-lenny/debian-main-i386/gnome-games_2.22.3-3_i386.deb/download/](http://pkgs.org/debian-lenny/debian-main-i386/gnome-games_2.22.3-3_i386.deb/download/)

---

### Post by Patsfriend on 2011-12-04
Thanks for you efforts, Tried it as well.... got much further along
yet, Failed on Dependency error.

   ERROR: Dependency is not satifiable" gnome-games-data (>= 1:2.22)

it is Greek to me.

> **poliltimmy said:**
> Try this package. As I remember I had a bunch of problems too. This might be the package I used. My memory ain't what it used to be.

[http://pkgs.org/debian-lenny/debian-main-i386/gnome-games_2.22.3-3_i386.deb/download/](http://pkgs.org/debian-lenny/debian-main-i386/gnome-games_2.22.3-3_i386.deb/download/)

---

### Post by Lars Noodén on 2011-12-05
It would be easier if it were packaged and part of the official repository, either as part of another package or standalone.

[https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/900279](https://bugs.launchpad.net/ubuntu/+source/gnome-games/+bug/900279)

---

### Post by lm13700 on 2011-12-21
I hate swell foop it runs very slow on my corei5.:(
SameGnome ran very fast on my old single core p4 1.8:P

SameGnome is a much better name for the game than swell foop:confused:

---

### Post by Lars Noodén on 2011-12-22
What can be done to have SameGnome in the repository while SwellFoop is being worked on?

---

### Post by kidguayas on 2012-06-27
Hey do you have any idea how to install blackjack on ubuntu 12.04?

---

