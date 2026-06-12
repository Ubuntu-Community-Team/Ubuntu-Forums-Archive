---
title: "Can't Uninstall KDE"
date: 2017-02-26
forum: Desktop Environments
---

### Post by O)9(yo&amp;# on 2017-02-26
I installed the KDE plasma DE on Ubuntu 16.04. It didn't work, the screen faded and went blank.  I tried uninstalling with apt-get uninstall kubuntu-desktop, but it didn't fully uninstall. I am not happy with either Gnome or Unity, and now I'm thinking of Xfce, which I I always liked on Mint. (In case anyone asks, I can't use Mate, as every version of  Mate I have ever tried fails to recognize my audio device). Should I  continue trying to uninstall KDE and then install Xfce, or just say the heck with it, and download [s]K[/s]Xubuntu?

---

### Post by oldos2er on 2017-02-26
After ```
sudo apt remove kubuntu-desktop

sudo apt autoremove
``` it should be uninstalled. If there are any errors please copy/paste them here in full.

---

### Post by O)9(yo&amp;# on 2017-02-26
Thanks for the help. Here is what I came up with:
```

michael@michael-GT5656:~$ sudo apt remove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
michael@michael-GT5656:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not installed
E: Unmet dependencies. Try using -f.
michael@michael-GT5656:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
michael@michael-GT5656:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic
  linux-image-4.4.0-59-generic linux-image-extra-4.4.0-59-generic
  ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  kde-config-telepathy-accounts
The following NEW packages will be installed:
  kde-config-telepathy-accounts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
705 not fully installed or removed.
Need to get 0 B/137 kB of archives.
After this operation, 825 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 318368 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.12.3-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+16.04.20160126-0ubuntu1
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.12.3-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
michael@michael-GT5
```

I did run the suggested commands.

Note: I should also point put that in my original post, I meant Xubuntu, not Kubuntu. I don't think my system can handle Kubuntu.

---

### Post by ajgreeny on 2017-02-26
If the autoremove command dioesn't work for you, command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | grep kubuntu-desktop
``` will show you the date and time you installed the kubuntu-desktop package and then using ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | 2017-02-03
```will show all packages installed on that date  (I used 2017-02-03 only as an example).

You can then manually remove all packages installed at that time with ```
sudo apt remove {list of packages}
``` by copying the package names if necessary, though some clever script guru may know how to do that more quickly.

---

### Post by O)9(yo&amp;# on 2017-02-26
I'm trying the commands you suggested, AJ, but on the second one I got "command not found." I copied it exactly, only changing the date (to yesterday, 2/25).

---

### Post by vasa1 on 2017-02-26
> **michael_diemer said:**
> I'm trying the commands you suggested, AJ, but on the second one I got "command not found." I copied it exactly, only changing the date (to yesterday, 2/25).

All the same, please post the entire command here.

---

### Post by O)9(yo&amp;# on 2017-02-26
[COLOR=#000000]grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | 2017-02-25

[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by vasa1 on 2017-02-26
> **michael_diemer said:**
> [COLOR=#000000]grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | 2017-02-25

[/COLOR]
[COLOR=#000000][/COLOR]

The date should be part of the search string fed to a command and not a command by itself. As it stands the output of grep is "piped" to the command "2017-02-25".

So try```
grep " installed " /var/log/dpkg.log.1 /var/log/dpkg.log | grep 2017-02-23
```
or whatever date you want. Here, what we're doing is running two commands sequentially. The first goes through the latest log file and its immediate predecessor for lines with the string " installed " (including the leading and trailing spaces.

That output is further filtered by date. You probable don't need to look at */var/log/dpkg.log.1* if you interested in very recent installs, but no harm.

---

### Post by vasa1 on 2017-02-26
> **michael_diemer said:**
> I installed the KDE plasma DE on Ubuntu 16.04. It didn't work, the screen faded and went blank.  I tried uninstalling with apt-get uninstall kubuntu-desktop, but it didn't fully uninstall. I am not happy with either Gnome or Unity, and now I'm thinking of Xfce, which I I always liked on Mint. (In case anyone asks, I can't use Mate, as every version of  Mate I have ever tried fails to recognize my audio device). Should I  continue trying to uninstall KDE and then install Xfce, or just say the heck with it, and download [s]K[/s]Xubuntu?

[LIST]
[*]1. I fixed Kubuntu to Xubuntu. You can edit your own posts :)
[*]2. Always show us the exact command when possible. That obviously will be more difficult when you use a GUI.
[*]3. While it's totally possible to add multiple DEs to an existing installation, it maybe cleaner to test out live instances of various DEs to ensure that they play well with your hardware and then do a clean install of the one you like best.
[*]4. Some DEs, "kubuntu-desktop" included, are provided by meta-packages. A meta-package, simply and probably inaccurately, is just a list of packages. Once the DE is installed, the metapackage can be removed without affecting performance. It maybe needed at a later date if you're going to do a version upgrade, say 16.04 to 16.10).
[*]5. Removing a meta-package won't automatically remove the packages it specified. For that reason, you need to resort to the type of command ajgreeny provided and then use that information to delete packages watching all the time what the system tells you will be removed along with the packages you specify. This is not a step to be undertaken before one is fully awake ;)
[/LIST]
```
apt show kubuntu-desktop
Package: kubuntu-desktop
Version: 1.338
Priority: optional
Section: universe/**metapackages**
Source: kubuntu-meta
Origin: Ubuntu
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>

```
And I've come across several instances where additional steps are need to bring things back 100% to the way they were before a new DE was installed.

[center]****[/center]
And it's worth mentioning that you're often provided with a chance to back off from a proposed action. You'll see something like```
Y/n
```in which the uppercase option is executed if you hit the enter key.

Some commands also come with a *dry run* option. *apt* and *apt-get* allow for *-s* (simulation).

---

### Post by O)9(yo&amp;# on 2017-02-26
I tried running the first 3 or 4 of the special commands, AJ, but probably did not do them correctly. This is getting to be fairly deep waters for me. It may be simpler to just leave things as they are, if everything works OK. If not, I can do a reinstall, with Xubuntu. I have everything backed up.

E: Unable to locate package 2.11.94-0ubuntu1.1
E: Couldn't find any package by glob '2.11.94-0ubuntu1.1'
E: Couldn't find any package by regex '2.11.94-0ubuntu1.1'
michael@michael-GT5656:~$ sudo apt remove  man-db:amd64 2.7.5-1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 2.7.5-1
E: Couldn't find any package by glob '2.7.5-1'
E: Couldn't find any package by regex '2.7.5-1'
michael@michael-GT5656:~$ sudo apt remove libc-bin:amd64 2.23-0ubuntu5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 2.23-0ubuntu5
E: Couldn't find any package by glob '2.23-0ubuntu5'
E: Couldn't find any package by regex '2.23-0ubuntu5'
michael@michael-GT5656:~$ sudo apt remove ca-certificates:all 20160104ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 20160104ubuntu1
michael@michael-GT5656:~$

---

### Post by ajgreeny on 2017-02-27
I am sorry, but my mistake was to miss the second "grep" from the command that included the date but thank goodness vasa1 noticed that.

The second command that I thought I had typed correctly with the second grep, will show all packages that were installed at the time of kubuntu-desktop, but you need just the paqckage name, not any of ther version information unless it is part of the package name itself.

My apologies for my "whoopsie" but you will not have done anything truly bad after it as you simply got the errors about package not found, so as vasa1 said, show us the full output of that second command of mine and I can tell you exactly what to type to remove those packages that you added.

---

### Post by O)9(yo&amp;# on 2017-02-27
No apologies necessary! I appreciate your time and effort to help me solve this problem. This stuff may not be rocket science, but it's pretty close!

I'll give it another go later. I'm on my Zorin drive at the moment.

---

### Post by O)9(yo&amp;# on 2017-02-27
Back on Ubuntu. Here is the output of the second command:

michael@michael-GT5656:~$ sudo grep " installed " /var/log/dpkg.log.1 /var/log/dpkg.log | grep 2017-02-25
[sudo] password for michael: 
/var/log/dpkg.log:2017-02-25 17:37:58 status installed fontconfig:amd64 2.11.94-0ubuntu1.1
/var/log/dpkg.log:2017-02-25 17:38:14 status installed man-db:amd64 2.7.5-1
/var/log/dpkg.log:2017-02-25 17:38:16 status installed libc-bin:amd64 2.23-0ubuntu5
/var/log/dpkg.log:2017-02-25 17:38:22 status installed ca-certificates:all 20160104ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:10 status installed shared-mime-info:amd64 1.5-2ubuntu0.1
/var/log/dpkg.log:2017-02-25 17:39:11 status installed dbus:amd64 1.10.6-1ubuntu3.3
/var/log/dpkg.log:2017-02-25 17:39:19 status installed hicolor-icon-theme:all 0.15-0ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:20 status installed bamfdaemon:amd64 0.5.3~bzr0+16.04.20160824-0ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:20 status installed gnome-menus:amd64 3.13.3-6ubuntu3.1
/var/log/dpkg.log:2017-02-25 17:39:20 status installed desktop-file-utils:amd64 0.22-1ubuntu5
/var/log/dpkg.log:2017-02-25 17:39:21 status installed mime-support:all 3.59ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:22 status installed sgml-base:all 1.26+nmu4ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:22 status installed systemd:amd64 229-4ubuntu16
/var/log/dpkg.log:2017-02-25 17:39:23 status installed ureadahead:amd64 0.100.0-19
/var/log/dpkg.log:2017-02-25 17:39:30 status installed libglib2.0-0:i386 2.48.2-0ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:30 status installed libglib2.0-0:amd64 2.48.2-0ubuntu1
/var/log/dpkg.log:2017-02-25 17:39:31 status installed gconf2:amd64 3.2.6-3ubuntu6
/var/log/dpkg.log:2017-02-25 17:39:33 status installed doc-base:all 0.10.7
/var/log/dpkg.log:2017-02-25 17:58:11 status installed libc-bin:amd64 2.23-0ubuntu5
/var/log/dpkg.log:2017-02-25 17:59:04 status installed libc-bin:amd64 2.23-0ubuntu5
michael@michael-GT5656:~$

---

### Post by ajgreeny on 2017-02-27
We do not need to know the status which came from your grep search of " installed "; we need you to repeat that last command with " install " as the grep search term to show what pacvkages were installed by you adding kubuntu-desktop on that date.
Show us again the output of that which should include a lot of kde applications unless you've already removed some of those.```
grep " install " /var/log/dpkg.log.1 /var/log/dpkg.log | grep 2017-02-25 
```

---

### Post by O)9(yo&amp;# on 2017-02-28
I have tried posting the results of this command, but I keep getting an error having to do with a missing security token. I finally contacted admin as advised by the error message.

It did get a boatload of results, including kde/plasma related.

---

### Post by oldos2er on 2017-02-28
The security token error is a known issue some people are seeing when trying to post a large amount of text. You can use [https://paste.ubuntu.com/](https://paste.ubuntu.com/) then post the link here as a workaround.

---

### Post by O)9(yo&amp;# on 2017-02-28
Sorry, but I haven't used Ubuntu pastebin before. Could I just do the same with Box.com? I don't know how pastebin works. I did go there and pasted the material, but I can't see what to do next. I obviously need to have used it before.

---

### Post by oldos2er on 2017-02-28
You enter your forum name in the Poster: field, paste the relevant text into Content:, click the Paste! button at the bottom, then copy the resulting URL into a post here.

---

### Post by O)9(yo&amp;# on 2017-02-28
That was easy!  OK, here is (finally) the output I believe you are looking for:

[https://paste.ubuntu.com/24087945/](https://paste.ubuntu.com/24087945/)

---

### Post by ajgreeny on 2017-03-01
Wow!!
709 packages, and they do all appear to be related to your kubuntu-desktop installation, a lot of them being packages with k in the name along with lots of qt library packages.  If you installed kubuntu-desktop as a lone activity without installing anything else at the same time we can be sure they all came in with that operation so should be removable.

You now have to decide if it is worth trying to extract just the package names from that long list in order to remove them all, or if it is better to continue as you are at present, but perhaps remove just the installed kde applications that you know you do not want and will not use, along with any dependencies of theirs that are removed with them.

Well, as a training exercise for myself, I have easily managed to extract all the package names from the list so here is the long list as a txt file.  Use it if you want to, but note, libreoffice is included in the list; you may wish to keep that so remove it along with any others you think you might still want.

I will leave you to remove all the line endings to make a long string of text from that file and then run ```
sudo apt-get remove -s <package names string>
``` which will simulate what is going to happen. If all appears OK just remove the -s option and run it again to actually remove all those packages, then finally to clean up run ```
sudo apt-get autoremove
```

---

### Post by O)9(yo&amp;# on 2017-03-01
Thanks AJ. Just one question: in removing the line endings, should there be a space between the lines, or a dash, semicolon, etc; or should they all just run together?

---

### Post by ajgreeny on 2017-03-02
A space; easy to do but takes a while with 709 lines, though there may be a way with sed or another command line tool which I can not help you with.

---

### Post by O)9(yo&amp;# on 2017-03-02
Thanks for getting back to me, AJ. I had tried it that way with  a few of the lines, and it seemed to work (whereas semicolons did not). Now I'll go ahead and do the rest. I thought I'd wait for confirmation before embarking on that clerically demanding task.

---

### Post by ajgreeny on 2017-03-02
It's not very clerically demanding; just start at the end of line at the top and keep hitting "space - delete - down" and repeat 709 times to get the long string.
It's time consuming but needs no copy paste or anything complicated, just repeated "space - delete - down"

---

### Post by O)9(yo&amp;# on 2017-03-02
Oh, I was backspacing and then hitting space; then reposition cursor at next line, etc. I gave up after about 45 minutes. I figured I would never do them all without a mistake, so I've been contemplating either living with a dysfunctional KDE install, using Gnome, and hoping updates would go ok;  or bite the bullet and reinstall Ubuntu. But I'll try it the other way, I should be able to do that.

---

### Post by ajgreeny on 2017-03-02
Sorry, I should have said space delete end, not down.
My bad!

---

### Post by O)9(yo&amp;# on 2017-03-02
Not at all; I should know something as basic as that!

---

### Post by O)9(yo&amp;# on 2017-03-02
Things have gotten weirder. When I paste in the long string, I get a message saying "3 incorrect password attempts." This without me even trying to put in a password. In  fact, I don't even have time to do it before I get the message. I did a very simple terminal command to see if it worked at all, namely updating grub, and that went OK, I was able to enter my password fine. I did some research on this, and some have suggested to boot into recovery mode and repair broken packages. Others say to boot a live DVD. Not sure where to go with this.

I remember doing an "in-place" reinstall once of Ubuntu. It was successful, and my programs were untouched, even my Thunderbird email was fine. I'm considering trying that again, things are just getting too weird here. I should have never have installed Plasma. I successfully installed Cinnamon a while back, and uninstalled without any issues, so I assumed I could do the same with Plasma. But clearly that's not the same animal.

---

### Post by ajgreeny on 2017-03-03
I wonder if there is an upper limit on the number of packages that apt and dpkg can manage in a single operation, and if that is causing your latest hiccup?  I have no knowledge of that but perhaps you could break down that long string into shorter ones and then repeat the ```
sudo apt-get remove <short-package-string>
``` to see if that gets you anywhere.

If not, I'm afraid I am now floundering a bit in waters that are deeper than my abilities.

---

### Post by O)9(yo&amp;# on 2017-03-03
Yes, that's a thought that may be worth trying, AJ. Fortunately, I did save the long string. No way I would want to go through all that again!

---

### Post by O)9(yo&amp;# on 2017-03-03
OK, I copied just half of the string, and was able to enter my password. However, all I got was a long list of unmet dependencies.

So, I'm leaning more and more to a reinstallation. As I said earlier, I have most everything backed up, so I should be ok. When I had 14.04, I installed 16.04 "over it," and it went fine, and I had all my programs (or most, can't remember exactly), and settings etc. So I think I'm going to try that again. Just need some more research on this kind of install. If you know of any tips, please feel free to share them!

---

### Post by ajgreeny on 2017-03-03
Fair enough.  Just make sure, as I'm sure you already have, that backups are available for your personal files before you start the reinstallation.

---

### Post by O)9(yo&amp;# on 2017-03-03
Coming at you live from my new Ubuntu 16.04 install. I had to do a new install, as I had Zorin on the drive as well as Ubuntu. Apparently, you can only do the reinstall over Ubuntu, if you don't have any other Linux distros on drive. Not sure if it would work if you had Windows. But I've got things set up pretty much the way I had them. 

Now, the only DE I feel confident to install is Cinnamon, as I successfully did that before. I tried to get used to Unity, but for me it's just counter-intuitive. I just can't get the hang of the start menu. The filter is what screws me up. 

Anyway, all good now, and I want to express my thanks to AJ, who helped me a lot. The problem was just too much to deal with, and reinstalling was easier. but I learned a lot, so it was still worthwhile.

---

### Post by deadflowr on 2017-03-04
> Apparently, you can only do the reinstall over Ubuntu, if you don't have any other Linux distros on drive.
You can reinstall over any system in the ***something else*** option.
Reinstall over single partition
Reinstall over all partitions
Reinstall over a selection of various partitions

Reinstall and fully wipe out your personal settings and data (to do this you mark the partition to be formatted)
Reinstall and keep your personal settings and data (to do this you do not mark the partition for formatting, but you also need to use the same the username you used, as well as all partition settings as was; ie, size and type must be the same as it was) I have done this a few times, and it works, though it actually takes a lot longer and complains a bunch about various configuration/et al files already existing on the system. but it works nonetheless. But, also, I wouldn't recommend it without a net, so to speak, and you should keep and maintain backups anyway. just in case.

All these and more can be done from with the something else option in the Installation section during install.

Besides, something else is more trustworthy, imo.

---

### Post by O)9(yo&amp;# on 2017-03-04
Thanks flowr, great info. I have used the something else option in the past, though can't remember if I did a reinstall that way.

I seem to have screwed things up again. I installed Cinnamon, but it came without any wallpapers. So I uninstalled it. Ran into the same problems as before. It didn't work. I got errors about dependencies and so on. I figured it was risky to do this, but I did it successfully in the past, installing and then uninstalling. If only I had left it on there...

so now, I'm in the same boat. I'm beginning to think that it's best not to install DE's, only the full OS. If you want Unity, install Ubuntu. If you want Cinnamon, Mint. And so on. At least on this system.

I'n trying to decide now whether to reinstall Ub 16 again, and just leave it, and live with Unity. Or use Gnome Compiz or Metacity. Which brings me to another question: Before I did all this, I had the Gnome DE's just mentioned on my system, and could choose between them and Unity. But now, they are missing. I can't remember if I had installed them, or they came via an update.

The other option is to go with another Ubuntu flavor. I like Mate, but I get no sound with it. May be a driver issue. I also like Xfce. There's also Gnome Ubuntu. I tested the live version of Fedora, which has Gnome 3 DE. It also didn't work with my audio. I also found Gnome 3 to be rather limiting. So it looks like either Mate (if I can get the sound working) or Xfce. Or stay with Ubuntu, and get Compiz and Metacity back somehow. any way I go, I will have to reinstall again.

---

### Post by deadflowr on 2017-03-04
> I'n trying to decide now whether to reinstall Ub 16 again, and just leave it, and live with Unity. Or use Gnome Compiz or Metacity. Which brings me to another question: Before I did all this, I had the Gnome DE's just mentioned on my system, and could choose between them and Unity. But now, they are missing. I can't remember if I had installed them, or they came via an update.

That is probably gnome-panel, or more commonly know as gnome flashback (or fallback, depending on the whims of the developers at the time, I guess)
Here's Kansasnoob's little diddy on getting that setup:
[https://ubuntuforums.org/showthread.php?t=2302432]("https://ubuntuforums.org/showthread.php?t=2302432")


> I like Mate, but I get no sound with it.
I like mate as well, so that sounds odd.
Maybe try what this does:
[https://ubuntu-mate.community/t/ubuntu-mate-14-10-sound-problems/246]("https://ubuntu-mate.community/t/ubuntu-mate-14-10-sound-problems/246")

---

### Post by O)9(yo&amp;# on 2017-03-04
I also saw a thread where uninstalling Pulse is what worked (see below). In my situation, I have an external pro grade interface, a Steinberg UR-22. While it shows up under sound devices, and you can select it, there is just no sound. This is a problem which has plagued me with every version of Mate I have tried. But it may be solvable. I'm going to fool around with the live version of U-Mate and see if I can get it to work.

Edit: I'm now on Live Ubuntu Mate, and I have the sound working. I had seen something about disabling the built-in audio, so I tried that and it worked. I will probably install it, it looks really nice.

[URL="http://askubuntu.com/questions/428466/how-to-fix-no-sound-in-ubuntu-12-04-with-mate-desktop-environment"]http://askubuntu.com/questions/428466/how-to-fix-no-sound-in-ubuntu-12-04-with-mate-desktop-environment



[/URL]

---

### Post by O)9(yo&amp;# on 2017-03-04
Well, when I began this thread I needed help removing KDE. I never solved that problem, but in working on it I did discover Ubuntu Mate, which I now have up and running. I think this is the Ubuntu version for me. The sound works fine after disabling the built-in audio. Now I finally have an Ubuntu where I like the desktop, in fact absolutely love it. Sorry to jump ship! (But it's still Ubuntu, after all).

---

