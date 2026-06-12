---
title: "Wubi + windows 7?"
date: 2009-02-07
forum: General Help
---

### Post by Fzang on 2009-02-07
Here's how it's like:

Windows 7 as main OS
Windows vista as only-taking-up-disk-space OS

And the system runs with the windows 7 bootloader

Can I install Wubi on either vista or windows 7 or will the windows 7 bootloader screw something?

---

### Post by racie on 2009-02-07
I'd install Wubi on Vista just to be safe if I were you.

---

### Post by OutOfReach on 2009-02-07
I agree with racie, I'm not saying it will or won't work in 7. But 7 is still Beta, and as stable as it seems, it could choke up on you unexpectedly.

But a problem is that the bootloader is 7's, so it would be useless installing in Vista (right?)

---

### Post by Fzang on 2009-02-08
Yes, it's the bootloader I'm worried about, not where it places the .disk file. Hmm... I guess I could always give it a shot, or maybe manually edit the boot file

---

### Post by christhawkSMR on 2009-02-08
I tried installing Wubi with Win7 64-bit (with XP still hanging around like you've got Vista) and it doesn't show up in the loader.  I think we'll have to wait for the next Wubi, or official 7, or both?

---

### Post by Fzang on 2009-02-09
Hmmm, I guess we'll have to do that

Or maybe... maybe we could add it manually?

Is there anywhere that states whatever wubi is writing to vista's bootloader? I'm pretty sure you could just add it to 7's bootloader manually

---

### Post by nation-x on 2009-02-09
I had installed Ibex using wubi under Vista Home Premium. Later I upgraded to Windows 7 Beta. There were o issues at all... Ubuntu still shows up in the bootloader and loads fine.

---

### Post by DaEarl on 2009-06-28
Hi I'm in the situation that I have installed Windows 7 (64bit) on my only hard drive, only partition. After that I read that is impossible to install Ubuntu like in Vista by creating a partition from large unused space, so I wanted to use Wubi. I downloaded Kubuntu 9.4 and tired to install it within windows 7. I'v read that I have to run Wubi in vista compatibility mode to have the grub installed correctly, but after the Wubi uninstaller is installed I allways get the error: "writelines() argument must be a sequence of strings" and the installation stops. What could be the problem? IS the only other option to make a correkt dual boot to install Linux first and then install windows 7?

---

### Post by SuperSonic4 on 2009-06-28
To be honest it would probably be easier to manually install ubuntu onto it's own partition (perhaps overriding vista, perhaps not) and then grub will be installed

---

### Post by Sef on 2009-06-28
> After that I read that is impossible to install Ubuntu like in Vista by creating a partition from large unused space....

You would have to dual boot it by manually partitioning the hard drive.  Read the I[llustrated Dual Boot]("http://members.iinet.net/%7Eherman546/index.html").

---

### Post by DaEarl on 2009-06-29
I have read the instructions, but the autor has already a multibooting system. Will my system boot up correctly if I just let Ubuntu install the GRUB into the MBR where windows 7 is booting?

---

### Post by hibliss on 2009-06-29
> **DaEarl said:**
> I have read the instructions, but the autor has already a multibooting system. Will my system boot up correctly if I just let Ubuntu install the GRUB into the MBR where windows 7 is booting?

Yes it will. I would seriously advise against installing Ubuntu via Wubi in Windows 7 RC1 which is set to expire in less than a year.

---

### Post by DaEarl on 2009-06-30
Thx for the advise and the link, everithing went fine during installation. I now dualboot Kubuntu 9.4 and Windows 7. Ther's only one funny thing, in the bootloader I have Windows Vista instead of W7, but I think this would be only a matter of editing. Everithing works OK Thx again.

---

### Post by hibliss on 2009-06-30
> **DaEarl said:**
> Thx for the advise and the link, everithing went fine during installation. I now dualboot Kubuntu 9.4 and Windows 7. Ther's only one funny thing, in the bootloader I have Windows Vista instead of W7, but I think this would be only a matter of editing. Everithing works OK Thx again.

You can edit the names in the grub list very easily, but Ubuntu will recognize any Windows 7 install as Vista.

---

### Post by zorglubx on 2009-07-25
I just read on another forum, that to make wubi work with 7, you need to run wubi with vista compatibility, nothing else.
So i just tried that, and yes it does add the ubuntu to the boot loader (windows 7 boot loader). But there is an issue, that it do not boot correctly into ubuntu, but instead gives me an error "Try (hd0,0 ) " (and some more info?!).

I suspect that the hidden partition that windows create for the system restore stuff, is somehow messing up the partitions wubi can see, so it sets the wrong partition in the bootloader. I tried to check with the program called "bcdedit" but it is not exactly easy to use.

And they got rid of the boot.ini file, so i cannot check there.

Any bright idea's ?

---

### Post by jeffytheboss on 2009-07-27
> **zorglubx said:**
> I just read on another forum, that to make wubi work with 7, you need to run wubi with vista compatibility, nothing else.
So i just tried that, and yes it does add the ubuntu to the boot loader (windows 7 boot loader). But there is an issue, that it do not boot correctly into ubuntu, but instead gives me an error "Try (hd0,0 ) " (and some more info?!).

I suspect that the hidden partition that windows create for the system restore stuff, is somehow messing up the partitions wubi can see, so it sets the wrong partition in the bootloader. I tried to check with the program called "bcdedit" but it is not exactly easy to use.

And they got rid of the boot.ini file, so i cannot check there.

Any bright idea's ?


I am in exactly the same spot as you. First it wouldn't add Ubuntu to the Windows boot loader, and would boot straight into Win7. Tried bcdedit but only listed the entry for windows 7. Ran it in vista compatibility and now its listed but says  I also suspect it has something to do with the hidden partition is the culprit, and informs me to "Try (hd0,0 )"

as of now no clue where to go from this point. However, Win 7 in VM Fusion on my macbook installs wubi just fine.  Gonna poke around that for a minute and see if i can find a difference...

---

### Post by jeffytheboss on 2009-07-27
It may be a bit premature but I think i may have made a Breakthrough! I managed to get it to boot into the ubuntu install, if it works after the reboot I will let reply with instructions. Crossing fingers..

---

### Post by jeffytheboss on 2009-07-28
I spoke too soon. I still not able to get this working properly....so unless anybody else has any suggestions, im throwing windows to the curb.

---

### Post by Zero Circuit on 2009-08-04
> **jeffytheboss said:**
> I am in exactly the same spot as you. First it wouldn't add Ubuntu to the Windows boot loader, and would boot straight into Win7. Tried bcdedit but only listed the entry for windows 7. Ran it in vista compatibility and now its listed but says  I also suspect it has something to do with the hidden partition is the culprit, and informs me to "Try (hd0,0 )"

as of now no clue where to go from this point. However, Win 7 in VM Fusion on my macbook installs wubi just fine.  Gonna poke around that for a minute and see if i can find a difference...

I was having the same issue with the x64 of ubuntu with win7 ultimate RTM running bitlocker. 

deleted the x64 tried i386 got a little bit further 

thought maybe the image was corrupt re downloaded x64 suspended bitlocker and got the try hd0 error again

finally got sick and tired of dicking with it and set up another partition and installed x64 on it's own partition 

I liked the idea of it being installed in windows but too much of a headache for me

---

### Post by GraffitiSucks on 2009-10-22
Oh, hello there. :P

Will Windows 7 x32 bit work with Wubi?
I'm to afraid to try because it might screw up.

All the best, GraffitiSucks.

:popcorn::popcorn::popcorn::popcorn:

---

### Post by carcar1 on 2009-10-23
It does work 100% with win 7 build 7600 rtm which is a little different then the retail version.  I have it working just fien it even upgraded to 9.19 rc with no problems. Cheers

---

### Post by phillw on 2009-10-23
Unless you *really* need to, why not pop ubuntu onto it's own partition ? It can happily see the stuff on your fat/ntfs area.

Just a thought - The instructions are here ...

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Regards,

Phill.

---

### Post by GraffitiSucks on 2009-10-24
> **phillw said:**
> Unless you *really* need to, why not pop ubuntu onto it's own partition ? It can happily see the stuff on your fat/ntfs area.

Just a thought - The instructions are here ...

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Regards,

Phill.
Okay. I think your guide is a bit fishy. But, I'm not going to read it.

---

### Post by GraffitiSucks on 2009-10-24
> **carcar1 said:**
> It does work 100% with win 7 build 7600 rtm which is a little different then the retail version.  I have it working just fien it even upgraded to 9.19 rc with no problems. Cheers
Thanks. I have RC Build 7100. Will that work?

---

### Post by eggs588 on 2009-11-17
Hey, just wanted to say that wubi works fine on my laptop..currently in a triple boot scenario...

Windows XP - original os
windows 7 32 bit RC (Build 7100) - Main OS
and then I used my ubuntu 9.10 cd to install wubi, it worked perfectly with no problems at all. I have windows 7 boot loader with XP, 7, Ubuntu, and Unidentified Operating System on Drive C. 

Lol, the unidentified one is my (no longer hidden) lenovo service partition. Its useless, I just didnt bother removing the entry.

This is my first post on forums.. =D
I used wubi for a month last year, but removed it to make space for 7...and this time..I only installed it for compiz-fusion. 
(Not that Windows Aero is bad...but I like having my windows catch on fire when I minimize em. =P)

---

### Post by Lee3155 on 2010-02-10
Windows 7 Is Now Supported. Go here for more info: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi) << it says Windows 7 is supported.

Enjoy!

Also I installed it on my laptop(which has windows 7) the other day and it worked fine. 

- Lee

---

