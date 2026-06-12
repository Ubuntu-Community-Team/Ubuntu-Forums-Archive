---
title: "Can't set up my Canon PIXMA MP600 printer"
date: 2007-02-27
forum: Desktop Environments
---

### Post by mjg123 on 2007-02-27
Hi.

  I'd really like to install Ubuntu on my laptop, but When I try it out via the livecd (v6.06) I find a problem.  The printer itself is connected to a Windows XP machine.  When I run gnome-cups-add (the add printer wizard) I can select Windows Share (SMB), then my XP machine and the printer itself appear in the dropdown lists ok.  Copying the advice from [http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600) I tried to install using the canonip4200.ppd.  Everything looks as if it works, but the printer is not installed :(

  Actually there is this output from gnome-cups-add:
** (gnome-cups-add:8296): WARNING **: authenticating with MSHOME for IPC$
Selected ppd file = custom/canonip4200.ppd

** (gnome-cups-add:8296): WARNING **: IPP request failed with status 1280

  I don't know what to do about that.  I tried what it says at [http://ubuntuforums.org/showthread.php?t=258124&page=2&highlight=the+cups+server+could+contacted](http://ubuntuforums.org/showthread.php?t=258124&page=2&highlight=the+cups+server+could+contacted) i.e. removing, purging and installing cups.  It didn't help.

Like I said, I'm running from the livecd, if that makes any difference.  I'd love to switch to Ubuntu completely, but not being able to use my printer would be a dealbreaker.  Please help?

---

### Post by watersevenub on 2007-04-17
It seems that Canon released MP600 Linux drivers for Fedora. Have a look in:

[http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx)

In Ubuntu Edgy Eft, I've used "alien" to convert the RPMs to DEB and then "dpkg -i" to install the Debian files. Then I added a new printer with the 2.70 MP600 driver. However, for some reason the printer does not respond. I'm almost sure it will work in Fedora. Why wouldn't it work in Ubuntu?

---

### Post by easy_target on 2007-04-22
I am having exactly the same problem. I installed the drivers from Canon and converted the rpm's using alien. I didn't see any error messages during installation of the packages. I went on to System>Administration>Printing and the printer it was detected in the first dialogue. Going forward I couldn't see the model in the drivers list  and after a little search I installed the ppd located at /usr/share/cups/model/ which showed the driver as being named MP600-Ver.2.70. Installation went on without a hiccup after that.
The problem is that when I try to print anything the only thing that happens is the printer LCD display coming up. No error message, no nothing. Could a kind soul more savvy than I (not quite difficult considering I am a newbie) try the new drivers and see if they can get them working? 

Thanks in advance!

---

### Post by easy_target on 2007-04-25
Okay, I came up with a partial solution. I have a version of Feisty that is pure and used the drivers that come with it for the IP4200. It seems to work okay, but I still have no scanning capabilities. 
It is really strange that we have to use alternative drivers when in the australian canon page you have drivers for both the scanner and the printer. 
My plea goes to all those brilliant people in the forums capable of examining the original canon rpm driver and finding out why it wouldn't work. 

Thanks folks!

---

### Post by easy_target on 2007-04-28
NOT ALL IS LOST!

I've just downloaded the scanner drivers from the Canon Australian website and it works!!!
Here is what I did to get them working in Feisty:

Download  the drivers for the MP600 at [http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx)

Select Driver Downloads and select "MP600 Scanner Driver Ver. 1.00 (Linux)"
Scroll down the page and Download the files:
scangearmp-common-1.00-1.i386.rpm 
scangearmp-mp600-1.00-1.i386.rpm

CD to the directory where the files are. If you downloaded them to your Desktop, then:

```
cd Desktop
```

then do the following:

```
sudo apt-get install alien libpng3

sudo alien scangearmp-common-1.00-1.i386.rpm

sudo alien scangearmp-mp600-1.00-1.i386.rpm

sudo dpkg -i scangearmp-common_1.00-2_i386.deb

sudo dpkg -i scangearmp-mp600_1.00-2_i386.deb
```

After that, to run the scanning program just type on console:

```
scangearmp
```

I hope this helps!!! :biggrin:

---

### Post by mgmiller on 2007-04-30
Thank you easy-target.  I have installed all per your instructions, but I can only get it to run as root.  scangearmp gives me: Cannot find Canon MFP scanner device.  IF I run it a gksudo scangearmp or sudo scangearmp, it works, but everything it saves is saved as belonging to root.  I have tried changing the permissions of the executable file /usr/local/bin/scangearmp and tried uninstalling both packages after changing the ownership to me and reinstalling, but all to no avail.  It only runs as root.  Do you have any thoughts?

---

### Post by mgmiller on 2007-04-30
I actually figured it out!!! 
I am running this on a clean install of feisty.

 The following instructions are a modification from the following page:
[http://gentoo-wiki.com/HOWTO_Installing_USB_Scanner#Configuration]("http://gentoo-wiki.com/HOWTO_Installing_USB_Scanner#Configuration")

UDEV

When scangearmp works successfully under root and not as user, it normally means that you have a permissions problem. The default permission rules for udev currently set scanners to belong to the root group and not to the scanner group. The most elegant method to solve this is to write a custom permissions rule and place it into /etc/udev/rules.d. This is achieved as follows:

Udev processes the rules files in /etc/udev/rules.d in lexical order, so your local settings should be stored in a file lexically ahead of the default 50-udev.rules so that they are processed first. The name of your new file must end in .rules, otherwise udev will ignore it.

create a new entry:
```
gksudo gedit /etc/udev/rules.d/10-udev.rules
```

enter the following in the new file:
```
# scanner devices
KERNEL=="sg0", GROUP="scanner"
```

Assuming hotplug is installed and working, simply unplug/replug in your scanner so that udev updates your permissions. Users in the scanner group can now use scangearmp.

That is all I needed to get it to work.  The following info is from the same page, but I have not tried it.

As another alternative USB users can also try the following runscript. However it will need to be restarted every time you remove/replug your scanner.

# touch /etc/init.d/usbscanner
# chmod +x /etc/init.d/usbscanner
# nano /etc/init.d/usbscanner

Edit:
I just did another install of the scanner driver on another fresh install Of feisty, but for some reason, the program failed to load and gave the message that it could not find a shared library file called libpng.so.3 or similar ( I am doing this from memory, but if you have the problem, you will see the exact file name in your terminal.  

To fix it, all I did was go to /usr/lib and create a link to the file named libpng12.so.0.15.0  I then named the link libpng.so.3

This fixed the problem.  You will need to do this with gksudo nautilus or you won't have permission to create or rename the link.  Of course, you could also do this with a terminal command, but I did it this way.

EDIT again:
I just figured out why I got the "can't find missing file" message.  I forgot to:
```
sudo apt-get install libpng3
```

DOH! ](*,)

My not so elegant cheating solution of creating the symlink worked because I believe the file I linked to contains all the data in libpng3 plus more.  I think it may have replaced it.  Since it still works fine, I will leave it that way for now.

---

### Post by AvixK7 on 2007-06-19
My mp600 works fine using the mp500 drivers over SMB :) test page printed perfectly as far as I can see :)

---

### Post by lerrup on 2007-06-19
> **easy_target said:**
> NOT ALL IS LOST!

I've just downloaded the scanner drivers from the Canon Australian website and it works!!!
Here is what I did to get them working in Feisty:

Download  the drivers for the MP600 at [http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx](http://www.canon.com.au/products/all_in_one_printers/all_in_one_printers/mp600_support.aspx)

Select Driver Downloads and select "MP600 Scanner Driver Ver. 1.00 (Linux)"
Scroll down the page and Download the files:
scangearmp-common-1.00-1.i386.rpm 
scangearmp-mp600-1.00-1.i386.rpm



Does anyone have a copy of these that I could have - the Oz Canon site seems to be down at the moment :(

But the Singapore one is up and running! :)

[http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio&country=SG](http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio&country=SG)

thanks.

---

### Post by wcj786 on 2007-07-26
> **mgmiller said:**
> I actually figured it out!!! 
I am running this on a clean install of feisty.

 The following instructions are a modification from the following page:
[http://gentoo-wiki.com/HOWTO_Installing_USB_Scanner#Configuration]("http://gentoo-wiki.com/HOWTO_Installing_USB_Scanner#Configuration")

UDEV

When scangearmp works successfully under root and not as user, it normally means that you have a permissions problem. The default permission rules for udev currently set scanners to belong to the root group and not to the scanner group. The most elegant method to solve this is to write a custom permissions rule and place it into /etc/udev/rules.d. This is achieved as follows:

Udev processes the rules files in /etc/udev/rules.d in lexical order, so your local settings should be stored in a file lexically ahead of the default 50-udev.rules so that they are processed first. The name of your new file must end in .rules, otherwise udev will ignore it.

create a new entry:
```
gksudo gedit /etc/udev/rules.d/10-udev.rules
```

enter the following in the new file:
```
# scanner devices
KERNEL=="sg0", GROUP="scanner"
```

Assuming hotplug is installed and working, simply unplug/replug in your scanner so that udev updates your permissions. Users in the scanner group can now use scangearmp.

That is all I needed to get it to work.  The following info is from the same page, but I have not tried it.

As another alternative USB users can also try the following runscript. However it will need to be restarted every time you remove/replug your scanner.

# touch /etc/init.d/usbscanner
# chmod +x /etc/init.d/usbscanner
# nano /etc/init.d/usbscanner

Edit:
I just did another install of the scanner driver on another fresh install Of feisty, but for some reason, the program failed to load and gave the message that it could not find a shared library file called libpng.so.3 or similar ( I am doing this from memory, but if you have the problem, you will see the exact file name in your terminal.  

To fix it, all I did was go to /usr/lib and create a link to the file named libpng12.so.0.15.0  I then named the link libpng.so.3

This fixed the problem.  You will need to do this with gksudo nautilus or you won't have permission to create or rename the link.  Of course, you could also do this with a terminal command, but I did it this way.

I attempted to follow these instructions, but ran into a problem.  I am currently on Feisty Fox and my /etc/udev/rules.d/ directory does not have any file resembling 50-udev.rules.  Here are th entries into the rules.d directory:

00-init.rules                      65-persistent-input.rules
025_logitechmouse.rules            65-persistent-storage.rules
05-options.rules                   80-canon_mfp.rules
20-names.rules                     80-programs.rules
25-dmsetup.rules                   85-alsa.rules
25-iftab.rules                     85-brltty.rules
30-cdrom_id.rules                  85-hdparm.rules
40-permissions.rules               85-hplj10xx.rules
45-hplip.rules                     85-hwclock.rules
45-libgphoto2.rules                85-ifupdown.rules
45-libnjb.rules                    85-pcmcia.rules
45-libsane.rules                   90-modprobe.rules
50-xserver-xorg-input-wacom.rules  95-hal.rules
60-symlinks.rules                  99-udevmonitor.rules
65-libmtp.rules

I created a new file 10-permitusers.rules and copied the 40-premissions.rules into it, then edited the folder just like it said to do, but I got nothing.

Also, when I look into System Settings, I do not even see a scanner allocated.  When looking into Adept for HOTPLUG, I do not see it available.  I already installed the printer, and it is working with the MP600 drivers, but during that, I created a link named libpng.so.3 in /usr/lib/, so if I modify that, won't it affect the printer?

I am at a loss as to what to do.  I am a born again n00b.  I worked in Unix for a couple of years, but that was twenty years ago.  I no longer understand it, so if anybody gets this working correctly, can you type out the commands one by one, so that I can easily understand how to do it?:lolflag:

---

### Post by mgmiller on 2007-07-26
> I created a new file 10-permitusers.rules and copied the 40-premissions.rules into it, then edited the folder just like it said to do, but I got nothing.

Try to put everything back the way it was.  You did not follow the instructions I gave.

You are  creating a new file in the /etc/udev/rules.d/ folder called "10-udev.rules".  Use the command exactly as I wrote it to create this file.

```
gksudo gedit /etc/udev/rules.d/10-udev.rules
```

You then paste the following into the new empty file:

```
# scanner devices
KERNEL=="sg0", GROUP="scanner"
```

Do not put anything else into this new file.  Just save it as is.


That is all you need to do.

Unplug the USB cable for the MP600 and plug it back in.

Scangearamp should now work as a regular user.

If the program fails to load and gives the message that it could not find a shared library file called libpng.so.3 or similar ( I am doing this from memory, but if you have the problem, you will see the exact file name in your terminal.)

To fix it, all I did was go to /usr/lib and create a link to the file named libpng12.so.0.15.0 I then named the link libpng.so.3

This fixed the problem. You will need to do this with ```
gksudo nautilus
``` or you won't have permission to create or rename the link. Of course, you could also do this with a terminal command, but I did it this way.

EDIT:

I just reread the thread and I realize I forgot to:
```
sudo apt-get install libpng3
```

That is why I got the error message that required the link, as it is still working fine the way I did it, I will leave it like that for now.  I believe the library I linked to is a newer version that contains all the data in libpng3 plus more things.

---

### Post by wcj786 on 2007-07-27
I am using Kubuntu and do not have Nautilus on my system.  I did find a website that had info on how to install a scanner in Dapper, [http://home.arcor.de/wittawat/pixma/ubuntu-howto.html]("http://home.arcor.de/wittawat/pixma/ubuntu-howto.html") , but after trying this, it is still not working.  I did modify these instructions slightly, due to the scanner being a MP600, not MP150.  (The site states that the MP600 also works using the 0.13.0 backend.  I edited the 45-libsane.rules file with **sudo vi /etc/udev/rules.d/45-libsane.rules**, then added the following:

# PIXMA MP600
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1718", MODE="664", GROUP="scanner"

That should have identified the correct scanner ID, based on previous info on that webpage.  Also, the Canon MP150 was already built in that file.  Regardless, the laptop still does not recognize the scanner.

I would be more than satisfied to try your scenario, but as I mentioned in an earlier post, the  link that you used to point to libpng2.so.0.15.0 (libpng3.so) is already in the /usr/lib directory.  It was built when I got the printer to work.

I am confused about this, as I am a n00b, with very little Unix/Linux experience.  I don't want to break my printer to get the scanner going.  I am just anxious that if I do what you suggest, it would affect my printer.  Also, I do not know how to set up links, at this point.

---

### Post by wcj786 on 2007-07-28
I now have it working.  I found a web page that shows how to get it to work in Dapper, [**here**]("http://home.arcor.de/wittawat/pixma/ubuntu-howto.html"), but slightly modified, due to the MP600 working on the 0.13.0 back-end.  Here are the steps I took to get it to work.

1)  Downloaded the drivers to Desktop

2) cd Desktop

3) sudo apt-get install alien libpng3
    sudo alien scangearmp-common-1.00-1.i386.rpm
    sudo alien scangearmp-mp600-1.00-1.i386.rpm
    sudo dpkg -i scangearmp-common_1.00-2_i386.deb
    sudo dpkg -i scangearmp-mp600_1.00-2_i386.deb

At this point, in an earlier post, Easy_Target stated that you should be able to run **scangearmp**.  This did not work for me.  That is not to say he was wrong, it just would not work for me, so I then did the following:

4) sudo apt-get install build-essential
    wget [http://home.arcor.de/wittawat/pixma/mp150-0.13.0.tar.bz2](http://home.arcor.de/wittawat/pixma/mp150-0.13.0.tar.bz2) (modification to web page)
    sudo tar xjf mp150-0.13.0.tar.bz2 -C /usr/src (modification to web page)
    cd /usr/src/mp150-0.13.0/ (modification to web page)
    sudo make
    sudo ./scan -L

5) sudo cp libsane-pixma.so /usr/lib/sane/libsane-pixma.so.0.13.0
    sudo ln -s /usr/lib/sane/libsane-pixma.so.0.13.0 /usr/lib/sane/libsane-pixma.so.1
    (The web page states to modify **dll.conf**, but I found that **pixma** was already in the file.)

6) sudo vi /etc/udev/rules.d/45-libsane.rules  (I use **vim** as my editor.)

At this point, I added the following lines in this file:

# Pixma MP600
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="1718", MODE="664", GROUP="scanner"

7) sudo /etc/init.d/udev restart

This is the end of the directions from that webpage, but at this point, the scanner still did not work for me (and **scangearmp** was not showing up in my K Menu under Graphics).

So, I started looking in the** /etc/sane.d/dll.d** folder to see if there was anything in there that might be causing the problem.  I identified that the only file in that folder was **hplip**.  So , I copied that file, then modified it, naming the new file **pixmalip**.  That file has the following in it:

# dll.conf snippet for pixmalip
#

canonaio

In the **sane.d** directory, I also modified the **canon.conf** file to look like:

#canon.conf
# Canon Pixma MP600  (This was not there originally.)
usb 0x04a9 0x1718      (This was not there originally.)
#/dev/scanner             (This was not commented out originally.)
#/dev/sg0

After doing the above steps, I got the **scangearmp** program to run and scan for me.  I am sure there may be numerous steps that I took, that might not necessarily be necessary, so if somebody knowledgeable wants to take a look at these steps to identify which are valid and which aren't, it might help quite a few people.

---

### Post by wcj786 on 2007-07-28
There is one last problem I am having with the scanner.  I can run SCANGEARMP from a terminal window without having to use the SUDO command, but when I launch it from the K Menu, it states that it can not find a scanner device.  If anybody can help me on this, I would appreciate it.

Also, MGMILLER, thank you for your advice.  I appreciate you taking the time to help out a n00b, even if I was unable to follow your advice (my uncertainty about messing up my printer to get that scanner working).  It is the people who provide their time and knowledge that make me want to stay with Linux (and away from the other guy :evil:)

---

### Post by mgmiller on 2007-07-28
wcj786:

Glad to hear you got it working.  This community can be very helpful.  I know I learned a lot from it and I try to give back where I can.

I didn't know you were running Kubuntu.  Apparently there are enough differences between Ubuntu and Kubuntu that I and Easy_Target couldn't directly help you, but it looks like we at least pointed you in the right direction.  Look at how much you learned getting the scanner to work.  Anyone else reading this thread can now benefit from your experience.

> I can run SCANGEARMP from a terminal window without having to use the SUDO command, but when I launch it from the K Menu, it states that it can not find a scanner device.

This may be one of those kde specific things again.  In the Gnome menu system, commands run from the menu execute just the same as from terminal.   How did the entry to your K Menu get created?  If it was done automatically by Kubuntu, then take a look at the actual command that was created and change it if need be to match what works in terminal.  Or possibly, change it to give the full path to the scangearamp executable.  Also, watch your case, remember, Linux is case sensitive on all commands.  SCANGEARAMP is not the same as scangearamp.

I don't know how to edit the menus in Kubuntu.  In Ubuntu/Gnome you would right click the Applications entry in the top panel and select Edit Menus.  You could then navigate to the menu entry and right click it and modify it to whatever you want.

I am sure there must be a K Menu editor somewhere as Kde lets you configure way more stuff than Gnome does.


Wheee! Isn't this fun?:lolflag:

---

### Post by wcj786 on 2007-07-28
Whoops, I did not correctly identify the scanner utility in the K Menu.  I saw a program in the Graphics section of the menu and assumed that it was **scangearmp**.  Instead, it was Xsane, which did not recognize the scanner.

It is possible to right click on the K Menu button and select Menu Editor.  Once that is done, go to the place you want to install the new program, then expand the directory.  Right click on the Directory name (in my case, I put it in Graphics) and add a new entry.

Once the entry is added, left click on the entry.  This will bring up the info for it.  Add comments to describe the program and then the command to run the program.

Go to File, select Save and the new entry is added.  This is how it worked for me and I was able to get **scangearmp** in the K Menu and it works.

---

### Post by mgmiller on 2007-07-28
Excellent news!  Now that you have discovered the menu editor, you can pop back in there and remove the check mark next to xsane.  This will not uninstall it, but will make in not display in the kmenu so you don't have to worry about confusing it again.

See?  I told you this is fun.:D

---

