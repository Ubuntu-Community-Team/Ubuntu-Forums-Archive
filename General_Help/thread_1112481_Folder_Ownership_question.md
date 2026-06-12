---
title: "Folder Ownership question"
date: 2009-03-31
forum: General Help
---

### Post by leojreimroc on 2009-03-31
I'm relatively new to Ubuntu, and definitely a beginner a terminal.

I've had WoW installed on my system (using Wine), and it worked very well before yesterday where it hanged my system.  So I decided to reinstall Wine and WoW.

Now the problem is when I use the Blizzard Downloader, it can't write new files to the default Wine directory (/host/Worldofwarcraft) because the /host folder's owner is root.

I did some research but I still can't seem to be able to change the folder owner to myself.

I opened a terminal, logged into root user (*su* and password), then I did:
[I]
chown joelcormier /host[/I]


The terminal does not show any errors at this point, but when I type ls -l, the /host folder is still root.  When I do: *users*, it shows: joelcormier joelcormier (so my user twice, which I found strange)

Any help on what I'm doing wrong would be greatly appreciated.  Thank you.

---

### Post by change_mode on 2009-03-31
You might need the -R option for recursive ownership change, not sure though. You can also try -v (verbose) to see if it shows any additional information.

Also try 'man chown'. The help pages can be very useful, not only in this case.

Be careful, don't change the wrong folders ;)

---

### Post by leojreimroc on 2009-03-31
chown -v joelcormier /host  gives this :

changed ownership of `/host' to joelcormier


However, again, when I type ls -l, this is what I get for the host folder

drwxrwxrwx   1 root root  8192 2009-03-28 16:17 host

---

### Post by _Purple_ on 2009-03-31
Did you try -R?

---

### Post by bodhi.zazen on 2009-03-31
> **leojreimroc said:**
> I'm relatively new to Ubuntu, and definitely a beginner a terminal.

I've had WoW installed on my system (using Wine), and it worked very well before yesterday where it hanged my system.  So I decided to reinstall Wine and WoW.

Now the problem is when I use the Blizzard Downloader, it can't write new files to the default Wine directory (/host/Worldofwarcraft) because the /host folder's owner is root.

I did some research but I still can't seem to be able to change the folder owner to myself.

I opened a terminal, logged into root user (*su* and password), then I did:
[I]
chown joelcormier /host[/I]


The terminal does not show any errors at this point, but when I type ls -l, the /host folder is still root.  When I do: *users*, it shows: joelcormier joelcormier (so my user twice, which I found strange)

Any help on what I'm doing wrong would be greatly appreciated.  Thank you.

If the folder is owned by root that implies you ran wine as root.

NEVER RUN WINE AS ROOT.

See the wine section here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by leojreimroc on 2009-03-31
I actually do not run Wine as root.  The default folder that wine is setup to has minimal hard disk space.  The /host folder however has tons of space, that is why I want to change the /host folder to normal user.

I did try -R and it didn't do anything new.

---

### Post by leojreimroc on 2009-04-01
When I type

chown -Rv joelcormier /host

I get:



changed ownership of (every file/folder in /host) to joelcormier



However, again, when I go into the /host folder and type ls -l, everything still says root.

---

### Post by change_mode on 2009-04-01
Where exactly is the /host folder located? The default wine directory is

```
/home/user/.wine
```

and programs should be installed to

```
/home/user/.wine/drive_c/Program Files/
```

The .wine folder should have all the space you need to install programs, because it's part of your home directory (where all your personal files go).

---

### Post by WilliamJenningsBryan on 2009-04-01
A couple of possibilities:

Did you remember to sudo?

If the /host folder is on another drive, make sure that the drive is mounted read/write. If you type the command mount by itself, you'll get a list of mounted file systems. Make sure that after the line for your /host folder that there is no "ro" option.

Also, if all you're to do is be able to write to the folder, you could use ```
sudo chmod -R 777 /host
```, but that gives every user read/write/execute to every file and directory.

---

### Post by leojreimroc on 2009-04-03
> **change_mode said:**
> Where exactly is the /host folder located? The default wine directory is

```
/home/user/.wine
```

and programs should be installed to

```
/home/user/.wine/drive_c/Program Files/
```

The .wine folder should have all the space you need to install programs, because it's part of your home directory (where all your personal files go).

I must have installed Ubuntu wrong, because my home folder is not where most of my disk space is.  For some reason, all of my space is on the /host folder.  My /home folder has around 10G and /host has about 200G.  

So what I did when I installed wine, the C: drive is on home, but I made an E: drive on /host where my I put my files.

Both /home and /host are in the same place, what is it called? root?

---

### Post by CyberMando on 2009-04-03
I think your problem is that it  is a mount point. Unmount /host, change the ownership of the /host mountpoint, and remount. It should then take the ownership from the mountpoint.

---

