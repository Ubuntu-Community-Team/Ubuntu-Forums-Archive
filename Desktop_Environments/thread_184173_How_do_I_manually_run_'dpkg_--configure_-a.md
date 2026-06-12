---
title: "How do I manually run 'dpkg --configure -a?"
date: 2006-05-29
forum: Desktop Environments
---

### Post by leica on 2006-05-29
I download taskjuggler with apt from one of the standard repositories that are recommended.  Something happened during the installation and taskjuggler was not installed properly.  I tried to reinstall the program and the reinstall did not work.  I tried to remove taskjugger and the follow message was displayed,"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."  How do I manually run 'dpkg --configure -a?

Thank you for your help in advance.

---

### Post by kingmonkey on 2006-05-29
in terminal type
```
sudo dpkg --configure -a 
```

---

### Post by aris25k on 2007-07-08
hello m8....i have the same problem... but when i type "sudo dpkg --configure -a" i cant type anything in the Password field..... it's like the keyboard is stuck for some reason but when i hit "Enter" it sais "Sorry, try again." Please if some one can help me because i've searched a lot for this problem in the web but i cant find the solution. And by the way im new in linux so............:)

---

### Post by milton1 on 2007-07-08
Anything typed in the password field will not show on screen, for security reasons. Make sure you have your password correct; remember passwords are case sensitive. If you cant get it to work, you can get around it by booting to recovery mode (should be an option on your grub menu).

---

### Post by aysiu on 2007-07-08
> **aris25k said:**
> hello m8....i have the same problem... but when i type "sudo dpkg --configure -a" i cant type anything in the Password field..... it's like the keyboard is stuck for some reason but when i hit "Enter" it sais "Sorry, try again." Please if some one can help me because i've searched a lot for this problem in the web but i cant find the solution. And by the way im new in linux so............:)
Read this:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by aris25k on 2007-07-09
thx a lot m8s, it realy help me. However another problem came up. Originaly i was trying to install virtualbox to my Ubuntu Feisty. I didn't use the terminal and i opened the package i downloaded "virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb" . The installation was taking too long 15-20 min so i tried to close it. The window did not respond to "Close" so not knowing an other way i restarted my linux. this caused the synaptic package problem. But now that i fixed it it writes "E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.". Wen i try to install it again from the terminal this happens "aris@Arix:~/Desktop$ sudo dpkg -i virtualbox_1.4.0-21864_Ubuntu_feisty_i386.deb
Password:
dpkg: status database area is locked by another process" 

If anyone can help me please................!!!!!

---

### Post by ayoli on 2007-07-09
Close all package manager tools before running dpkg, you can't run multiple instances of package managing tools (ie: when update-manager works, you can'"t run synaptic without having such message : "status database area is locked by another process").
So, be sure you have closed synaptic, update-manager, gdebi and run again :
```
dpkg --configure -a
```

---

### Post by bean77 on 2007-07-11
Is something supposed to happen after this command?

---

### Post by Happy_Man on 2007-07-11
It should start showing stuff on how it's trying to fix the problem. If nothing happens, and you get another prompt, something else is wrong.

---

### Post by bean77 on 2007-07-11
Oh fantastic.

---

### Post by Happy_Man on 2007-07-11
> **bean77 said:**
> Oh fantastic.
And is that a "Yay! It's working!" kind of sentence, or a sarcastic "Oh ****" kind of sentence?

---

### Post by bean77 on 2007-07-11
LOL-the latter!

---

