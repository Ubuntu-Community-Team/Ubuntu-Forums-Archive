---
title: "how can you access your hard drives through virtualbox."
date: 2009-01-11
forum: General Help
---

### Post by dragos240 on 2009-01-11
Hey i was wondering how you can access your normal hard drive, while inside virtualbox. Is this possible? If so, how?

---

### Post by sp0nge on 2009-01-11
By "normal" hard drive, are you referring to the partition your primary OS is on? If so, then I believe the answer is no.

VirtualBox gives you the opportunity to create a new machine out of the hardware on which it's installed. By setting up a virtual machine, that creates a partition on which data can be stored, but it's like a fresh, new, separate machine.

The alternatives, as I see it, are to mount the files you want to access onto a flash drive, then attempt to mount this in the virtual machine. You can also email the file(s) and retrieve them that way.

---

### Post by howefield on 2009-01-11
From the Virtualbox manual

"..Shared folders allow you to access files of your host system from within the guest system, much like ordinary shares on Windows networks would – except that shared folders do not need a networking setup. Shared folders must physically reside on the host and are then shared with the guest; sharing is accomplished using a special service on the host and a file system driver for the guest, both of which are provided by VirtualBox.
.."

Chapter 4.6 it is.

You need Guest Additions installed.

---

### Post by dragos240 on 2009-01-11
> **howefield said:**
> From the Virtualbox manual

"..Shared folders allow you to access files of your host system from within the guest system, much like ordinary shares on Windows networks would – except that shared folders do not need a networking setup. Shared folders must physically reside on the host and are then shared with the guest; sharing is accomplished using a special service on the host and a file system driver for the guest, both of which are provided by VirtualBox.
.."

Chapter 4.6 it is.

You need Guest Additions installed.

Where can i find these?

---

### Post by aesis05401 on 2009-01-11
If you are using the current release of VirtualBox then there should be a menu item accessible when the VM is running.

I had a minor issue with config - so I had to manually download the image - Google turned it right up.

---

### Post by howefield on 2009-01-11
Select the option to install Guest Additions from the VirtualBox menu. You’ll need to do this after your guest is running.


Devices > Install Guest Additions.

---

### Post by fermin on 2009-01-11
> **howefield said:**
> Select the option to install Guest Additions from the VirtualBox menu. You’ll need to do this after your guest is running.


Devices > Install Guest Additions.

I don't think you need to install the Guest Additions to share files but you should install them as they are very useful anyway (for mouse and display integration).

Also, you don't need to be running the machine to setup shared folders; in any case the machine should be off.

From the main virtualBox window, select your virtual machine and click on configure, in the appeared dialog windows look for shared folders and you can add them in there. You can share your entire ubuntu home if you like and even share the /media folder to access your USB flash drives if you're using VirtualBox OSE. :guitar:

---

### Post by drs305 on 2009-01-11
Here's a link to installing Guest Additions. Fairly straightforward. Just start your guest first:
[http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/]("http://ubuntu-tutorials.com/2007/10/13/installing-guest-additions-for-ubuntu-guests-in-virtualbox/")

For shared folders, you can set them up before starting the machine from the options on the right after highlighting the specific VM.

---

### Post by albinootje on 2009-01-11
> **fermin said:**
> I don't think you need to install the Guest Additions to share files but you should install them as they are very useful anyway (for mouse and display integration). 

Yes, I also seem to remember that for sharing folders the Guest Additions are not needed.
But the Guest Additions are very useful to install.
Full screen mode is possible for the guest VM, higher resolutions, and personally I find it very annoying to having to deal with the mouse capturing when the G.A. are not installed yet.

---

### Post by noelvh on 2009-01-11
As I love VB and use it allot, when helping my Windows friends.
What I do is create a VBox share folder, then load that folder with links to other folder on my system. I have not done this but I am sure you could even link your home folder in there.
Now you will have access to any file you link to.

Hope this helps.

Noel

---

### Post by Knutsch on 2011-01-15
Hi Guys,

I am using Ubuntu Maverick with Virtual box (3.2.8). I have a Win 7 and a Mac Snow Leopard installed. The problem was always the same. I could not share Folders between the systems. Even If I shared Machine folders and Transient folder, I was not able to get out of the machine, or get in. (Except of course DropBox :D, moving left and right Gs, but it was taking too long)

I installed Guest Additions, and I was able to share at first a flash drive. Folders (but only on Fat partitions - of course)

Mac, Win, Linux shared folders, access trough virtualbox.

The only problem now,(relative minor) (I was not able to solve it yet) is that the VM is crashing if I am loading/using the shared folder in more than 1 system at once.
If I am moving some files in the folder, and at the same time I am taking/removing some other files in the same folder but from system loaded in the VM, I always get to crash the VM session.


Conclusion:
Without Guest Additions I was not able to directly share folders.

---

### Post by ibod on 2011-01-15
Hi 

From the Virtual box manual, here [http://www.virtualbox.org/wiki/Documentation](http://www.virtualbox.org/wiki/Documentation) Note: Virtual box is now at version 4.0 the below is based on V 3.2.12 

3.11 Shared folders
Shared folders allow you to easily exchange data between a virtual machine and your host. This
feature requires that the VirtualBox Guest Additions be installed in a virtual machine and is
described in detail in chapter 4.3, Shared folders, page 60.

I use the PUEL version  and not the release in the ubuntu repository,  because it has better usb access, It can be found here  [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) there are versions for  most ubuntu versions in common use.

I created a folder to share, but as said above you can share an existing folder if you want 

When creating the virtual machine (can be done later) select the machine  on the main screen and before starting it, scroll to the bottom of the  right hand panel. Click on the Shared Folder option and set up the path  the the folder you want to share. Click  the add shares folder icon and  pop down the folder path gadget in the Add Share window, and select  Other, you can then browse to your folder and select it.

when this is done start the machine and as detailed in posts above load the VirtualBox Guest Additions, They are needed!

You may then need to re boot the V-Machine (I cant remember)

The shared folder should then be accessible

e.g. in an XP guest. start windows explorer and look under My Network Places its listed as  "VBOXSVRvboxshared on Vboxsvr" on my machine

or you can create a shortcut with an appropriate path e.g.  \\VBOXSVR\vboxshared   points to my folder called vboxshared in my home  folder on my ubuntu host.

I hope this helps

---

### Post by nikieme on 2011-03-27
Hello everyone,

I had the same shared folder issue in virtual machine, which is now resolved by reading the above replies. Thanks for all your help.

Now another thing i want to ask you all is how do you add stuff into the shared folder. Suppose you want to put a text file from Windows 7 installed on Virtual Box into a shared folder , then how do you do it ???

Awaiting for your reply,
Nick

---

### Post by JP121 on 2011-03-27
On windows the shared folder looks like a network drive.  All you need to do is figure out how Windows 7 mounts network drives and find the one on the vbox domain.  Then you can just drag-and-drop any folder you want into the new folder.

---

### Post by nikieme on 2011-03-27
Hi,

The problem is when i try to drag and drop a file into the shared drive, it says permission denied...

I am attaching a screen shot of the error message i am getting.

---

### Post by scottbomb on 2013-04-04
I hate to resurrect an old topic but I'm having this issue. The newest version of VirtualBox doesn't have a Devices menu. I've searched through all the menus and cannot find anything related to Guest Additions. Even if it's installed, where are they mounted? I did sudo mount and do see any shares listed.

---

### Post by oldos2er on 2013-04-04
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

