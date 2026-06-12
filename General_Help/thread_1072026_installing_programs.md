---
title: "installing programs"
date: 2009-02-17
forum: General Help
---

### Post by sansa dude on 2009-02-17
im kinda a newbie when it comes to installing files in ubuntu because im used to windows having all installation files being automatic or in a .exe file. i trying to install some programs that came in .tar.gz files can some one help me as to how to install these files it would be greatly appreciated :D

---

### Post by gettinoriginal on 2009-02-17
Here ya go:  :p
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

---

### Post by mikewu on 2009-02-17
Programs that come in .tar.gz (tarballs) are generally source files. It's easiest to do this from a shell.

Navigate to the direction containing the tarball (cd command)

Then to unpack the tarball, use the tar command. (Tarballs are really an archive that was zipped)

> tar -xvzf name_of_tarball.tar.gz 
This tells the tar program to -x extract, -v be verbose, -z unzip the file with gzip, and -f run on the file following this flag.

Assuming that was successful, cd into the created folder. 

Read the README if there is one. Follow their instructions if they deviate from mine.

run the command
> ./configure 

This will check that the your computer has necessary files and will configure the program to match your computer.

Sometimes it will return with an error and you will need to download other libraries.

If it does return sucessfully, then run
> make

This will compile the source code.

After a few minutes, it will finish. Then run

> sudo make install

This will move the files to the correct places and install the program.

Good luck!

---

### Post by sansa dude on 2009-02-17
ok so if i were to install a file from my desktop how would i do that? could some one give me the exact sort of codes to do this from the desktop please ;)

---

### Post by oldos2er on 2009-02-18
What program is it? Chances are it's in the repositories, and you'd be much better off installing it from there. See the menus Applications, Add/Remove, or System, Administration, Synaptic Package Manager.

---

### Post by mikewu on 2009-02-18
oldos2er is right. First check if the program is in the repositories. apt-cache search name_of_program will return package names that match. sudo apt-get install package_name will install them. 

This method is better because it resolves all the dependencies for you and the program is precompiled as well. 

If you're not used to the command line, go to the synaptic package manager as oldos2er described.

Press the search button. 
Enter in the program name. 

Scroll through the list and if you find the program, click on the checkbox and choose mark for installation.

Then hit apply at the top of the program. Everything should install itself.




If only a source version is available then open gnome-terminal

```
cd ~/Desktop
```
Change the working directory to desktop

```
tar -xzvf name_of_tarball.tar.gz
```
Extract the folder

```
cd name_of_tarball
```
Go into folder

```
./configure
```
Check and configure options

```
make
```
Compile source

```
sudo make install
```
Install program

---

### Post by sansa dude on 2009-02-21
thanks for the support and they are programs like a youtube mp3 downloader and some games that im pretty sure arnt in the add remove section

---

### Post by WaffleCode on 2009-02-21
You can always run *apt-cache search [program name]* to be sure ....

---

### Post by ramjet_1953 on 2009-02-21
Have you enabled the extra repositories?

Navigate to:

[COLOR="Blue"]Applications>Add/Remove[/COLOR]

When the window opens, click on the Show drop-down menu at top centre and select [COLOR="Blue"]All Available Applications[/COLOR].

Regards,
Roger :D

---

