---
title: "Intipunku 0.4 pre 2"
date: 2008-11-12
forum: Desktop Environments
---

### Post by irielion on 2008-11-12
Hi!
I would like to promote my photo manager Intipunku. Intipunku has been an attempt to provide a good feature rich photo manager for linux. At the moment Intipunku offers many things.
* Quick and easy photo filters and correction (incl redeye)
* Manual controls for contrast, brightness, temperature and colors
* Panorama creation
* Tagger
* Export to html album, flickr, picasaweb, flash video
* Import from camera, directory and picasaweb
* Translated in many languages
and more...

Currently i have released 0.4-pre2. It contains some bugs, however I would like to see how people think about it.

I fully support ubuntu (incl mint). There is an installer that configures you apt repo and adds intipunku repo, it will ask you for which optional components you would like to install and then finally installs. You can also easily install the apt repo and then install it with the package manager, when you want to access a feature in intipunku it will ask you whether you want to install the necessary package.

Check out all this at: [http://intipunku.berlios.de](http://intipunku.berlios.de)

I ve attached some screenshots.

---

### Post by binbash on 2008-11-12
It is cool to see linux photo management softwares.But the installer script SHOULD only be executable via root only.You should end the script if not runned via root or root privilages.

---

### Post by irielion on 2008-11-13
No because i use gtksudo do install the packages. So you can start it was user and then it will ask for passwords. Doesn't it work?

---

### Post by binbash on 2008-11-13
> **irielion said:**
> No because i use gtksudo do install the packages. So you can start it was user and then it will ask for passwords. Doesn't it work?

If there is a missing key at apt it does not work.

---

### Post by irielion on 2008-11-13
How come, i do this with synaptic and synaptic will simply say no verified or something and you can override it.

---

### Post by binbash on 2008-11-13
I dont know but importing my missing key file (wine repo) , it works perfect

I guess the problem is occurs when you try to write : 

# Intipunk APT repository
deb [http://ppa.launchpad.net/intipunku/ubuntu](http://ppa.launchpad.net/intipunku/ubuntu) hardy main


I didnt check the script but after adding this you probably give apt-get update command and it stucks there i guess : )

---

### Post by irielion on 2008-11-13
But did it add the line? apt-get update should make a fuz about no apt-keys

---

### Post by binbash on 2008-11-13
> **irielion said:**
> But did it add the line? apt-get update should make a fuz about no apt-keys


Yes it adds but it stucks at terminal.I fixed the key and it works perfect after that.

---

### Post by irielion on 2008-11-13
Maybe a stupid question, how do you fix the key? I have added my own key to the apt db, but it still complains.

---

### Post by binbash on 2008-11-13
> **irielion said:**
> Maybe a stupid question, how do you fix the key? I have added my own key to the apt db, but it still complains.

It is not about your key.

Let me give you an example ( this is what caused me to stuck) :

You add wine repo : 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and dont add the key via synaptics or command line.

Your installer script (AT LEAST FOR ME) stuck at terminal if you dont add wine key.

Please test it since it may not be a global problem (only for me :) )

---

### Post by irielion on 2008-11-13
yea you're right i understand now. apt-get update should be a process that cannot hang.

---

### Post by Errol on 2009-01-10
Hi Mark
I must be too much of a newbie because I cannot install intipunku.
I put the relevant lines in the repo and changed to intrepid (my distro). I typed sudo apt-get install intipunku and was informed that the package did not exist.
Where do I go from here?
Thanks
Errol

---

### Post by irielion on 2009-01-10
Dont change it to intrepid. The packages are build for hardy, but work fine on intrepid. I guess you were too little of a newby ;). I however suggest you download the installer at intipunku.berlios.de because it can configure various extra packages. If you prefer this method, you can install them from the program.

---

### Post by Errol on 2009-01-10
Downloaded the installer. How do I now install the program? Changed the sources.list to back to hardy.

---

### Post by irielion on 2009-01-10
The installer, run it. I suppose it is executable and then just double click it, otherwise from console ./intipunku-installer...run

---

### Post by Errol on 2009-01-10
I still haven't been able to install inyipunku.
When double clicking on the download it open kete and I get this message:The file /home/errol/Downloads/intipunku-0.4-debinstall.run is a binary, saving it will result in a corrupt file.

If I open the terminal (I use kubuntu) I tried various ways to install and these are the results:
errol@errol-linux:~$ sudo /home/errol/Downloads/intipunku-0.4-debinstall.run
sudo: /home/errol/Downloads/intipunku-0.4-debinstall.run: command not found
errol@errol-linux:~$ /home/errol/Downloads/intipunku-0.4-debinstall.run
bash: /home/errol/Downloads/intipunku-0.4-debinstall.run: Permission denied
errol@errol-linux:~$ sudo /home/errol/Downloads/intipunku-0.4-debinstall...run
sudo: /home/errol/Downloads/intipunku-0.4-debinstall...run: command not found
errol@errol-linux:~$ ./intipunku-installer...run
bash: ./intipunku-installer...run: No such file or directory
errol@errol-linux:~$ ./intipunku-0.4-debinstall.run
bash: ./intipunku-0.4-debinstall.run: No such file or directory
errol@errol-linux:~$ ~./intipunku-0.4-debinstall.run
bash: ~./intipunku-0.4-debinstall.run: No such file or directory
errol@errol-linux:~$ sudo /home/errol/Downloads/intipunku-0.4-debinstall.run
[sudo] password for errol:
sudo: /home/errol/Downloads/intipunku-0.4-debinstall.run: command not found
errol@errol-linux:~$ /home/errol/Downloads/intipunku-0.4-debinstall.run
bash: /home/errol/Downloads/intipunku-0.4-debinstall.run: Permission denied
errol@errol-linux:~$ /home/errol/Downloads/intipunku-0.4-debinstall...run
bash: /home/errol/Downloads/intipunku-0.4-debinstall...run: No such file or directory
errol@errol-linux:~$

I am obviously doing something wrong but what????

---

### Post by irielion on 2009-01-11
Huh, well i tried it in gnome. From commandline you should do: ./intipunku..run
No need for sudo. But remember if you write sudo command, it is looking in PATH. if you do sudo ./command it will find it. Good luck tell me if you have more problems.

---

### Post by Errol on 2009-01-12
Hi Mark
I eventually managed to install and get Intipunku to work. At the moment when the program tries to read folders on a NTFS partition it doesn't read anything. On the Linux partition (ext3) it reads and sees my photos without a problem. 
I am able to enter all my NTFS partitions from Ubuntu but not with Intipunku. Is this a known problem?


On more thorough investigation I now see that intipunku is not what I am looking for. It does the same thing that Digikam does, and that is make anther copy of ALL the photos it finds and keeps them in a separate file. That isn't what I'm looking for. Sorry.
What I hoped and thought Intipunku was is a program that catalogs photos on my various hard drives, leaves them in place and save a record of thumbnails where the photos are.
I THINK Kphotoalbum does this and am now investigating it.
Thanks for all your effort, Mark, in helping me!
Errol

---

### Post by irielion on 2009-01-12
First, it does NOT make a copy of all photos, it makes thumbnails.
Concerning the NTFS i remember i heard of this problem before, however after testing it i had no problems. Please file a bug report in launchpad, with the output of the program when you run it in terminal.

---

### Post by Errol on 2009-01-14
MArk, You're right of course. A copy of the thumbnails is made but as it creates a folder in Intipunku that is the same size as the one I have already on my NTFS drive, it isn't the way I want to work. My computer will become full of duplicate folders, instead of a database file which is much smaller than the original. I hope I'm making myself clear. It seems to me that KPhotoalbum does make a database file even though using KPhotoalbum has problems (for me) of its own. At the moment makig one database is complicated but hopefully things will change. The whole file (folder) import method of intipunku is the way I would like KPhotalbum to work. 
Since my last posting I have installed KDE 4.2 (neon beta) and intipunka now has no problems "seeing" and importing from NTFS partitions.
Errol

---

### Post by irielion on 2009-01-14
I dont understand what is your problem, it does NOT make any copy. It CREATES thumbnails, no copy. It doesnt make any new folders either. It just indexes the files in a database and generates thumbnails, and they dont use that much space anyway.

---

### Post by Errol on 2009-01-19
I am obiously using the program incorrectly. I'll explain what I do to see the photos in Intipunku. From the outset I must explain that my background is Windows and my knowledge of the Linux file system is understood in that context. The other point I want to make is what I am trying to do. I am trying to find a linux progrm that will catalogue all my photos. I am looking (preferably) for a program that will thumbnail all my photos no matter where they are - whether on the computer or on an external drive. 
What I did to "see" all my photos on my computer usng Intipunku was to use the "import photos" icon, find the relevant folder and import them. This creates a duplicate copy of that folder on my home drive in a folder called images. That duplicate copy is exactly the same size as the folder from where it was copied (in one case 220MB).I found no other way to "see" photo folders on my hard dive (most of the folders are on a NTFS partition) with Intipunku. 
As I said above I must be doing something wrong but I didn't find explanations on how to look on the hard drives using Intipunku. I really like the look of Intipunku but I seem to need some "hand holding" to understad how to use it correctly.
Errol

---

### Post by irielion on 2009-01-19
The import function is to import fotos to your current library. Intipunku has one central library folder. You can change this folder in the preferences.In the startup wizard i asked for a library folder, if this folder is empty, you are forced to import fotos. Maybe you went through that wizard too fast.

Btw, if you like this version the next version you;ll like more, it has more editor filter/corrections, you can make collages (piles and popart), and you can play videos!

---

### Post by Errol on 2009-01-19
Mark sorry for being such a PITA but I don't understand what to do. Let's say I have a folder called "my_shots" on a drive somewhere with 200 photos in it. How do I get Intipunku to build the central library for itself. My central library in Intipunku is called "images". Maybe if you described a stage by stage description I would understand. When I do "import" in Intipunku, and mark the folder "my_shots", it builds another folder with the same name AND all the photos that were in "my_shots".

---

### Post by irielion on 2009-01-19
Yes, look, this is how i have my folders structured:

~/Images/album1,album2,album3/photos

so you should create a folder images, and put the photo containing folders in this central folder.

---

### Post by Errol on 2009-01-19
Ah! I think I understand. ALL my PHOTOS have to be imported into a central intipunku folder? If that is the case I have the same problem with Intipunku that I have with Digikam. I don't want all my photos in one central place. There are too many to have on one hard drive. I have three HD's and photos are spread out between them. 
I thought Intipunku would catalog my photos and enable me to leave tham on the drive they were on, while creating pointers (thumbnails) to the originals.
Am I now understanding the workings of Intipunku correctly?

---

### Post by irielion on 2009-01-19
I guess, but remember you can try to make symlinks pointing out to the different dirs you have.

---

### Post by Errol on 2009-01-19
symlinks???? how does that work?

---

### Post by irielion on 2009-01-19
In computing, a symbolic link (also symlink or soft link) is a special type of file that contains a reference to another file or directory in the form of an absolute or relative path and that affects pathname resolution.

You make them with the command ln -s
In GNOME you can make them with make link in nautilus, however i dunno about kde.

---

