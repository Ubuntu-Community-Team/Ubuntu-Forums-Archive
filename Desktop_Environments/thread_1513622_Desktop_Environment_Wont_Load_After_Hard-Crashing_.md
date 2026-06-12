---
title: "Desktop Environment Wont Load After Hard-Crashing During Software Updates"
date: 2010-06-19
forum: Desktop Environments
---

### Post by printf() on 2010-06-19
During a software update the machine froze for a long time, I had no choice but to hard-crash (hold the power button to shutdown) starting up again I can get to the login screen and log in but there is no desktop environment visible, just a mouse pointer (which can be moved about) on a blank screen.

I'm using Karmic Koala with Gnome (I am relatively new to Linux, I am essentially using the default package)

---

### Post by printf() on 2010-06-20
Can anyone offer any suggestions?

Is it possible to re-install the desktop environment from the command line in recovery mode?

I'm looking for a solution other than wiping the partition as I want to keep my files.

Any suggestions would be appreciated.

---

### Post by JustinR on 2010-06-20
On your login screen when you click your username under Sessions on the bottom taskbar does it list any desktop environment? If not go to a terminal (CTRL + ALT + F1) and change your directory into /usr/share/xsessions. See if gnome.desktop is in the folder. If it is, type "nano gnome.desktop" and if all you see is gibberish delete gnome.desktop and use nano to make a new file in the same directory with these contents:

```

[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session
TryExec=gnome-session
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-2.0

```

I can clarify anything if you need help! I just recently went through this problem and it was very frustrating but it was a relatively easy fix!

Good Luck!

---

### Post by printf() on 2010-06-20
Thank you for your help.

In the log-in screen under sessions are the options gnome, failsafe gnome and xterm. The only one of which that actually works is xterm.

I checked the contents of gnome.desktop with nano and it is exactly as you have typed.

A couple of things I should have mentioned before, when the log-in screen first loads an infomation box appears for about 5 seconds saying: -

[I]Install Problem!
The configuration defaults for GNOME Power Manager have not been installed correctly.
Please contact your computer administrator.
[/I]

Also, when I open a terminal there is a note that appears saying that there are 32 updates ready to be installed. Perhaps I need to install these because crashing during updates is what caused the problem in the first place. Can this be done from the terminal?

I appreciate the help, thank you.

---

### Post by MooPi on 2010-06-20
Try this  while in xterm session: ```
sudo dpkg --configure -a
```

---

### Post by JustinR on 2010-06-20
Edit: I suggest using MooPi's solution first - I never would have thought of that!

Oh okay I've also been through this problem!;)

The only option I suggest would be uninstalling gnome - this will uninstall your default ubuntu programs and everything else GNOME but will keep your settings without having to reinstall.

This code removes gnome

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Although the link says pure KDE copy the code for removing Ubuntu Desktop(GNOME). This will remove GNOME, and then do "sudo apt-get install ubuntu-desktop. This should reset any problem updates and should download the latest updates.

I suggest to use this only as a last resort though because depending on your internet connection it could take a long time to reinstall Ubuntu-Desktop (GNOME).

---

### Post by printf() on 2010-06-20
Thank you.

I tried MooPi's suggestion and got the following response: -

*dpkg: parse error, in file 'var/lib/dpkg/updates/0148' near line 0: MSDOS EOF (^Z) in field name `'*

I'm sorry I may not be able to post in this thread until tomorrow as it's nearly 4am here, if you can offer any more help I will read it and try whatever you suggest.

Thank you both for helping a random stranger on the internet.

---

### Post by printf() on 2010-06-21
> **JustinR said:**
> Edit: I suggest using MooPi's solution first - I never would have thought of that!

Oh okay I've also been through this problem!;)

The only option I suggest would be uninstalling gnome - this will uninstall your default ubuntu programs and everything else GNOME but will keep your settings without having to reinstall.

This code removes gnome

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Although the link says pure KDE copy the code for removing Ubuntu Desktop(GNOME). This will remove GNOME, and then do "sudo apt-get install ubuntu-desktop. This should reset any problem updates and should download the latest updates.

I suggest to use this only as a last resort though because depending on your internet connection it could take a long time to reinstall Ubuntu-Desktop (GNOME).

Thanks for the advice, one thing to be aware of though is that is a lot of code and as I have no GUI I can't copy and paste from linux. I see only 4 options here: -

1. manually write the whole lot down and type it out
2. save the script to a text file on a memory stick and try to find a way to use nano to copy and paste the commands into the terminal. What is the linux equivalent of a batch file? that would be easier
3. the same as 2 put store the file somewhere on the windows partition, mount it in linux then get the file from there
4. find an easier command to do this, is there an uninstall/reinstall command that will do the job with these broken packages? I've tried a few that I've found on this forum with no luck.

any other suggestions?

---

### Post by JustinR on 2010-06-21
Yes it is a lot of code but it definitely will remove GNOME successfully without error.

Open your preferred text editor, then on the first line type "#!/bin/bash" (without the quotes) then just copy the code on the line below it. Save it as a .SH file. Then once you get to Ubuntu's terminal mount the windows drive or USB flash drive you will be using as the location for the script. Change the directory of your flash drive or windows drive to where the script is located then type the command "chmod +x 775 SCRIPT.sh" (without quotes). Then type "./SCRIPT.SH"( without quotes). This will execute the commands.

[COLOR="Red"]REMEMBER[/COLOR] remove "&& apt-get install kubuntu-desktop" (not exact wording I believe) from the end of the command! After the removal of GNOME is done is type "sudo apt-get install ubuntu-desktop".

Good Luck!

---

### Post by printf() on 2010-06-21
When I tried "chmod +x 775 killgnome.sh" it gave the following error: -

"chmod cannot access '775': No such file or directory"

I tried it without the "775" and it gave no error. However when I typed "./killgnome.sh" it gave the error: -

"bash: ./killgnome.sh: /bin/bash^M: bad interpreter: No such file or directory"

All of this was done from within the mounted directory containing the .sh file.

It's just occured to me, doesn't "./" indicate from the root, should I have just typed killgnome.sh? I will try this when I next reboot.

Thank you again.

---

### Post by JustinR on 2010-06-21
Well if It Chmod-ed correctly go into the directory of your script (you should already be there). Don't type sudo, all you need to type is:

./KillGNOME.sh

The first dot means current directory.

---

### Post by printf() on 2010-06-22
I'm still getting the same errors as before so I tried "bash killgnome.sh", I think the script did run because I was prompted for a password, then it produced the error: -

*E: dpkg was interrupted, you must manually run  sudo dpkg --configure -a to correct the problem.*

---

### Post by printf() on 2010-06-22
WHOAH!

I just used xterm to delete the problem updates file. I then ran the script and it appears to have worked. I then typed  "sudo apt-get install ubuntu-desktop" and that seemed to work far too quickly, about 5-10 seconds. I restarted and now when I start ubuntu it goes into GNU GRUB, with no options just a command line "sh:grub>".

I am WELL out of my depth here and really need some help.

I assume my files are still on that partition, I don't even have the option to transfer them to the windows partition anymore.

Have I just dug a huge hole for myself?

---

### Post by JustinR on 2010-06-23
What do you mean you deleted update files?

---

### Post by printf() on 2010-06-23
the file "0148" located here: "var/lib/dpkg/updates/0148", it was the one shown in all the error messages. I actually copied it to my windows partition for "safety" thinking I may be able to repair any errors later. Ironically this is now pretty much all I have left of my linux partition.

This really sucks

---

### Post by JustinR on 2010-06-24
So have you tried to see what files are left on the partition? You can use a live cd/usb to see and we can go from there.

---

### Post by printf() on 2010-06-24
I was thinking the same thing, I can't do it today because I have no recordable CDs and my computer wont consider USB as part of its boot sequence.

I'll try to get it done tomorrow. If I can get my files out I'm happy to just format the partition and start over with lucid instead.

Thank you for continuing to come back to  this thread I'm probably going to need more help at some point.

---

### Post by printf() on 2010-07-03
I'm sorry about this, I've just burned a copy of lucid onto a cd on another computer (as mine can't write CDs) and just remembered that my CD drive barely works and for this reason I actually originally installed ubuntu using the windows installer so I don't think I ever had a separate partition in the first place. My CD drive is struggling to work for long enough to boot lucid and my computer wont allow USB as part of the boot sequence.

If I installed using the windows installer how can I acess the files?

Is there a free open source partition management program that will work under windows?

Thank you.

---

