---
title: "Headphone works but not speakers"
date: 2008-12-12
forum: General Help
---

### Post by Athena1 on 2008-12-12
Hi,

Im new to linux, mine is CQ45-112AU compaq presario laptop. I have altec lansing speakers, got ubuntu installed couple of days ago. Only headphone works and nothing works with laptop speakers. It would be of great help if anyone can help to debug this problem.

---

### Post by gettinoriginal on 2008-12-12
Right click your volume icon and make sure nothing is muted.  If thats ok, make sure alsa and pulse are installed via synaptic.  :p

---

### Post by aminy on 2008-12-14
Hi ,
I am new to ubuntu,
I have this same laptop CQ45-112AU, the same problem, headphone works but no sound from the altec lansing front speakers, Please someone has a fix?

Thanks,

---

### Post by iponeverything on 2008-12-14
while sound is playing try plugging headphone jack and unplugging it again.

don't ask me why.

---

### Post by aminy on 2008-12-14
Thanks but still no sound... :(

---

### Post by iponeverything on 2008-12-14
Is there a bios setting?

---

### Post by aminy on 2008-12-14
hi,

No, The bios doesnt have any sound control options.
any other things to do?

Thanks.

---

### Post by Athena1 on 2008-12-25
Well...no solution yet !! Has anybody solved this problem??

---

### Post by Zorael on 2008-12-25
Head over to [http://ubuntuforums.org/showthread.php?p=5017453](http://ubuntuforums.org/showthread.php?p=5017453) and see if anything there helps.

---

### Post by pyromanic123boom on 2008-12-25
This is one possible solution:

Assuming you use alsamixer, double click your Volume icon. Go over to the "Switches" tab, and uncheck headphone.

---

### Post by Athena1 on 2009-01-24
:(...nope not working despite unmuting the switch...any other solution???

---

### Post by Athena1 on 2009-02-12
Geeeeeeee I resolved my problem :)

I looked at the alsa gnome chip configaration and found out that it was Dell series..weird..compaq presario having dell as its model!!!

---

### Post by aminy on 2009-02-13
Athena1,

Can you please help me.? how and where you changed the configuration settings?

thanks for your help.
Amin.

---

### Post by aminy on 2009-02-13
thanks for your help Athena,

I used 
options snd-hda-intel model=dell-m4-2

and its working great.

---

