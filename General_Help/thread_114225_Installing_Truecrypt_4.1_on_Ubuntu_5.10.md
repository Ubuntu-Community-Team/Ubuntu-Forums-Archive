---
title: "Installing Truecrypt 4.1 on Ubuntu 5.10"
date: 2006-01-08
forum: General Help
---

### Post by virtadept on 2006-01-08
HI!

I am trying to install TrueCrypt. I cannot find it using the synaptic package manager. When going to TrueCrypt.org homepage it's possible to download an debian package for ubuntu5.10 but when I try to install using this command
sudo dpkg -i truecrypt_4.1-0_i386.deb

I get an error message including the following line:
Error: Linux kernel version 2.6.12-9-386 required.

What linux kernel version is included in Ubuntu 5.10?

DO anyone know how to install TrueCrypt 4.10 on Ubuntu 5.10?
IF this way involves compiling something then do you know any good guides for learning this as well.

KInd Regards

---

### Post by Thirsteh on 2006-01-08
Hey virtadept.

Have you installed all the updates that are available for you, and if so, what is the output when you type: uname -r

I have upgraded my kernel, although running the -686 version, and my kernel version is 2.6.12-10. It seems that your package possibly requires that specific version -9 and not above, though? Oh well. If you do have a Pentium 4 processor or similar, I recommend that you install the 'linux-686' package.

---

### Post by virtadept on 2006-01-08
Hi!
I only have a 32bit CPU. Athlon XP+3000..
 uname -r gives:
2.6.12-10-386

So I guess the Kernel is to new for the truecrypt package?

The source for TrueCrypt is available for download on the TrueCrypt site. How hard is it to compile this to a working file or install package?

---

### Post by virtadept on 2006-01-08
After downloading the TrueCrypt source, downloading the Linux kernel and some binary tools. Decompressed the linux source to the folder usr/src/linux
I get the following message:
sudo make -C ../../../usr /src/linux config modules
sudo: make: command not found

Does that mean that the compiler and linker is not installed in my installation?
How do I install cc and make?

Is it anyway to skip all these ../../../ when describing folder names? Is there something you can write which works like the root folder?

---

### Post by ahave2005 on 2006-01-08
You need the programs required to build from source. In a console try this first:
> sudo apt-get install build-essential

You might have other dependencies troubles a long the way. Just keep a look out for what the error message is, and install those things.

That is the reason synaptic exsists, to let a package manager deal with dependencies.

/ahave

---

### Post by lamego on 2006-01-08
You should compile truecrypt from the source to match your current ubuntu kernel instead of downgrading your kernel to meet the truecrypt requirements.

---

### Post by virtadept on 2006-01-08
Hi!

I'm trying to recompile Truecrypt for my kernel. But I have to do some stuff to the kernel source first. 
- Linux kernel source code must be configured and all modules built
  (make config modules). 
The result when I'm trying to "make config module" is:
virtadept@sirserver:/usr/src$ sudo make -C linux config modules
make: Entering directory `/usr/src/linux'
Makefile:485: .config: Filen eller katalogen finns inte
/usr/src/linux/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Kommandot hittades inte
make[1]: Inget behöver göras för "Makefile".
/usr/src/linux/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
  HOSTCC  scripts/basic/fixdep
/bin/sh: gcc-3.4: command not found
make[2]: *** [scripts/basic/fixdep] Fel 127
make[1]: *** [scripts_basic] Fel 2
make: *** [config] Fel 2
make: Leaving directory `/usr/src/linux'
Sorry for Swedish. I guess my problem might be that I'm executing make from the wrong path? OR that I have placed the source in the wrong path? Or something?

---

### Post by virtadept on 2006-01-08
Btw. Thanks for the help ahave2005 and others. Now it feels like I'm getting closer to complete this.

---

### Post by lamego on 2006-01-08
Erm, the error is clear, you are missing gcc3.4, install it from synaptic.

---

### Post by virtadept on 2006-01-09
Hi!

I didn't realise that I needed older versions of the compiler as well. The 4.0 version was already installed. OK. Thanks. Now I've managed to do the "build config" it was a nightmare were I had to answer 5 million questions regarding what to include or not. In most cases I just used <enter> to use the default choice....
OK. AFter doing that I was able to execute the build.sh to build TrueCrypt. But now I have a new problem when trying to execute the install.sh file.

virtadept@sirserver:~/truecrypt-4.1-source-code/Linux$ sudo ./install.sh
Checking installation requirements...
Testing truecrypt... Done.

Install binaries to [/usr/local/bin]:
Install man page to [/usr/local/man]:
Error: /usr/local/man/man1 does not exist

The folder /usr/local/man exists on my computer.. But not man1, but I thought the  
installation script should create that directory? 
Is it that I should execute this script from the root somehow? OR include some ../../../ before usr/local/man???

Kind Regards
VirtAdept

---

### Post by lamego on 2006-01-09
You should not use those pathes, those are default for other systems.
For ubuntu the correct paths are:
/usr/bin for binaries
/usr/share/man for the manpages
You will need to run the script with sudo (root)
The script does not create those dirs because those are system dirs, the corrects paths already exist...

---

### Post by virtadept on 2006-01-10
Hi!
I thought I had got it to work now. But it is still some step that has failed...

Installation worked fine:
virtadept@sirserver:~/truecrypt-4.1-source-code/Linux$ sudo ./install.sh
Password:
Checking installation requirements...
Testing truecrypt... Done.

Install binaries to [/usr/local/bin]: /usr/bin
Install man page to [/usr/local/man]: /usr/share/man
Allow non-admin users to run TrueCrypt [y/N]: Y
Installing kernel module... Done.
Installing truecrypt to /usr/bin... Done.
Installing truecrypt man page to /usr/share/man/man1... Done.
;----------------------
But executing TrueCrypt tells me I have some problem: 
virtadept@sirserver:/$ sudo truecrypt ntfs1/IamDArkness.dat
Enter password for '//ntfs1/IamDArkness.dat':
FATAL: Error inserting truecrypt (/lib/modules/2.6.12-10-386/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module
;-----------------------------------------------------------------------------
IamDArkness.dat is a working TrueCrypt file under WindowsXP. Iäve tried copying the file to an FAT32 partion but got the same error message.
Somehow the build of Truecrypt must have failed or some file is being copied to the wrong path?

---

### Post by lamego on 2006-01-10
It seems the module compilation was not successfull...

You can try to manully load the kernel module with:
(Yes you need to use the ` `)
`moprobe -v truecrypt`

---

### Post by virtadept on 2006-01-12
Ok. Thanks for the help but I cannot get that command to work. I've tried copy and paste the command into the shell, including the ' ' signs. 

To make matters worse. When I rebooted the machine my ddclient installation suddenly stopped working and when I try to launch it manually I get some confusing error message. Also the TeamSpeak server did not AutoStart as I hoped it would. 

To make a long story short I'm deciding to give up on Linux for awhile. I was planning to evaluate it for one month, but because I so far haven't succeded with Truecrypt, dyndns, team-speak, pure-ftp, sharing the fat32&ntfs drive on the LAN network and getting the Creative Audigy SE audiocard to work. I estimate it will take me at least 6 month to get all the things I want working. While in Windows Xp my main problem is that the FTP server is not working good enough. 

I hope future versions of Ubuntu will make it easier to install applications, include more guides for using ntfs&fat32 drives, and so on.

---

### Post by philxxx on 2006-02-04
After having the same problem mentioned above (having a newer kernel than the truecrypt.deb file was builded for) I wourl like to know if anybody has successfully 
setup TrueCrypt in Ubuntu 5.10 (kernel: 2.6.12-10-386)

I really hope there is a solution or howto, since I can't image, that it can be that hard to setup truecrypt in ubuntu compared to how easy it was to setup truecrypt on my Windows XP machine.

regards

P h i l

---

### Post by peterx14 on 2006-03-08
I just installed Truecrypt 4.1 on a 2.6.12-10 kernel and here are the notes I made:
```
sudo apt-get install build-essential
```
I was asked for the Ubuntu install CD here, so you'll probably need it handy.

Note: Below I apt-get headers for 2.6.12-10-386. Obviously, you should substitute whatever is the current and appropriate version for your CPU.
```
sudo apt-get install gcc-3.4
sudo apt-get install linux-headers-2.6.12-10-386
sudo apt-get install linux-source-2.6.12
cd /usr/src/
sudo tar xvjf linux-source-2.6.12.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.12 /usr/src/linux
make -C /usr/src/linux-source-2.6.12 config modules
```
This last command asks absolutely *loads* of questions (literally hundreds). I just pressed return to all of them to get the defaults.
After this, it takes approx. 45 minutes (on my PC -- a 2.8GHz Celeron with 1GB RAM) and it output loads of warnings, which I ignored! :-D 

Next, unpack the TrueCrypt source archive. I did this by right-clicking on the archive and choosing "Extract here".

Back in a terminal, change to the extracted archive folder and then into the Linux folder (you'll likely need to modify the path on the first command here):
```
cd Linux
./install.sh
```
This will build and install TrueCrypt. When you are asked which directories to install the binaries and man page to, do not use the defaults! Use these directories respectively:
```
/usr/bin
/usr/share/man

```
And thats it!!

You can use **man truecrypt** to get the command syntax. You'll need to create a directory as a mount point, e.g. **sudo mkdir /mnt/tc**

To mount a truecrypt volume, enter something like this:
```
truecrypt /whereever/secret.tc /mnt/tc
```

Hope this help! If I've made any mistakes, or missed an important step, please  mention it for the benefit of others. :D

---

### Post by Rotlaus on 2006-03-14
[QUOTE=peterx14]
```

make -C /usr/src/linux-source-2.6.12 config modules
```
This last command asks absolutely *loads* of questions (literally hundreds). I just pressed return to all of them to get the defaults.
[/QUOTE]

You can skip the hundreds of questions if you copy your actaul configuration from your /boot Directory and then call the make command:
```

sudo cp /boot/config-2.6.12-10-386 /usr/src/linux
make -C /usr/src/linux-source-2.6.12 modules

```

regards,

Andre

---

### Post by Cleaner on 2006-04-30
[QUOTE=Rotlaus]You can skip the hundreds of questions if you copy your actaul configuration from your /boot Directory and then call the make command:
```

sudo cp /boot/config-2.6.12-10-386 /usr/src/linux
make -C /usr/src/linux-source-2.6.12 modules

```
[/QUOTE]

Just a small correction: actually, it must be

```

sudo cp /boot/config-2.6.12-10-386 /usr/src/linux/**.config**
**sudo** make -C /usr/src/linux-source-2.6.12 modules

```

Flo

PS: for a summarisation of this thread, see also [here]("http://ubuntuforums.org/showpost.php?p=970784&postcount=6")

---

### Post by ToniWiki on 2006-05-01
Hi !!

I needed to launch:
```
**sudo** make -C /usr/src/linux-source-2.6.12 modules
```
without sudo it fails. is this ok ?

And another question, what's the different between 
```
make -C /usr/src/linux-source-2.6.12 config modules
```
and
```
make -C /usr/src/linux-source-2.6.12 modules
```
??

I'm newbie to kernel compile.


regards
Toni

---

### Post by Cleaner on 2006-05-29
[QUOTE=ToniWiki]
I needed to launch:
```
**sudo** make -C /usr/src/linux-source-2.6.12 modules
```
without sudo it fails. is this ok ?
[/QUOTE]

Yes, you're right. Of course, you have to use sudo or run make as root (I corrected that in my posting).

[QUOTE=ToniWiki]
And another question, what's the different between 
```
make -C /usr/src/linux-source-2.6.12 config modules
```
and
```
make -C /usr/src/linux-source-2.6.12 modules
```
??
[/QUOTE]

That's something I don't know either, sorry.

Flo

---

### Post by ToniWiki on 2006-06-16
I have installed truecrypt 4.2 on my dapper (with kernel 2.6.15-23-k7) follow the text above and it works ok. Today, my system has been updated to 2.6.15-25-k7 and when i try to run truecrypt i get the message: "FATAL: Module truecrypt not found. truecrypt: Failed to loadTrueCrypt kernel module"

Is it necessary to recompile the kernel modules and/or truecrypt module to truecrypt works fine ? edit any config files ? How to do it ?

Regards,
Toni, a newbie to kernel questions.

---

### Post by Cleaner on 2006-06-17
Hi Toni,

Although I'm neither an expert on kernel questions, my advice would be that you  try to reinstall Truecrypt first. If that fails I fear you have to recompile the kernel modules as well as the Truecryp module.

Flo

---

