---
title: "Rant warning - productivity and Ubuntu/Linux"
date: 2009-02-17
forum: General Help
---

### Post by vmajor on 2009-02-17
*Flame suit on*

I have to vent or I'll explode, or just have a coronary and die.

I have one question (several actually) for the linux office suite developer community.

What the hell are you doing? For what sensible (substitute "sensible" with your favourite swear word/phrase) are you not allowing files to be opened or saved on a network drive?

I have an NFS directory that works beautifully with no errors anywhere, until I try to open any of the documents using Open Office. This is of course impossible as Open Office linux version has a bug/lack of functionality. It does not allow you to open files on a network drive.

Then I tried the KDE Office thing and they do not even offer an option to open from a network drive! KDE Office only sees the local mounts.

I mean what the sensible (see above)?

Linux is a fantastic successor to UNIX. They were both made great by the sheer power of connectivity and the ability to work in groups, on a network. 

So again I ask, what the sensible? How is it possible that Open Office and KDE Office do not allow you to access files over a network? KDE Office claims that they do, but the NFS share is not visible in the file browser, and I am stuffed if I am going to start digging through config files to enable this fundamental functionality.

...anyway, this is such a deal breaker that I am going to have to install Windows and dual boot. How the hell can MS do networking right and linux cannot? It's mind boggling.

I love my CentOS server, but my attempt to get work done on a desktop platform was an utter failure.

V.

---

### Post by 73ckn797 on 2009-02-17
Don't you think you ought to be venting in the OpenOffice forums?

---

### Post by yther on 2009-02-17
As this is your rant, I won't try to offer technical tips here; I'll just say that yes, OOo's utter lack of network (Samba, NFS, etc.) support shocked me as well.  I swear, *it used to be there*, but maybe I just imagined it.  I haven't tried the KOffice suite lately, though I've heard it has improved a lot in the past few years.  (It was total crap the last time I tried it, not useful to me at all.)  KDE apps should support any protocol they have an ioslave for, so I'd be surprised at them not working over NFS, unless for some reason the ioslave wasn't installed.

Wait, I'm starting to get technical!  Stop!

Anyway, I fixed my system to work around the OpenOffice deficiency, because I was determined to get it working.  Now the only time I need to boot Vista (on my laptop) is if I need to print anything more complex than single-sided letter, because none of the many apps here can deal with "big boy" printers&#8212;I want my stuff to come out folded, stapled, and with correctly-sized, intact images, but I haven't been able to manage that yet.

Oh yeah, and production printing from Acrobat?  Forget about it, no options for you!  :(

---

### Post by MartyBuntu on 2009-02-17
Open Office...opening up many formats of files on my samba shares all over my network as I type...all over the network...

...and this is an out-of-the-box configuration of Open Office too.


Maybe the problem is particular to NFS drives?

---

### Post by HermanAB on 2009-02-17
It sounds like a configuration problem to me.  Once a foreign file system is mounted, it should be transparent and it should not matter whether the underlying transport is NFS, Samba, Sshfs or any other network file system.

To browse the network, you simply browse your local file tree starting at the local mount point in /media or /mnt.

Browsing a network has nothing to do with OOo or Koffice.  These applications are not aware of the actual file locations.  That is why you have an OS.

Cheers,

Herman

---

### Post by vmajor on 2009-02-17
> **73ckn797 said:**
> Don't you think you ought to be venting in the OpenOffice forums?

Not really. OO 2.4 is included in the distro, besides the KDE Office is mentioned too and this is a general rant.

Just to expand it a bit more, there is also GIMP 2.6 that opens Photoshop .PSD files, unless they are actually the useful CMYK production proofs or designs. Thus I am unable to open or work with any of our suppliers' files.

[QUOTE=yther]Anyway, I fixed my system to work around the OpenOffice deficiency, because I was determined to get it working. Now the only time I need to boot Vista (on my laptop) is if I need to print anything more complex than single-sided letter, because none of the many apps here can deal with "big boy" printers—I want my stuff to come out folded, stapled, and with correctly-sized, intact images, but I haven't been able to manage that yet.[/QUOTE]

There is a workaround? I'd love to hear more about that. I managed to set up our MFC Epson CX11 printer, so that works. If only I could now actually work on the files without doing the byzantine copy to desktop, open in OO, save to desktop and copy back onto the NFS share.

[quote=MartyBuntu]Open Office...opening up many formats of files on my samba shares all over my network as I type...all over the network...

...and this is an out-of-the-box configuration of Open Office too.[/QUOTE]

That is very interesting, are you saying you are running OO 2.4 on Ubuntu 8.10 and it is allowing you to open Samba shares?

Why are you using samba to share linux directories? Perhaps I should try that.

Mind you,  Ubuntu 8.10 x64 that I am using steadfastly refuses to see any shared drives on the Windows network - including the samba share that I have on the server that serves all the files without a hitch to the Windows XP and Vista PCs on the network.

V.

---

### Post by yther on 2009-02-17
> **vmajor said:**
> There is a workaround? I'd love to hear more about that. I managed to set up our MFC Epson CX11 printer, so that works. If only I could now actually work on the files without doing the byzantine copy to desktop, open in OO, save to desktop and copy back onto the NFS share.

Yeah.  Basically you mount the share into your filesystem, like in /mount or /media, so that apps such as OOo just think it's a normal folder.  The OS takes care of the actual transport.

I have to do this with Windows shares where I work, so I use CIFS, and I did not use [this guide]("http://ubuntuforums.org/showthread.php?t=288534") but did something similar.  I think I will refine my setup based on that, actually!

NFS looks a bit more complicated, but I found [a setup guide for that]("https://help.ubuntu.com/community/SettingUpNFSHowTo"), too.  I haven't tried it, though.

Doing all of this in the filesystem prevents frustration when individual apps refuse to handle it themselves.  ;)

---

### Post by handy on 2009-02-17
I love it when rants go somewhere.

---

### Post by HermanAB on 2009-02-17
Mounting a NFS share is very simple.  Assuming that the server works and is read-write, you can mount the share like this:

$ sudo mkdir /mnt/share
$ sudo mount -t nfs -rwv 192.168.1.1:/home/share /mnt/share

That is all there is to it!

Now, the share should be browsable:
$ ls /mnt/share

Write something to the share to see whether it works:
$ echo wtf>/mnt/share/wtf.txt

List it:
$ cat /mnt/share/wtf.txt

Start OOo and try to open the file
$ soffice /mnt/share/wtf.txt

NOTE: If soffice open the file READ ONLY, then you have a file locking error on your server.  You can either try to fix the server, or disable file locking in soffice:
$ whereis soffice

$ sudo gedit /usr/lib/ooo-2.3/program/soffice

Edit file soffice, scroll down a little and comment out FILE LOCKING:
# file locking now enabled by default
#SAL_ENABLE_FILE_LOCKING=1
#export SAL_ENABLE_FILE_LOCKING

Now soffice should open the file read-write.

Hope that helps!

Herman

---

### Post by 73ckn797 on 2009-02-18
> **vmajor said:**
> Not really. OO 2.4 is included in the distro, besides the KDE Office is mentioned too and this is a general rant.

I have not had the problem you mention, so I was only wondering. I have been able to open documents from my Windows drive into OO in Ubuntu with no problems.

---

### Post by TwiceOver on 2009-02-18
I think he may be talking about using "File -> Open" in OpenOffice.  In that case, yes, there is no way to browse the network.

The solution to this is to mount the network share as a folder as stated above.

---

### Post by vmajor on 2009-02-18
I spent several hours trying to properly mount the nfs share.

I thought it was working, but it was not.

All I got was an SSH mount and some shortcuts.

So trying to set up nfs is a pain. I think there is something wrong with my Ubuntu setup as I cannot cannot see the Samba share or the Windows network. The Samba share is visible and working well with Windows machines.

mount nfs command results with host unreachable error.

Meh, at least I am not in a ranting mood anymore, so I will try to solve this by trawling the forums.

I am hopeful.

V.

---

### Post by vmajor on 2009-02-19
I remember now what happened with the server hosted share access issue.

I used the "Connect to server" application to create an SSH connection.

The SSH share cannot be read by Open Office.

I then tried for about a day to set up a mounted NFS connection, failing utterly.

I then also tried to set up a Samba share using command line and GUI Network broswer in Ubuntu, again failing utterly.

FInally I succeeded in setting up the Samba share using the same "Connect to server" application and selecting "Windows share".

OO is now happily opening and saving files to the Samba share.

No changes were made to the server and yet now Samba share miraculously works.

Conclusion: 

1. OO is buggy
2. Ubuntu 8.10 is buggy
3. This is so annoying.

V.

---

### Post by igknighted on 2009-02-19
> **vmajor said:**
> *Flame suit on*

I have to vent or I'll explode, or just have a coronary and die.

I have one question (several actually) for the linux office suite developer community.

What the hell are you doing? For what sensible (substitute "sensible" with your favourite swear word/phrase) are you not allowing files to be opened or saved on a network drive?

I have an NFS directory that works beautifully with no errors anywhere, until I try to open any of the documents using Open Office. This is of course impossible as Open Office linux version has a bug/lack of functionality. It does not allow you to open files on a network drive.

Then I tried the KDE Office thing and they do not even offer an option to open from a network drive! KDE Office only sees the local mounts.

I mean what the sensible (see above)?

Linux is a fantastic successor to UNIX. They were both made great by the sheer power of connectivity and the ability to work in groups, on a network. 

So again I ask, what the sensible? How is it possible that Open Office and KDE Office do not allow you to access files over a network? KDE Office claims that they do, but the NFS share is not visible in the file browser, and I am stuffed if I am going to start digging through config files to enable this fundamental functionality.

...anyway, this is such a deal breaker that I am going to have to install Windows and dual boot. How the hell can MS do networking right and linux cannot? It's mind boggling.

I love my CentOS server, but my attempt to get work done on a desktop platform was an utter failure.

V.

I find this really hard to believe... but I am running KDE4.2 and so cannot (last I checked) install the latest koffice to test.  But KDE uses kioslaves to open files across networks (think gvfs/gnome-vfs but a million times better), and I've never had an issue with it.  Perhaps you just need to preference it with nfs:// to get it to use the right protocol?

As for OOo... being a gtk leaning application, it's possible it wants to use gnome-vfs (or gvfs, i forget which is the new one), and that is why it won't work.

Have you tried abiword yet?

---

### Post by vmajor on 2009-02-19
Hey Igk* (sorry have beer, hard to spell),

Thanks for your reply. I will try KDE sometime later. I was not too fond of it on our CentOS server so I did not try to run it in Ubuntu.

In any case my original problem is now fixed. I would still like to know what the heck is going on and why the command line and other GUI methods failed.


...oh and I see your avatar. You ride bikes? We sell bikes :D .. I ride them too, badly.


V.

---

### Post by mixmaster on 2009-02-19
> **TwiceOver said:**
> I think he may be talking about using "File -> Open" in OpenOffice.  In that case, yes, there is no way to browse the network.

The solution to this is to mount the network share as a folder as stated above.

You can browse anything mounted.  This is the general linux/unix philosophy ... you normally have to mount a filesystem to access the files on it.

Sounds to me as if the ranter is looking for "My Network Places" or "Entire Microsoft Network" type functionality.

---

