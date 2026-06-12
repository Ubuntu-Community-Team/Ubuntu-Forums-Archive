---
title: "Dell repos won't authenticate after upgrade to 8.04"
date: 2008-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dak-AD on 2008-06-24
Just got a dell (inspiron 530n) with ubuntu gutsy, which i upgraded to hardy.

Following the advice [here]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry"), i added dells repos to /etc/apt/sources.list.

Now, however, the kernel module that update-manager is offering me (linux-ubuntu-modules-2.6.24-19Dell) 'cant be authenticated'.

Do i have to add a gpg key or something? if so, how, please?

btw: there were no entries in my sources.list for dell to change, so i just added them. i can't see why adding dell's repos would be wrong, given that i've got a dell computer, but if i should remove them again please say.

thanks.

---

### Post by bcom on 2008-06-24
I don't know the answer to your question.  For what it is worth, I have a Dell Inspiron 1420n that came pre-loaded with Ubuntu 6.04. I upgraded to version 7.10 using the Dell iso that I downloaded from Dell's website.  I then upgraded to Ubuntu 8.04 using Synaptic.

I checked my sources.list and do not see any references to the two repos listed in the link you posted.

I haven't had any problems with my computer even though I do not have those two repos in my sources.list file.  

Perhaps someone more knowledgeable will weigh in.

---

### Post by veedub on 2008-06-24
I didnt even know that dell repos even existed(my pc came with vista).  Mind you, I never bothered looking for any.  8.04 works perfectly for me

---

