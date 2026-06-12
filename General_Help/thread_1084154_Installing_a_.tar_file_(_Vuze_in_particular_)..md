---
title: "Installing a .tar file ( Vuze in particular )."
date: 2009-03-01
forum: General Help
---

### Post by noseforsharpies on 2009-03-01
I'm running Ubuntu 8.10, 64-bit version. How do I install Vuze, from a .tar file? I'm really new at this, so if you could dumb it down a good bit, that'd be awesome. I need to learn it eventually, I know . . . Heh. Well, thanks, guys ( or gals ).

---

### Post by metalhead0010 on 2009-03-01
It's like a zip file.  Unzip it into a folder open your terminal and type 
cd [folder were you unzipped it]
Type
./configure; make; make install
Your welcome.

---

### Post by noseforsharpies on 2009-03-01
Does 'cd' need a 'sudo' before it? I tried the command with and without it, and here's what I got:

derek@derek-laptop:~$ cd azureus
bash: cd: azureus: No such file or directory
derek@derek-laptop:~$ sudo cd azureus
[sudo] password for derek: 
sudo: cd: command not found
derek@derek-laptop:~$ cd azureus
bash: cd: azureus: No such file or directory
derek@derek-laptop:~$ cd /Documents/azureus
bash: cd: /Documents/azureus: No such file or directory
derek@derek-laptop:~$ sudo cd /Documents/azureus
sudo: cd: command not found

The contents of the .tar are unzipped in a folder named 'azureus,' so I'm not sure why it's not working.

---

### Post by Rallg on 2009-03-01
General advice, not particular to your system or Vuze:

It depends what is in the *.tar file. Right-click it, and look inside with the archive manager.

If it is a *.deb file, extract it, then install via Terminal:

sudo dpkg -i name-of-file.deb

That assumes the file is sitting in your home folder. If not, then put the path along with the file name. Some applications do not need sudo, most do. I should point out that you should not sudo ANYTHING unless you are confident of its purpose and authenticity.

If the enclosed file is an *.rpm (Redhat package), you will need to use Synaptic package manager to install the "alien" program, which converts from *.rpm to *.deb. Then, invoke alien via Terminal. It may take awhile to do the conversion, so be patient. Then install the *.deb as above.

However, something inside a *.tar file is likely to be source code, not an installable package. If so, you will have to compile the program on your system. This takes time, and you may need to install other packages that support the source code. If there is a home page for the Vuze project, or a Debian project page, go there and see what packages you need, then install them. If you've never compiled anything, use Synaptic to get build-essential, which has stuff that is common to most compilations.

A package of source code usually contains text instructions in an "install" file, that tells you what to do. Most, but not all, compilations require you to open Terminal, change directory to the folder that has the source code, then do this:

./configure
make
sudo make install

Again, don't sudo anything you don't need to sudo. If you are missing a necessary component package, a Terminal error message will inform you.

Sometimes the make step takes a lot of time, You can minimize the Terminal window and do other things while that happens, such as surf the Internet. Just don't accidentally close the Terminal while work is in progress, or you will need a do-over.

---

### Post by Rallg on 2009-03-01
Regarding that cd azureus:

Exactly where is the azureus folder? When you use cd, it is relative to the folder in which the prompt is already placed. When you open a Terminal, you are in your user Home folder. Is that where azureus is? Perhaps it is on your Desktop? If so, use cd Desktop/azureus.

Generally, when you cd, beginning with the slash starts you from the file system top level. Beginning with the tilde starts you from your user Home directory. Anything else starts your from wherever you are now (which might be your user Home directory).

Using sudo cd is rarely of benefit.

---

### Post by noseforsharpies on 2009-03-01
Well, now the terminal is giving me this:

derek@derek-laptop:~/Documents/azureus$ 

What commands am I supposed to use now?

---

### Post by Rallg on 2009-03-01
See reply #4.

---

### Post by noseforsharpies on 2009-03-01
derek@derek-laptop:~/Documents/azureus$ ./configure
bash: ./configure: No such file or directory

What am I doing wrong here? I tried replacing the '.' with 'azureus' and '/Documents/azureus' as well, and nothing's working.

---

### Post by Rallg on 2009-03-01
Let's go back to square one.

Did you get Vuze from its project home page on sourceforge.net? It provides Vuze_Installer.tar.gz. Double-click it. The archive manager opens, Extract the contents.

You will obtain folder named "vize" (not azureus). Inside, there are instructions in a README file. No compilation necessary. The program is  Java application, so you must have Java installed. On a 32-bit system, that is easy: Sun Java has a native version. But you are on a 64-bit system. The trick is to get Java working there. That, I cannot advise.

If, on the other hand, you have source code for a 64-bit system, then you will need to read its "install" file for advice.

---

### Post by noseforsharpies on 2009-03-01
Alright, I got it to start. The only problem I have left is that I have to go through the terminal to start it up. Is there a way to form an icon for it, or something along those lines?

---

### Post by noseforsharpies on 2009-03-01
Nevermind, I figured that part out. Well, problem solved. Thanks, everybody.

---

### Post by aktiwers on 2009-03-01
> **noseforsharpies said:**
> Alright, I got it to start. The only problem I have left is that I have to go through the terminal to start it up. Is there a way to form an icon for it, or something along those lines?

Where do you want to create the Icon?
Right-click on your desktop and pick "create launcher".
Or on your Panel and pick "add to panel" then "Add custom launcher"

Fill in the fiels and in the command field pick the one you used to launch it from terminal.

Want to add it to your application menu?
look here: [http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html](http://www.ubuntugeek.com/howto-add-entries-in-gnome-menu.html)

---

