---
title: "tips for debian"
date: 2007-08-12
forum: Debian
---

### Post by Ozeuss on 2007-08-12
I just installed lenny on another partition (along feisty).
i'm sharing a /home partition, and i was wondering what is more preferable- using the same user in both feisty and lenny, or seperate users? 
also, i've installed sudo and enabled it the ubuntu way (%admin group in sudoers), is it also a good practice to lock the root account, or is it redundant?

any other recommendations are welcomed. i wish i looked in this sub-forum earlier, that way i would have used the tip to install etch first and then upgrade to lenny. the lenny netinst gave me a bit of an X headache, and i had to complete the installation by chrooting...

---

### Post by kerry_s on 2007-08-12
i'd go with a different user, debian and ubuntu do things differently.

don't lock the root account debian is set up to use su or gksu. for instance if you disable root you can't use synaptic from the menu unless you change that or use sudo synaptic from the terminal.

i alway's start from etch then just add the lenny repos and apt-get dist-upgrade.

---

### Post by dfreer on 2007-08-12
Hmmm. The only problem I've run into using sudo in Debian is that all of the administrative programs (like System > Administration > Login Window) require that you enter the actual *root* password, instead of your user password. I believe this is because it is launching the programs with gksu instead of gksudo.
I seem to be unable to edit my menus in lenny (By right-clicking on the menubar and selecting "Edit Menus"). The program just hangs. But if you can get the administrative programs to work with gksudo, I would definitely lock the root account.

EDIT: Correction. I would lock the root account if this is a standalone desktop machine, like for a home user. For a multi-user server, I generally would leave root intact and only give out sudo powers if absolutely needed.

---

### Post by kerry_s on 2007-08-12
> **dfreer said:**
> Hmmm. The only problem I've run into using sudo in Debian is that all of the administrative programs (like System > Administration > Login Window) require that you enter the actual *root* password, instead of your user password. I believe this is because it is launching the programs with gksu instead of gksudo.
I seem to be unable to edit my menus in lenny (By right-clicking on the menubar and selecting "Edit Menus"). The program just hangs. But if you can get the administrative programs to work with gksudo, I would definitely lock the root account.

I usually launch the programs from term using sudo, but if you want to disable it>

sudo passwd -l root
to enable again>
sudo passwd root

once you disable root, the root account will expire and you'll get error messages everytime you try to use root. i forget the fix for that, guess you'll just have to google it if you run into that problem.(the fix: sudo nano /etc/shadow, remove the 1 from the end of root line)

i just put a really long random string for the password and then just> sudo passwd root < if i want to use it. in other words i just drag my hand across the keyboard. :)

---

### Post by Ozeuss on 2007-08-13
> **kerry_s said:**
> 
i just put a really long random string for the password and then just> sudo passwd root < if i want to use it. in other words i just drag my hand across the keyboard. :)
 i don't think i got that last line. do you mean that you set a password that you don't even remember for root? (effectively locking it?)
 
about the gksu -gksudo part, i just marked the relevant tick box in gconf to force it to use sudo (the same happens in ubuntu).

---

### Post by dfreer on 2007-08-13
> **Ozeuss said:**
> about the gksu -gksudo part, i just marked the relevant tick box in gconf to force it to use sudo (the same happens in ubuntu).

wait... there's a gconf setting to control that behavior? 0.o

Then why the hell did I just spend the last hour wrestling with alacarte!?!
](*,)

Thanks for that, I'll go look for it ASAP and purge this alacarte blight upon my system.

---

### Post by kerry_s on 2007-08-13
> **Ozeuss said:**
> i don't think i got that last line. do you mean that you set a password that you don't even remember for root? (effectively locking it?)
 
about the gksu -gksudo part, i just marked the relevant tick box in gconf to force it to use sudo (the same happens in ubuntu).

Yep, you got that right. i use gksudo, not gksu.

---

### Post by Pobega on 2007-08-13
Am I missing something? Why are we locking the root account?

Doing everything from a single user account is a horrible practice, and you can cripple your system is you lose your /etc/sudoers file. You become even more prone to attacks, due to the fact that it's easier to just delete a single file rather than crack a password.

If you want to do a single command with root, you can always use *su -c "command"*, or you can even alias *su -c* to *sudo*, because I know how hard old habits die.

---

### Post by Ozeuss on 2007-08-14
> **Pobega said:**
> Am I missing something? Why are we locking the root account?

Doing everything from a single user account is a horrible practice, and you can cripple your system is you lose your /etc/sudoers file. You become even more prone to attacks, due to the fact that it's easier to just delete a single file rather than crack a password.

If you want to do a single command with root, you can always use *su -c "command"*, or you can even alias *su -c* to *sudo*, because I know how hard old habits die.

i was wondering what was the reason ubuntu locks it-  it seemed to me as a measure just for noobies to linux. i was wandering if there was a security measure as well...

---

### Post by kerry_s on 2007-08-14
it's a security thing, root will be the first place that gets attacked, becausae they know there's a root user, so they only have to crack the password. using sudo they will have to crack both the user name & password, because they don't know what the user name is.

---

### Post by cb34 on 2009-01-04
> **Ozeuss said:**
> about the gksu -gksudo part, i just marked the relevant tick box in gconf to force it to use sudo (the same happens in ubuntu).

this was EXTREMELY USEFUL!! thank you so very much for this info!!
googling and reading for hours..
-did a search in the debian section of this amazingly helpful forum [sudo su gksudo gksu] and BAM! 1 thread, and the exact answer i've been pulling my hair out looking for, and soooo simple.

Toda Raba Ozeuss! ;) ......:p

i'm dropping Ubuntu 8.04 and 8.1 for Lenny, and the only thing that was really bugging me and i didn't know how to fix was it was asking me for root password when for example opening synaptic from the gui menu(command is gksu blahblah), and i could just change it to gksudo or run synaptic from the terminal ok.. but in ubuntu the launch command for synaptic in the gui menu is gksu and it loads up fine, and i wanted that part of debian to run like ubuntu. now i know how it was done. amazing!!! thanks!!
-----
-----

another thing please if anyone is out there.. this is a pretty old thread i know.:)

when i installed debian, i did not install/enable a root account, it never asked me for a root password. i did this on purpose.. like it is in ubuntu. but why for example does that gksu synaptic launcher in the gui menu ask me for the root password(not my sudo user pass)and(before i changed the gconf su>sudo option)..

how can it ask me for root pass, when there is no root account.

or is there a root account, just when you dont install it during the installation process, it just doesn't have a password and is disabled?

during the installation process, when it asks me if i want to make a root account, and i say no. is that infact basically just asking if i want to enable or disable the root account, but the root account always exists??

i really dont get this aspect of it, and reading all the manuals and docs from here or debian or all over google, im lost on this one.

Thanks for any insight.. hehe.. thanks if anyone even notices this post and replies...hehehe

---

### Post by Bachstelze on 2009-01-04
> **cb34 said:**
> 
or is there a root account, just when you dont install it during the installation process, it just doesn't have a password and is disabled?

during the installation process, when it asks me if i want to make a root account, and i say no. is that infact basically just asking if i want to enable or disable the root account, but the root account always exists??

That's right. You *always* have a root account.

---

### Post by albinootje on 2009-01-04
> **dfreer said:**
> 
I seem to be unable to edit my menus in lenny (By right-clicking on the menubar and selecting "Edit Menus"). The program just hangs.


Debian Lenny is still not released as Debian Stable.
Feel (more than) free to report bugs and help them to get fixed.

---

### Post by kerry_s on 2009-01-04
yeah it is a old thread, lots of changes since then. :D

> when i installed debian, i did not install/enable a root account, it never asked me for a root password. i did this on purpose.. like it is in ubuntu. but why for example does that gksu synaptic launcher in the gui menu ask me for the root password(not my sudo user pass)and(before i changed the gconf su>sudo option)..


you can change gksu by running> **gksu-properties**
there you have a choice of su or sudo.
i also always lock my root.

---

### Post by cb34 on 2009-01-04
Thanks HymnToLife! :)
and
Thanks kerry_s, i'll go check that gksu-properties program now. :)
(edit-> checked, and cool little program! good one.)

you guyz are awesome! :guitar:

---

### Post by polmir on 2009-01-04
[URL="http://qref.sourceforge.net/Debian/reference/index.en.html#contents"]
Read first[/URL]
[sudo]("http://qref.sourceforge.net/Debian/reference/ch-tune.en.html#s-sudo")

---

