---
title: "pioneers"
date: 2009-06-22
forum: Gaming &amp; Leisure
---

### Post by chriszatch on 2009-06-22
for some reason its not working on my computer. (64 bit 9.04) im trying to play against computers and as soon as i hit launch server after ive added computer players, the client window pops up then quickly goes away to nowhere. can anyone help me? is this game not suited for 64 bit?

---

### Post by Wiebelhaus on 2009-06-22
> **chriszatch said:**
> for some reason its not working on my computer. (64 bit 9.04) im trying to play against computers and as soon as i hit launch server after ive added computer players, the client window pops up then quickly goes away to nowhere. can anyone help me? is this game not suited for 64 bit?

You paid for that [OS which means they offer support for it]("http://www.tapioneer.com/") , I'd hit them up.

---

### Post by chriszatch on 2009-06-22
i was really confused what you were talking about at first... then i realized i lacked clarity. Im talking about the pioneers game that resembles settlers of catan

---

### Post by Wiebelhaus on 2009-06-22
> **chriszatch said:**
> i was really confused what you were talking about at first... then i realized i lacked clarity. Im talking about the pioneers game that resembles settlers of catan

Ohh! lol , My bad.

---

### Post by Wiebelhaus on 2009-06-22
Open the terminal and launch the application there , the terminal will provide output and you should be able to pull some information from there to further diagnose the issue.

Let's say the launch is being interrupted and the terminals last bit of output is > /user/lib/l that may hint that the application is having an issue accessing a dependency library. Or it may provide an error such as > cannot access such and such that may be a permission issue.

---

### Post by chriszatch on 2009-06-22
aight, so i launched it from the terminal and it did all the same stuff as i mentioned before. but the terminal didnt say anything. to launch it in the terminal, i just typed pioneers. did i do that right?

---

### Post by wolfyking2 on 2009-06-22
No, you have to put the launcher for the game in the terminal.  Just open a terminal, and drag the launcher in there, and post the output here.

---

### Post by chriszatch on 2009-06-22
this is what it said.
zatch@Naruto-Uzumaki:~$ '/usr/share/applications/pioneers.desktop' 
bash: /usr/share/applications/pioneers.desktop: Permission denied

so how do i fix the permissions

---

### Post by curvedinfinity on 2009-06-23
Try this:

```
sudo chmod 666 /usr/share/applications/pioneers.desktop
```

Did you install the game via a binary installer run as root? (As opposed to a deb package?) If you did, it is likely you'll have to run the game with "sudo" every time you play it. Either that, or you'll have to reinstall the game under your own user.

---

### Post by chriszatch on 2009-06-23
aight. i tried that and it asked me for my password then after i entered it it brought up another command line and did nothing more.  i installed pioneers through add/remove applications.

---

### Post by TokyoYank on 2009-12-19
> **chriszatch said:**
> for some reason its not working on my computer. (64 bit 9.04) im trying to play against computers and as soon as i hit launch server after ive added computer players, the client window pops up then quickly goes away to nowhere. can anyone help me? is this game not suited for 64 bit?

I got it to work, hope it helps:  [http://ubuntuforums.org/showthread.php?t=1359342](http://ubuntuforums.org/showthread.php?t=1359342)

---

