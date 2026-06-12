---
title: "Help With Root Am Lost"
date: 2005-05-18
forum: Desktop Environments
---

### Post by shopyoungway on 2005-05-18
i am trying to work with the sudo and trying to run the archive manager.  I am trying to install XPde into the usr/share folder untarring it.  I am new to the whole linux scene and have found ubuntu enjoyable other then permissions and sudo.  Can someone please tell me what i am doing wrong.  I go into the run aplication and the type gksudo Archive Manager and then it asks for password i enter the correct password and nothing happenes  it does nothin is there another way or am i doing it wrong.

Thanks in advance for the help.
Please remember that i am new to linux.
Charles

---

### Post by bored2k on 2005-05-18
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)
Have fun with xfce

---

### Post by lorap on 2005-05-18
good evening Charles
you just simply open a regular archive manager and extract tar file via it.
then open a terminal window and write:

sudo sh ...

after "sh" write the full path to the extracted installation script.
on the other hand get them both open, i mean terminal window and the directory where the extracted files were placed and then after you write "sudo sh " just grab the file with the mouse to the terminal window after what press enter. that should work.
have a nice day Charles.
wellcome to the linux community.

p.s.:
if my answer wasn't complete or not good at all, i'm sure there'd be person who'll give you the better solution.
pavel

---

### Post by shopyoungway on 2005-05-18
i have tryed the rootsudo file but it did not work and i cannot extract the file to the usr/share because it tells me i dont have the proper permisions so i am between a rock and a hard place.  Is there a way to create a "root" account to do all this in.  in other words is there a way to un "disable" the root account.  that way anything i need to do wont be bogged by "not enough permissions.

---

### Post by bored2k on 2005-05-18
[QUOTE=shopyoungway]i have tryed the rootsudo file but it did not work and i cannot extract the file to the usr/share because it tells me i dont have the proper permisions so i am between a rock and a hard place.  Is there a way to create a "root" account to do all this in.  in other words is there a way to un "disable" the root account.  that way anything i need to do wont be bogged by "not enough permissions.[/QUOTE]
 sudo passwd
will enable root.

---

