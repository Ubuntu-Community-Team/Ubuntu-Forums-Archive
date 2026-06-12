---
title: "Unreal Tournament 2004 on Ubuntu? Show me!"
date: 2010-05-17
forum: Gaming &amp; Leisure
---

### Post by Jimbo8098 on 2010-05-17
I have had UT2004 for quite a while and have been using it mainly on pc BUT now that i find out that the game can be used on linux i am dying to try it out! I have the DVD version of the original game and inside the DVD there is a linux installer BUT when i try to run it i get an error message saying:

------

Could not open the file /media/UT2004_DVD/linux-installer.sh.

gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.

------

Is it possibly due to the fact that I am running a 64 bit system? I have tried all of the options it gives me and i cannot run the installer. The exe doesnt work cos its linux. So all I am left to do is dream of the happy fraggy world that could have been mine today :'(

Any help appreciated :)

---

### Post by wieman01 on 2010-05-17
By the way, you can also install via Wine. Just install Wine and execute the corresponding Windows setup file. That's how did it a while back.

---

### Post by ELD on 2010-05-17
> **wieman01 said:**
> By the way, you can also install via Wine. Just install Wine and execute the corresponding Windows setup file. That's how did it a while back.

That is a Wine install, why would someone do that when there is a native installer?

To the OP: You are trying to open it the wrong way, gedit is a text editor. You need to run the file, using the terminal is probably the best way.

```

./linux-installer.sh

```
In terminal will do it. You will need to be in that directory though.
So
```

cd /media/UT2004_DVD/

```
First.

---

### Post by Jimbo8098 on 2010-05-17
Ye i was just about to reply saying that but ubuntu crashed. OK so ill try that.

---

### Post by Jimbo8098 on 2010-05-17
OK tried that and i get a message saying that that directory doesnt exist :(. Just carry on and try to get the directory?

---

### Post by Rustybolts on 2010-05-17
Open terminal then drag and drop the file into terminal window.
Press enter

---

### Post by Jimbo8098 on 2010-05-17
I get a message saying:

bash: /media/UT2004_DVD/linux-installer.sh: Permission denied

when i drag and drop into the terminal and press enter

---

### Post by Rustybolts on 2010-05-17
type sudo first then drag and drop then

---

### Post by Jimbo8098 on 2010-05-17
sudo: /media/UT2004_DVD/linux-installer.sh: command not found

another one :)

But it does ask for my password so it must be along the right lines

---

### Post by Rustybolts on 2010-05-17
sudo '/media/cdrom0/linux-installer.sh' 
[COLOR=Red]not[/COLOR] sudo[COLOR=Red]:[/COLOR] '/media/cdrom0/linux-installer.sh'

---

### Post by Jimbo8098 on 2010-05-17
Thats what i did , that the error message i got :(

---

### Post by Rustybolts on 2010-05-17
Did you press space after you typed sudo if not you need to before dragging and dropping file

---

### Post by Jimbo8098 on 2010-05-17
Yeah i did press space after I dragged the file there. Heres the input and output:

jimbo8098@jimbo8098-desktop:~$ sudo '/media/UT2004_DVD/linux-installer.sh' 
sudo: /media/UT2004_DVD/linux-installer.sh: command not found

---

### Post by Ziggy Stardust on 2010-05-17
Try this:

```
sudo sh '/media/cdrom0/linux-installer.sh' 
```

---

### Post by buddyd16 on 2010-05-17
just went through this myself last night and got it to run with no sound.

first cd to the disc directory on ubuntu 10.04 for me it was

```
cd /media/UT2004_DVD/
```

then:

```
export SETUP_CDROM=*/path/to/your/mounted/cdrom*
```

because the installer script will look for the dvd at /cdrom not /media

then: (while in the disc directory)

```
sudo sh linux-installer.sh
```

if you get through the full install process the you will need to find the 64 bit version of libdc++5 I think it is and place it in the games system folder which if I recall corretly will be at /usr/local/games/ut2004/system

---

### Post by Jimbo8098 on 2010-05-17
Nope lol . Heres what i get:

jimbo8098@jimbo8098-desktop:~$ sudo sh '/media/cdrom0/linux-installer.sh'
sh: Can't open /media/cdrom0/linux-installer.sh

---

### Post by Rustybolts on 2010-05-17
Make a copy of linux-installer.sh to your desktop right click it and in properties enable permissions to execute as program then repeat my steps again with this copy

---

### Post by u235sentinel on 2010-05-17
> **Jimbo8098 said:**
> Ye i was just about to reply saying that but ubuntu crashed. OK so ill try that.

I also recommend upgrading to the latest version for the linux install.  The installer is on the disk and was a little buggy for me.  After upgrading to the latest version I haven't had a problem since.

---

### Post by Jimbo8098 on 2010-05-17
The installation process began successfully however when i try to specify where i want the files to go i get an error saying :

No write permission to /usr/local/games

Thats the default path so ill try some others

---

### Post by Jimbo8098 on 2010-05-17
> **u235sentinel said:**
> I also recommend upgrading to the latest version for the linux install.  The installer is on the disk and was a little buggy for me.  After upgrading to the latest version I haven't had a problem since.

Im using Lucid Lynx right now but is this really on the install cd? Why didnt it install during initial install?

---

### Post by Rustybolts on 2010-05-17
Install to your home directory e.g
/home/[COLOR=Red]your username here[/COLOR]

---

### Post by Jimbo8098 on 2010-05-17
Tried usr/games and it says the same thing. I also tried / again same thing happened

---

### Post by Jimbo8098 on 2010-05-17
It let me install there but now its asking me if i want to install symbolic links. What is a symbolic link?

---

### Post by buddyd16 on 2010-05-17
jimbo8098 refer to my previous post.

---

### Post by Jimbo8098 on 2010-05-17
> **buddyd16 said:**
> jimbo8098 refer to my previous post.

which part ?

---

### Post by buddyd16 on 2010-05-17
run through the whole process and let me know if it is more succesful for you.

---

### Post by Rustybolts on 2010-05-17
don't install symbolic links. Carry on with your install your almost there.

---

### Post by Jimbo8098 on 2010-05-17
Base install asks me to insert the play disc , but it is a DVD and all of the cds are on it.

---

### Post by Jimbo8098 on 2010-05-17
Im asked to do the same during installation of the source code too. Dam :(

---

### Post by buddyd16 on 2010-05-17
Jimbo8098 you need to do this

```
export SETUP_CDROM=/path/to/your/mounted/cdrom
```

before you run the installer

for me the above looked like this

```
export SETUP_CDROM=/media/UT2004_DVD/
```

---

### Post by Jimbo8098 on 2010-05-17
Ok it seems to have installed but it wont start up. I did notice that the installer gave messages like "not enough space on any of the cdroms for announcer.something" and some missing files. So its still technically not working though i have no idea why...

---

### Post by Jimbo8098 on 2010-05-17
On another not there is a solution to buddy's sound problem:

[http://ubuntuforums.org/showthread.php?t=366789](http://ubuntuforums.org/showthread.php?t=366789)

---

### Post by buddyd16 on 2010-05-17
you need to get either the 32 bit or 64 bit version libdc++5, it'll tell you if you try and run the game via the terminal, depending on your system. I found it on these forums somewhere I'll see I can't find the link again and post it here for you.

thanks for the link on the sound fix.

---

### Post by Jimbo8098 on 2010-05-17
Is this guy talking about the same thing?

[http://www.linuxforums.org/forum/redhat-fedora-linux-help/27139-thunderbird-question.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/27139-thunderbird-question.html)

---

### Post by Jimbo8098 on 2010-05-17
What about this tool?

[http://dag.wieers.com/rpm/packages/apt/](http://dag.wieers.com/rpm/packages/apt/)

---

### Post by Jimbo8098 on 2010-05-17
Hmmm look at this input output:

jimbo8098@jimbo8098-desktop:~$ ls -la /usr/lib | grep libstdc++
lrwxrwxrwx   1 root root       19 2010-05-15 20:42 libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r--   1 root root  1044112 2010-03-27 00:16 libstdc++.so.6.0.13

I was following advice from:

[http://ubuntuforums.org/showthread.php?t=160003&highlight=libdc](http://ubuntuforums.org/showthread.php?t=160003&highlight=libdc)

---

### Post by Jimbo8098 on 2010-05-17
I/O:

jimbo8098@jimbo8098-desktop:~$ sudo apt-get install libstdc++5
[sudo] password for jimbo8098: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++5
jimbo8098@jimbo8098-desktop:~$ ^C
jimbo8098@jimbo8098-desktop:~$ 

Following instructions from later in that article. Why wont it install?

LOL @ my ctrl+c mistake

---

### Post by buddyd16 on 2010-05-17
[http://ubuntuforums.org/showthread.php?t=1309697]("http://ubuntuforums.org/showthread.php?t=1309697")

that thread runs through it pretty nicely

---

### Post by u235sentinel on 2010-05-17
> **Jimbo8098 said:**
> Im using Lucid Lynx right now but is this really on the install cd? Why didnt it install during initial install?

because the update come out after the cd/dvd was created.  There were several updates actually.  The latest works great :D

---

### Post by Jimbo8098 on 2010-05-18
> **u235sentinel said:**
> because the update come out after the cd/dvd was created.  There were several updates actually.  The latest works great :D

I did intall all of the updates using the update manager but i have no idea where the file you are talking about is. Ill look on the disk. Cant find it on the disk and i have the most up to date version according to update manager and i have tried upgrading too , there are no more upgrades. So either it is something really silly or something really serious.

So basically , where do you find these updates?

---

### Post by u235sentinel on 2010-05-18
> **Jimbo8098 said:**
> I did intall all of the updates using the update manager but i have no idea where the file you are talking about is. Ill look on the disk. Cant find it on the disk and i have the most up to date version according to update manager and i have tried upgrading too , there are no more upgrades. So either it is something really silly or something really serious.

So basically , where do you find these updates?

I found it on fileplanet.com.

There were many maps out there as well as some really cool skins.

---

### Post by Jimbo8098 on 2010-05-18
I was talking about the ubuntu crash problem but fair enough XD

---

### Post by Perfect Storm on 2010-05-18
If you checked the stickies you would have found this; UT2004 DVD 64-bit [http://gwos.org/doku.php/guides:64bit:ut2004](http://gwos.org/doku.php/guides:64bit:ut2004)

---

### Post by wieman01 on 2010-05-18
Listen to AI... if anyone knows anything about gaming, it's him. :-)

---

### Post by u235sentinel on 2010-05-18
> **Jimbo8098 said:**
> I was talking about the ubuntu crash problem but fair enough XD

AI will not lead you astray :-)

Oh and I was also talking about your crash problem.  The site has the linux patch (3306 I think it was).  I had no problems period after applying it.

And to apply it I had to copy stuff into the ut2004 file structure.  No installer and I don't recall any real instructions there also.  Just copy and you're golden.

Oh and listen to AI :-)

---

### Post by Jimbo8098 on 2010-05-19
I just finished playing ut2004 on a test run! Turns out all i had done so far was right but i still needed to do this:

> sudo apt-get update && sudo apt-get upgrade
wget [http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb)
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_amd64.deb


So ye AI was right!Thanks all who helped! Also could you maybe pm me the location of that update sentinel?

3369 is the only patch i can find for linux. Found it here 

[http://www.beyondunreal.com/main/ut2004/ut2004wizard.php](http://www.beyondunreal.com/main/ut2004/ut2004wizard.php)

Thats ALL the updates for linux version i think. Thanks to all who helped.

=== Topic Solved :) ===

---

### Post by Jimbo8098 on 2010-05-19
O and that update was for a normal retail disc , if you want the collectors editions go here:

[http://www.beyondunreal.com/main/ut2004/ut2004essential.php](http://www.beyondunreal.com/main/ut2004/ut2004essential.php)

---

### Post by u235sentinel on 2010-05-19
> **Jimbo8098 said:**
> I just finished playing ut2004 on a test run! Turns out all i had done so far was right but i still needed to do this:

sudo apt-get update && sudo apt-get upgrade
wget [http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb](http://fr.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_amd64.deb)
sudo dpkg -i libstdc++5_3.3.6-17ubuntu1_amd64.deb

So ye AI was right!Thanks all who helped! Also could you maybe pm me the location of that update sentinel?

3369 is the only patch i can find for linux. Found it here 

[http://www.beyondunreal.com/main/ut2004/ut2004wizard.php](http://www.beyondunreal.com/main/ut2004/ut2004wizard.php)

Thats ALL the updates for linux version i think. Thanks to all who helped.

=== Topic Solved :) ===


I figured everyone should benefit from this...

The latest linux patch is 3369.. didn't remember the version number.  Here is the location

[http://www.fileplanet.com/141074/140000/fileinfo/Unreal-Tournament-2004-Patch-v3369-%5BLinux%5D-](http://www.fileplanet.com/141074/140000/fileinfo/Unreal-Tournament-2004-Patch-v3369-%5BLinux%5D-)

Enjoy!

---

