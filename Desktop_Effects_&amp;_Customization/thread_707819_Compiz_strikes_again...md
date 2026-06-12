---
title: "Compiz strikes again.."
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by Darkchef on 2008-02-25
Hi,

I've been playing about with the Ubuntu 7.10 distro and thought id have a go at using compiz however all i get is this error when loading compiz through the terminal:

[I]dan@dan-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity [/I]

i've already tried to install xgl and is marked in synaptic as installed.

I'm also not too sure what it means as a "whitelisted driver" as i have a restricted driver already for the graphics, although i am currently using ubuntu in VMware workstation to get used to the interface before I switch to it on my new pc i'm currently building. 

Any help would be appreciated, cheers

Dan

---

### Post by Keywil on 2008-02-25
Sounds like you might be making things harder than they need to be...

open a terminal and enter:*sudo apt-get install compizconfig-settings-manager*

After it's installed,  *System>>Preferences>>Advanced Desktop Effects Settings*

that what worked for me...

I don't think you can use Compiz inside of vmware.  I believe that VMWare has it's own video driver.

---

### Post by Darkchef on 2008-02-25
Thanks for the reply Keywil, i tried it but it seems to be already installed:

[I]dan@dan-desktop:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

I've done some more tweaking and discovered that the visual effects cannot be changed from none as i get a "Desktop effects could not be enabled" error. 

EDIT : yeah, its probably because of VMware and the drivers its using, but I thought it would have worked okay. Hopefully it will work on the new build im doing. 

Anyone have a different idea??

---

### Post by Msane on 2008-02-25
how much ram does ur video card have .... for compiz to be enabled you are going to need atleast 128mb video card ,,,,, if it is ... boot to the BIOS of the VM and check to see if the video card is running to the fullest potential

---

### Post by Darkchef on 2008-02-25
i have a 256mb ATI radeon xpress 1100 on this acer laptop and ive just checked the vmware bios like you said and there doesnt seem to be any mention of a graphics card on there.

thanks for you help anyway but i think its not gonna work.

---

### Post by daqron on 2008-03-14
Running Ubuntu 7.10 in VM and having similar issues. I concur that compiz isn't going to work. You can try adding vmware to the whitelisted drivers in /usr/bin/compiz, but the outcome for me was unqualified failure.

---

### Post by mimada on 2008-03-14
Virtual machines typically don't have 3D capability. There's been some testing with VMware and OpenGL but nothing I've seen available yet.

---

