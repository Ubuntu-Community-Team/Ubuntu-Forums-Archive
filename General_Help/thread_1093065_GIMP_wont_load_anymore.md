---
title: "GIMP wont load anymore"
date: 2009-03-11
forum: General Help
---

### Post by solorize on 2009-03-11
Hi,

Everytime I click on GIMP it starts to load and shows it in
the bottom Taskbar, but never displays the full screen, it just
disapears.

I have tried to remove the application from the Add/Remove
menu, but when I install it again it still does not work.

I also tried to install using the "Synaptic Package Manager"
but it still wont work as it comes back with an error
saying something about a "lib**" file?

Does anyone know how I can get it to work or will I have to
do a full reinstall of Ubuntu to get it to work again?

Sorry I am a newbie at Ubuntu so am still trying to learn
how it all works ;)

FYI.
GIMP use used to work, but I tried to install 
GIMPshop which did not seem to do anything and I guess could
of messed up the original GIMP program. :(

Any help would be great.

Regards

Mark

---

### Post by dzark on 2009-03-11
try doing a "Complete Removal" in synaptic packet manager.. That also removes config files...

then install it again :)

and if it makes an error message, please do try to remember it.. Its the only info we've got to go on

---

### Post by solorize on 2009-03-11
Thanks for your prompt reply.

I will give it a go tonight and will post 
the exact error messge if it comes up again.

Regards

Mark

---

### Post by Shpongle on 2009-03-11
this sounds a bit like the prob im havin, tried to remove & reinstall it too nd tried synaptic, it says there was an error parsing a file,  but the file is gone, im still waiting on a reply too

heres the link i need the image-menu.xml file

[http://ubuntuforums.org/showthread.php?t=1092369](http://ubuntuforums.org/showthread.php?t=1092369)

---

### Post by geirha on 2009-03-11
Post the output of this:
```
aptitude search '~i gimp'
```
It searches for and lists all installed (~i) packages containing the string "gimp".
```
aptitude search '~c gimp'
```
This one is similar, but only lists packages that have been removed, but not purged.

---

### Post by Sava on 2009-04-13
I'm having the exact same problem. However it doesn't show any error either in Synaptic window or in Terminal when installing GIMP.

APplications => Graphics => GIMP won't start. Taskbar will only shows: "Starting GIMP IMage...." and that's about it. It disappears in a few seconds.

In Terminal, when I type: gimp, the message returned is "Segmentation fault".

I've tried googling around, however none that I found is relevant.

Please help,


PS: Of course Photoshop on wine is another solution, but I prefer Ubuntu's GIMP. As well, I tried wine install GIMP, but the program seems to have bugs, it displays weird.

---

### Post by Sava on 2009-04-13
> 
$ gimp; echo "Exit status is $?"
Segmentation fault
Exit status is 139


Please help,

---

### Post by Sjun on 2009-04-14
I'm having a segmentation fault at basically everything i try to do;
for instance; "sudo top" in a terminal prompts for a password, and after providing it, it exits with segmentation fault.

ehm... help! :)

---

### Post by Sava on 2009-04-15
lolz Sjun, in that case I'd not hesitate reinstalling the system right away

---

### Post by animefan82 on 2009-04-16
I'm having segfault problems with compiz, eclipse and evince document viewer. Googling for "intrepid \"segmentation fault\"" allows me to confirm that this started happening after the latest kernel and nvidia upgrade. At least the kernel upgrade. For me it's version 2.6.27. My gimp doesn't segfault though.

---

### Post by StuartN on 2009-04-16
It is possible that Gimp does load and has a zero-size window - the file ~/.gimp-2.6/sessionrc contains the window positions from your last session to use the next time. If you delete this file then Gimp will use the installation defaults and rewrite the file. In fact if you have other Gimp hangovers that persist when you uninstall and re-install then it is likely that this directory is preserving the odd settings. You should be able to safely delete all these rc files and have them rebuilt when you next run Gimp, but you lose any customization.

The entire ~/.gimp-2.6/ directory structure is empty when Gimp is installed.

---

### Post by danebramaged on 2009-09-20
> **solorize said:**
> Hi,

Everytime I click on GIMP it starts to load and shows it in
the bottom Taskbar, but never displays the full screen, it just
disapears.

I have tried to remove the application from the Add/Remove
menu, but when I install it again it still does not work.

I also tried to install using the "Synaptic Package Manager"
but it still wont work as it comes back with an error
saying something about a "lib**" file?

Does anyone know how I can get it to work or will I have to
do a full reinstall of Ubuntu to get it to work again?

Sorry I am a newbie at Ubuntu so am still trying to learn
how it all works ;)

FYI.
GIMP use used to work, but I tried to install 
GIMPshop which did not seem to do anything and I guess could
of messed up the original GIMP program. :(

Any help would be great.

Regards

Mark

I get the same thing except for the fact that I don't get any error messages at all.

So, I started System Monitor and noticed a 45% spike in cpu usage however, I don't see anything new actually showing up in system monitor at all.

I can run gimp from the command line but it comes up as 2.2.  I had 2.6 installed.  It works, but not from the menu and I have to go through  the install splash screen every time.

Please help the dainbramaged.

---

### Post by danebramaged on 2009-09-20
> **geirha said:**
> Post the output of this:
```
aptitude search '~i gimp'
```It searches for and lists all installed (~i) packages containing the string "gimp".
```
aptitude search '~c gimp'
```This one is similar, but only lists packages that have been removed, but not purged.

I tried this using the root terminal but was informed that this aptitude does not have super cow powers.  What must I do to achieve super cow powers?

---

### Post by geirha on 2009-09-21
> **danebramaged said:**
> I tried this using the root terminal but was informed that this aptitude does not have super cow powers.  What must I do to achieve super cow powers?

You probably got the help screen. It shows that help screen if it doesn't recognize the command (search in this case). Sure you didn't have a typo in there? Try copy/pasting.


I get the following output btw. This is on Ubuntu 9.04, without having gimpshop (ever) installed
```
$ aptitude search '~i gimp'
i   gimp                            - The GNU Image Manipulation Program        
i   gimp-data                       - Data files for GIMP                       
i   gimp-help-common                - Data files for the GIMP documentation     
i   gimp-help-en                    - Documentation for the GIMP (English)      
i A gimp-help-no                    - Documentation for the GIMP (Norwegian)    
i   libgimp2.0                      - Libraries for the GNU Image Manipulation P

```

---

### Post by Michal77 on 2009-09-22
> **StuartN said:**
> It is possible that Gimp does load and has a zero-size window - the file ~/.gimp-2.6/sessionrc contains the window positions from your last session to use the next time. If you delete this file then Gimp will use the installation defaults and rewrite the file. In fact if you have other Gimp hangovers that persist when you uninstall and re-install then it is likely that this directory is preserving the odd settings. You should be able to safely delete all these rc files and have them rebuilt when you next run Gimp, but you lose any customization.

The entire ~/.gimp-2.6/ directory structure is empty when Gimp is installed.

I had similar problem. GIMP didn't want to lunch. Your post did steer me to the solution. I went to the system monitor and killed GIMP process, them just start GIMP normally from the menu.
M.

---

### Post by danebramaged on 2009-09-22
> **geirha said:**
> You probably got the help screen. It shows that help screen if it doesn't recognize the command (search in this case). Sure you didn't have a typo in there? Try copy/pasting.


I get the following output btw. This is on Ubuntu 9.04, without having gimpshop (ever) installed
```
$ aptitude search '~i gimp'
i   gimp                            - The GNU Image Manipulation Program        
i   gimp-data                       - Data files for GIMP                       
i   gimp-help-common                - Data files for the GIMP documentation     
i   gimp-help-en                    - Documentation for the GIMP (English)      
i A gimp-help-no                    - Documentation for the GIMP (Norwegian)    
i   libgimp2.0                      - Libraries for the GNU Image Manipulation P

```

aptitude search '~i gimp'
i   gimp                                             - The GNU Image Manipulation Program                         
i   gimp-data                                        - Data files for GIMP                                        
i   gimp-data-extras                                 - An extra set of brushes, palettes, and gradients for The GI
i   gimp-dds                                         - DDS (DirectDraw Surface) plugin for the gimp               
i   gimp-help-common                                 - Data files for the GIMP documentation                      
i   gimp-help-en                                     - Documentation for the GIMP (English)                       
i   gimp-normalmap                                   - Normal map plugin for GIMP                                 
i   gimp2.0-quiteinsane                              - A Qt based SANE plugin for GIMP 2.0                        
i   gimpshop                                         - GimpShop package                                           
i   grokking-the-gimp                                - GIMP tutorial book by Carey Bunks (HTML)                   
i   libgimp2.0                                       - Libraries for the GNU Image Manipulation Program           

O.K.,  ... So now what do I do?  How does this info help me? :confused:

---

### Post by geirha on 2009-09-23
You've still got the gimpshop package installed. Purging it, should hopefully revert your gimp back to the 2.6 version.

```
sudo aptitude purge gimpshop
```

---

### Post by danebramaged on 2009-09-23
user/local/lib was the culprit.

barrels full of gimp 2.0 stuff were secreted away under user /local/lib beyond the reach of apt-get commands such as remove --purge and clean and autoclean etc., etc.

I used gnome commander and ripped it out by hand.

Then, when I used apt-get install gimp, it pulled down over 50 meg instead of 12.8.

Now, after all that hassle, it just works. :P

Problem = Sorted.  (but not solved) 'cause how did it get like that in first place?

Gimp never had a problem before and, this system is typically used for surfing and email.  The only updates are for security and intrepid backports.  :confused:

gimp-2.6 installed into my home folder like it should have once 2.0 was removed from /user/local/lib


Oh Well,  ... Everythings just like popcorn now. :popcorn:

---

### Post by cocozz on 2009-11-03
That worked for me:

```

rm -fr ~/.gimp*
rm -fr /usr/local/lib/gimp*

apt-get remove --purge gimp
apt-get remove gimp*

apt-get install gimp

```

Last one is a little hardcore, but whatever...

Hope it helps :popcorn:

---

