---
title: "blackscreen afte install of 'live' boot"
date: 2005-11-08
forum: Desktop Environments
---

### Post by sanderrrrrr on 2005-11-08
Hi,

I just installed ubuntu and it is not working very smooth.

If I boot, i see a black screen after a while (I never get to the login screen). So I tried the live CD, also a blackscreen. If I hit the power button I see this  errormessage:

"cscreensaver-command: no screensaver is running on display :0.0"

So, anyone any idee how to solve this?

Tnx,
Sander

---

### Post by matthewv on 2005-11-08
Can you get to the terminal; i.e can you type in commands.

---

### Post by sanderrrrrr on 2005-11-09
Did that, done that ... but ... what's next?

I can see more ppl have got this problem. It seems that the solution is somewhere in the xorg.conf. But I have no idee what lines I have to modify.

The specs of the laptop:
Intel Pentium M Processor 740 (1,8 Ghz)
ATI Mobility Radeon X700

Should be enough :-)

Tnx

:edit: I can't find the option 'Edit threat' The title must be "blackscreen afte**r** install **or** 'live' boot ".

I have to stop living 18 hours a day ;-)

---

### Post by Who on 2005-11-09
If you don't want to modify any lines specifically then try this

sudo dpkg-reconfigure xserver-xorg

{sudo means 'exeute the following as super user (I.E administrator), dpkg is the Debian Packaging Tool, and you are reconfiguring a package called 'xserver-xorg' which will write you a shinny new xorg.conf)
after logging in. The password it asks for is your password, not a root password

HTH

Who

(PS: dkg-reconfigure has been suggested at least once in these forums in the last 2 days...often you can get an answer to a question more quickly by googleing for it or using the forum search, rather than waiting for someone to reply)

---

### Post by Who on 2005-11-09
Oh, it is bizzarre, and I haven't seeen it on Ubuntu yet, but it is possible that the Xserver is configured but not starting (I say this because if my xorg.conf is no good then I get blue error screens....) 
so, you _could_ try logging in and typing
startx

-it's a long shot
Who

---

### Post by sanderrrrrr on 2005-11-09
oke, I tried both options but it is still not working.

If I Typ sudo dpkg-reconfig etc. There is an option where you can select the sreen inch. My laptop ´ve got an 15,4 inch screen. But this option is not listed.

I bought this laptop last week. Is it maybe possible that ubuntu just can't handle this product yet?

I searched the internet for hours now (and yesterday, and the day before yesterday) but nothing have been succesfull. :(

---

### Post by cpinfdp on 2005-11-14
Same problem dude, tried reconfiguring in ati, vesa, and vga, and the live still doesnt work.  If anyone has a solution, please help.  Thanks.

---

