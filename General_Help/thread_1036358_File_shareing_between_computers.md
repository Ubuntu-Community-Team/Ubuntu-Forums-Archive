---
title: "File shareing between computers"
date: 2009-01-10
forum: General Help
---

### Post by Silvernail on 2009-01-10
I have 8.04 on 2 computers and hooked to the same router. I would like to share files between the 2.

what application do I  use to negotiate this?

On my old Linspire system it was called 'filesharing manager'

TIA
Dave

---

### Post by nothingspecial on 2009-01-10
[[COLOR="Lime"]ssh[/COLOR]]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by x22 on 2009-01-10
well, this is where "network file system" comes in handy.
try "man nfs" for more info

---

### Post by Silvernail on 2009-01-12
I'm getting  into things I  don't understand when reading about 'ssh' and 'nfs'.

The 2 computers I want share files between sit about 6 feet apart. Can I connect them together with an ether net cable or a USB cable?

What application would I use?

Thanks
Dave

---

### Post by albinootje on 2009-01-12
> **Silvernail said:**
> I'm getting  into things I  don't understand when reading about 'ssh' and 'nfs'.

The 2 computers I want share files between sit about 6 feet apart. Can I connect them together with an ether net cable or a USB cable?

What application would I use?


You wrote that they both connect to the same router, then there's no need to use another network cable.
Try the right-click on a folder, and test the "Sharing Options".

NFS is another option, but not that easy for a Linux beginner who prefers a GUI.
If you want to try, see here :
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
-> Installation and Configuration

---

### Post by Silvernail on 2009-01-25
I'm going to say this problem is solved if I can find the button.

In following ya'll advice, on the computer that I have the 200 gig drive that I want access to, I opened 'nautilus' and it recognized the drive.
I now have access  to the data I want.

So whoever said whatever was said the sent me down that lane of thinking, Thanks.

Dave

---

### Post by adamlau on 2009-01-25
Consider the GUI-based Dropbox for remote file sharing.

---

### Post by scouser73 on 2009-01-25
Check this tutorial out; [http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/]("http://tombuntu.com/index.php/2008/12/19/simple-desktop-file-sharing-with-giver/")

---

### Post by Silvernail on 2009-01-25
Ok guys, will do.

I'm also going to try Unison as soon as my other computer gets finish with its present job.  Ripping 38 more cassette tapes.

Thanks
Dave

---

### Post by Kain000 on 2009-01-25
also, if you want a drop-box like Gui for local networks try the program Giver.

---

### Post by Silvernail on 2009-01-26
> **Kain000 said:**
> also, if you want a drop-box like Gui for local networks try the program Giver.
Where do I find giver. It's not in the repository.

Dave

---

### Post by jerome1232 on 2009-01-26
You can just right click the folder you want to share, then click "sharing options" and turn on file sharing from there. It will probably install samba for you, ask you to restart your session. Once that's done right click the folder again and share it.

Now that folder should be browsable by going to Places-Network from the other computer.

---

### Post by albinootje on 2009-01-26
> **Silvernail said:**
> Where do I find giver. It's not in the repository.

Dave

Giver is in the Intrepid repository.

Here's a howto for Giver :
[http://ubuntuforums.org/showthread.php?t=494198](http://ubuntuforums.org/showthread.php?t=494198)
Make sure to read the whole thread.

And I think file sharing via Nautilus in (as someone else already mentioned) is easier.

---

