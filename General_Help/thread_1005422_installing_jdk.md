---
title: "installing jdk"
date: 2008-12-08
forum: General Help
---

### Post by fababhi on 2008-12-08
Hi,

i have downloaded jdk for Unix system and have placed da file on the desktop. when i tried to install the file using the command :
  
sudo apt-get install <file-name>
1. it asks for da password
2. Reading package lists done
3. Building dependcy tree 
4. Reading state information done
 and then
 it hangs up saying : Could not find the package
 
let me tell u,i have entered da name of the file correctly infact I copypasted the name in the terminal.Can u help ? what could be the problem ?

---

### Post by taurus on 2008-12-08
```
sudo apt-get install <file-name>
```

Will install the package, <file-name>, from the repos.  If you want to install the version that you've downloaded, you must do it by hand.  What is the exact name of the file and did you save it to your ~/Desktop?

```
cd ~/Desktop
ls -la
```

Otherwise, replace the <file-name> with sun-java6-jdk if you want to version from the repos.

---

### Post by fababhi on 2008-12-08
Yes,I have saved the file on the desktop and its name is <jdk-6u10-linux-i586-rpm.bin>. And u meant that  apt-get installed the package. No how do i complete the installation manually ? "by hand" as u meant ?

Also, can u temme how to access and modify windows registry using ubuntu..

i tried :

install ntfs 3g
install ntfs progs..
sudo mkdir media/windows
i am facing problem with :

sudo ntfs-3g -o rw /dev/**<device-name>**/media/windows 
the error dat i get is :**ntfs-3g: Failed to access volume '/dev/sda2/media/windows': Not a directory**


what will come in place of <device name> ?

i have tried various names. discretely though..Filesystem, sda1,sda2 

can u help brother ?
thanks a lot for any help...

---

### Post by ibutho on 2008-12-08
The file jdk-6u10-linux-i586-rpm.bin is for RPM based distros like Fedora, openSUSE, Mandriva etc. To install the sun Java JDK on Ubuntu, take a look at this [article]("https://help.ubuntu.com/community/Java").

---

### Post by lovelyvik293 on 2008-12-08
For ubuntu you can use the .bin file.

---

### Post by sandyd on 2008-12-08
cd ~/Desktop

./jdk-6u10-linux-i586-rpm.bin

and i fail to understand why your using the rpm version. That one is for Fedora based distros, not ubuntu

just type

sudo apt-get install sun-java6-jdk

to install the jdk

---

### Post by jespdj on 2008-12-08
Install the JDK from the Ubuntu software repository instead of by downloading it and trying to install it manually. Use the command already mentioned above:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by fababhi on 2008-12-08
ohhhhh....datz so stupid of me....but i want to thank you all for the instant replies..thankyou so so much for da concern...ok now i am gonna irritate u wid another question...ok lemme confess...i am new to ubuntu....so just like millions i mite get lost amid navigations ...and i mite pop-in questions frequently...hope u dont mind...
my next query is :

while the update manager in operation, can u not execute the "apt-get" or any other command...a minute back i tried to follow ur suggestion on installin jdk and an error i came across was :

[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/B]

what i understand is dat, the system locks resources for the update manager but what
i fail to understand is, why wont it let u multitask....isn it an issue of scalability ? or do u have a solution for it..?

---

### Post by ibutho on 2008-12-08
One reason for the behaviour you mentioned, could be that the package management tools write to the same files and one database. If more than one instance is running at the same time, this can corrupt the files and database.

---

