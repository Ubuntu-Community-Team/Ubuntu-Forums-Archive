---
title: "tarball files and the ./configure command"
date: 2009-04-12
forum: General Help
---

### Post by MatthewZ31 on 2009-04-12
im new at linux but im getting the hang of it, and im really starting to like it.

and while just mess around with TGZ files and trying to install them, 2 questions arose

1. is it nessacary to extract the folder out of the tgz file through code, even though u can do it the easier way of clicking and dragging like any other archive file type?

2. say i extracted the folder onto the desktop, and then changed the directory by typing this.

cd /home/username/Desktop/

then i type the name of the folder i just extracted to the desktop

cd foldername/

now isn't this the part where u type,

./configure

i ask because this is when my noob coding stops.
i get this,

bash: ./configure: No such file or directory

so whats the next 'real' step?

---

### Post by ad_267 on 2009-04-12
1. No it's not necessary, you can extract them from the gui like any other archive.

2. It depends on what you've downloaded, not all source packages are the same. Some are simple enough that they don't need a configure script, and you can simply run make. Others require you to run aclocal, autoconf and automake before being able to run ./configure.

There should be a README or INSTALL file you can read to find out the procedure required. If you want to read a file from the command line, less is a good program to use. eg. "less README"

Also just to make sure, because a lot of people new to Linux don't realise it, you know most applications can be easily installed from the package manager without having to compile them?

---

### Post by RuleMaker on 2009-04-12
As ad_267 said, ./configure is the next step in most cases but not always.
We could help you much more if you give us the output of ls -a and the name of the package you want to install (compile).

---

### Post by MatthewZ31 on 2009-04-12
Thanks for the quick reply!

Oh i know about the Package manager, only had linux for a day and finding that was amazing, lol.

pretty impressive.

but this program isn't in the package manager, plus this is something i really want to know how to do.

as for the README and INSTALL file, i look for those 1st and came up dry.

but out of coureosity,

how is the chmod 755 command used?
and the csh command?

Thanks again.

---

### Post by MatthewZ31 on 2009-04-12
sry, ur post came up as i was writing the last one.

but i am guess you,Rulemaker, what me to post this?

matthew@matthew-laptop:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
matthew@matthew-laptop:~$ cd /home/matthew/Desktop/
matthew@matthew-laptop:~/Desktop$ cd shake-v4.00.0607/
matthew@matthew-laptop:~/Desktop/shake-v4.00.0607$

---

### Post by RuleMaker on 2009-04-12
```
sudo chmod 755 <file_name>
```
I never heard about the second command.

EDIT:
No, do the ls -a inside the shake-v4.00.0607 directory.

---

### Post by ad_267 on 2009-04-12
csh is a shell, like the bash shell which is used by default in Ubuntu. The shell is the thing that runs when you open a terminal, and is what you enter commands into.

You can find out about a command by entering "man command_name", eg "man chmod"

chmod modifies file permissions. 755 means read, write and executable permissions are set for the user, and read and executable permissions are set for the group and other users. Do a search for linux or unix file permissions for more information.

If you post the list of contents of the extracted archive or tell us where to find the file you downloaded we should be able to help.

---

### Post by ad_267 on 2009-04-12
I did a search for shake and found this:
[http://ubuntuforums.org/showthread.php?t=185656](http://ubuntuforums.org/showthread.php?t=185656)

It looks like you probably don't have a source archive but an archive containing the actual executable file. You should be able to do:
```
sudo apt-get install tcsh
cd ~/Desktop/shake-v4.00.0607/bin/
csh shake
```

---

### Post by MatthewZ31 on 2009-04-12
I want to say thanks, this has to be the most fastest responding forum ive ever been on.


here is what directly in the Shake folder,

matthew@matthew-laptop:~/Desktop/shake-v4.00.0607$ ls
bin  doc  fonts  icons  icons.pak  include  keys  lib


this is whats in the bin folder,
matthew@matthew-laptop:~/Desktop/shake-v4.00.0607/bin$ ls
mkpak  shake  shkv.exe  shkx.exe  tshake  tshkx.exe

i would give where i dl the file but it wasn't a direct download.


ill try this code
sudo apt-get install tcsh
cd ~/Desktop/shake-v4.00.0607/bin/
csh shake

ive found this already but forgot to go back once i found out how to make the desktop the directory. Its easy to lose track of what to do when learning the basics as u go, lol 

i already have tcsh because of it.

ill give it a shot


and thanks ill make good use of this "man command_name". =)


i entered 
~/Desktop/shake-v4.00.0607/bin$ csh shake

and nothing happened..?
it just enter down the next line, not even showing the "matthew@matthew-laptop:"
its just a blank line, whats that mean?

---

### Post by RuleMaker on 2009-04-13
Seems to me that you have a wrong package.
Linux don't use such extensions as .exe
Tell us what exactly you want to install and we will tell you where to find it and how to compile/install it.

---

### Post by MatthewZ31 on 2009-04-13
i would like to install the compositing application Shake 4.1 or 4.0, both i believe are for linux, I'm a Visual Effect student, but considering most forums and their intolerance toward pirated software..im not sure how far you may go to help me.

don't get me wrong,
i would be glad to buy it, but it coast 5000 bucks, 4999 to be exact,lol.

so i'm sure im on my own trying to find the app.

---

### Post by RuleMaker on 2009-04-13
I can't guide you much further since we are talking about commercail software, try to find the answer [here]("http://www.vfxtalk.com/forum/shake-4-linux-help-t9089.html?").

---

### Post by MatthewZ31 on 2009-04-13
I figured as much, but u guys where alot of help.
understand this OS is getting easier and easier.

im sure ill have more questions about commands, but thats another day.
hope to see you around.

but can u answer this,

sometimes in the terminal. and i enter code
it justs enters down to the next line, not even showing the "matthew@matthew-laptop:"
its just a blank line,u can type but u cant put in code anymore, whats that mean?

---

### Post by ad_267 on 2009-04-13
> **MatthewZ31 said:**
> sometimes in the terminal. and i enter code
it justs enters down to the next line, not even showing the "matthew@matthew-laptop:"
its just a blank line,u can type but u cant put in code anymore, whats that mean?

I'd say that usually means the program is running, it's just stuck somewhere. It could also be waiting for input.

I'd try running that file with ./shake instead of csh shake and see if that helps.

---

### Post by RuleMaker on 2009-04-13
ad_267 told you what is it, you can get out from that situation by pressing ctrl+c.
It can happen when you execute a command without specifying it's required parameters.

---

### Post by MatthewZ31 on 2009-04-13
thank you, again.
getting out of it now is wonderful, lol.

i tried using ./shake
it gave me,
./shake: Permission denied

---

### Post by ad_267 on 2009-04-13
Try changing the file permissions:

```
chmod a+x shake
```

---

### Post by MatthewZ31 on 2009-04-15
yeah chmod a+x was a no go.

it seems ALOT of ppl are having issues,
even a fellow student and i, unknowingly, where runing tandem with this app.

same errors same nonsense.

no idea. =/

---

### Post by MatthewZ31 on 2009-04-16
HALLALOYA!!! it works.

you MUST do these steps if ur using Ubuntu 8.04
it will not run unless u do some modifications.

BEFORE you do anything shake must be in its directory;
/usr/shake-v4.00.....

1. install 32-bit libs (not sure if entirely necessary)
2. download libX11-1.0.3-8.fc7.i386.rpm
3. extract the folder and locate libX11.so.6.2.0
4. place libX11.so.6.2.0 in lib folder in shake directory
5. rename libX11.so.6.2.0 to libX11.so.6
6. go into shake-v4.00../bin folder and open the shake file, and run it so you can modify the code;
7. change the lines;   step 7 isn't needed for version 4.1.

if ${?LD_LIBRARY_PATH} then
setenv LD_LIBRARY_PATH
/usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:${LD_LIBRARY_PATH};
else
setenv LD_LIBRARY_PATH
/usr/lib:${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa;
endif

to

if ${?LD_LIBRARY_PATH} then
setenv LD_LIBRARY_PATH ${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:${LD_LIBRARY_PATH}:/usr/lib
else
setenv LD_LIBRARY_PATH ${NR_SHAKE_LOCATION}/lib:${NR_SHAKE_LOCATION}/lib/mesa:/usr/lib
endif

now u can launch shake using ./shake command.



all of this info can also be found: [http://ubuntuforums.org/showthread.php?t=766327&highlight=shake+hardy](http://ubuntuforums.org/showthread.php?t=766327&highlight=shake+hardy)

---

### Post by ad_267 on 2009-04-16
Glad you got it working!

---

