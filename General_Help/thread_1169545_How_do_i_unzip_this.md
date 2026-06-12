---
title: "How do i unzip this ?"
date: 2009-05-25
forum: General Help
---

### Post by Squinchy on 2009-05-25
Hi

I'm trying to unzip a video file that has been ziped in to all these separate zip files, and archive manager dose not suport this

file name is
aaf-ufc98.cd1.r00
aaf-ufc98.cd1.r01
aaf-ufc98.cd1.r02
and so on

What can i do ?
[IMG]http://pic60.picturetrail.com/VOL1731/12315575/21907249/365293968.jpg[/IMG]
[IMG]http://http://pic60.picturetrail.com/VOL1731/12315575/21907249/365293968.jpg[/IMG]

---

### Post by Wobblybob on 2009-05-25
Hi, this looks like the sort of thing Windows Winzip does and you open the first i.e the one ending with a 0 and it then opens the rest, have you tried opening the numeric first file?

edit: just had a thought, have you got rar installed? in synaptic look for rar and unrar, install them and then double click on the numeric first file in the list and hit the extract button on the archive manager when it comes up.

---

### Post by mike555 on 2009-05-25
Not sure, but it looks to me that someone split up a video inti smaller parts (like to fit on a bunch of floppy discs or to send through several emails) , you will probably need to find the program that did it ... probably a windows program   ... like the ones here;  [http://www.nonags.com/nonags/filesplit.html](http://www.nonags.com/nonags/filesplit.html)

---

### Post by CatKiller on 2009-05-25
Looks like a RAR file archive to me. Install RAR support through Synaptic and then open the file that ends .rar. It should all extract automatically.

---

### Post by lloyd_b on 2009-05-25
> **Squinchy said:**
> Hi

I'm trying to unzip a video file that has been ziped in to all these separate zip files, and archive manager dose not suport this

file name is
aaf-ufc98.cd1.r00
aaf-ufc98.cd1.r01
aaf-ufc98.cd1.r02
and so on

What can i do ?
[IMG]http://pic60.picturetrail.com/VOL1731/12315575/21907249/365293968.jpg[/IMG]
[IMG]http://http://pic60.picturetrail.com/VOL1731/12315575/21907249/365293968.jpg[/IMG]

That's a fairly common multipart "rar" file.  Install the package "unrar" ("sudo apt-get install unrar" in a terminal window, or use the package manager of your choice), and then in a terminal window "unrar e <filename>" (I have no clue how to get the archive manager to recognize the "rar" file for what it is).

Lloyd B.

---

### Post by linux_tech on 2009-05-25
To unzip them, you can use unzip in terminal or open archive manager and double click on them

---

### Post by x33a on 2009-05-25
hi

first install unrar
```
sudo aptitude install unrar
```

then cd into the directory containing these files, and use this command from the terminal
```
unrar x *.rar
```

---

### Post by CatKiller on 2009-05-25
> **lloyd_b said:**
> (I have no clue how to get the archive manager to recognize the "rar" file for what it is).

You don't have to. It happens automatically when you install the rar or unrar packages.

---

### Post by XCan on 2009-05-25
> **CatKiller said:**
> You don't have to. It happens automatically when you install the rar or unrar packages.

+1. On my machine, after installing unrar I could just double click on one of the .r# files and archive manager would open it correctly.

---

### Post by Squinchy on 2009-05-25
> **XCan said:**
> +1. On my machine, after installing unrar I could just double click on one of the .r# files and archive manager would open it correctly.

how do i install unrar on my pc, i tried going to Applications>Add/remove applications but did not find it there

I don't understand this "code" thing or where it goes

Edit:
I added an application called Rar, now i can just right click the .r00 and select Extract here and it dose all the work :), thanks for the help :)

---

### Post by Champain on 2009-05-25
What you want to do is install a program called 7-zip, its under the Add/Remove section. Once you have it installed you should be able to open the first file with Archive Manager and extract it to your desired location.

---

### Post by oldos2er on 2009-05-25
> **Squinchy said:**
> how do i install unrar on my pc, i tried going to Applications>Add/remove applications but did not find it there

I don't understand this "code" thing or where it goes

 Open a terminal (Applications, Accessories, Terminal), and copy and paste this into it:
```
sudo apt-get update && sudo apt-get install rar unrar
``` Once that's done, Archive Manager will be able to handle rar files.

---

