---
title: "Folder Sharing - Virtual Machine"
date: 2009-05-27
forum: General Help
---

### Post by luisridaocruz on 2009-05-27
I have installed a Virtual Machine under Ubuntu in which the guest is Windows XP.
I'm trying to share a folder (Data folder in Ubuntu) with the guest W XP.
In the virtual machine I have set up a shared folder (Name: Data ,, Path:/media/Data)
Following the instructions in the user manual I execute in the terminal window:

VBoxManage sharedfolder add "VirtualBox" --name "Data" --hostpath "/media/Data"

But I get the following message:

VirtualBox Command Line Management Interface Version 2.1.4_OSE
(C) 2005-2009 Sun Microsystems, Inc.
All rights reserved.

[!] FAILED calling a->virtualBox->FindMachine(Bstr(a->argv[1]), machine.asOutParam()) at line 4159!
[!] Primary RC  = VBOX_E_OBJECT_NOT_FOUND (0x80BB0001) - Object corresponding to the supplied arguments does not exist
[!] Full error info present: true , basic error info present: true 
[!] Result Code = VBOX_E_OBJECT_NOT_FOUND (0x80BB0001) - Object corresponding to the supplied arguments does not exist
[!] Text        = Could not find a registered machine named 'VirtualBox'
[!] Component   = VirtualBox, Interface: IVirtualBox, {339abca2-f47a-4302-87f5-7bc324e6bbde}
[!] Callee      = IVirtualBox, {339abca2-f47a-4302-87f5-7bc324e6bbde}

Can anyone help please?

Best,
Luis

---

### Post by kpkeerthi on 2009-05-27
**[COLOR="Red"]Text = Could not find a registered machine named 'VirtualBox'[/COLOR]**

Correct the virtual machine name. Or use the GUI to add a Shared folder.

---

### Post by luisridaocruz on 2009-05-27
I have tried all kinds of names:

VirtualBox
virtualbox_ose
VirtualBox OSE

....
....
and I still get the same error message.

---

### Post by YldGuy on 2009-05-27
as far as i remember i didnt have to use the terminal for the virtualbox to create a shared folder. whats stopping you from using the GUI?

---

### Post by kpkeerthi on 2009-05-27
The virtual machine name is the name of guest you gave when creating a virtual machine for it.

---

### Post by luisridaocruz on 2009-05-27
I have used the GUI to create the shared folder.
But the gust application (Windows XP) does not detect it.
I go to  "My Networking           Places" -> "Entire Network"  and the "VirtualBox Shared Folders"
does not come up.

Best,
luis

---

### Post by kpkeerthi on 2009-05-27
Have you installed the Guest Additions on your Guest OS?

---

### Post by YldGuy on 2009-05-27
check this thread... [http://ubuntuforums.org/showthread.php?t=367155](http://ubuntuforums.org/showthread.php?t=367155)

---

