---
title: "How do I use a Windows Networked Printer from Ubuntu?"
date: 2008-04-03
forum: Desktop Environments
---

### Post by Grrruff on 2008-04-03
I am using Ubuntu ver 7.10 as a workstation.  I plugged it into my Windows Network and have some troubles seeing the network locations as well as printing.

I've tried to use the printer setup wizard numerous times

When I select 'New Printer'  I get the windows network printer list and the wizard allows me to step through setting up a kyocera Mita KM-4035 printer.

The test page works intermittently.  Printing any document fails.  Sometimes nothing happens Sometimes I get the garbage characters printed using the wrong input tray and output to the wrong tray as well.

I posted this in the beginners section but it seemed like only begginers responded.  No help there.

Anyone tackled this before?

~T

---

### Post by warp99 on 2008-04-03
You may have to update the PPD driver. The current driver is available here:

[http://openprinting.org/download/PPD/Kyocera/en/Kyocera_Mita_KM-4035_en.ppd](http://openprinting.org/download/PPD/Kyocera/en/Kyocera_Mita_KM-4035_en.ppd)

I believe the ppd driver is located in '/usr/share/cups/model/'. So you need to replace the file with the one from openprinting.org.

Edit:

You're setting this printer as a Jet Direct printer on port 9100, correct?

---

### Post by Grrruff on 2008-04-04
Thanks for the reply.  

The target folder you mention is empty.

I copied the link to a text file and opened it from the Ubuntu PC.
Saved the file to the desktop. 

 The OS will not allow me to copy the .PPD file to the target folder...???

How do I gain this permission?

~T

---

### Post by Kemono on 2008-04-04
> **Grrruff said:**
> Thanks for the reply.  

The target folder you mention is empty.

I copied the link to a text file and opened it from the Ubuntu PC.
Saved the file to the desktop. 

 The OS will not allow me to copy the .PPD file to the target folder...???

How do I gain this permission?

~T

Type **sudo nautilus** in a terminal. This will open a browser with root permissions. Navigate to the folder.

---

### Post by Grrruff on 2008-04-04
Thanks Warp99, Kemono

That did it.  I pointed the printer setup wizard to use the PPD in the \usr\share\cups\model folder.  It prints correctly now.  :)

I guess it will take some time for me to glom onto the command line interface.  I just assumed that since we have a graphical interface that the tools to allow global permissions would be available within it.

*sigh*  

The command line does feel a bit like old MSDOS.  :/

Shall I start another thread about my Windows Network Interface problems or can we just continue in this one?

~T

---

### Post by Kemono on 2008-04-04
I'm a GNU/Linux user for about 2 months now and was a Windows XP user before that (although I'm still dual-booting). I've never typed a line in the command line before, but when I switched to Ubuntu I started learning _fast_. Besides, sometimes it's a lot faster from the terminal.

About the graphical interface: I heard (or read) that the new Nautilus in Hardy Heron will prompt for password if you try to modify, paste, move etc. something in the system.

I guess you could start a new thread if it's not related to your printer. Do search for a similar problem in the forums before you post though.

---

### Post by warp99 on 2008-04-04
> **Grrruff said:**
> Thanks for the reply.  

The target folder you mention is empty.

I copied the link to a text file and opened it from the Ubuntu PC.
Saved the file to the desktop. 

 The OS will not allow me to copy the .PPD file to the target folder...???

How do I gain this permission?

~T

We need to do more than just copy the file since the original file is not there. Open a terminal and do the following:

```
sudo cp ~/Desktop/Kyocera_Mita_KM-4035_en.ppd /usr/share/cups/model/
```

then we need to change the permissions on the file:

```
cd /usr/share/cups/model/ && sudo chmod 444 Kyocera_Mita_KM-4035_en.ppd
```

then change the groups ownership as follows:

```
sudo chown root:lpadmin Kyocera_Mita_KM-4035_en.ppd 
```

Now the driver is ready to receive postscript from the printer.

---

### Post by warp99 on 2008-04-04
> **Grrruff said:**
> Thanks Warp99, Kemono

That did it.  I pointed the printer setup wizard to use the PPD in the \usr\share\cups\model folder.  It prints correctly now.  :)

I guess it will take some time for me to glom onto the command line interface.  I just assumed that since we have a graphical interface that the tools to allow global permissions would be available within it.

*sigh*  

The command line does feel a bit like old MSDOS.  :/
~T

Some operations using the command line interface (CLI) are faster why others using the desktop GUI are faster. There are shortcuts to the CLI that can make things much easier, such as these little tidbits:

While in the terminal if you press the up arrow you can scroll through the last 100 commands you entered. Make a mistake with your command string. Press the up key, the last command string you entered pops up on the prompt, make your changes, press enter again.If you type a command but only remember the first few letters press the tab key twice and a list of commands beginning with those few letters will appear. You can also type most of the letters of a command press the tab key and the remaining letters will be there on the prompt.If you start to type the name of a file or a directory press the tab key once and the remaining name of the file will appear at the prompt. If several files exist with the first few letters press the tab key twice and a list naming all the files beginning with those letters in that directory will appear. Let's say you want  to change to the directory /usr/share/cups/model. You would just type cd /u (tab) sha (tab) cu (tab) mod (tab) and the prompt would read 'cd /usr/share/cups/model'.

Once you master some of these shortcuts the command line becomes lighting fast for most operations. How can I copy 3,000 mp3 files beginning with the letter 'y' and ending with the number 3?

```
cp y*3.mp3 /target_directory
```

How long would that take with GUI tools? By the time someone opens the file dialog box for searching I've already executed the copy process and I'm on to something else. You can use the CLI or the GUI if you like since you have total control of the OS. Linux is all about choice, and choice my friend is very good. :guitar:

---

