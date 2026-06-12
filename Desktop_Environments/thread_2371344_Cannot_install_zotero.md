---
title: "Cannot install zotero"
date: 2017-09-13
forum: Desktop Environments
---

### Post by david12 on 2017-09-13
Hello:  I'm running Ubuntu Mate 16.04.3. 32-bit

I'm trying to install [Zotero]("https://www.zotero.org"), which is a program that keeps track of bibliographic information.

The installation process is (or should be) simple:

You download the program, unpack it, and put it in a directory.  I have used /opt.

Then you need to run a couple of scripts, and that is where the problem comes in.  The most important script should create a directory and profile file in my home folder.  When I run the script the directory is created, but the profile isn't.

Two errors ensue:
In the terminal: Error: Access was denied while trying to open files in your profile directory."
And separately in a GUI: " Your Zotero profile cannot be loaded. It may be missing or inaccessible."

I have tried everything I can think of.  Those steps are chronicled in a lengthy exchange I have had on the Zotero forum which can be read here: [https://diigo.com/0a948a](https://diigo.com/0a948a) .

The very last suggestion is that I install from the PPA. I did but that did not work.  I have not tried installing Zotero in ~/.local/share/applications, as adamsmith suggests on the zotero forum, yet.  But I did try to install it in /home/USER.  I will follow up on the ~/.local/share/applications idea, but I'm not sure that it represents something I haven't tried already.

Anyway, I cannot help but think it must be something right in front of me, but I'll be darned if I can figure it out.

Thanks.

---

### Post by Jenske on 2017-11-17
You'd better absolutely NOT put files manually in the /opt directory. Better is to make a directory in your own home-directory (e.g. \David\Zotero).

I've done so.

That being said, unfortunately, my zotero doesn't start up. Nothing happens and the Zotero-site itself doesn't give a clue to how to solve my (and your) problem.

---

### Post by again? on 2017-11-17
Don't use Zotero but installed as a test.
I used the ppa recommended.
```
sudo add-apt-repository ppa:smathot/cogscinl
sudo apt update
sudo apt install zotero-standalone
```

Started successfully from Application launcher in the dash.
On first launch creates: 
[LIST=1]
[*] a $USER data directory @  **~/Zotero** 
[*] a config directory at **~/.zotero** 
[*] opens [https://www.zotero.org/start_standalone](https://www.zotero.org/start_standalone) in firefox to install the Zotero Connector.
[*]
[/LIST]

Also starts in terminal without error:
```
/opt/zotero/zotero
```
FYI /usr/share/applications/zotero.desktop points to /opt/zotero/zotero
```
glen@Xen2:~$ cat /opt/zotero/zotero
#!/bin/sh

# Increase open files limit
#
# Mozilla file functions (OS.File.move()/copy(), NetUtil.asyncFetch/asyncCopy()) can leave file
# descriptors open for a few seconds (even with an explicit inputStream.close() in the case of
# the latter), so a source installation that copies ~500 translators and styles (with fds for
# source and target) can exceed the default 1024 limit.
# Current hard-limit on Ubuntu 16.10 is 4096
ulimit -n 4096

CALLDIR="$(dirname "$(readlink -f "$0")")"
"$CALLDIR/zotero-bin" -app "$CALLDIR/application.ini" $*
```
```
glen@Xen2:~$ ls -al /opt/zotero/
total 102976
drwxrwxr-x 11  501  501     4096 Oct 15 04:15 .
drwxr-xr-x  6 root root     4096 Nov 18 11:28 ..
-rw-rw-r--  1  501  501      237 Oct 15 04:15 application.ini
drwxr-xr-x  3  501  501     4096 Oct 15 04:15 chrome
-rw-r--r--  1  501  501     7307 Oct 15 04:15 chrome.manifest
drwxr-xr-x  2  501  501     4096 Oct 15 04:15 components
drwxr-xr-x  3  501  501     4096 Oct 15 04:15 defaults
-rw-r--r--  1  501  501      157 Oct 15 04:15 dependentlibs.list
drwxr-xr-x  2  501  501     4096 Oct 15 04:15 dictionaries
drwxrwxr-x  3  501  501     4096 Oct 15 04:15 extensions
drwxr-xr-x  2  501  501     4096 Oct 15 04:15 fonts
drwxr-xr-x  3  501  501     4096 Oct 15 04:15 gmp-clearkey
drwxr-xr-x  2  501  501     4096 Oct 15 04:15 gtk2
drwxr-xr-x  2  501  501     4096 Oct 15 04:15 icons
-rw-r--r--  1  501  501 10911568 Oct 15 04:15 icudt58l.dat
-rw-r--r--  1  501  501      899 Oct 15 04:15 libfreeblpriv3.chk
-rwxr-xr-x  1  501  501   553392 Oct 15 04:15 libfreeblpriv3.so
-rwxr-xr-x  1  501  501    58400 Oct 15 04:15 liblgpllibs.so
-rwxr-xr-x  1  501  501  2377808 Oct 15 04:15 libmozavcodec.so
-rwxr-xr-x  1  501  501   257872 Oct 15 04:15 libmozavutil.so
-rwxr-xr-x  1  501  501     6688 Oct 15 04:15 libmozgtk.so
-rwxr-xr-x  1  501  501    75752 Oct 15 04:15 libmozsandbox.so
-rwxr-xr-x  1  501  501  1155024 Oct 15 04:15 libmozsqlite3.so
-rwxr-xr-x  1  501  501   239448 Oct 15 04:15 libnspr4.so
-rwxr-xr-x  1  501  501   671064 Oct 15 04:15 libnss3.so
-rwxr-xr-x  1  501  501   573856 Oct 15 04:15 libnssckbi.so
-rw-r--r--  1  501  501      899 Oct 15 04:15 libnssdbm3.chk
-rwxr-xr-x  1  501  501   160376 Oct 15 04:15 libnssdbm3.so
-rwxr-xr-x  1  501  501   188128 Oct 15 04:15 libnssutil3.so
-rwxr-xr-x  1  501  501    19472 Oct 15 04:15 libplc4.so
-rwxr-xr-x  1  501  501    15184 Oct 15 04:15 libplds4.so
-rwxr-xr-x  1  501  501   177688 Oct 15 04:15 libsmime3.so
-rw-r--r--  1  501  501      899 Oct 15 04:15 libsoftokn3.chk
-rwxr-xr-x  1  501  501   269272 Oct 15 04:15 libsoftokn3.so
-rwxr-xr-x  1  501  501   312792 Oct 15 04:15 libssl3.so
-rwxr-xr-x  1  501  501 68765056 Oct 15 04:15 libxul.so
-rwxr-xr-x  1  501  501   926944 Oct 15 04:15 minidump-analyzer
-rw-rw-r--  1  501  501  9773608 Oct 15 04:15 omni.ja
-rwxr-xr-x  1  501  501   110000 Oct 15 04:15 pingsender
-rw-r--r--  1  501  501      166 Oct 15 04:15 platform.ini
-rwxr-xr-x  1  501  501   147088 Oct 15 04:15 plugin-container
-rwxrwxr-x  1  501  501      368 Oct 15 04:15 set_launcher_icon
-rw-r--r--  1  501  501      825 Oct 15 04:15 Throbber-small.gif
-rwxrwxr-x  1  501  501    93904 Oct 15 04:15 updater
-rw-rw-r--  1  501  501      140 Oct 15 04:15 updater.ini
-rwxrwxr-x  1  501  501      543 Oct 15 04:15 zotero
-rwxr-xr-x  1  501  501   155600 Oct 15 04:15 zotero-bin
-rwxrwxr-x  1  501  501      155 Oct 15 04:15 zotero.desktop
-rw-rw-r--  1  501  501  7309027 Oct 15 04:15 zotero.jar
```

```
glen@Xen2:~$ apt policy zotero-standalone 
zotero-standalone:
  Installed: 5.0.23-ubuntu1
  Candidate: 5.0.23-ubuntu1
  Version table:
 *** 5.0.23-ubuntu1 500
        500 http://ppa.launchpad.net/smathot/cogscinl/ubuntu xenial/main amd64 Packages
        500 http://ppa.launchpad.net/smathot/cogscinl/ubuntu xenial/main i386 Packages
        100 /var/lib/dpkg/status
```

---

