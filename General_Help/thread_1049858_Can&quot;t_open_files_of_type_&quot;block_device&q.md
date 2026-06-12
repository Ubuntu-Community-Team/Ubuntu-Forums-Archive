---
title: "Can&quot;t open files of type &quot;block device&quot;"
date: 2009-01-25
forum: General Help
---

### Post by Stan15 on 2009-01-25
I'm using xubuntu downloaded with wubi.

What I'm trying to do is use truecrypt to mount an encrypted volume from the windows section of my hard drive. Truecrypt says that everything was mounted fine but when I try to open the volume from truecrypt I get an error message that says 

"No such file or directory: nautilus". 

Truecrypt says the actual location of the virtual drive is "/dev/mapper/truecrypt1" so I went over there and clicked on "truecrypt1" and I get a prompt that says 

"Open truecrypt1 and other files of type 'block device' with" then it shows a list of applications

I think the actual problem is that I just need to get Nautilus (which I don't know how to do) but I'm a complete linux novice so I included all that in case I'm wrong. Also if you keep any help as simple as possible it would be much appreciated.

---

### Post by whoop on 2009-01-25
I think you have nautilus and that nautilus is throwing the error message. Nautilus is the "file manager". But this is a bit strange as you say you are using xubuntu which should have the thunar file manager.
Try going to the truecrypt directory using the terminal and see what error it throws there.
I think the problems you are having could be caused by the fact that your truecrypt volume resides on windows and your xubuntu is not configured to write to windows partitions.

---

### Post by Stan15 on 2009-01-25
I don't understand what you mean about going to the truecrypt directory.

As for not being configured to read and write from windows, I can save things to and read from the windows section just fine.

Thanks for answering

---

### Post by Stan15 on 2009-01-27
Never mind I just got this working. Looks like I was just trying to open the wrong thing. Instead of going to "/dev/mapper/truecrypt1" I should have gone to "/media/truecrypt1". It still throws up the same error when I try to open it via Truecrypt but this works well enough. Thanks for your help though.

---

### Post by peyre on 2009-04-04
I'm experiencing the same issue.  I'm running Xubuntu 8.10 natively (not via Wubi).  I had Nautilus installed then removed it because it kept hijacking my Desktop (unchecking "Allow Xfce to manage the desktop") on bootup.  I also had TrueCrypt installed.  So I uninstalled Nautilus, and the Desktop issue went away.  But now I get the same error when I try to mount a TrueCrypt volume: "No such file or directory: nautilus".  I removed and reinstalled TrueCrypt, thinking the program just needed to be installed when Nautilus wasn't around, but I'm still getting the error.

---

