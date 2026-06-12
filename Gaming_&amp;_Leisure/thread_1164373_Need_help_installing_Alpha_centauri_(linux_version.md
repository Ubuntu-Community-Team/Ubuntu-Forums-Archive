---
title: "Need help installing Alpha centauri (linux version) on Xubuntu"
date: 2009-05-19
forum: Gaming &amp; Leisure
---

### Post by mal1958 on 2009-05-19
I have a copy of the Linux version of the Alpha centauri Alien crossfire Planet pack from my brother.  I have tried several times to patch the thing, but to no avail.  I have tried to follow the instructions here [http://lordhedgehog.hedgie.com/smac/](http://lordhedgehog.hedgie.com/smac/) and met with no success.  At first I kept getting the message that linux_patch could not be found, untill I renamed the directory in the fixed patch from alpha to x86.  Then the message changed to unexpected "(" or something.  Has anybody gotten the game to work?  Here are the base specs of my system:


[LIST]
[*]Pent 3  1 ghz
[*]384 megs ram
[*]60 gig HD
[*]Nvidia 6200 vid card w/256 megs vid ram
[*]Sound Blaster Audigy sound card
[*]Xubuntu 9.04  [COLOR=Red](edited in)[/COLOR]
[/LIST]
  ****  I am a NOOB, so I ask that any reply be in simple english.  I have no knowlege of tech talk, save to a VERY minor degree.

   Can anybody help me?

---

### Post by MDxm on 2009-05-19
Don't have the game, but tried this tutorial? [http://patrick.wagstrom.net/weblog/2005/03/07/alphacentauri/]("http://patrick.wagstrom.net/weblog/2005/03/07/alphacentauri/")

---

### Post by mal1958 on 2009-05-19
> **MDxm said:**
> Don't have the game, but tried this tutorial? [http://patrick.wagstrom.net/weblog/2005/03/07/alphacentauri/](http://patrick.wagstrom.net/weblog/2005/03/07/alphacentauri/)


Thanks, But I already did.  I am looking for some plain talk type of tutorial that will walk me through the steps, including how to change a directory from root to mine.  As I said in the first post in this thread, I am a [COLOR=Red]NOOB[/COLOR] and as such I need a gratuitous bit of hand holding through this.  Being fifty years old doesn't help much, since I cannot soak up the knowledge as I did when I was eighteen, or even at thirty.  So I guess I am an [COLOR=Red]OLD NOOB[/COLOR] which is worse then a general NOOB:p.

Mike

---

### Post by oldrocker99 on 2009-05-19
/ = root
~/ = your home directory

<- 60 yrs...

:guitar:

---

### Post by mal1958 on 2009-05-19
Thanks oldrocker99.  Now I don't feel so out of place.  But what I was referring to by the changing of root to mine was the permissions.  According to one tutorial, I have to change the permission of a directory to play the game since the Loki installer seems to install as root.   I also still need to find a plain language tutorial for fixing Alpha Centauri Planet pack so I can play it.  I am an old Sid Meier's fan[COLOR=Red](atic)[/COLOR] and want to play my favorite games in my favorite OS.  If you know of any such tutorials for a total NOOB then please post the link here, or give me the directions.  I miss my fix of SMAC & SMAX.  Not to mention Civ 3, Gettysburg, and a few others.  I have managed to get Pharaoh, and Caesar 3 running, with sound! in wine, but I want my Sid Meier's games :cry: and find it frustrating to be thwarted.

Mike

---

### Post by MDxm on 2009-05-20
First we need to establish exactly how Old Noob you are. I just started using Ubuntu a few months ago, so. :p

'sudo' and your user password gives you administrative previlegies.
BTW, being old does not mean you can't still soak up new knowledge, not ever.
But do you know how to sudo yet, Mike? ;)
the likes of "sudo ./update.sh" for example?


I Might have to resort to piracy before I can help you any further though. :p

---

### Post by mal1958 on 2009-05-20
> **MDxm said:**
> First we need to establish exactly how Old Noob you are. I just started using Ubuntu a few months ago, so. :p

'sudo' and your user password gives you administrative previlegies.
BTW, being old does not mean you can't still soak up new knowledge, not ever.
But do you know how to sudo yet, Mike? ;)
the likes of "sudo ./update.sh" for example?


I Might have to resort to piracy before I can help you any further though. :p


  Oh Yeah, I know how to use the sudo command and such.  What I find boggleing is the fact that I cannot run the patch.  it either says that lokipatch cannot be found, or 'unexpected "(" encountered' what ever that means.  At the one tutorial site they gave a link to download the latest patch (supposedly on filefront) and when I click on it I get a file not found.  Google has not been able to help me, and Loki is gone.  So unless I can find a patch that does work, I am SOL.

    And what I meant by saying that being old, and knowledge, is that it is harder to learn something.  At least for me.  When I bring up a terminal and try to pull up a file and directory listing, my fingers seem to type 'dir' even though I know that it should be 'ls'.  I spent too much time in the old dos shell days, I guess :D.  But yeah, I know how to list files, move them, copy them, remove them, and all that.  I am no novice to a shell.  It's just that I spent too much in a DOS shell, and now I have to break old habits.  Not to mention, with dos there was never this much control.  It takes a bit to get used to it, that and a lot of hand holding through the process.

Mike

---

### Post by Tarvok on 2009-05-21
Try to start from scratch if you can, and give the older kernel instructions a try. Let us know what you don't understand. I just got it working on my computer about a week ago using this set of instructions, plus a minor edit to the install script to account for my 64 bit processor, so I can vouch for that particular set of instructions.

---

### Post by mal1958 on 2009-05-21
> **Tarvok said:**
> Try to start from scratch if you can, and give the older kernel instructions a try. Let us know what you don't understand. I just got it working on my computer about a week ago using this set of instructions, plus a minor edit to the install script to account for my 64 bit processor, so I can vouch for that particular set of instructions.

  Will do, Tarvok.  I am going to fight to keep this OS, just as hard as I fought to config Bill Gates 'Brain-Dead' Child 'Winblows'.   

Mike

[COLOR=Red]Edit:   Do yiou know a valid link to a valid copy of the patch for the game?  The patch link on the site that MDxm provided is giving me a no file or directory found message,
Mike[/COLOR]

---

### Post by Grishka on 2009-05-21
> **mal1958 said:**
> [SNIP] When I bring up a terminal and try to pull up a file and directory listing, my fingers seem to type 'dir' even though I know that it should be 'ls'. [/SNIP]

sorry for an offtopic, but you certainly don't HAVE to use ls, instead of dir. I'm using dir all the time, since I'm not too keen on coloured filenames. most problems have different solutions, most things can be done in a few different ways. so don't force yourself to do things against yourself. use what works best for you. your knowledge of dos should help, not hinder you. anyway, you may have trouble running some of these games. loki patches are outdated, and with no access to their source, it's nearly impossible to fix them. I think the easiest way to run some of these games would be virtualising windows 95 or 98, if you have an old copy lying around. try [virtualbox](http://www.virtualbox.org/). sorry I couldn't be of more help in this particular case.

---

### Post by mal1958 on 2009-05-22
Ok, progress so far.  still have not found a working patch.  All links to any of the copies of smac-6.0a-x86.run or smac-6.0b-x86.run seem to have vanished off the face of the earth.  If anybody has a stray copy floating around on your HD please could you email it to me, or upload it to a file hold place where I can download it?   

    Found out that my cats got a hold of my smac planet pack cd and had fun with it on the floor.  They seem to love those giant shiney hockey pucks.  Luckily, I also found an iso image of the game so no foul there.  Now I am just waiting on the patch.  can anybody help me there?

Mike

---

### Post by peyre on 2009-09-02
Mal1958, did you finally get the game working?  It took me a while to work out myself, but I finally got it working on my machine.  Basically, I had to install it to my home folder rather than /usr/local.  These are the instructions I wrote up for future reference:


Install the game to somewhere in your home directory (don't let it install to the default, /usr/local/games/smac).  I installed it to /home/leon/Games/smac.  Install the whole game, of course.

Exit when setup is complete.

Patch the program by running smac-6.0b-x86.run.

Open loki_compat_libs-1.1.tar.bz2 and unzip the Loki_Compat to the Alpha Centauri folder.

You'll have to give the system extra information.  (Replace /home/leon/Games/smac with the path to the Alpha Centauri folder).  Use the following to open:

ALPHA CENTAURI
LD_PRELOAD=/home/leon/Games/smac/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib/libX11.so /home/leon/Games/smac/smac.dynamic

ALIEN CROSSFIRE
LD_PRELOAD=/home/leon/Games/smac/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/lib/libX11.so /home/leon/Games/smac/smacx.dynamic

TO CREATE ICONS

Create script files, e.g. runsmac and runsmacx, in the Alpha Centauri directory, containing (respectively) just the code above.

Make them executable (open a terminal window there and enter "chmod +x runsmac" and then "chmod +x runsmacx").

Create Launchers that point to those scripts.

---

