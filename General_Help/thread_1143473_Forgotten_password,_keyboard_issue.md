---
title: "Forgotten password, keyboard issue"
date: 2009-04-29
forum: General Help
---

### Post by BluShift on 2009-04-29
Hello everyone. I am sorry if this has been posted, but I searched and searched and could not find it. If it is, please point me to it.

I know what to do when you forget your password; the standard "hack" is to press "esc" at GRUB and edit the line starting with "kernel" adding rw init=/bin/bash to the end, and then booting into the root account, and then running "passwd <username> to reset your password.

I have done all this. But I have a new issue that I can not find support for. Whenever I try to type in my new password (the "Enter new UNIX password:" prompt) it accepts one character before jumping to the next line, prompting me to re-enter my password, as if I had pressed "enter/return."

Whenever I try doing any other commands after the first one, nothing comes up after the prompt, but when I press "enter" it runs the command I typed; it just doesn't display the command. It seems to me (total noob) like the keyboard is malfunctioning, but honestly that's just a guess. Plugging in a USB keyboard refuses to solve the issue.

I tried using single user mode as well.. and again the display stuff gets screwed up.

I never have these issues when I actually run the operating system, just in these circumstances.

If there is any other way (or a way to fix the above) to reset my password, please let me know.

info:

Laptop: HP DV2000
1 GB RAM
140 GB HDD
Xubuntu 8.10 (intrepid)

Any help will be greatly appreciated. 

Thanks again,

-Alex

---

### Post by adult swim on 2009-04-30
i have never seen this issue before.  what if you, for the time being, just make your password one letter. then enter the same letter again when it prompts you to enter it again.  then see if you can boot your system and change the password to a password with more strength.

---

### Post by BluShift on 2009-04-30
> **adult swim said:**
> i have never seen this issue before.  what if you, for the time being, just make your password one letter. then enter the same letter again when it prompts you to enter it again.  then see if you can boot your system and change the password to a password with more strength.

Sorry I guess I didn't say it before; I already tried it and it did not work.

I saw this before on one of the Archives, but no one responded to it because it was after the thread creators question has been answered.

---

### Post by adult swim on 2009-04-30
hmm thats weird.  try loading the keyboard layout.  boot into recovery mode, select root terminal and then try ```
loadkeys us

passwd username
```

---

### Post by BluShift on 2009-04-30
Ok, I got it working. I don't know exactly what I did right, but I booted into the root account, then switched to my user name, and THEN did the whole "sudo passwd <alex>". It still was doing the funky keyboard stuff, I just had to make sure what I typed the first time was right. It was like issuing commands without a monitor lol. But it worked! So I'm back in.

Thanks for you help :)

---

