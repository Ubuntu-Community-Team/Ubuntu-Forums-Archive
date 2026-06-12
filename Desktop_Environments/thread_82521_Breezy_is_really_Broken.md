---
title: "Breezy is really Broken"
date: 2005-10-26
forum: Desktop Environments
---

### Post by goneskiing on 2005-10-26
After having k3b fail to burn several times and having tried to do it from SUDO as a last resort - now I cannot log into my main account (the one I need to do SUDO from )  - Now do have to totally reinstall my system ??

Hey guys what is going on here????  These are pretty critical errors!  Is Breezy really this broken and should I just switch back to kanotix?

---

### Post by matthew on 2005-10-26
Breezy has been working perfectly for me and thousands of other people.

Breezy is not broken.

You will find help easier to come by when you choose ***not*** to start off with an accusation of incompetence.

---

### Post by afonic on 2005-10-26
You probably tried to work out the k3b problem and you messed up seriously. Its bad, but it doesn't mean it's Breezy's fault.

Try GnomeBaker as a burner, if it doesn't work too then probably something is wrong with your settings. (enable DMA maybe?). You can post more info and people will try to help you.

---

### Post by angkor on 2005-10-26
[QUOTE=goneskiing] After having k3b fail to burn several times and having tried to do it from SUDO as a last resort - [/QUOTE]

maybe k3b is broken on your system. What were the error messages?

[QUOTE=goneskiing]
now I cannot log into my main account (the one I need to do SUDO from )
[/QUOTE]

Again, what are the error messages. No one is going to be able to help you out if you don't let us know what's going on.

---

### Post by goneskiing on 2005-10-26
k3b - is taking an extremely long time to start to write (like several minutes), then long to write (simply 4 mb ) , then fails - suggests using DAO - tried that - that showed success but then the cd won't mount.

login on sudo account - gives me error message that it didn't last 10 seconds - check disk space, .... I have plenty of disk space.  Logged in under failsafe, logged out but still locked out of gnome or kde 

No CD burning and locked out of SUDO = broken to me.  Wasting 4 hrs and missing important deadline = broken to me.  Didn't have these problems before.  If there's a quick and reliable fix, good, otherwise I'm gone.

---

### Post by Ferio on 2005-10-26
It seems there are 2 factions, one being composed by those to whom Breezy works perfectly, and other composed by us (I've downgraded to Hoary) who can't even open tags in Firefox with it (literally). Neither could I burn with K3b, not opening files with OpenOffice2, and some things else. I don't think it's an accusation, it's just what happens when you don't use smileys to show your mood and you are nervous (I myself have lost my day messing around with Breezy). So let's calm down everybody and try to solve Breezy's problems if possible, I'm looking forward to come back to it. So: K3b works perfectly in Hoary, but not in Breezy, is there any difference apart from the version numbers? I mean, does Breezy use diferent libraries or something? This is not the first thread (nor the second or third) I see with this problem, and I think it's an important problem.

---

### Post by gillion on 2005-10-26
[QUOTE=goneskiing]  If there's a quick and reliable fix, good, otherwise I'm gone.[/QUOTE]

**THEN GO !** my friend and peace be with you.

---

### Post by awtomlinson on 2005-10-26
"gives me error message that it didn't last 10 seconds"

login in terminal mode.  then, 

sudo rm .ICEauthority

---

### Post by nix4me on 2005-10-26
My breezy is flawless.

nix4me

---

### Post by goneskiing on 2005-10-26
awtomlinson
"gives me error message that it didn't last 10 seconds"
login in terminal mode. then,
sudo rm .ICEauthority

thank you - easy fix 

but lack of cd burning is show stopper for me - I have to get work done - without fix I'll have to switch distros tonight.  (ps I also tried Nautilus burner - writing stopped with error msg)

I actually like Breezy - but had too many key problems and I don't feel should have been released (ie too rushed)
1) had to reinstall due to bad default us repositories - lost 6 hrs
2) had to fix really bad fonts - lost 4 hrs
3) broken cd burning - lost 5 hrs today, missed key work deadline
*** too much lost time ***

---

### Post by zenwhen on 2005-10-26
People who open their threads with comments like the ones in this one aren't worth our effort. If you ask us, we will help. If you threaten us, we will likely not. We don't OWE you anything.

---

### Post by zenwhen on 2005-10-26
People who open their threads with comments like the ones in this one aren't worth my effort. If you ask, I will help. If you threaten me, I will not.

---

### Post by kleeman on 2005-10-26
Here's a positive suggestion for the future for those with frustrations:

Find a spare partition on your system and install the development branch of Ubuntu (dapper at present). Try out everything you need for mission critical applications. Probably some of it will be broken. Carefully report the breakage with appropriate output in bugzilla. Watch as the developers fix bugs. I did this with breezy and I reported around 15 bugs. Believe it or not about 13 of them were fixed. This included some very serious ones like non-functioning network cards. 

At present I have only one minor bug in breezy. I'm sure I would have had more if I had not helped out with bugs. BTW one of Dapper's objectives is greater stability because they need to support it longer. This means the devs will be extra attentive to your bug reports.....

---

### Post by Psquared on 2005-10-26
I've not noticed anything terribly wrong with Ubunutu - certainly nothing as bad as hooking up Xpee to a network and being hacked or invaded by worms and spyware.

I have not tried to burn a CD in Breezy yet, but in Hoary I did it by using gksudo k3b. Worked perfectly and the CD sounded as good as anything I made in Xpee using Roxio or the other burning software in Media Player and Real Player.

---

### Post by afonic on 2005-10-27
[QUOTE=goneskiing]
but lack of cd burning is show stopper for me - I have to get work done - without fix I'll have to switch distros tonight.  (ps I also tried Nautilus burner - writing stopped with error msg)

I actually like Breezy - but had too many key problems and I don't feel should have been released (ie too rushed)
1) had to reinstall due to bad default us repositories - lost 6 hrs
2) had to fix really bad fonts - lost 4 hrs
3) broken cd burning - lost 5 hrs today, missed key work deadline
*** too much lost time ***[/QUOTE]

Sorry but you had a work deadline and you installed a new distro to "try out"??

I really cannot understand how you think dude. Breezy works, its NOT broken and yes, it has problem with some PC configurations and needs some tweaking.

If you need help post some more info (like the exact error message), tell us if DMA is enabled, try GnomeBaker or Nero Linux.

Don't come here and rant about Breezy because:
1) Breezy comes with NO WARRANTY. Its not Ubuntu's fault you cannot make it work.
2) This forum is Ubuntu SUPPORT not chit chat or anything. If you want to say how ugly, slow or broken Ubuntu is, post somewhere else.

---

### Post by GrumpyBob on 2005-10-27
It should have occurred to the OP that another option for CD burning might have been worth trying.  I burn data CDs through Nautilus.  

The login problem reported by the OP is something that a quick search of this forum would reveal as easily sorted.

For the record, Breezy is working perfectly on my Laptop, just as Hoary is on my dektop PC.

Robert

---

### Post by kakashi on 2005-10-27
breezy has many major issues. 
for one it failed to configure my sound hardware which hoaray did well. 
2. it has very little software in the repos.

---

### Post by gillion on 2005-10-27
[QUOTE=kakashi]breezy has many major issues. 
for one it failed to configure my sound hardware which hoaray did well. 
[/quote]

I doubt that... did you seek help ?

> 
2. it has very little software in the repos.

How many repos are you using ?

---

### Post by angkor on 2005-10-27
[QUOTE=kakashi]
2. it has very little software in the repos.[/QUOTE]

I agree, 16000+ packages is no where near enough for me, I need 100k packages at the very least to get my work done....

:rolleyes: 
:rolleyes:

---

### Post by Magneto on 2005-10-27
wow this thread is on fire

only breezy bug ive seen is adding compressed themes in the gnome theme manager by drag and drop from nautilus caused my whole system to lock up and is repeatable - adding them other ways all work aka control or icon tabs

k3b dvd burning works flawlessly for me 

how can you make a thread with a title like this when you obviously do not know what you are doing?

---

### Post by GIBson3 on 2005-10-27
I haven't tried k3b, However burning with GnomeBaker and Nautilus have been flawless on my box.  That said, helping would be easier if you didn't just say it doesn't work... posting error Messages and Hardware/config info will go a long way to NOT missing a deadline.

Also, upgrading an Mission critical box just before a deadline without verifing everything to be working in your hardware configuration isn't a good idea. I don't care if it's linux, bsd, windows, BeOS, MacOS, whatever...

---

### Post by matthew on 2005-10-27
[quote=goneskiing]missed key work deadline
*** too much lost time ***[/quote]
For future reference I strongly recommend you NEVER change things around (i.e. by installing new software) on a missions critical computer when a deadline is looming...that's a huge and potentially disasterous error. If someone working for me did that they would certainly receive a warning, possibly a reprimand, and potentially a pink slip.

---

### Post by pjs_flyer on 2005-10-27
These forums are great - not only do I get more support and helpful info than from any flavour of any other operating system I've used, but there's comedy too!

No operating system works perfectly with all hardware, but Breezy makes a pretty good stab at it; broken it is not.  It reminds me of the "is linux ready for the desktop" type threads. Desktop? It's there for the laptop as far as I can see.

But although these threads are entertaining, I'm not too sure what the point of them is - if there's a bug, bugzilla is top right on your screen.  Otherwise, what sort of response do you expect to a comment like "breezy is broken" on a breezy forum?

---

