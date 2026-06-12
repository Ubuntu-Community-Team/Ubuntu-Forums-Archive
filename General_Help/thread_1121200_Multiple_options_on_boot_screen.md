---
title: "Multiple options on boot screen"
date: 2009-04-09
forum: General Help
---

### Post by n8izzle on 2009-04-09
Hello,
           well this is my first post and i am stuck.. i tried to download ubuntu from online and when i tried to install it Ubuntu would error out.. I did this multiple times until i finally received my live cd and now i got it all working.. The issue is that now when i log in it doesnt just give me an option to which operating system i want to log into.. it gives me multiple options... there are about 3 for Ubuntu and only 1 for windows..The bad thing is that only one of them works too!! i click on any other Ubuntu then it gives me the error from when i first started... Any ideas on how to remove them.. I'm sorry if i didnt explain myself right or for any confusion.. any help would be great...


thank you in advance
Nate

---

### Post by JECHO on 2009-04-09
> **n8izzle said:**
> Hello,
           well this is my first post and i am stuck.. i tried to download ubuntu from online and when i tried to install it Ubuntu would error out.. I did this multiple times until i finally received my live cd and now i got it all working.. The issue is that now when i log in it doesnt just give me an option to which operating system i want to log into.. it gives me multiple options... there are about 3 for Ubuntu and only 1 for windows..The bad thing is that only one of them works too!! i click on any other Ubuntu then it gives me the error from when i first started... Any ideas on how to remove them.. I'm sorry if i didnt explain myself right or for any confusion.. any help would be great...


thank you in advance
Nate

run this command and delete everything you don't want at the bottom.
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Yvan300 on 2009-04-09
Provide more info please, like what is the error message you are having and it is the grub list you are talking about right, where you are able to choose the kernel version to use?

---

### Post by mb_webguy on 2009-04-09
Actually, there's a better way to do that -- and actually the way it *should* be done.

First, though, you should know what those options are and why they're there.

One of the options you're seeing for Ubuntu is the actual Ubuntu entry to log in normally.  

You may also see one that says "memtest".  This is used to check your system memory for problems.  You don't generally have to use this much.

You may also see one that says "recovery console".  This is the "OMG, I screwed up and can't start Ubuntu to fix why I can't start Ubuntu" option.  This is the uber-user console that gives you a lot of power to repair your system if the shift hits the fan.  You may want to keep this in case something really bad happens.

Finally, you may see one or more menu items that are identical to the normal Ubuntu login entry, but with a slightly different string of numbers.  By default, you get another one of these every time the kernel is updated.  The old entries are left there in case the new kernel causes problems and you need to continue using the older kernel.  This is rare, but has been known to happen.

Anyway, to change what you see at the GRUB menu, you should edit the "/boot/grub/menu.lst" file as JECHO said, using "gksu gedit /boot/grub/menu.lst".  However, rather than deleting the entries, you should edit the options.  The GRUB menu is occasionally automatically updated (such as when the kernel is updated), and the options are used to create the new menu.  If you just edit the menu itself, when the GRUB menu is automatically updated you'll get the same stuff all over again.

To remove the memtest and recovery items (which I do not recommend), look for the following section and change "true" to "false" on the bottom line.```
## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true
```

To control how many old kernels are listed, look for the following section and change the number on the bottom line.```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2
```

If you want to just remove the memtest item but leave the recovery mode, look for the following section and change "true" to "false".```
## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true
```

If your computer is located somewhere other people can gain physical access to it, such as in a dorm room, you may want to password-protect the alternate options (particularly recovery mode).  Look for the following section and add the line in italics, replacing "yourpassword" with whatever you want.```
## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
*password yourpassword*
```You also have to find the following section and change "false" to "true".```
# should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false
```

Once you're done making the changes you want, save and exit.  Now, in the terminal, enter the command "sudo update-grub".  This will make the appropriate changes to the GRUB menu based on the options you set.  And those changes will remain even when a software update causes the GRUB menu to be updated.

---

### Post by n8izzle on 2009-04-09
wow thank you all for your help.. i am making the changes as we speak... i will let you all know what happens.. thank you very uch

---

### Post by MikeSz on 2009-07-03
Can I just check something on this?  On a laptop I have, there are loads versions of ubuntu listed in the grub start-up menu and it seems to have just added to the menu every time there has been a major update.  Can I just remove the menu instances in the list file as suggested above in order to tidy it up or is it more complex than that?

for instance, my grub screen reads:

Ubuntu 8.10, kernel 2.6.27-14-generic
Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-13-generic
Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-12-generic
Ubuntu 8.10, kernel 2.6.27-12-generic (recovery mode)

....and it carries on that way down to 2.6.27-7.  Obviously I only need the top two.  Are these other versions actual versions installed on my machine or are they just menu entries that simply havent been removed by some automated process?

---

