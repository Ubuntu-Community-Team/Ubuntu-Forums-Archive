---
title: "Firefox 1.5.0.5 - Segmentation Fault"
date: 2006-08-01
forum: Desktop Environments
---

### Post by mygravity on 2006-08-01
Am using Dapper Drake (with all current updates) and Firefox 1.5.0.5 with the following extensions:

[LIST=1]
[*]Aardvark
[*]All-In-One Sidebar
[*]ColorZilla
[*]CSSViewer
[*]Diggler
[*]Flashblock
[*]Google Toolbar
[*]ScrapBook
[*]Screen grab
[*]Tab Mix Plus
[*]URLParams
[*]View Cookies
[*]Web Developer
[/LIST]

When I start Firefox form the command line, it stops immediately and reports "Segmentation Fault". It will start after about three attempts though.

I've seen a few other forum thread regarding the same problem when using Breezy, and posters seemed to hope it would be fixed in Dapper. However it obviously isn't fixed via the usual updates. Has anyone managed to fix this?

Cheers

Andy

---

### Post by aysiu on 2006-08-01
You listed all the extensions you have. Have you tried [using a fresh profile](http://www.ubuntuforums.org/showthread.php?t=103930&highlight=corrupt+firefox)?

---

### Post by Paulus on 2006-08-01
I dont mean to hijack this thread.. but i have a similar problem.. I can't update firefox:
```
      

  (Missing operator before bus_register?)
Bareword found where operator expected at /usr/sbin/update-mime line 243, near ""
        (Missing operator before videobuf_mmap_free?)
syntax error at /usr/sbin/update-mime line 243, near ""
Execution of /usr/sbin/update-mime aborted due to compilation errors.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
And when I try and run firefox:
```
paulus@paulus-desktop:~$ firefox
Segmentation fault
paulus@paulus-desktop:~$
```

the samer error as the poster, i'm totally stuck on this one, i can't remove firefox or update it!

My Dad unplugged my pc while it was on the other day... think this may have caused something like this to happen?

---

### Post by mygravity on 2006-08-02
Ah. Seem to have solved the problem by removing some extensions that I wasn't using such as:

FireBug
HTML Validator

Cheers

Andy

---

### Post by vladimirprieto on 2006-08-02
i got the same problem, and i realice that -at least- is colorzilla extension the problem.  so i uninstalled it and firefox came back to normal function.

also download firefox from official site (mozilla.com), but with that "package" that extension works fine.  even more, colorzilla didn't work at all with firefox from repositories, but did work with official firefox.

so obviously the problem is with ubuntu's firefox.

---

### Post by snellgrove on 2006-08-06
Definately a problem with the repository firefox, I cannot get this thing to download at all.

I removed firefox because I was having constant segmentation faults (everytime, when opening a certain web-page) and it also happened when I deleted a bookmark, as soon as you clicked delete..BANG! it vanished leaving Segmentation fault in the terminal.

I also tried a fresh profile several times, but to no-avail.

But anyways, installing firefox gives this:

```
Unpacking firefox (from .../firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb) ...Replaced by files in installed package libnss3 ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb (--unpack):
 unable to create `./usr/lib/firefox/libgfxpsshar.so': No such file or directorydpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package epiphany-browser.
Unpacking epiphany-browser (from .../epiphany-browser_2.14.3-0ubuntu1_i386.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tried running the following:

```

sudo apt-get clean
sudo apt-get autoclean
```

and then retrying the download / install of Firefox, same result each time.

I installed Lynx (good to have a terminal-friendly backup browser!) and it was fine.

:edit:

Haven't tried Firefox from the mozilla website. I am currently using Opera as they now have a Ubuntu .deb file available, which makes things nice and easy :)

:edit again: ...

I also now have noticed this problem:

I saw the updates icon in the tray, so I click it. It tells me:

```
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
```

So I try sudo apt-get install -f

```
sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
matt@matt-desktop:~$ clear

matt@matt-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following extra packages will be installed:
  firefox
Suggested packages:
  firefox-gnome-support latex-xft-fonts libthai0
The following NEW packages will be installed
  firefox
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/7916kB of archives.
After unpacking 23.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 127453 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb) ...Replaced by files in installed package libnss3 ...
dpkg: error processing /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb (--unpack):
 unable to create `./usr/lib/firefox/libgfxpsshar.so': No such file or directorydpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.5-0ubuntu6.06.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

of course, it wont work as Firefox wont ever download / install properly.

---

### Post by JcZndeR on 2006-08-08
I have a similar problem, it also says segment fault in a different form.
I have tried to reinstall twice but it all ended in vain.
I started a thread before I saw this one.
[http://ubuntuforums.org/showthread.php?t=231898](http://ubuntuforums.org/showthread.php?t=231898)

---

### Post by snellgrove on 2006-08-10
I've given up on the repository version of Firefox.

I went to mozilla.org and downloaded firefox there, you dont need to install it.. just unzip to somewhere (mine is in /home/*username*/programs/firefox/

runs perfect - no crashing anymore

I still have Opera installed as an alternative though, I dont trust Firefox enough to not have any backups ;)

---

