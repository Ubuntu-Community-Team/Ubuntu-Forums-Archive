---
title: "What is resycled/boot.com?  I can't delete it."
date: 2008-12-17
forum: General Help
---

### Post by Patrick Snyder on 2008-12-17
[LIST=1]
[*]Is this related to USB startup disks?
[*]Or can this be some sort of virus from my friends' computers, transfered to my USB stick?
[*]Is there a way to change permissions so I can delete it?
[/LIST]


_**Background info**_
I'm fairly new to linux.
I love the idea of putting an OS on a USB stick.  

So I put Puppy Linux on one, played around with it on my and my friends' computers.  And then I installed Ubuntu on my computer and saw "**Create a USB startup disk**" in System/Administration.

I copied all the files I didn't recognize from my USB stick into a folder on my Ubuntu desktop (thinking anything I didn't recognize had to do with Puppy).  And then ran Ubuntu's "Create a USB startup disk".

After trying it a few times with my own and my friends' computers, I wanted more space on the USB drive for files so again I moved any files I didn't recognize into a folder on my Ubuntu desktop.

Then I wondered why I was saving them and trashed them.  But I noticed a folder called "resycled" with 1 file "boot.com" inside.  It wouldn't delete from my Ubuntu trash or from my USB stick.

So I Googled it and came up with [this article]("http://www.bleepingcomputer.com/forums/topic185275.html") that said it was a malware/virus.  Really?


_Hence my questions_
[LIST=1]
[*]Is this related to the USB startup disks?
[*]Or is this from my friends' computers?
[*]Is there a way to change permissions so I can delete it?
[/LIST]

Thanks in advance (^_^)/

---

### Post by ibuclaw on 2008-12-17
Ubuntu doesn't get infected by malware, viruses, spyware, or any other windows phenomenon.

If it is malware, my guess is that you got it from a Windows computer that you plugged the usb stick into while windows was running.

Other than that, can you take a print screen of the error for clarification of what is happening on screen?

[EDIT]
While browsing your USB stick in the file browser, press **Ctrl+H**, is there a folder named "**.Trash-1000**" or something like that? Can you delete it?

Regards
Iain

---

### Post by Patrick Snyder on 2008-12-17
> Ubuntu doesn't get infected by malware, viruses, spyware, or any other windows phenomenon.And for that I'm very grateful!  (^_^)  I'm more concerned for my friends' computers whom I share files with often.  But I thought it might be there because the USB was made bootable.  And that Ubuntu didn't want to delete it, because it may make the device unbootable.  I'm trying to discern which one it is.

> While browsing your USB stick in the file browser, press Ctrl+H, is there a folder named ".Trash-1000" or something like that? Can you delete it?Yeah, I've had to delete .Trash-1000 a few times, because my USB keeps filling up.  Of course it keeps coming back, but the files inside are gone.  I just did it again now.




I get this exact same error when I try to delete the resycled folder from either my Trash or USB stick.

[IMG]http://img510.imageshack.us/img510/1592/resyclederrordl7.png[/IMG]

---

### Post by ibuclaw on 2008-12-17
Notice the Lock icon on that folder? You don't have write permissions on it.
So it looks like we'll have to use sudo to remove that demon :evil:

Open up a terminal remove the unwanted directories (I would recommend that you'd copy and paste them in)
```
sudo rm /media/disk-1/.Trash-* -rf
```
```
sudo rm /media/disk-1/resycled/ -rf
```
```
sudo rm ~/.local/share/Trash -rf
```
Let us know how it goes, or if you are unsure about anything.

Also, **NOTE**: don't run "sudo rm -rf" ever unless you are 110% certain you know the consequences of running it :)

Regards
Iain

---

### Post by Patrick Snyder on 2008-12-17
Thank you!!!  (^_^)
Fixed

---

### Post by ibuclaw on 2008-12-17
Also, may I suggest that you run a virus scan on the computer too,
That is **ALL** Drives :)

Naturally, I would say clamAV (terminal-based) or clamTK (GUI based)
```
sudo apt-get install clamtk
```

Although, I have recently found three other good alternatives too.

[F-Prot]("http://www.f-prot.com/download/home_user/")
[Avast!]("http://www.avast.com/eng/download-avast-for-linux-edition.html")
[Avira]("http://www.free-av.com/en/download/download_servers.php")

(Minor Note):
For avast to be in your Applications Menu, you'll have to run this script after installing it (not that you will install, of course, but you never know ;))
```
cd /usr/lib/avast4workstation/share/avast/desktop
sudo ./install-desktop-entries.sh install
```

Regards
Iain

---

### Post by CharmlessMan on 2009-01-19
I'm having a similiar problem. No resycled but I cannot delete trash-1000. It's read only & it won't let me change permissions

[IMG]http://i125.photobucket.com/albums/p71/jigsaw695/Screenshot.png[/IMG]

---

