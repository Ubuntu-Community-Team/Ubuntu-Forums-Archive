---
title: "i Have 12.04LTS Desktop 64bit which is dead after 491 updates"
date: 2014-01-05
forum: Desktop Environments
---

### Post by mat125 on 2014-01-05
Hi i've recently tried to update a Pc but i cannot even get the mouse to work when it boots up. After booting up in safe mode and tried apt-get update etc and got -- you need to dpkg configure -a .But when i tried this it said its a read only file.I Have been warned i'm missing libqt4-xml aswell. This PC is not mine and i'm really in the ____t with it. All i initially wanted to do was update firefox. When i accepted all 491 the United Kingdom server for Ubuntu updates was so slow i pressed cancel and changed it to a Norway Server.After that i got the strange missing libqt-xml file missing and an update manager failer.Can anyone help its an emergancy.

Thanks Matt

---

### Post by bapoumba on 2014-01-05
You need to run the command with sudo:
```
sudo dpkg configure -a
```

If you interrupted the upgrade:
```
sudo apt-get update
sudo apt-get upgrade
```
to finish it up.

You do have admin access, don't you ?

---

### Post by mat125 on 2014-01-05
Many thanks for your reply.How do i get to run that command when my computer goes directly into my guest account and no cursor works. I cannot get into safe graphics mode or any kind of terminal otherwise i would have already completed the same commands take no offence. Is there anyway i can force a terminal open as root or get to my admin account from a dead cursor in a guest account ? I have password for Admin but cannot find a way there its a strange place to be. Why does'nt Ubuntu run correct checks on updates that should either install or not install why do we suffer the inbetween all the time ? Hope you can help i'm really stuck its my mothers computer !!!!
Hope someone can help soon !!!!
Matt

---

### Post by bapoumba on 2014-01-05
Alt-F2 and run gnome-terminal :)

---

### Post by mat125 on 2014-01-05
sudo dpkg --configure -a  in safe mode so far shows dpkg in read only mode.
Thanks for your reply will try out alt-f2 above now .

---

### Post by mat125 on 2014-01-05
My computer is only requesting the password for the guest account after ALT F2 in Terminal which i do not understand.Surely theres my admin account why can't my computer understand this ? Surely theres programming errors here !! I not sure but its asking for the computer password surely thats the admin one ?? I can swap out and reinstall operating systems without blinking but i'll never understand why the computer asks for an irrelevant main computer password which no one knows does anyone know what is happening ? I never felt so frustrated.
I must confess i have little patience with an update which take hours to download after which i press cancel. Surely the Ubuntu software should be able to handle a cancellation and a change of server for downloading update requests immediately.
I remember i have done the same thing in the past and i had no joy fixing the problem - i really think Ubuntu programmers should fix this.

---

### Post by steeldriver on 2014-01-05
If you truly are in the guest account, then you won't be able to do anything useful since neither 'sudo' nor 'su' are allowed from such an account afaik

You will probably need to reboot into 'recovery mode' via the main grub menu, and select the menu item to drop to a root shell, then remount the filesystem with read-write permissions

```
mount -o remount,rw /
```

and then do

```
dpkg --configure -a
```

or even (to reconfigure ALL packages - WARNING: this *will* take a while - think 1/2-hr or 1hr not seconds-to-minutes)

```
dpkg-reconfigure -a
```

---

### Post by mat125 on 2014-01-05
Hi Steel Driver thanks for your help it was genius. Tried :    mount -o remount,rw /      (next i tried)  :   dpkg --configure -a     (thats all) and it worked. Saw the updates coming through immediately afterwards. Thanks once again.

---

### Post by steeldriver on 2014-01-05
You're welcome - glad we got you up and running again

Please consider marking the thread as [SOLVED] via the 'Thread Tools' button to help others in the same situation

---

