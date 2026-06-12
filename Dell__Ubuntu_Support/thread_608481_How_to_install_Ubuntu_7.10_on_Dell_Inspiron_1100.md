---
title: "How to install Ubuntu 7.10 on Dell Inspiron 1100"
date: 2007-11-10
forum: Dell  Ubuntu Support
---

### Post by RedDawg on 2007-11-10
Many people have encountered problems installing Ubuntu 7.10 (Gutsy) on laptops with an Intel 82845G/GL integrated display adapter, such as the Dell Inspiron 1100. The installation is unable to detect the Intel 845GL display adapter and defaults to the "VESA" driver. Manually selecting the correct display adapter or continuing the installation using the "VESA" driver causes Ubuntu's setup to lockup.

**_How to install Ubuntu 7.10 (Gutsy) on a Dell Inspiron 1100_**

**Change Video Memory in BIOS setup:**

[LIST=1]
[*]Make sure your Dell Inspiron 1100 notebook has been upgraded to the A32 BIOS. 
[*]When you start your computer, hit F2 to enter Setup. 
[*]Press Alt-P (Turn the page) until you get to the page with the video memory. 
[*]Change the video memory from 1MB to 8MB. 
[*]Reboot
[/LIST]
**Run Ubuntu 7.10 Setup from CD:**

[LIST=1]
[*]Run Ubuntu Setup in "Safe Graphic" mode. 
[*]When Ubuntu Live finishes loading, open a "Terminal" window. 
[*]Type "sudo su" to become root in the terminal window. 
[*]Changed directory into /etc/X11 by typing: 

# cd  /etc/X11

[*]Edit "xorg.conf" using "vi" editor and locate the Section called "Device". 
[*]Change the Driver from "VESA" to "i810":

From:

Section "Device"
Identifier "Generic Video Card"
Driver "VESA"
BusID "PCI:0:2:0"

To:

Section "Device"
Identifier "Generic Video Card"
Driver "i810"
BusID "PCI:0:2:0" 

[/LIST]
**Perform Live Install Now:**

[LIST=1]
[*]Double click on the "Install" icon on the Ubuntu Live Desktop. 
[*]Follow the normal install procedure. When you are done, you will have a fully functional Ubuntu 7.10 Linux OS on your Dell Inspiron 1100 notebook.
[/LIST]
Hope this helps. :)

---

### Post by 5399771 on 2007-11-16
RedDawg,

Thank you. Your guide helped me out from my morning frustration. Once again I am amazed at how the Ubuntu community is so  helpfully specific.  

:)

---

### Post by gary8us on 2007-11-18
Hi:

This thread reflects my situation exactly -- and I'm still stumped. RedDawg: when I get to your step #4, this is where I can go no further.  For some reason, I can't get down to the field where I'd change the vidoe memory from 1Mb to 8 -- all I can seem to do on this page is change the time.  Any ideas?

thanks in advance.
g

---

### Post by DMBrazil on 2007-11-22
> **gary8us said:**
> Hi:

This thread reflects my situation exactly -- and I'm still stumped. RedDawg: when I get to your step #4, this is where I can go no further.  For some reason, I can't get down to the field where I'd change the vidoe memory from 1Mb to 8 -- all I can seem to do on this page is change the time.  Any ideas?

thanks in advance.
g

I think it is page 6 of 6 and it is listed as UMA size. 

Hope that helps!

---

### Post by DMBrazil on 2007-11-22
> **RedDawg said:**
> 
**_How to install Ubuntu 7.10 (Gutsy) on a Dell Inspiron 1100_**

**Change Video Memory in BIOS setup:**

[LIST=1]
[*]Make sure your Dell Inspiron 1100 notebook has been upgraded to the A32 BIOS. 
[*]When you start your computer, hit F2 to enter Setup. 
[*]Press Alt-P (Turn the page) until you get to the page with the video memory. 
[*]Change the video memory from 1MB to 8MB. 
[*]Reboot
[/LIST]
**Run Ubuntu 7.10 Setup from CD:**

[LIST=1]
[*]Run Ubuntu Setup in "Safe Graphic" mode. 
[*]When Ubuntu Live finishes loading, open a "Terminal" window. 
[B][*]Type "sudo su" to become root in the terminal window. 
[*]Changed directory into /etc/X11 by typing: 

# cd  /etc/X11

[*]Edit "xorg.conf" using "vi" editor and locate the Section called "Device". 
[*]Change the Driver from "VESA" to "i810":[/B]

From:

Section "Device"
Identifier "Generic Video Card"
Driver "VESA"
BusID "PCI:0:2:0"

To:

Section "Device"
Identifier "Generic Video Card"
Driver "i810"
BusID "PCI:0:2:0" 

[/LIST]
**Perform Live Install Now:**

[LIST=1]
[*]Double click on the "Install" icon on the Ubuntu Live Desktop. 
[*]Follow the normal install procedure. When you are done, you will have a fully functional Ubuntu 7.10 Linux OS on your Dell Inspiron 1100 notebook.
[/LIST]
Hope this helps. :)

Im really have trouble with this part. When i enter   # cd /etc/X11   it seems as though nothing happens and i just get a new root@ubuntu line.  Should anything happen then? And if not ... What is this VI editor and how do i get to it.. 

Any help would be much thanked! I've been working on this since about 2 pm and feel as though I'm finally getting somewhere!

---

### Post by gary8us on 2007-11-23
> **DMBrazil said:**
> I think it is page 6 of 6 and it is listed as UMA size. 

Hope that helps!

Ah -- that was the missing piece of information.  (I mistook the page that reported the memory size for the one that allows you to change it.) Thanks.

---

### Post by derby007 on 2007-11-23
To DMBrazil:
> Im really have trouble with this part. When i enter # cd /etc/X11 it seems as though nothing happens and i just get a new root@ubuntu line. Should anything happen then? And if not ... What is this VI editor and how do i get to it.. 

Any help would be much thanked! I've been working on this since about 2 pm and feel as though I'm finally getting somewhere!

Nothing should happen, you are now in the /etc/X11 directory. Do a 'pwd' at the command line, this tells you what directory you are in.

The VI editor or VIM editor is an (awkward) editor to let you edit files.
Type in : sudo vim /etc/X11/xorg.conf
Then enter your password, this lets you edit the file as root.
Then scroll down to the part in question. 
then hit : ESC 
then hit : A
then enter the desired change,
then hit ESC again,
then SHIFT ZZ
and the file is saved.
Then logout, then reboot / or go to next section of help.

---

### Post by gary8us on 2007-11-23
> **DMBrazil said:**
> Im really have trouble with this part. When i enter   # cd /etc/X11   it seems as though nothing happens and i just get a new root@ubuntu line.  Should anything happen then? And if not ... What is this VI editor and how do i get to it.. 

Any help would be much thanked! I've been working on this since about 2 pm and feel as though I'm finally getting somewhere!

This is where I'm at too.  Anyone?

Thanks,
g

---

### Post by gary8us on 2007-11-23
> **derby007 said:**
> To DMBrazil:


Nothing should happen, you are now in the /etc/X11 directory. Do a 'pwd' at the command line, this tells you what directory you are in.

The VI editor or VIM editor is an (awkward) editor to let you edit files.
Type in : sudo vim /etc/X11/xorg.conf
Then enter your password, this lets you edit the file as root.
Then scroll down to the part in question. 
then hit : ESC 
then hit : A
then enter the desired change,
then hit ESC again,
then SHIFT ZZ
and the file is saved.
Then logout, then reboot / or go to next section of help.

Thanks for helping out -- it's appreciated.

Okay, I'm still not having much luck -- possibly because the procedure is broken out into two messages now (yours and RedDawg's) that may/may not overlap completely.

First, I'm a "live session user," is that what your instructions are assuming?  I ask because you mention entering my password, which I think doesn't happen until you install the OS for real, no?

Second, when I type "Type in : sudo vim /etc/X11/xorg.conf" I get "command not found" in response.  Hmmm.

Third, when I type in a "pwd" I get ?/home/ubuntu root@ubuntu:/home/ubuntu #" back.  It doesn't sound like I'm where I need to be to carry out your instructions.

Any further help would be appreciated.


g

---

### Post by derby007 on 2007-11-24
If you are trying to install Ubuntu and it isnt working with the Live CD, then try the Alternate CD, ie. text mode. This CD wont require your graphics to be working. You can then alter your graphics options later after the install, with the help of my instructions earlier/or other solutions.

---

### Post by julep on 2007-11-24
> ... What is this VI editor and how do i get to it.. 

If you've never used the VI editor before, now is not a good time to learn. It's a great Unix tool but you can also cut your own foot off with it. If you've booted the live CD, just run the text editor from a terminal window as root:

```
 sudo gedit /etc/X11/xorg.conf 
```

It will open a window and you can scroll down to the section you need to change, make the change and save the file. It's a little slower but you won't cut your foot off and you will actually be able to see what you're doing.

After you get Ubuntu installed, learn VI. It may your life sometime.

./J

---

### Post by Nick Plunkett on 2007-11-28
I'm new at this whole OS installing thing.. and I'm in setup right now, however I can't seem to find the page with the graphics on it?

Can I have a page number or something?

Page6 of 6 is System Security and Hard-Disk Drive password(s)

and yes, I am on BIOS Version A32.

Probably just because my computer is weird.. I've gotten the blue screen of death about 3 times on it and had to re-install XP each time.. >.> this time wasn't as successful as the rest.. not all of the files got dumped/overwritten..

If it matters I just went from BIOS 23 to 32 in about 1-1.5 minutes

---

### Post by Nick Plunkett on 2007-11-29
Any Help with this?

---

### Post by Nick Plunkett on 2007-12-03
Someone has got to be able to help me with this >.>

---

### Post by Nick Plunkett on 2007-12-06
Somone please give me some support..

---

### Post by natehall on 2007-12-07
> **Nick Plunkett said:**
> Somone please give me some support..
 What is it you are trying to do, and with what are you trying to do it?

---

### Post by Nick Plunkett on 2007-12-09
> **Nick Plunkett said:**
> I'm new at this whole OS installing thing.. and I'm in setup right now, however I can't seem to find the page with the graphics on it?

Can I have a page number or something?

Page6 of 6 is System Security and Hard-Disk Drive password(s)

and yes, I am on BIOS Version A32.

Probably just because my computer is weird.. I've gotten the blue screen of death about 3 times on it and had to re-install XP each time.. >.> this time wasn't as successful as the rest.. not all of the files got dumped/overwritten..

If it matters I just went from BIOS 23 to 32 in about 1-1.5 minutes


Just found the page on the BIOS I needed :D, and now I shall continue installation.. hope it works >.>

EDIT: Problem solved, Ubuntu Installed, thanks Ubuntu Forums! :)

---

### Post by sporkfighter on 2007-12-13
I've followed your instructions, but I can't install. The install program window is still larger than the screen, so the options and buttons are off the bottom, out of reach.  I can't get past this.:confused:

---

### Post by pumpkinpapa on 2007-12-29
I also got to the point where Live cd is ready to install but I cannot open a terminal as I cannot access the launcher bar. Is there keyboard commands to access the launcher when you can't see it in 640x400?

---

### Post by SpookComix on 2008-01-03
> **RedDawg said:**
> Many people have encountered problems installing Ubuntu 7.10 (Gutsy) on laptops with an Intel 82845G/GL integrated display adapter, such as the Dell Inspiron 1100...

Many, many thanks for the perfect answer to a perplexing issue.  As a bonus, going from the A06 BIOS to the A32 seems to have enhanced things.  Now Ubuntu is telling me that my wife's laptop battery is only firing on 38% of its cylinders.

Thanks again, RedDawg.

--SpookComix

---

### Post by neiljansons on 2008-03-19
Thank you for the help on this
The first thing that helped was changing the video memory from 1mb to 8mb.
The second thing was to run the livecd in the safe graphics mode.

So now I have successfully installed Kubuntu 7.10

---

### Post by thecrambler on 2008-03-22
So I updated the BIOS and changed the video to 8mb. I attempt to install in safe graphics mode and it loads to a blank screen. Total blackness. I get the pretty Ubuntu loader bar which flows back and forth then a series of [OK] and then BLANK.
 Frustrated! HELP!

---

### Post by waspbr on 2008-03-22
never mind

---

### Post by thecrambler on 2008-03-22
NO! do mind! please! haha

---

### Post by Sav1 on 2008-04-15
I'm having the same problem as thecrambler, I follow the steps but end up with a blank screen. Can anyone help?

Edit: Never mind, kept on trying and eventually it worked. Thanks RedDawg for the guide.

---

