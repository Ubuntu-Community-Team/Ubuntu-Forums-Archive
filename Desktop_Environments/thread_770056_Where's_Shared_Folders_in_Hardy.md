---
title: "Where's Shared Folders in Hardy?"
date: 2008-04-27
forum: Desktop Environments
---

### Post by PryGuy on 2008-04-27
Hello all!
I found that the Shared Folders (shares-admin) disappeared from Hardy! Is that okay?

---

### Post by evozniak on 2008-04-27
goto nautilus and right click into a folder, and vuala here is shared folders, like in windows!

---

### Post by PryGuy on 2008-04-27
Wow! Hardy rocks! But anyway, think they had to leave it in System/Administration anyway...:icon_frown:

---

### Post by evozniak on 2008-04-27
you right, i fell lack a share-center..
its good to control all shares.

---

### Post by PryGuy on 2008-04-27
Anyways, typing ' shares-admin' in terminal gives you the window. ;)

---

### Post by ofb on 2008-04-27
> **PryGuy said:**
> Anyways, typing ' shares-admin' in terminal gives you the window. ;)

Thanks, that's good to know.

But I'd like to understand what they're intending with Hardy.

I've enabled sharing for a directory in Nautilus as mentioned above, but that dialog has no options for SMB and NFS, has no way of declaring Allowed Hosts, and the shared folder is not showing up on my Gusty machine. (The Hardy machine can use the SMB shares on my Gusty, so we know the network is set up.)

Nautilus just says it's shared now. No indication of how and with whom.

What's going on? And how's it supposed to work?

---

### Post by 22ppc on 2008-04-28
Hi. I am a newbie to Ubuntu as well forums in general, so feel free to flame me if I violate any protocols here.
Below is how I put a clean install of Hardy on my Windows Network:

1.	Create a folder on the Desktop called “HardyShared” 
2.	Right click this folder and choose “Sharing Options”
3.	Check “Share this folder”
4.	Get dialog “Sharing services not installed…”
5.	Click INSTALL SERVICES and provide our password at the prompt
6.	He downloads and installs the packages. When the “Completed” dialog pops up, we click CLOSE
7.	We are back at the “Folder sharing” dialog. 
We know that we must log out and back in here, or else an error
message results. (Known bug). We log out and back in.
8.	Right click the HardyShared folder and choose “Sharing Option”
9.	Check the “Share this folder” option and also the “allow
 other users to write to this folder” option (if you want to 
place files here from another computer) and click “Create Share”
10.	A dialog appears that asks if we want Nautilus to “Add permissions automatically”. We click to agree.
11.	Now we can see and access Hardy from WinXP, but he shows up in WORKGROUP instead of ROSAN (My workgroup name)


Add Shared Folder back into the menu
1.	System > Preferences > Main Menu > in the left panel click to select System > Administration.
2.	On the right side, click the “New Item” button. In the “Name” box of the “Create Launcher" dialog, provide a name. (eg Shared Folders)
3.	Click the Browse button. In the resulting screen, choose File System.
4.	Browse to /user/bin/ and select “shares-admin” and click the OPEN button.
5.	We are back at the “Create Launcher” dialog with the path box now filled in.
6.	In the Comment box add what you like. This is text that will be displayed when the mouse is hovered over our new menu icon. (eg. Shared Folder Configuration)
7.	Click OK. Now System > Administration should have a “Shared Folder” (or whatever you typed in the Name box) icon.
8.	If we choose to use this option, we can start Shared Folders, drag a folder into it and click to select it. Then choose the “General Properties” tab and change the “Domain/Workgroup” entry from WORKGROUP to ROSAN
9.	This makes Hardy appear in the same workgroup as the other computers on the network. It also changes the Workgroup= WORKGROUP entry in /etc/samba/smb.conf

Alternate method to change workgroup name
1.	I am nervous about using Shared Folders now. Maybe it was removed to discourage newbies like me from using it.
2.	Applications > Accessories > Terminal
3.	CODE:
	        gksudo gedit /etc/samba/smb.conf. 
Provide your password at the prompt
5.	Find the entry “Workgroup=WORKGROUP.
6.	Change this entry to read “Workgroup=(your workgroup name. In my case ROSAN)
7.	File > Save. Close gedit
8.	back in Terminal type exit

---

### Post by Club17 on 2008-04-29
Thank you so much. I didn't find how to change the name of WORKGROUP

;)

---

### Post by Sidster on 2008-04-29
Is it just me or is this a massive oversight. Does this mean that anyone on your network has access to that share??? What about if you take your laptop to work or university???

Please correct me if I'm wrong but doesn't this make it possible for someone to copy huge files to your machine and cause gnome to crash (known to happen when gnome runs out of disk space, not sure if it's been fixed in Hardy.) Sure, someone who knows about the security risk would much rather create a samba user and password protect it but your average person wouldn't.

IMO it would be much better if there was an easy way to create samba users and assign them a password from within the "Sharing Options" window.

Some investigation has yielded that even if I change the domain/workgroup name from "WORKGROUP" to "UBUNTU" i can still browse to the share by going to: Windows Network > _workgroup_ > "My Hostname > "My Shared Folder". In fact everything in "shares-admin" seems unrelated to the settings in "Sharing Options" Does that seem screwy to anyone?

I don't want to speculate since I'm a bit of a noob but doesn't that mean that the "Domain Name/Workgroup" has been hardcoded into the shared folders functionality somehow?

---

### Post by kidcharles on 2008-05-02
> **PryGuy said:**
> Anyways, typing ' shares-admin' in terminal gives you the window. ;)

Sure, the window comes up, but all the buttons are greyed out for me. This seems like it is because this new "unlock" feature to get sudo privileges wasn't incorporated into 'shares-admin' so it just doesn't work. I don't mind that you can now share folders by right-clicking on them, but why did they take away centralized access to controling shares by removing 'shares-admin' from the menu and making it impossible to use logged in as a regular user?

---

### Post by ofb on 2008-05-02
kidcharles, the shares-admin dialog that comes up on my Hardy has the Unlock button. I did a fresh install (over existing /home). Did you do Upgrade?

Meanwhile try 'gksu shares-admin' to see if that gives you the password dialog.

Notes: 

- shares-admin never worked for regular users - it always required password.

- I still think the new method is busted. Right-clicking to share in Nautilus doesn't make the share visible to my Gusty machine, and as said before I have no idea if that share is SMB or NFS, or who is allowed to use it.

Anyone found documentation for the new networking under Hardy? I'd like to find out what the developers intended here.

---

### Post by chemical on 2008-05-02
> **Sidster said:**
> In fact everything in "shares-admin" seems unrelated to the settings in "Sharing Options" Does that seem screwy to anyone?

It looks completely unrelated to me... in fact I used the right-clik-->share to share some folders and these folders don't appear in the shares-admin menù...

I'm sorry to say that, but Hardy is pretty screwed up... and it's an LTS too...

---

### Post by ofb on 2008-05-02
Um, wow. Check out this thread
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/208480](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/208480)

I'm not sure I can summarize that. Looks like the desktop team sees shares-admin as flawed and has replaced it with nautilus-share for SMB. Also they don't think NFS is appropriate for their target users, so it's not considered.

There is no mention at all of documentation for how nautilus-share is supposed to be used. Or documentation for Gusty users transitioning from the shares-admin method to nautilus-share.

I appreciate that Sebastien Bacher is getting a little testy about non-technical enquiries in that thread because that isn't the place for it, but where the heck /are/ we supposed to make those enquiries?

My problems:

1. shares-admin actually worked great under my Gusty machines. I was very impressed Ubuntu had finally made SMB work well via GUI as of Gusty, and am surprised to hear it is flawed.

2. nautilus-share is not in fact working on my Hardy, so I'd like the user documentation about how it's supposed to work.

3. Shame they don't like NFS. It does still need a lot of work to get it ready for the average user, but some application only work with NFS*, and the improvements to shares-admin with Gusty had cut the setup problems with NFS in about half. Things were getting better - I'm sorry to see a reversal.

* (like some music players running music from a network share - SMB doesn't mount a share in the normal seamless *nix style, so you have to use NFS.)

... so yeah, networking on Hardy does seem to be a mess. I'd really like to find the documentation about how it's supposed to work. I can do it the old fashioned way, but I'm trying to understand the currently intended method.

---

### Post by ofb on 2008-05-02
Would somebody thought-check this for me?

SMB is *Windows Networking*. It does most things for most people, and as a result does everything required by some people. But it is not a complete *Linux Networking* solution, and the SMB project does not intend it to be. NFS is *Unix Networking*. It follows the Unix convention of mounting devices, and is not intended to work with non-Unix systems. Also it has never been updated for modern Linux home computer use, so it's a bit of a pain to use that way. *Linux Networking* is simply a combination of SMB and NFS, with no particular refinement or enveloping technology or apparent game plan, other than the shares-admin dialog. *Ubuntu Networking* is whatever portion of *Linux Networking* the Ubuntu developers consider to be relevant to their target users.

Seems the Ubuntu devs found shares-admin inadequate for their requirements. (Apparently because it follows the SMB conventions, not because it does them wrong?) And they've chosen nautilus-share for Ubuntu Networking under Hardy.

Have I got that much right?

If so, that leaves the question of what the current Ubuntu Networking is intended to be able to do. Being an Ubuntu user I'm naturally curious about that, and I'd like it spelt out. Particularly because it seems to be a new approach.

---

### Post by doobydave on 2008-05-15
Another crucial feature that's disappeared from ubuntu gnome.


Something is screwed up with 'shares-admin' as it doesn't display any shares in it that have been created by right-clicking in nautilus.


It is absolutely necessary to be able to administrates all shares from a single place.
:(

---

### Post by bandyo on 2008-05-15
I have a slightly different problem. I have two machines A and B. A always runs Hardy. B dual boots between Hardy and XP. I have a shared folder in A. When B is WinXP it sees this folder in A. I have samba running. I can also see and read the WinXP shared folder. However, when both A and B are running Hardy, I cannot access the shared folder in A and vice versa.

I have samba running in both and I intalled NFS too. I created two shares for the same folder using shares-admin, one for smb one NFS in machine A. The smb was there before and I think it is used when I boot WinXP in machine B.

Please help.

Solved: It turned out I had entered the wrong static IP in the network configuration of the B machine in its Ubuntu system.

---

### Post by buccaneere on 2008-11-19
This is pretty interesting. 

Is there a gui which shows shares under NFS AND samba configurations?

---

