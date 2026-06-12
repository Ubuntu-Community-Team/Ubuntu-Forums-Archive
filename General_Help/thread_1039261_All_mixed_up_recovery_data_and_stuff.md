---
title: "All mixed up recovery data and stuff"
date: 2009-01-14
forum: General Help
---

### Post by lordtetris on 2009-01-14
I all started whit me having whanting to get my grub right.
I have i had windows xp and ubuntu on the same hardrive and then adding a hardrive whit ubuntu

Hda,0 win xp 
hda,1 ubuntu

hdb,0 ubuntu

then whanting to remove the ubuntu on hda becuse i had lost i perpose. I tryied to change the Grub using tutorials on the net. First it resulted in 
grub error 15.
Witch i guessed was somthing to do with the mbr having to diffrent startups and stuff. so i found a guide of how to clear the mbr on the hda.

result a working ubuntu! yay! 
But sadly the xp hardrive was unreadible. 
Guess i did that to it when clearing the mbr.

I have no problem reinstalling xp but i do not whant to lose the information on that hardive.

If theres a way to restore the xp installation ore just extract the files.
in some simpale way. please let me know.

thanks for your help!

(also the partinon editor finds the drive but buts a ! mark and ses its un reachible. i tryed to use  test disk it worked fine to analyse my ubuntu hardrive but when chosing the xp one it just did nothing an freezed)

---

### Post by lordtetris on 2009-01-14
I used some command like this one but with another bs number.
I guess its a bit more information. I relly hope somone knows how to fix it.
 
dd if=/dev/zero of=/dev/hda bs=512 count=1

so i used this command and after that i cant reach the hard drive ?

---

