---
title: "SMP Kernel causes lockup after/during GNOME login"
date: 2005-04-09
forum: Desktop Environments
---

### Post by Bil-E-daKid on 2005-04-09
Hey there guys!

I just upgraded from Warty to Hoary last night. My PC is a dual PIII-1Ghz and was previously working with the 686-SMP series kernel with Warty.

Restarting into Hoary works fine until I try to login to GNOME - it either hangs at the login splash screen or shortly after displaying my desktop. Complete freeze - can't do anything with mouse and keyboard and have to power machine off.

I installed the non-SMP 686 series (2.6.10-34) and now it works fine. Except I'd like SMP back!

I did a search for anyone else experiencing this problem and the only place I could fine was over at Tuxme. Here's a link (you'll see I've asked a question there too).

[http://www.tuxme.com/node/485#comme...3467b6849a5635d](http://www.tuxme.com/node/485#comme...3467b6849a5635d)

Please save me from my non-SMP madness.

Regards
Bil-E-daKid

---

### Post by Bil-E-daKid on 2005-04-11
Hey there guys,

I have fixed my own problem after seeing something apparently related in another thread.

Turns out the problem was the xorg xserver. I have run a 'sudo apt-get xserver-xfree86' and now I can use the SMP kernel again without funny lockups just after login.

Regards
Bil-E-daKid

---

### Post by valnar on 2005-05-25
I just tried this and I think my newbieness just showed through.  I can't get into X any more!  How can I configure Xfree to work again?

Robert

---

### Post by Bil-E-daKid on 2005-05-25
Hey there Valnar,

The Xfree86 configuration file is /etc/X11/XF86Config-4.

Run this: sudo vi /etc/X11/XF86Config-4

and you'll get to edit that file.

** WARNING ** You may want to substitute 'vi' for 'nano' or whatever text based editor you are used to. vi is an acquired taste....    ;-)

What does X do when it tries to start? (This will help with figuring out which settings you need to modify in the above file).

Regards
Bil-E-daKid

---

### Post by valnar on 2005-05-25
I may be green, but I assume that the command you specified two posts above removed Xorg in favor of Xfree86, correct?  At least, that is what apt-get appeared to be doing to my system as I watched in horror.   :neutral: 

That being the case, is there a way I can look up/at my old Xorg configuration?  Are the config files similar?  Better yet, can I look at yours for a comparison?  I don't know the syntax nor how they are *supposed* to look.

Thanks!

-Robert

---

### Post by Bil-E-daKid on 2005-05-25
No problems Robert!

You're completely correct. Installing xserver-xfree86 will remove xserver-xorg (and vice-versa).

The config file for Xorg is /etc/X11/xorg.conf and the syntax appears (to me) to be identical. You should find that this file still exists even after Xorg has been removed.

I have attached my XF86Config-4 file (had to add .txt to get it to upload to the forums) for your perusal.

What symptoms are you experiencing when X fails to start?

Regards
Bil-E-daKid

---

### Post by valnar on 2005-05-25
Thanks for your reply Bil-E-daKid.

OK, my DOS days came flying back to me.  I just replaced the "EDIT" command with "NANO" and I was on my way.  Also, using a freeware MOUNT program on the Internet helped me extract the files to Windows so I could write this reply.

I copied my old xorg.conf over the blank XF86Config-4 and tried to restart X again by rebooting.  Same problems.  I've attached both my xorg.conf and XFree86.log files which explain the error(s) according to the bootup messages on my screen.  If you can help , that would be great!  Otherwise, it's back to yet another ubuntu reinstall for me until I get this right!

-Robert

---

### Post by Bil-E-daKid on 2005-05-25
*grin* It's all good Robert - you're doing just fine!

I've had a squiz through the log files and, to be honest, can't really see what's wrong there - although the xfree log seems to show it can't find a screen.

Try dropping the XF86Config-4 file (in the attached ZIP) into your /etc/X11 directory.

Essentially, I've grabbed information about your card and screen, dropped them into my XF86Config-4 file and also added HSync and VSync values for your monitor (obtained from a google search of CM751).

Perhaps that just might work.

Good luck!
Bil-E-daKid

---

### Post by valnar on 2005-05-25
Thanks.  It didn't work.  Same problem.

I did an apt-get for Xorg from the original Ubuntu CD and all is well again.  It did uninstall Xfree86.  That was nice.... but I'm back to single CPU i386 mode, which is still not acceptable.    ](*,)  ](*,) 

-Robert

---

### Post by Bil-E-daKid on 2005-05-25
*blast*

Sorry to hear that Robert - that is most disappointing.

You could still install the 686 series (non-smp) kernel - that will help a little.

Also, you could try installing the nvidia drivers (rather than nv which you are currently using). These may both afford you some performance increase.

Once you've done that, I'd suggest trying the smp kernel again. The odd thing in all this is that my home PC (686-smp/xorg/nvidia drivers) works fine where my work pc (686-smp/xorg/ati) doesn't - so I just run Xfree at work.

Wander over to [http://ubuntuguide.org](http://ubuntuguide.org) to find information on installing the nvidia drivers - perhaps that will work instead.

I know how frustrating it can be not having SMP enabled when your PC can do it - good luck in getting it going.

Regards
Bil-E-daKid

---

