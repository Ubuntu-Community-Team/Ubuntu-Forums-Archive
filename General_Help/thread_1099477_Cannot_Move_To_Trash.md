---
title: "Cannot Move To Trash"
date: 2009-03-18
forum: General Help
---

### Post by accooper on 2009-03-18
OK, I have been trying to delete some old txt files to make more room on my hard drive.  When I try to delete them Ubuntu says they cannot be moved to the trash.  Why would this happen?

TIA
Andrew

---

### Post by drs305 on 2009-03-18
It is possible it is a permission problem. You could try deleting them as root by opening nautilus with the following command. If you delete them through *root* nautilus, I'd recommend using SHIFT-DEL to actually remove the files so they don't end up in root's trash bin. Be certain of what you are deleting as the files will not be recoverable.

```
gksudo nautilus
```

---

### Post by accooper on 2009-03-18
I still can't get the trash can to work.  If it's complicated please give me the steps as
1
2
3
4
5
6
7
8
9
I am new to ubuntu and I would like the trash can to work just in case I screw up.

Thanks
Andrew

---

### Post by negev on 2009-03-18
1. ALT + F2 or Applications -> Accessories -> Terminal
2. Type in sudo gksu nautilus
3. Through the window that opened, locate the files and delete them
4. Close the window

---

### Post by accooper on 2009-03-18
I really didn't explain myself too well.  Cut me a little slack since I am from Texas.#-o

What I meant was that when I delete a file it doesn't go to the trash can.  It is just deleted so I can never get it back if I make a mistake.  How do I get files to go first to the trash can and then I can delete them after a while?

Like windows does.

Andrew

---

### Post by drs305 on 2009-03-18
Ok, I think we now know what your problem is (that always helps).

Do you have a folder /home/yourusername/.local/share/Trash with two subfolders "info" and "files".
You might trying reinstalling gnome-applets and then make sure the ownership and permissions are set properly on these files with:
```


sudo apt-get install gnome-applets
sudo chown -R yourusername: ~/.local/share/Trash
chmod 700 -R ~/.local/share/Trash

```

Note: Plenty of slack given - I married a Texan. ;-)

---

### Post by accooper on 2009-03-18
Tried that but nothing.  I looked in the trash folder and there are no other subfolders.

Andrew

---

### Post by accooper on 2009-03-19
Hey, I ain't no dumb red neck.  I got the trash to work!  By putting it on my desktop!

Thanks for all the help!

Andrew

---

### Post by nu2this on 2009-04-19
Hmmm

---

