---
title: "urgent"
date: 2006-04-13
forum: Desktop Environments
---

### Post by tpnerdcore on 2006-04-13
hello everybody! i really need help. I use ubuntu/knoppix everyday. but i also use windows for gaming and other dumb stuff :-/.......well i had ubuntu installed on a 20 gig partition and the rest was windows. I had to rid of the ubuntu partition. So i fixed the grub with fixmbr. Well no my windows hangs. I boots but it stops at the login screen heres my boot.ini
hello everybody!
 
 i really need help. I use ubuntu/knoppix everyday. but i also use windows for gaming and other dumb stuff :-/.......well i had ubuntu installed on a 20 gig partition and the rest was ubuntu. I had to rid of the ubuntu partition. So i fixed the grub with fixmbr. WEll no my windows hangs. I boots but it stops at the login screen heres my boot.ini
 
 [boot loader]
 timeout=30
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Micro soft Windows XP Professional" /noexecute=optin /fastdetect
 
 no im almost possitive this is correct....but does anybody know the problem????
 
 regards
 -anthony

 now im almost possitive this is correct....but does anybody know the problem???? regards -anthony

---

### Post by vcorreia on 2006-04-13
Hi!

I've had this happening to me too, albeit for different reasons; i managed to get it working again by running fixboot and then fixmbr.

Try that and let us know if it worked for you.

Take care,

./vcorreia

---

### Post by tpnerdcore on 2006-04-13
hey! im almost sure that worked :) but...

about an hour into my frustration, i booted an XP cd and went to recovery mode :-/ i think that might have ruined things.....i got angry at the wait and rebooted. 

And here i am now with a fixed XP but the recovery startup inthe way..

is there anyway to just get around it???

regards
-anthony

---

### Post by vcorreia on 2006-04-13
i'm not sure i understand what u mean/where your're standing right now :-k 

could u be a bit more specific, please?

if u can boot xp but not ubuntu, then that would be a question of inserting the ubuntu cd, go to rescue mode and reinstall grub with grub-install /dev/hda.

./vcorreia

---

### Post by tpnerdcore on 2006-04-13
before i wrote the thread, i booted into a windows xp cd and did the recovery..... and i got mad and tunred it off. Well windows wanted to always boot into its recovery installation because of it. So i couldnt tell if "fixboot", "fixmbr" worked. 

and now after the recovery thing finished, the computer just restarts after itgets past the bios screens.

(the situation in a just: windows wouldnt boot, i went into the recovery installation because i thought i neededto repair my windows installation. Now Get a really weird Blue screen. and then it restarts....)

and help?

-anthony

---

### Post by tpnerdcore on 2006-04-13
sorry if that doesnt make sense.....

-anthony

---

### Post by vcorreia on 2006-04-13
darn... does the blue screen say anything about/like "inaccessible boot device" or whatever? or maybe the ntldr (nt boot loader) is missing?
if u could describe me the blue screen, it would help.

./vcorreia

---

### Post by tpnerdcore on 2006-04-13
man i wish i could but its really quick.....

it has really small text and i know the first sentence is something like this....

"unknown error......device 0 error.....boot error"

i know its not the ntldr

oh man i really messed up :( thanks for all of your time :)

anthony

---

### Post by vcorreia on 2006-04-18
hi! sorry for not answering sooner & sorry for not being able to help you  :( 

take care,

./vcorreia

---

### Post by nab on 2006-04-18
Hi Anthony,

I found this tread about removing ubuntu.
[http://www.ubuntuforums.org/showthread.php?t=113630]("http://www.ubuntuforums.org/showthread.php?t=113630")

Since it's using a floppy or cd to remove the dual boot, perhaps it can resolve your problem - if it's located in the dual boot.

If your windows partition is broken, I can't help you.

Hope this helps and it's a waste of your time!

regads,
Niko

---

