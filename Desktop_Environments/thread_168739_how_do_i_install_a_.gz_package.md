---
title: "how do i install a .gz package"
date: 2006-05-01
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-05-01
Hi,
my friend has installed ubuntu but has no net connection. he wanted Xmms so i downloaded the gz package, but have no ide how to install it

Could somebody please help me out

regards

-

dc

---

### Post by Ubuntuud on 2006-05-01
First you should untar it (I guess it's a .tar.gz). This can be done by simply clicking on it and select extract (or something like that) in the window that pops up. cd into the directory ("cd /dir/where/the/file/is/in"). Then type "./configure", if it produces some type of error, post it here.
If it runs fine run "make" (this will compile the files).
And after that "sudo make install".

Hope it helps.

---

### Post by dave9191 on 2006-05-01
Did you download a package or the source code? .gz is an extention for a compressed file, like .zip. You have to uncompress it first and then it depeneds what's inside it. 

--
Dave

---

### Post by derjames on 2006-05-01
you have to use the 'tar' command to extract the content of the package

using 

tar -xzvf <fileName>

however it is best to check the help for more info
type in terminal

tar --help
or 
man tar

for the on line manual for the tar command, hope this helps...
cheers

---

### Post by Sef on 2006-05-01
Read this tutorial on installing by source.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

Also to compile you will need to download build-essential.

sudo apt-get update

sudo apt-get install build-essential

---

