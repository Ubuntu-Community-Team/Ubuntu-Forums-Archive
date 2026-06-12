---
title: "CD &amp; DVD-RW Drives?"
date: 2009-04-17
forum: General Help
---

### Post by micahNTX on 2009-04-17
Hello everyone!
I have recently replaced Windows XP with Ubuntu 8.10.. And let me say I absolutely love it, but I am having technical difficulties at the moment! 
Almost everything is up and running good hardware related, except my CD-R and DVD-RW drives!
Now when I insert a CD into either one, in "Places>Computer", the drive letter will display what type of CD I have inserted.. So it is obviously at least recognizing the drives, right? Well, after I put a disc in, I have tried using CD burning software such as: Brasero, GnomeBaker, Amarok, and a few others.. ............Brasero has gotten the furthest so far, I'm able to actually put songs on a CD then click "Burn"..... "Burn" is disabled on Amarok so I cant even get it going... GnomeBaker just crashes as soon as I click "burn"... Brasero will start to Burn but ALWAYS gets towards the end and gives me an error saying "Burn failed, could not complete the operation" or something similiar to that effect..... My CD/DVD works fine for burning on Windows , so it's not the drives or CD's themselves...... I REALLY want to get Ubuntu configured all the way so I can *permanently* switch to Linux over Windows, as I prefer it much more! However, I have got to get these basics up & running before I can do so..... I'm not a very experienced Linux user, so I really do not know where to begin for troubleshooting! Now I have read and heard before that the drives must be mounted before they're able to used... Is this maybe the case? 
The only other thing I can think of is; my sound is not working, as I cannot seem to configure my "Creative SoundBlaster X-Fi" card correctly, or find the appropriate drivers for it. And every time I try to use a Movie or mp3 player to play one of my mp3's or DVD rips, the program usually fades to grey and freezes to where I have to "force quit"... As I said, I'm not a very experienced Linux user, so I'm sure I'm over looking something very minor... I really do love Ubuntu so far and am trying my hardest to get the system stable and reliable as possible! Any help would be greatly appreciated on this subject! I'm sure I'm not the first to encounter this problem in Ubuntu! On a smaller note: Ubuntu found a NVidia Driver for my GeForce 7600GTX series Graphics Card and wow compiz and the effects are amazing on here! Beats Windows anyday!

---

### Post by logos34 on 2009-04-17
amarok calls k3b for burning, so the latter needs to be installed (probably why it's grayed-out).  With Brasero and the others it may be a codec issue.  That's my guess

Do you have **[ubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%207.10,%208.04,%20and%208.10")** pkg installed?  The mp3 decoder is needed to read the songs before they can be burned to an audio cd.  Or if you have a mp3 cd player, try making a 'data project cd' with the songs.

While you're at it grab libdvdcss2 and w32codecs ([medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo)

---

