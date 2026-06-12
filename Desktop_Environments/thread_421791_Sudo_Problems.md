---
title: "Sudo Problems"
date: 2007-04-24
forum: Desktop Environments
---

### Post by t3hi3x on 2007-04-24
Havent look real hard for a solution, but its a really odd problem.

I think there is somehting wrong with my sudo command. It asks for my password, but then nothing else. The really odd thing is that my synaptic packet manager (i think) isnt installed. It just wont work, and i havent the slightest clue why not.

i tried using aptitude to fix it, but i cant use my sudo command.

sudo -i returns nothing so that doesnt work either.

any questions or help is greatly appreciated.

--
alex

---

### Post by taurus on 2007-04-24
What's the output of this command from a terminal?

```
id
```
To be able to use sudo, you need to belong to groups adm & admin so if you don't see those two groups from the output, then that would explain it.

---

### Post by t3hi3x on 2007-04-25
I dont understand why i wouldnt be in that group. its the account (and only account) and it was created when i installed ubuntu.

i guess i could check, but i see no reason. also it doesnt return an error when i use sudo. is it suppose to?

---

### Post by t3hi3x on 2007-04-25
apbresh@alex-laptop:~$ id
uid=1001(apbresh) gid=1001(apbresh) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),113(lpadmin),1001(apbresh)

i noticed it says lpadmin, i assume thats not the same as admin, so i used adduser and get need to be root use that command, and ofcourse sudo doesnt work

---

### Post by t3hi3x on 2007-04-25
so, i feel like an idiot. i had two users because of windows import thing, and the one i was using was not an admin account. thats why everythign was jacked.

srry :/

---

### Post by ericsprojects on 2007-08-31
I'm having this same problem.  When I installed, Ubuntu imported a username, but then prompted me to setup a new user.  I now have three users, with the same name!  I cann't sudo or su.  What can I do?  

-Eric

---

### Post by Ronfar on 2007-08-31
I believe a friend is also having the same problem, however I am not able to see his computer but he did install it over an XP so perhaps this import thing is the problem. Any advice on this?

---

