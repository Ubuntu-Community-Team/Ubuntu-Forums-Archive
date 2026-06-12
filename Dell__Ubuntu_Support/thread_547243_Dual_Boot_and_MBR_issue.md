---
title: "Dual Boot and MBR issue"
date: 2007-09-09
forum: Dell  Ubuntu Support
---

### Post by circuz_phreak on 2007-09-09
I had Vista pre-installed on my machine, set up a dual boot with Ubuntu.  Everything worked fine untill I updated ubuntu,  there was no harm done but the MBR (master boot record) seemed to have double up the linux entries.  There are 3 entries, generic (the OS), recovery mode, memory test.  Generic and recovery mode double up (there´s two entries for each now), but memory test is still on one.  Then underneath it all it says ¨other opearating systems¨ Vista(Longhorn loader), and Windows XP embedded (which isn´t an actualy choice.  I tried pressing ´e´ at the bootup screen but had no idea what to do after when editing.  How can I fix all of this up, to clear away the double entries and to even get rid of the embedded xp entry???

---

### Post by rsambuca on 2007-09-09
The kernel was just updated recently, so the new kernel is automatically added to your menu.lst

You have a few options: 

1.  Edit your menu.lst file to either remove the entries, or comment them out

2.  If you are positive that the new kernel works 100% on your setup, then you can uninstall the old linux-images.

I recommend number 1.

---

### Post by circuz_phreak on 2007-09-11
I'm guessing I do option 1 from the terminal in linux?  Where would the file be located?  Is the newer kernel the first entry, or the second set of entries?  What diffrence is there if I boot from a diffrent kernel everytime? Thanks

---

### Post by notwen on 2007-09-11
> Where would the file be located?

Check out /boot/grub/menu.lst.  I'd suggest making a backup copy first prior to editing in case you need to fall back to the backup. =]

---

### Post by rsambuca on 2007-09-11
Yes, to edit the menu.lst file you start at the command line, but don't worry, it is very easy.  You first need to open a terminal by going to your top Menu bar and selecting "Applications -> Accessories -> Terminal".

At the prompt, you can enter the following command to open the file in gedit, the ubuntu default text editor (You can just copy & paste this into the terminal if you wish)```
gksudo gedit /boot/grub/menu.lst
```

You can now just place a number sign '#' in front of the lines that you want to comment out (lines starting with the # are ignored by the program).  The newer up-to-date kernel will have the higher number, and if it works, it is the better one to use since it has the latest security updates.  For example, I have commented out the following kernel from my menu.lst as follows:```
#title          Ubuntu, kernel 2.6.20-15-generic
#root           (hd2,4)
#kernel         /boot/vmlinuz-2.6.20-15-generic root=UUID=024af315-92dd-48fa-9495-7d3d359459f6 ro quiet splash
#initrd         /boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

```

If you edit your menu.lst like this, the old kernels won't show up when you get to the grub loader screen.  Just save the file and close.

---

### Post by circuz_phreak on 2007-09-11
Awesome, thanks man...made a backup and changed the titles to how I like, got rid of the extra kernal text along with the embedded xp text.  Any tips you can give me for formatting (to make it look pretty, center aligned maybe) along with anything else I could do to it?

---

### Post by rsambuca on 2007-09-11
You can change the font colours and add a background image if you like.  All kinds of little stuff you can do.

Just so you aren't surprised in the future, if there is a kernel update, grub will be updated automatically, so the ones you edited out will re-appear.  Kernel updates are not very frequent, though.

---

### Post by Clawinus on 2007-09-17
Lets assume, I make a mistake in editing the menulist, but I have saved a backup copy of it. Now starting Ubuntu failswith a black screen because of the error . How do I replace the menulist with its backup copy if I cannot get back into Ubuntu?

---

### Post by rsambuca on 2007-09-17
> **Clawinus said:**
> Lets assume, I make a mistake in editing the menulist, but I have saved a backup copy of it. Now starting Ubuntu failswith a black screen because of the error . How do I replace the menulist with its backup copy if I cannot get back into Ubuntu?

If by a black screen you mean a command line terminal, then you can simply copy the backup file over the non-functioning menu.lst```
sudo cp /boot/grub/nameofyourbackupfile /boot/grub/menu.lst
```The 'sudo' command gives you the permissions to execute the copy command, 'cp' is the copy command.

---

