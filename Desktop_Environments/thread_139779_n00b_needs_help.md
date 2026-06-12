---
title: "n00b needs help"
date: 2006-03-04
forum: Desktop Environments
---

### Post by jjbird on 2006-03-04
I recently became interested in Linux and yesterday I installed Ubuntu on an older computer I had lying around.  Today I tried to put some programs on it but in the readme they indicated that I needed to "make" them.  I tried using the terminal but was completely lost there besides which the terminal did not recognize the "make" command.  If someone could help I would really appreciate it.
Thanks
BTW I reall like this OS, it really breathed new life into the computer I was using, I was ready to get rid of it as it was slow with Win 98.  Not exactly a speed demon now, but its very useable, especially for how nice Ubuntu looks on it.

---

### Post by tidy_boy on 2006-03-04
I am very new to ubuntu as well mate it sounds like you have downloaded source. to install source you need to use the terminal to navagate to the folder and do a 

./configure

make

make install

Thats what I did today :D

---

### Post by jjbird on 2006-03-04
I have seen ./configure or something like this in documentation that I have read, but unfortunately I am completely clueless when it comes to using the terminal.   The only folder I have been able to get to is home using cd /home after this i cant get anywhere it just says that the directory is invalid

---

### Post by jjbird on 2006-03-04
On further inspection i have found that using the familiar command prompt commands for browsing thru files worked, for some reason i didn't think to just use cd (filename) but anyway I still am clueless about ./configure and make

---

### Post by tidy_boy on 2006-03-04
ok do this cd /home/(yourusername)/Desktop

then do a ls


this will navagate to the desktop and show you a list of files

---

### Post by jjbird on 2006-03-04
ok i think that Ive got the navigation down, thanks for telling me about ls its a lot easier than opening the file browser and checking what the next directory should be.

---

### Post by tidy_boy on 2006-03-04
remember directories are case sensitive so if you did cd /home/(yourusername)/desktop it would not work.

Also to find out what directory you are in type pwd

:D

Hope this helps

---

### Post by jjbird on 2006-03-04
Thanks for all the filebrowsing tips but I still need lots of help on what this "make" thing is and how to use it.  Do i browse to the file that i want to "make" and then type make? Or is there something else i have to do? Also why does the terminal say that the "make" command is invalid?

---

### Post by white_tiger_daniel on 2006-03-04
I am having the same problem it's so annoying eh mate

---

### Post by tidy_boy on 2006-03-04
the software you have downloaded have you extracted the contents.

all you have to do then is navagate to the folder and then type 

./configure


then 


make


then 


make install


:D

---

### Post by Spano on 2006-03-04
As above by tidy_boy, except:
```
sudo make install
```
you need to be super user to install.  Ain't Linux Fun!?

---

### Post by jjbird on 2006-03-04
I typed in ./configure when i had navigated to the folder in question and got

./configure: no such file or directory

---

### Post by tidy_boy on 2006-03-04
where you super user when you did ./configure :D

---

### Post by pbransford on 2006-03-04
Pressing tab does tab completion... repeatedly pressing tab cycles through the possible completions...

example... pressing TAB at the end of:
/home/USERNAME/De
would likely (unless you had something starting with De that came before Desktop in alphabetical order) end up getting:
/home/USERNAME/Desktop


Also, ./configure tells the shell to execute the file "configure". "./" means current directory.

Be aware that you will likely run into issues with "dependancies" - software and libraries that must be installed to compile (or build, literally) the program. You also need the compilers and such installed.

If you are new, stick to using the included packaged programs (and package browsers like synaptic) untill you are more comfortable, otherwise frustration may get the better of you.



I suggest you take a gander at these:
[http://www.tldp.org/LDP/intro-linux/html/index.html](http://www.tldp.org/LDP/intro-linux/html/index.html)
for general linux information, and:
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)
for info on "bash" - the default shell. A shell is the thing that reads what you type on the command line and works with it.

---

### Post by jjbird on 2006-03-04
i tried to do sudo ./configure and it prompted me for a password when i typed nothing appeared on the screen, i typed my password anyway and hit enter, it said it was invalid and gave me another try.  After retyping a password (im not sure if it was the right one, if the root password is the one that I gave ubuntu during installation then it was the right one) it went back to ./configure: no such file or directory.  any further attempts to use sudo ./configure have met with similar results.

---

### Post by chettyk on 2006-03-04
I hate to raise this issue this far into the thread, but have you made sure that the software you want is not available in one of the repositories? If the compiled binary is there, installation is so much simpler.

If you want to know more about repositories and installing software from there, you could look at:
[Ubuntu Wiki User Documentation]("https://wiki.ubuntu.com/UserDocumentation")
or
[The Ubuntu Guide]("http://help.ubuntu.com/starterguide/C/index.html")

You could also look at the website [Ubuntu Packages]("http://packages.ubuntu.com/") and see if the software package you seek is there.

---

### Post by verbalshadow on 2006-03-04
installing from source is great but, have you checked to see if the program you want is in any of the repositories. Using apt-get or synaptic.  here is a good howto that covers a lot of  options on installing [http://doc.gwos.org/index.php/ProgramInstallBeginners](http://doc.gwos.org/index.php/ProgramInstallBeginners)

---

### Post by jjbird on 2006-03-04
Well i would look in the repository but the computer with ubuntu on it is not connected to the internet and it is not in a position where it could be without about 50' of CAT5 cable.

---

### Post by Spano on 2006-03-04
sudo is not necessary for ./configure.  
cd to directory then
./configure
make
sudo make install
make clean

You might try reading the "Install" and "README" files in the directory of the software your trying to install.  chettyk and pbransford give good advice use Synaptic - you'll probably find the software your wanting or an equivillant there.
If you want to continue trying to install from source read this page -
[http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm)
Ubuntu is debian based.
It helped me figure it all out, and I'm no genuis.  Good Luck.

---

### Post by jjbird on 2006-03-04
well it is still not recognizing the command.  I guess ill have to break down and connect my computer to the internet to use synaptic.  Thanks for all the help everyone.  Im really amazed at the level of community support here.  I was afraid that with this problem i'd be sifting through pages and pages of documentation that i didnt understand anyway.

---

### Post by rm -rf *.* on 2006-03-05
Have you verified that make is installed on your system?

```
whereis make
```

Also do you have the correct compiler and libraries for building your application? Build-essential comes right off the installation CD. 

```
sudo apt-get install build-essential
```


Good Luck. I would stick with the repositories, they make life a lot easier.

---

### Post by Ptero-4 on 2006-03-05
You can use synaptic to install build-essential (it's all on the install CD, no need for the net for those packages), it will give you gcc, cpp, make, etc.

---

