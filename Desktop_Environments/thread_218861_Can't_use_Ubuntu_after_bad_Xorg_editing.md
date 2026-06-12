---
title: "Can't use Ubuntu after bad Xorg editing"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Diafel on 2006-07-19
I'm new to Linux and thanks to the users of Digg, have been persuaded to give Ubuntu, the user friendly operating system a try. The first problem I had was with Grub somehow completely ignoring my Windows XP install. I had to go through tens of threads on these forums looking for a fix just to be able to log into Windows again. Astounding.

My next problem involved the screen resolution. My laptop uses 1280x800 but Ubuntu (the Linux for human beings) is quite comically limited to 3 options, one of which (640 x 480) has never been used by a human since the year 2000. I manually edited the Xorg file so that it included my desired resolution. I assume after editing you would see the resolution in the dropdown box in "Screen Resolution" but this was not the case. 

Someone suggested using sudo dpkg-reconfigure xserver-xorg which goes through a truly insane amount of questions to help you configure your xorg settings. I used almost all the defaults and when asked about screen resolutions I selected mine (by the way there is absolutely no documentation or anything to suggest you would need to the spacebar to select anything... I really appreciated needing to search for something so simple). And of course now when I try to boot up it gives me some sort of error with the xorg file and I can't boot into Ubuntu. Though the thought of an official program completely ruining my install is quite comical, I'm beginning to suspect Ubuntu is not as user friendly as I was lead to believe.

 When I saved it indicated it created a backup of the xorg file, but I have no idea how I would access this and restore my system. Any help?

---

### Post by Ramses de Norre on 2006-07-19
It's not because you are a little unluckily with ubuntu that it's a parody..

When you are in ubuntu press ctrl-alt-F1 and do ```
ls /etc/X11
``` write down the output and post it here.

---

### Post by kinematic on 2006-07-19
so just because you have a problem it's a parody of an operating system created by a retarded monkey.....yet it works without a hitch for so many other people.
but it's okey...you just had to vent some stuff i guess,now go troll somewhere else.

---

### Post by matthew on 2006-07-19
> **Diafel said:**
> Though the thought of an official program completely ruining my install is quite comical, I'm beginning to suspect that Ubuntu is some sort of elaborate parody of an operating system, possibly created by some sort of mildly retarded monkey.Your post was great except for this unneded line. In the future, just keep it professional or at least polite. Thank you.

> **kinematic said:**
> so just because you have a problem it's a parody of an operating system created by a retarded monkey.....yet it works without a hitch for so many other people.
but it's okey...you just had to vent some stuff i guess,now go troll somewhere else.Your response was over the top. Next time just hit the "report post" button and notify the staff or just say nothing. Thank you.

Now, let's return this thread to the original topic and allow this guy to get some help.

---

### Post by goobers on 2006-07-19
> **Diafel said:**
> Though the thought of an official program completely ruining my install is quite comical, I'm beginning to suspect that Ubuntu is some sort of elaborate parody of an operating system, possibly created by some sort of mildly retarded monkey.

Its also quite comical that you'd come to the "mildly retarded monkey" community that helped create Ubuntu to ask for help...

---

### Post by philippe_carlo on 2006-07-19
Getting X to work can always be a bit tricky, independent of what distribution you use. Bear in mind that most hardware out there is created for Windows only and that a lot of volunteers are trying to make this Linux thing work for you and your hardware too, in many cases without any help of the hardware manufacturers. 

We will need some more information in order to help you out, though. Can you tell us which graphics card you are using? And maybe post the contents of your /etc/X11/Xorg.conf file?

---

### Post by matthew on 2006-07-19
> **goobers said:**
> Its also quite comical that you'd come to the "mildly retarded monkey" community that helped create Ubuntu to ask for help...Okay, everyone. Now, I realize you probably were writing this as I was posting the above, but now that all have had a chance to see the staff's perspective let's allow this thread to  continue on topic.

---

### Post by Diafel on 2006-07-19
Relax, I'm just kidding around. This whole experience has been such a pain I can't do anything but laugh.

I tried using the Recovery mode, something I assume is meant to work like the Windows safe mode, but the scrolling text simply stopped. 

When I boot Ubuntu it gives me 3 progressive error screens. Then it asks for my login and password on a black screen and after inputing those it prompts for (I think) Terminal code, like sudo gedit etc

I cannot post the xorg.conf because I cannot log into Ubuntu.

Graphics card is ATI Mobility X1300

---

### Post by Lunar_Lamp on 2006-07-19
I also use a 1280*800 resolution on my Acer Aspire 5024 laptop.  It can be a bit tricky to get a good graphics setup on this due to the ATI graphics card, but it's a lot easier than it used to be.

To get your old xorg.conf back:

You need to 'cd /etc/X11' (cd = change directory)
Then 'ls' (ls = list files and directories) - you should see a range of files.
Then 'rm xorg.conf' (rm = remove)
Then 'mv xorg.conf.[numbers here indicating time of backup] xorg.conf' (mv = move).

Then you need to restart x - this can be done by a reboot, hitting ctrl+alt+backspace when in x, or by typing 'startx'.

Now, to set up your graphics card properly you will need to know what graphics card you have.  If you are unsure, you can find out what card by typing: 'lspci' which will list all the pci devices in your laptop.  I'm not going to give an entire guide here on how-to setup your graphics card as there are a load around on the forums - but feel free to post back any problems :)

---

### Post by Ramses de Norre on 2006-07-19
You're in ubuntu when you get that terminal, you just don't have a graphical environment.
I suggest you enter all commands mentioned in this thread, write down the output and post it here. We need that info to determine what's wrong there.

EDIT: to see the contents of a file in terminal use the less command, so less /etc/X11/xorg.conf (mind the caps!)

---

### Post by Diafel on 2006-07-19
> **Lunar_Lamp said:**
> I also use a 1280*800 resolution on my Acer Aspire 5024 laptop.  It can be a bit tricky to get a good graphics setup on this due to the ATI graphics card, but it's a lot easier than it used to be.

To get your old xorg.conf back:

You need to 'cd /etc/X11' (cd = change directory)
Then 'ls' (ls = list files and directories) - you should see a range of files.
Then 'rm xorg.conf' (rm = remove)
Then 'mv xorg.conf.[numbers here indicating time of backup] xorg.conf' (mv = move).

Then you need to restart x - this can be done by a reboot, hitting ctrl+alt+backspace when in x, or by typing 'startx'.

Now, to set up your graphics card properly you will need to know what graphics card you have.  If you are unsure, you can find out what card by typing: 'lspci' which will list all the pci devices in your laptop.  I'm not going to give an entire guide here on how-to setup your graphics card as there are a load around on the forums - but feel free to post back any problems :)Tried all this, was going well but when I tried to remove the original xorg.conf it said I did not have permission. Hmmmm

---

### Post by goobers on 2006-07-19
you need to do 'sudo rm xorg.conf'

sudo will give you the access rights to remove it. just type in your password when prompted

---

### Post by Ramses de Norre on 2006-07-19
This will work better (and safer):
```
cd /etc/X11/
sudo mv xorg.conf xorg.conf.bak
ls|grep -i xorg.conf
sudo mv xorg.conf.[numbers here indicating time of backup] xorg.conf
```
Use the output of ls to determine which numbers to fill in.

I doubt this will work, if not post the output of the other suggested commands.

And if sudo asks a password you just enter your user password, you wont see any characters when you type but that's perfectly normal.

---

### Post by nicbink on 2006-07-19
> **Diafel said:**
> Tried all this, was going well but when I tried to remove the original xorg.conf it said I did not have permission. Hmmmm

the parent poster forgot to put "sudo" before the rm and mv command

this will give you temporary "admin" rights to do the needful.
-------------

i have a widescreen laptop running 1920x1200 (ati x1400) so it is possible to get yours working.


have you installed the FGLRX driver (ATI's offical driver)?

if you have then just run:

```
aticonfig --initial
```

that should regenerate an xorg.conf

if you have not installed that driver you will most likely need to... 

```
sudo apt-get install xorg-driver-fglrx
```

this should install all the dependencies and you can run the aticonfig line from above afterwards just to make sure it's setup.

if all else fails just reinstall ubuntu and keep your home partition (assuming you have a separate partition for it)


EDIT::i forgot to mention that you have to have the universe packages enabled to install the xorg-driver-fglrx --- i'll let someone else fill you in on the command prompt method of doing that, i gotta take off

---

### Post by Ramses de Norre on 2006-07-19
xorg-driver-fglrx is in the restricted repo which is enabled by default.

---

### Post by Diafel on 2006-07-19
Used the recent advice and as I'm typing this from Ubuntu at the moment, it obviously worked. Thanks to everyone for the help! I will try and install the xorg-driver-fglrx and see if that fixes my resolution problem.

---

