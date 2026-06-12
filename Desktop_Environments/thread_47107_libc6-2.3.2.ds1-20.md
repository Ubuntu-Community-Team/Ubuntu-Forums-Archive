---
title: "libc6-2.3.2.ds1-20"
date: 2005-07-07
forum: Desktop Environments
---

### Post by cotcot on 2005-07-07
A number of apps cannot be installed due to the missing of a recent version of a couple of libs (glibc-2.3.2.ds1-20ubuntu13, libc6, libvorbis0a 1.0.1.1).
Hence I cannot use apps such as dvd-slideshow, hugin, panotools, qdvdauthor, ...).
Searching on the net and in this forum confirms this problems and does not give a solution.
That is a pity because I like Ubuntu very much. I tested Mandrake 10.0 (pay for the club and more packages) , Suse 9.2 (good but slow), FC2 before.
I hope this will be solved with Breezy (5.10).(If not I will probably switch to FC4.)
Or has some body a better idea ?

---

### Post by alastair on 2005-07-07
I have a pretty standard Ubuntu 5 (Hoary) install.

I just installed "dvd-slideshow" without a problem. So, I am not sure what problem you are describing. Can you be more specific? What happens when you try and install "dvd-slideshow"?

---

### Post by jcohen on 2005-07-07
I think you're using the marillat source which is intended for Debian and not Ubuntu. While Ubuntu is based off of Debian, the dependencies on packages are not identical. Debian has a different version of libc6 (a core library) and you DO NOT want to upgrade libc6. You'll break all your Ubuntu applications. The solution is to remove your marillat source (and packages if you have installed any) and install the packages you want from Ubuntu Backports. See [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) for instructions. After editing /etc/apt/sources.list you need to apt-get update to update apt's list of available packages. After you install the packages that you want from Backports, you should comment out the backports line in /etc/apt/sources.list by adding a # before the line and running apt-get update again. 

I'm almost positive you're using Marillat because neither Ubuntu or Backports provides packages for qdvdauthor. If removing marillat and adding a backports source doesn't work, paste your /etc/apt/sources.list and we'll go from there.

Good Luck

---

### Post by cotcot on 2005-07-08
Thank you for the replies.
I unmarked the marillat repositories and could then (after apt-get update) succesfully install 'dvd-slideshow'.
'qdvdauthor' 'libpano12' and 'hugin' are not on the synaptic list. So I suppose I cannot get them.
Installing panotools and hugin the described by [http://rbpark.ath.cx/articles/compile-hugin-ubuntu](http://rbpark.ath.cx/articles/compile-hugin-ubuntu) does not work either. It works fine for everything before Panotools. With ./bootstrap I get (and I apologize for the long list ; I do not know what could be of any intrest for diagnostics) : (edit : list deleted)


I have g++ 3.4 installed.

I do not really need qdvdauthor (I can do it in terminal ; all the command are in /usr/bin/)

---

### Post by avilella on 2005-09-01
Installing hugin under Ubuntu Hoary

wget [http://3demi.net/debian/debs/libpano12_2.7.0.7pre20041028_i386.deb](http://3demi.net/debian/debs/libpano12_2.7.0.7pre20041028_i386.deb)
sudo dpkg -i libpano12_2.7.0.7pre20041028_i386.deb

Add this to your /etc/apt/sources.list:

# hugin, enblend
deb [http://3demi.net/debian](http://3demi.net/debian) debs/./
deb-src [http://3demi.net/debian](http://3demi.net/debian) debs/./

sudo apt-get update
sudo apt-get install hugin
sudo ln -s /usr/lib/libpano12.so /usr/lib/libpano12.so.0

You should be able to run hugin now...

---

### Post by cotcot on 2005-10-23
Thanks , your procedure was succesfull.

---

