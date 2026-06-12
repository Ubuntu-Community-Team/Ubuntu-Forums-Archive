---
title: "Windows 7 and Ubuntu do they place nice?"
date: 2009-04-05
forum: General Help
---

### Post by leveliv on 2009-04-05
Im not dual booting, This is exactly why I am asking I have WoW installed on the Win 7 computer which is my main computer for all the games and stuff 

so I am deleting Vista (and my other install of WoW) 

so Im thinking if I delete Vista and WoW I will just transfer the other install of WoW via my network, but...How well do they play together, I understand that Vista's networking and Win 7's isn't really the same..due to that stupid Homegroup crap...

I'll still be backing SOME stuff onto DVDs but not WoW ...thats 18GBs of DVDs I would rather keep for more important things.

And yes you can just transfer the install, Theres a thread on the Blizz forum about it, just incase people don't think you can.

---

### Post by lovinglinux on 2009-04-06
You have another thread [here](http://ubuntuforums.org/showthread.php?t=1117122) with the same topic, but there you say you want to transfer files from Vista to Ubuntu partition and now you say you are not dual-booting, which one should be considered?

Why don't you install WoW in the other computer/partition and simple copy the patches from the original installation folder?

---

### Post by leveliv on 2009-04-06
before I had ubuntu installed under Wubi on the PC that in this thread I am installing Ubuntu on Natively and getting rid of Vista completely sorry I should have stated that. 

I have my main computer set up with Win 7 Beta, that I am using. then I had this computer with Vista and ubuntu but am scrapping Vista. 

I've tried to make the switch  I don't know how many times...its just that when ubuntu comes out like every 3 month I get tired of updating but at the same time I want to update to get new things :P 

and I have read into win 7 and vista networking they are the same...just they added homegroup for a little bit more security but I've shared with win 7 from Vista and back without problems. 

Also is there a program in ubuntu that can manage my shares..or do I have to use Nautilius?

---

### Post by Karsa on 2009-04-06
Ubuntu and Win7 actually go really well together. At least they do for me. I've got no problems to mount win7-shares on my ubuntu machines. Just do a quick search for one the great threads on cifs here. IIRC the syntax is something like > mount -t cifs //compname//share /mountpoint -o user=youruser,pass=yourpass

As for managing shares, just mount them and use whatever file manager you prefer =)

---

### Post by leveliv on 2009-04-07
Thank you, Seeing as I am only sharing with one computer I just simply installed samba then in a terminal :

nautilus smb://x.x.x.x the x.x.x.x being the network IP for the other machine. Worked great I am now transferring files.

---

