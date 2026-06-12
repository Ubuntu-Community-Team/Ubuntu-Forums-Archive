---
title: "weird terminal/gedit action"
date: 2006-08-29
forum: Desktop Environments
---

### Post by nsolo on 2006-08-29
When trying to edit the smb.conf file in the ect/samba directory, I type the following in terminal:

sudo gedit /ect/samba/smb.conf

What happens after being prompted to give my password is that a "blank" smb.conf file is created. If I just type "sudo gedit" and then drag and drop the smb.conf file into terminal, the file opens up with the corresponding text.

What am I doing wrong?

---

### Post by Omnios on 2006-08-29
when using gedit with a file that does not exzist gedit opens a blank file with that name. Could possibly that there is a typo in the files name.

---

### Post by nsolo on 2006-08-29
I thought of that, but I took SSSSSSSSSSSSOOOOOOOOOOOOOO much care in typing out the command, that if I did make a mistake, I don't see where. 

Thanks for your input, I'll try again.

NSolo

---

### Post by Tomosaur on 2006-08-29
Well, you just typed out 'etc' incorrectly twice, so maybe that's your problem :P
(It's /etc/samba/smb.conf)

---

### Post by nsolo on 2006-08-29
you're right, I'm an idiot. Dyslexic, maybe. Eye can't sea two well!!!!

Thanks for pointing out my mistake.

NSolo

---

