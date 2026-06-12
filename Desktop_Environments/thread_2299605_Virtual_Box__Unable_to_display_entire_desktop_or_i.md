---
title: "Virtual Box:  Unable to display entire desktop or increase VB desktop display area"
date: 2015-10-19
forum: Desktop Environments
---

### Post by hpng on 2015-10-19
[INDENT] 		Unable to display entire desktop or increase (**_not same as zoom in_**) VB's  display area

I have this version of VB (virtual Box):

Version 5.0.6 r103037 

When I installed Ubuntu 64 and Ubuntu 64 server in VB, the screen is small.
And it only show a portion of the Ubuntu desktop.
Using VB's screen scaling only **magnify** the screen.
It does not display the entire Ubuntu desktop inside VB.
 
So I deleted the installed ISO shown on the left panel of VB application.
then I read on forum of people doing something like this:
Devices> install Guest addition

But I do not see any access to menu item "Devices".

For Ubuntu 64 server v14.xx, the screen in only a third or a quarter of full display size. 
When I install Ubuntu 32 v15.xx version with graphics in VB, screen is about 2/3 of display size.

How do I go about making the screen cover entire screen of display and also show entire desktop of installed OS?

Thanks. 	
[/INDENT]

---

### Post by v3.xx on 2015-10-19
Try this inside the guest install.

```
sudo apt-get install virtualbox-guest-dkms
```

and reboot the guest

---

### Post by hpng on 2015-10-19
Thanks.
But will not do any good...  because ... 

hpng $ sudo apt-get install virtualbox-guest-dkms
[sudo] password for hpng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**virtualbox-guest-dkms is already the newest version.**
The following packages were automatically installed and are no longer required:
  libdbusmenu-glib4:i386 libdbusmenu-gtk4:i386 libsdl-ttf2.0-0 virtualbox-5.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.

When you said "... and reboot the guest"
do you mean restart VB?

---

### Post by v3.xx on 2015-10-20
Then you need to install guest additions.

You can also use scale for the console.
[ATTACH=CONFIG]265052[/ATTACH]

---

### Post by hpng on 2015-10-20
>> "Then you need to install guest additions."

Please explain what you mean by guest additions.
If you can, please provide a link to such instruction.

>> You can also use scale for the console.
This does not solve my problem.
In my first post, I wrote this:
"Using VB's screen scaling only **magnify** the screen.
It does not display the entire Ubuntu desktop inside VB."

---

### Post by SeijiSensei on 2015-10-20
Read the paragraph about the Extension Pack at [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads).

If I click on the link for the appropriate Extension Pack in Firefox, it prompts me to open the package with VirtualBox.

---

