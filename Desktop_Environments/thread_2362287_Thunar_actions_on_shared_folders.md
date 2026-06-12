---
title: "Thunar actions on shared folders"
date: 2017-05-26
forum: Desktop Environments
---

### Post by guneves on 2017-05-26
[SIZE=4]XFCE4 Thunar Patch - xap.sh

[SIZE=2]Thunar by default **disables** custom actions from appearing in network folders and even on desktop.[/SIZE][/SIZE] 
Some non-custom actions are also disabled, like "open terminal here".

This issue has been discussed on this closed thread of 2011:
[https://ubuntuforums.org/showthread.php?t=1889890](https://ubuntuforums.org/showthread.php?t=1889890)

**There is a patch to address this issue, but pending since 2011.**

Bug tracker link:
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/899624?comments=all](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/899624?comments=all)

Patch link:
[https://bugzilla.xfce.org/attachment.cgi?id=3482](https://bugzilla.xfce.org/attachment.cgi?id=3482)

**I have created a Bash script that automates the whole patch build and install process:**
[SIZE=3][https://github.com/tavinus/xap.sh](https://github.com/tavinus/xap.sh)[/SIZE]

Should work on any debian-based distro. 
Tested on Ubuntu16+XFCE4, Xubuntu16, Mint17.3 XFCE (32bit & 64bit).

**Example of a successful [*xap.sh*]("https://github.com/tavinus/xap.sh") run**:
```

[FONT=courier new]$ ./xap.sh 

XAP - XFCE Actions Patcher v0.0.1

Checking for sudo executable and privileges, enter your password if needed.
[sudo] password for tavinus: 
Done | Updating package lists
Done | Installing thunar, thunar-data and devscripts
Done | Installing build dependencies for thunar
Done | Preparing work dir: /home/tavinus/xap_patch_temp
Done | Getting thunar source
Done | Downloading Patch
Done | Testing patch with --dry-run
Done | Applying patch
Done | Building deb packages with dpkg-buildpackage
Done | Locating libthunarx deb package

Proceed with package install? (Y/y to install) y
Done | Installing: libthunarx-2-0_1.6.11-0ubuntu0.16.04.1_i386.deb

Success! Please reboot to apply the changes in thunar!

The work directory with sources and deb packages can be removed now.
Dir: /home/tavinus/xap_patch_temp

Do You want to delete the dir? (Y/y to delete) n
Kept working dir!

Ciao[/FONT]

```

After running xap.sh and rebooting, thunar actions should work fine at network folders and desktop.

**EDIT: Download and Install instructions available below at the 3rd post.**

**EDIT2: To remove the patch, just reinstall thunar with this:**
```
$ sudo apt-get --reinstall install thunar thunar-data
```
**EDIT3: I am a person that keeps editing his answers, this is actually the EDIT#122 (joking)**

Cheers!
Gus

---

### Post by cmcanulty on 2017-05-26
Can you explain more fully. Where to save that file and what part of it to copy to file and how to run it. You seem to have all the output in the file so it is hard to see where the script ends. Thank you

---

### Post by guneves on 2017-05-28
> **cmcanulty said:**
> Can you explain more fully. Where to save that file and what part of it to copy to file and how to run it. You seem to have all the output in the file so it is hard to see where the script ends. Thank you

Hi!

I didn't really attach any files, just the link to my github repository, which is:

[SIZE=4][https://github.com/tavinus/xap.sh](https://github.com/tavinus/xap.sh)

[/SIZE]The CODE I posted above is an EXAMPLE RUN of xap.sh.
So if you run it successfully, it should look like that.
And it ends where it says Ciao :)

There is a quite extensive README.md file at github, explaining in detail most stuff with examples.

So, first of all, **do you use XFCE4?** 
This is irrelevant for other Desktop environments.
I have actually implemented a check to see if xfce4 is running or abort and tell people they should install XFCE4 manually before running xap.sh.

What system are you trying to run xap.sh? 
Xubuntu? Ubuntu + XFCE4? Other?

**Just by running xap.sh you will be already installing stuff with apt-get install.**
There are many requisites to be able to recompile XFCE4 Thunar, this is the main reason we have xap.sh in the first place.
Installing all the requisites with apt-get is fine and safe, but you should at least know that you WANT to install the final patch before running this.

All that said, the final patched .deb installed has about 250 Kb only, thats libthunarx for ya.
The patch is also a very simple change to the libthunarx package, enabling custom actions anywhere (or disabling the check that was disabling custom actions at these places, to be more precise).

**I would really recommend [reading the README.md]("https://github.com/tavinus/xap.sh") at github**,
 but if you just want a quick installation guide, here it goes.

**Steps**

[LIST=1]
[*]Enable source-repositories on your system (screenshots below)
[*]Download xap.sh and make it executable (could be on your $HOME folder)
[*]Run: ./xap.sh and confirm the patch install with Y when asked
[*]You may keep the generated files by not using Y at the end, when it asks to delete the work folder
[*]Reboot and test thunar actions on a network folder to make sure it worked
[/LIST]
The location of the work folder is $HOME/xap_patch_temp.
$HOME is a shortcut to your home folder. 
Eg. $ echo $HOME # will print /home/tavinus in my computer

As you can see in my first post in the example run, to run xap.sh and apply the patch you just need to run it, like this:
```
$ ./xap.sh
```
[B]Downloading
[/B][I]Note: Any line that starts with a **$**, denotes a shell command line. Remove the **$** if you copy-paste it. It also tells you where each command starts.

[/I]_Using git_
If you have git, you can use it to clone xap.sh like this:
```

[FONT=courier new]$ git clone https://github.com/tavinus/xap.sh.git
$ cd xap.sh
$ ./xap.sh --help[/FONT]
```

_Manual download_
[You can download the full xap.sh zip file by clicking here]("https://github.com/tavinus/xap.sh/archive/master.zip"). 
Then extract the zip and open a terminal inside the xap.sh folder.
To make sure xap.sh is executable:
```
[FONT=courier new]$ chmod +x ./xap.sh
$ ./xap.sh --help[/FONT]
```

Or you can use these quick and dirty oneliners that will download only xap.sh and make it executable.
In this case, the patch will be downloaded during the script run.

_wget oneliner_
```
[FONT=courier new]$ wget 'https://raw.githubusercontent.com/tavinus/xap.sh/master/xap.sh' -O ./xap.sh && chmod +x ./xap.sh
$ ./xap.sh --help[/FONT]
```

_curl oneliner_
```
[FONT=courier new]$ curl -L 'https://raw.githubusercontent.com/tavinus/xap.sh/master/xap.sh' -o ./xap.sh && chmod +x ./xap.sh
$ ./xap.sh --help[/FONT]
```

**Enabling source-code repos**
If you don't know how to enable source-code repositories, here are the screenshots for Xubuntu16:

[IMG]https://raw.githubusercontent.com/tavinus/xap.sh/master/screenshots/xubuntu16-01.jpg[/IMG]
 
[IMG]https://raw.githubusercontent.com/tavinus/xap.sh/master/screenshots/xubuntu16-02.jpg[/IMG]

[Most of this info came from the README.md file, but there is a lot more there.]("https://github.com/tavinus/xap.sh")
Any problems, you can ask here or open an issue at github.

Cheers!
Gus

---

### Post by cmcanulty on 2017-05-28
Thank you for the excellent and clear explanation. It is easy to follow and worked great. I was unclear that the original post was all output not some output and some  input. I have it installed and working. I am running xubuntu 16.04. Great help!

---

### Post by guneves on 2017-05-28
LOL

I just finished editing the answer and you already have it running.
Thanks for reporting back!

May I know what system you have it running?
Xubuntu16? 32bit? 64bit?

Use this command to get it if you don't know:
```
$ cat /etc/*release
```

Glad you got it working.

I made this installer because I made a bunch of custom actions to be used by a company and then we couldn't use it because we basically only need the custom actions on network folders. Then I saw the patch pending for many years and decided to make xap.sh.

Mixed feelings when you write a software that you also hope that becomes irrelevant. LOL

EDIT: Thanks for reporting your system!

---

### Post by cmcanulty on 2017-05-28
I am running Xubuntu 16.04 64 bit on about 20 machines as I am tech volunteer for a small library and really missed those functions.This is great!

---

### Post by guneves on 2017-05-28
Makes me wonder, though.

I have JUST POSTED _*xap.sh*_ online a couple of days ago, but this patch has been pending for many years.

Have you just now wanted to patch this? 
Were you following any of the links I posted in my 1st post?
I mean, how did you find this thread?

Cause that was quick... 
Quicker than it took me to finally publish xap.sh, which was about 4 days I think?

I think I spent more than 2 days on creating checks and testing on non up-date systems, 32 & 64 bit, other setups, etc.
It was good though, it did fail on some of those and then I changed xap.sh to comply.

Main issue was on systems not up to date. 
Because then you download the sources of the most recent thunar (which is not installed)
And then you install a newer patched libthunarx on an older version of thunar, which is obviously not good. 
Easy fix is to install (update) thunar before anything, which is done.

Post-fix is running sudo apt-get install -f, after things get dirty. (which we try to avoid, but will be done if dpkg exits with an error).

The only thing that could be bad about this patch that I found *(written by someone at the bugtracker)* is that some actions may not like the %U URL format of samba shares, but I couldn't find an issue in my tests and my bash actions that use %F and %f also work fine with gvfs (thunar automount of smb:// shares).

In any case, still not sure why this patch is pending for so long, but seems since you found this so quick, I guess there are others wanting it.

Did you patch all those machines? 

**If the machines are all running the same system/version and are all up to date you can just install ONE of the .deb files from your work folder on them and it will work.**

The deb files will be on xap.sh's work folder after you successfully run xap.sh: 
```
$HOME/xap_patch_temp
```
**You can run xap with the -k flag to make sure you keep the work folder at the end. As in:**
```
$ ./xap.sh -k
```
**Deb File: **(on your work folder, **NOT** the libthunarx**-dev**-<VERSION> file)
```
**[FONT=courier new]libthunarx-<VERSION>.deb[/FONT]**
```
**Example of a deb file generated on a Xubuntu 32bit:** (outuput from xap.sh)
```
Done | Installing: libthunarx-2-0_1.6.11-0ubuntu0.16.04.1_i386.deb
```
**Make sure you run this on each machine before installing the deb though.**
Or you may have the version mismatch problem.
```
$ [FONT=courier new]sudo apt-get update && sudo apt-get install thunar thunar-data[/FONT]
```
**Then you can double-click the .deb file on each machine and run a REINSTALL.**

Or if you prefer the command line way:
```
$ sudo dpkg -i /path/to/libthunarx-<VERSION>.deb
```
The beauty of this method is only having to install the compiling dependencies and actually compile once.
It also makes easy to just copy the deb file to each machine and apply the patch (you may even open the .deb file from the network).

But you need to make sure all of the systems are up-to-date with the one that compiled the deb file.
Reboot is needed for thunar to work on remote folders, same as if running xap.sh.

Cheers!
Gus

---

### Post by cmcanulty on 2017-05-28
Haven't patched all as library is closed for the holiday weekend. I was just installing a new computer and remembered how those functions were so nice and now missing so I did a few searches and found your post. I did do it on 2 home computers. It really irritates me that the latest trend on most apps is to remove and dumb down stuff instead of adding features. Nautilus is a great example. I like toolbars options etc, not some stripped down view that you either have to know where the secret settings are or else look for them. This explains why I use xfce rather than unity. Gnome 2 was perfect and I think Ubuntu could have really taken off from 10.04 but then all the radical changes and splintering made it less popular. for the library I want everything there for people to see and click on whether they are used to windows, mac, or whatever. I guess I missed something though, you mention a .deb file for this and I don't see that in the posts or links. I do religiously keep everything updated with a nice set of aliases so I can type ud for update, dug for dist update or live dangerously and type ug for both. I always do the ud and dug first on a couple of computers before I do the rest as simply ug. I use remmina so can remotely run a bunch of tabs and keep them all updated really quickly. What I waste most of my time on are the 3 librarian's machines that still run win 10. With them is it check for updates (forever) preparing updates (forever) reboot forever repeat ad nauseum and half the time there is a problem with the updates that takes lots of troubleshooting etc. I am close to getting everything on linux. The issue stopping that is we absolutely need quickbooks and I can't find a tweak to do that in linux.

---

### Post by guneves on 2017-05-28
I have edited my answer with more detailed instructions.

**But basically for a mass deploy of the patch (with a single xap.sh run) you need to:**
[LIST=1]
[*]Make sure all machines are running the same system/version
[*]Run [FONT=courier new]$ ./xap.sh -k[/FONT]  in one of the machines, -k to keep files
[*]Mark the [FONT=courier new]libthunarx-<VERSION>_<ARCH>.deb[/FONT] file name that xap.sh says to have installed.
[LIST=1]
[*]This is what we will install on all the other machines and is located at
[*][FONT=courier new]$HOME/xap_patch_temp/libthunarx-<VERSION>_<ARCH>.deb[/FONT]
[/LIST]

[*]Run [FONT=courier new]sudo apt-get update && sudo apt-get install thunar thunar-data[/FONT] **on each target machine**
[*]Double click the libthunarx-<VERSION>_<ARCH>.deb on each machine and run a REINSTALL
[*]Or use the cli [FONT=courier new]$ sudo dpkg -i /path/to/libthunarx-<VERSION>_<ARCH>.deb[/FONT]
[/LIST]
There are two libthunarx-*.deb files created after compile. 
We want the one that **does NOT have dev** in its name.

EDIT1: Yes, windows update is very boring.
EDIT2: You may cancel ./xap.sh with CTRL + C when ./xap.sh asks you to install the package if you just want to recompile it and get the .deb file. Or even press anything that is not an Y.

Cheers!
Gus

---

### Post by cmcanulty on 2017-05-28
I am feeling really stupid I can't find any deb file and when I do I get an error 

```
./xap.sh -k
```

```
cmcanulty@ubuntu1:~$ ./xap.sh -k
bash: ./xap.sh: Is a directory
cmcanulty@ubuntu1:~$ 

```


I am also frustrated by spending hours trying to install wine with about a hundred different tutorials and half of them including synaptic don't show it as installed afterwards. It works on some fails on others. I may be too dumb for any of this!

---

### Post by guneves on 2017-05-29
Hi!
Sorry for the delay.

I think it is what it says. :)

You seem to be one level ahead where you should be. 
It seems like you are trying to run the xap.sh folder, instead of the xap.sh file (which is inside the xap.sh folder). 
If you used either git or manual download (zip), you will have a xap.sh folder, and the xap.sh file inside that folder.

So, if it is saying it is a folder, you would:
```
$ cd xap.sh
$ ./xap.sh -k
```
Or you can open a new terminal inside the folder. Or you can even redo the whole process of download, etc.

[B][COLOR=#b22222]And then remember that the actual work folder for XAP is gonna be $HOME/xap_patch_temp.
The debs will be in this folder.[/COLOR][/B] Depending on what you have chosen when you first ran xap.sh, you may still/already have the work folder with the .deb files. 
If you have chosen to delete after patching, then yes, you need a re-compile.

If you are not sure, you can always just run ./xap.sh on each machine to apply the patch. 
XAP makes things a bit safer for the patch by making sure we do all that needs to be done.

PS : Wine can be quite confusing, specially when you start messing with it. But my main problem with wine is that it is inconsistent. It may work great some times and make you go nuts on other times. Anyways, wine is very different from anything similar (there is nothing even similar actually). In general, I would recommend you trying to migrate to another native linux tool, like GnuCash or something else. If that is really not doable, then go through all the hassle of trying to make it run stable on Wine (and you will have to learn the "wine way" in the process).

---

### Post by cmcanulty on 2017-05-29
Thank you again! But the xap.sh folder has no deb in it

[ATTACH=CONFIG]275350[/ATTACH]

---

### Post by guneves on 2017-06-12
Hi.
Sorry for the delay!

There is some confusion going on.
Your xap.sh folder will contain your xap.sh script which will create the xap work folder at your $HOME after running.
The .deb files would be on the work folder AFTER running xap.

cd into WORK FOLDER: 
```
[SIZE=3][FONT=courier new]$ cd "$HOME"/[COLOR=#24292E]xap_patch_temp[/COLOR][/FONT][/SIZE]
```
list deb files: [COLOR=#24292E][FONT=SFMono-Regular]
[/FONT][/COLOR]```
[FONT=courier new][SIZE=3]$ ls -l *.deb[/SIZE][/FONT]
```

Then go back to my post where I explain which exact debian file to use.

[FONT=arial narrow][COLOR=#b22222][SIZE=4]**Honestly, just run xap.sh on each machine and you will most probably have no problems guaranteed.**
**This kind of multi-install with a single compile is not really supported or super easy to do.**[/SIZE][/COLOR][/FONT]

Just enable source repos and copy xap.sh to each machine, make it executable and run it. ;)

Cheers!
Gus

---

