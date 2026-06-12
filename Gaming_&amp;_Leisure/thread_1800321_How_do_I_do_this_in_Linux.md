---
title: "How do I do this in Linux"
date: 2011-07-08
forum: Gaming &amp; Leisure
---

### Post by BulgarianBoy on 2011-07-08
Okay so the that said this is working from windows and only on windows. But we have the same problem in common he cannot run maplestory from VMware. I was wondering if the guide he gave for Windows could some way be used on linux so I could get it to work because I tried doing this when I was in VMware on Windows XP and searched up "VBOX__" but nothing showed up.

Here is what he said.

VMWare:
 Originally Posted by Someone at Sleepywood 
I figured it out for VMWare. Just change the value of 
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Class\{4D36E968-E325-11CE-BFC1-08002BE10318}\0000]
"DriverDesc"="VMware SVGA II"
to anything.
Basically it was just checking the description of the video card driver.






VirtualBox:
 Originally Posted by Someone at Sleepywood 
Start, Run, regedit, ctrl-f, check all the "Look at" boxes, enter:
VBOX__ 
into the text field. Hit Enter. Right-click on the key name, Export, then right-click the key name again, Rename to edit the string(to BBOX__ in my case).

Ctrl-f again, enter:
VBOX - 1 
into the text field. Hit Enter. Right-click on the key name, Export. Double-click on the entry in the Name column to edit(to BBOX - 1 in my case)

Restore the exported entries before exiting the VM, or just run from a Snapshot. You should only have to change the first occurrences you find. I do not know if something similar would work with other virtualization software.



Enjoy. 


Additiona options:

If you get a message from themida preventing you from even starting MapleStory you will need to do this.
Go to the location where you Virtual Machine's .vmx file is stored. Make sure your VM is off & open the vmx file with notepad. At the bottom of the file add this line.
Code:

monitor_control.restrict_backdoor = "TRUE" 
Save & start your virtual machine. Since you've already made the registry change to bypass hackshield & changed your vmx file to bypass themida MapleStory should run normally. 


----------
Anyone got an Idea?

---

