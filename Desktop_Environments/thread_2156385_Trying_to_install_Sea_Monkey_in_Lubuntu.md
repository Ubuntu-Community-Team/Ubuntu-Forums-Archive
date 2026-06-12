---
title: "Trying to install Sea Monkey in Lubuntu"
date: 2013-06-21
forum: Desktop Environments
---

### Post by M_Mynaardt on 2013-06-21
Hi there!

Does anyone know how to go about installing theh Mozilla Sea Monkey Internet suite in Lubuntu?  I tried a couple of things for it yesterday, but didn't really have much luck with it.

I tried this suggested way of installing Sea Monkey:
```
$ sudo add-apt-repository ppa:joe-nationnet/seamonkey-dev 
$ sudo apt-get update 
$ sudo apt-get install seamonkey
``` 

I got this from the repository command, so I thought it was working thus far:
```
You are about to add the following PPA to your system:
 
More info: https://launchpad.net/~joe-nationnet/+archive/seamonkey-dev
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpte6_1v/secring.gpg' created
gpg: keyring `/tmp/tmpte6_1v/pubring.gpg' created
gpg: requesting key A8F0C7B7 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpte6_1v/trustdb.gpg: trustdb created
gpg: key A8F0C7B7: public key "Launchpad Seamonkey 2.0" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```

However, I got these error messages from the update part: 
```
Err http:ppa.launchpad.net raring/main i386 Packages 404  Not Found
W: Failed to fetch http:ppa.launchpad.net/joe-nationnet/seamonkey-dev/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found
```

I also tried the TAR.BZ2 file from the Sea Monkey web site and that doesn't actually install anything.  I tried to take the resulting /seamonkey directory and save it in /usr/local.  That sort of worked; but it didn't save any of the settings from the last session, so it wasn't very helpful.

Would anyone know why these error messages crop up and what I can do to try putting a proper install of Sea Monkey on Lubuntu?

Thanks in advance for any help someone can send my way!

---

### Post by marinara on 2013-06-21
they haven't built seamonkey for raring.

here you go.  i love seamonkey!
[http://install-climber.blogspot.com/2013/05/linux-ubuntu-raring-howto-install-latest-seamonkey-browser-email-client.html](http://install-climber.blogspot.com/2013/05/linux-ubuntu-raring-howto-install-latest-seamonkey-browser-email-client.html)

---

### Post by c4c on 2013-06-24
We use SeaMonkey's Composer on Lubuntu 13.04 and have a shortcut tutorial that uses SeaMonkey as an example of how to install and make a shortcut to it in the menu. [http://computers4christians.org/FAQ/OS/HowTo/Shortcut/Example.html](http://computers4christians.org/FAQ/OS/HowTo/Shortcut/Example.html)

---

### Post by Lemuriano on 2013-06-25
Have you try; [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by BBQdave on 2013-06-25
[http://www.seamonkey-project.org/doc/install-and-uninstall](http://www.seamonkey-project.org/doc/install-and-uninstall)

**Linux Installation Instructions**

 To install SeaMonkey by downloading the tar.bz2 file: 
  
[LIST=1]
[*]Create a directory named "seamonkey2" (mkdir seamonkey2) and     change to that directory (cd seamonkey2).
[*]Click the link on the site you're downloading SeaMonkey from to      download the package (seamonkey-2.*.tar.bz2) file into the seamonkey2      directory.
[*]Decompress the file with the following command:     tar jxvf seamonkey-2.*.tar.bz2
     This creates a "seamonkey" directory under your seamonkey2 directory.
[*]Change to the seamonkey directory (cd seamonkey).
[*]Run SeaMonkey with the following command:     ./seamonkey

[/LIST]

---

### Post by M_Mynaardt on 2013-07-01
Thanks for the information all.  Unfortunately SeaMonkey just didn't seem willing to work for me in Lubuntu.  It was worth a shot, though.

---

### Post by PaulBx on 2013-07-18
I also tried this, using c4c's recipe. Get a warning message about "file not found", the file being /usr/share/seamonkey/seamonkey, even though that file exists.

I've used seamonkey for years; hope I can get it running.

---

### Post by PaulBx on 2013-07-19
So, since c4c's method didn't work for me, I want to uninstall it. Basically it downloads and installs manually from the mozilla site. To remove it do I just delete /usr/share/seamonkey? I was going to try the ubuntuzilla repository method and I'm guessing I shouldn't just install over what I have now.

---

### Post by Lemuriano on 2013-07-20
> **PaulBx said:**
> I was going to try the ubuntuzilla repository method and I'm guessing I shouldn't just install over what I have now.

Ubuntuzilla works flawlessly at least in my xubuntu box. :D

---

### Post by d0006 on 2013-08-05
I use Seamonkey on Lubuntu 64-bit with (almost) no problems.
Go here: [http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)

64-bit:  [ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.19/contrib/seamonkey-2.19.en-US.linux-x86_64.tar.bz2](ftp://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.19/contrib/seamonkey-2.19.en-US.linux-x86_64.tar.bz2)
Go here: [http://www.seamonkey-project.org/doc/install-and-uninstall](http://www.seamonkey-project.org/doc/install-and-uninstall)

Here is the trick for me:
```
cd /usr/local/
sudo chown -Rv 1000:1000 seamonkey 
```This changes ownership of the seamonkey directory to the first user (the user who installed the OS. For me this is the only user. You can use your actual username; i.e. chown -Rv foobar:foobar ... if you want).  The -R (recursive) option changes ownership for ALL files and directories in /usr/local/seamonkey/. The v option is verbose. I just like to see the list of files that changed ownership.
(I suppose you could also chmod, but chown is easier for me)

4. Change to the seamonkey directory (cd seamonkey)
IMPORTANT!!
5. Run SeaMonkey with the following command[B]:
./seamonkey
[/B](must use ./ )!

The hardest part for me was creating a desktop shortcut.  This is not so easy in Lubuntu!

You can use the file manager to extract the tar.bz2 but you might have to start it in a terminal with:
```
gksu pcmanfm
```because /usr/local/ is owned by root, so only root can write.
The problem here is that the extracted files will be owned by root, thus the chown command above.

I really like Seamonkey so I hope more people use it.

---

### Post by r_avital on 2013-09-03
Er.. Nope.

1. The ppa method resulted in the same error(s) as reported above.
2. Downloaded sable 2.20 archive from [http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.20/linux-i686/en-US/](http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/2.20/linux-i686/en-US/)
3. Unpacked in /opt, it created its own seamonkey directory, as expected.
4. Created symbolic link
5. Ran seamonkey in terminal. Result:

```
XPCOMGlueLoad error for file /opt/seamonkey/libxul.so:
libasound.so.2: cannot open shared object file: No such file or directory
Couldn't load XPCOM.
```

6. Running ./seamonkey > same result.

Not solved.

EDIT: Nevermind, ignore the above.

---

