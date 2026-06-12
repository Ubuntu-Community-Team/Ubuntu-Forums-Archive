---
title: "XP boot partition"
date: 2009-03-30
forum: General Help
---

### Post by bcbotha on 2009-03-30
how do i check what partition my XP boots off. my ubuntu boots from hd0,1 but how do i check that for XP?

---

### Post by j7%&lt;RmUg on 2009-03-30
Check you Menu.lst file:

In ubuntu open a terminal and and type:
```
cd /boot/grub
```
This command takes you to the location /boot/grub on your hard drive. Next type:
```
sudo gedit menu.lst
```
It will then ask you for a password this is the password that you chose when you last installed ubuntu. Type it in and hit enter. It should then open gedit text editor with the menu.lst file already open.

Now simply scroll down till you find something like this:
```

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

Where it says:
```
root            (hd1,0)
```

This is the location of your windows install.

---

### Post by bcbotha on 2009-03-30
sudo fdisk -l worked and showed me its in /dev/sda2. now how do i add that to my grub menu so i can boot XP from grub? any ideas?

---

### Post by j7%&lt;RmUg on 2009-03-30
Ok refer to my post above on how to get to the menu.lst file. Once your there copy and paste the following code just above where it lists your ubuntu install but below where it says:

## End Default Options ##

Here is what you need to copy and paste:
```

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

It should then boot to your windows install if you select windows xp when you boot. If it comes up with an error then something is wrong please post what error it was if you get one.

---

### Post by bcbotha on 2009-03-30
i get Error 21: selected disk does not exist

---

### Post by j7%&lt;RmUg on 2009-03-30
Hmmm in that case replace (hd1,0) with (hd0,0).

---

### Post by bcbotha on 2009-03-30
it's still not working, giving me the same error. is there anything else we can do to make sure we have the right path for XP? would it be any use to uninstall XP and start again?

---

### Post by j7%&lt;RmUg on 2009-03-30
Im not sure. Im running out of ideas since i had a different problem with grub when i first installed ubuntu.

Try replacing (hd0,0) with (hd1,1).

If this doesnt work i am really sorry but that is everything i can think of. One other thing you can try if the above doesnt work is to do a google search for "grub error 21" and try everything that comes up.

---

### Post by bcbotha on 2009-03-30
thanks for the help, i'll try it and will post what i did if i come right.

thanks

---

### Post by j7%&lt;RmUg on 2009-03-30
Ok cool im happy to help, but there is a limit to everyones knowledge. Im going to watch this topic to see how it gets solved and maybe i can learn from it.

---

### Post by bcbotha on 2009-03-30
hay nisshh all i did was change

title Windows XP
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

to

title Windows XP
root (hd0,1)
chainloader +1
makeactive
boot

and now its booting and working fine. thanks again for the time and effort, i appreciate it.

---

### Post by j7%&lt;RmUg on 2009-03-30
Ah good usually its the other way around where you have to have that bit otherwise it doesnt work, thats why i didnt think it was relevant.

Happy to help.

---

