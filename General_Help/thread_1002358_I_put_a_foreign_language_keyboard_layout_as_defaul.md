---
title: "I put a foreign language keyboard layout as default, and now can't log in!"
date: 2008-12-04
forum: General Help
---

### Post by alontkach on 2008-12-04
Hi people,

I am new to Ubuntu 8.10, and I went to System>> Prefences>> Keyboard>> Layouts, and I added a foreign language, and chose it as default. Then I restarted the computer, and I couldn't log in because it would ONLY type in that foreign language (and my user name and password are in english), and I tried many keyboard shortcuts, such as: "left ctrl + left shift", "alt + alt", "super key + alt", etc. but it wouldn't switch me back to English.

Please help, I do not know how to switch back to english, and I can't log in to my computer!

Thank you very much in advance!

Al

---

### Post by mdurham on 2008-12-04
Try rebooting in safe mode and resetting the language.

---

### Post by alontkach on 2008-12-04
> **mdurham said:**
> Try rebooting in safe mode and resetting the language.

Hi do you mean to choose the "failsafe gnome" session in the login options?

---

### Post by falcon61102 on 2008-12-04
While that may work, it would probably be better to start in the Recovery Mode version of the kernal.  It's normally the second option in the GRUB.

---

### Post by alontkach on 2008-12-04
> **falcon61102 said:**
> While that may work, it would probably be better to start in the Recovery Mode version of the kernal.  It's normally the second option in the GRUB.

I chose "Failsafe GNOME" and restarted, and it didn't work. My keyboard can still only write in the foreign language, and **I cannot log in as a result**

---

### Post by falcon61102 on 2008-12-04
Restart your computer and as it boots up you should see be presented with the GRUB.  If not, as soon as the BIOS finishes loading, press ESC.  Now you should be at the GRUB.  Select the second item in the list which should say something like Ubuntu 8.10 Recovery Mode

---

### Post by alontkach on 2008-12-04
I should probably add that I clicked on "Apply System-wide" on the Keyboard Layouts window. 

Also, I pressed Ctrl + Alt + F1 to go on tty1, and it STILL types in the foreign language only!

This is so frustrating, please help

---

### Post by alontkach on 2008-12-04
> **falcon61102 said:**
> Restart your computer and as it boots up you should see be presented with the GRUB.  If not, as soon as the BIOS finishes loading, press ESC.  Now you should be at the GRUB.  Select the second item in the list which should say something like Ubuntu 8.10 Recovery Mode

ok I did it, and now the options in the recovery menu are: resume, clean (try to make free space), dpkg (repair broken packages), fsck (file system check), root (drop to root shell prompt), xfix (try to fix x server).

Which option do I choose? And what do I follow after that?

Thanks a lot for being so patient with me,
Al

---

### Post by falcon61102 on 2008-12-04
Clicking Resume is going to boot up as normal and I'm not sure if that will help you.

Try clicking on root and seeing if that will at least type in the right languange and then we'll see if we can find the terminal command for changing the keyboard layout.

---

### Post by alontkach on 2008-12-04
> **falcon61102 said:**
> Clicking Resume is going to boot up as normal and I'm not sure if that will help you.

Try clicking on root and seeing if that will at least type in the right languange and then we'll see if we can find the terminal command for changing the keyboard layout.


Doesn't type in English in Root! :(

---

### Post by falcon61102 on 2008-12-04
When you were at the GRUB did you notice any other kernal versions listed there?  If so, restart and try loading one of those up and seeing if it comes up with an English keyboard layout.

---

### Post by alontkach on 2008-12-04
> **falcon61102 said:**
> When you were at the GRUB did you notice any other kernal versions listed there?  If so, restart and try loading one of those up and seeing if it comes up with an English keyboard layout.

Tried it on all those other Kernel versions and it still didn't help. :(

---

### Post by falcon61102 on 2008-12-04
One thing you can try is loading up a LiveCD and editing your xorg.conf file on your HD.  You should see a section that looks like this:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
```

If you don't, try creating one and then saving it.

---

### Post by nickski on 2008-12-04
I know in windows, if you crack open your case, and you should see a little battery that looks like a watch battery.  If you remove that for about 15 minutes, it resets your chmos settings, and there will be no more xp passwords, if i'm not mistaken.  Not sure if this will work for linux.  Also, there is something called ophcrack that you can download, and it cracks os passwords, but i think that is also only for windows.  I have never tried it with linux.  Just thought i would throw some ideas out there.  [www.ophcrack.sourceforge.net](www.ophcrack.sourceforge.net)

Ophcrack says it does work with linux hashes, so i'd give that a try.  Go to that url, and download the live cd.  Mount the image file with poweriso or another iso burning program.  Burn this to a disc, and run it at boot.  It should start right away.  Goodluck

Sorry, i just realized that this will give you your old password.  You still cant type that out.  You might as well run your live cd and try to configure that file, or yank your hd out and connect it to another computer and run it as an external hd.  Find the file, and do what the person ahead of me said to do.  Last case senerio, back up everything (videos, music, important files) and just wipe the hd and start over.  Dban is an amzing program to do it.  just google it

---

### Post by falcon61102 on 2008-12-05
Resetting your CMOS really has little to do with your actually OS and mainly just deals with BIOS parameters.  The only passwords that would get reset would be any BIOS passwords that were being stored in the CMOS.  

The above should work, I was just trying to circumvent manually editing the host computer's xorg.conf.

---

### Post by sisco311 on 2008-12-05
in the grub menu highlight ubuntu (NOT the recovery mode) 

press e for edit 

highlight the *kernel* line and press e for edit

change lang=*xy* to lang=us

press enter, then b to boot.

log in, edit the menu.lst file:
```
gksu gedit /boot/grub/menu.lst
```and set the language to *us*

---

### Post by alontkach on 2008-12-05
> **sisco311 said:**
> in the grub menu highlight ubuntu (NOT the recovery mode) 

press e for edit 

highlight the *kernel* line and press e for edit

change lang=*xy* to lang=us

press enter, then b to boot.

log in, edit the menu.lst file:
```
gksu gedit /boot/grub/menu.lst
```and set the language to *us*

Ok so I'm just going to go step-by-step to make sure I got everything you're saying:

1) I highlighted "Ubuntu 8.10, kernel 2.6.27-9-generic"
2)I pressed "e"
3)this brought me to a menu which had 4 options
  i) uuid 85fecbcc-f902-441a-aadc-f8de0355a60f
  ii) kernel /boot/vmlinuz-2/6/27-9-generic root=UUID=85fecbcc-f902-441a-a-->
  iii) initrd  /boot/initrd. img-2.6.27-9-generic
  iv) quiet

4) I highlighted option (ii) and pressed e
5) This brought me to this: 
     "[Minimal BASH-like line editing is supported. FOr the first word, TAB lists possible command completions. ANywhere else TAB lists the possible completions of a device/filename. ESC at any time exits.]

<-f902-441a-aadc-f8de0355q60f ro quiet splash _ "

6) At this point I don't know what I should type. 

Please let me know what I'm doing wrong, thank you so much guys for your prompt help!

Al

---

### Post by tacutu on 2008-12-05
what language is the keyboard? French? German?

---

### Post by sisco311 on 2008-12-05
just append the line with *lang=us*.

this hopefully will boot the system with the us keyboard layout.

if this doesn't work then boot a live cd. mount the root partition.

assuming that the root partition is mounted in /media/ubuntu edit the

gdm.conf file:

```
gksu gedit /media/ubuntu/etc/gdm/gdm.conf
```

and setup the automatic login:
> ...
[daemon]
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=**"write your user name here (without the quotes)"**

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30
...
(ex.: AutomaticLogin=**alontkach**)

edit the shadow file to make your account passwordless:
```
gksu gedit /media/ubuntu/etc/shadow
```

find the appropriate line for your account.
it'll look something like this:
```
*alontkach*:**$1$2TUdk8Z0$tb2Fn6Idgo8dq9EgYv4xZ0:13721**:0:99999:7:::
```
change the second part (in bold here) to match this second part (also in bold):
```
*alontkach*:**U6aMy0wojraho**:13721:0:99999:7:::
```

save the file and reboot.

now you should be logged in automatically and run administrative apps without a password.
(just hit enter if you are asked for the password)

change the keyboard layout to english and reboot.

**[COLOR="Red"]set a new password for your user:[/COLOR]**
```
passwd
```**and disable the automatic log in**.

hope this helps

---

### Post by nickski on 2008-12-05
> **falcon61102 said:**
> Resetting your CMOS really has little to do with your actually OS and mainly just deals with BIOS parameters.  The only passwords that would get reset would be any BIOS passwords that were being stored in the CMOS.  



Yea you are right, i wasn't sure though thank you for correcting me...

---

### Post by mdurham on 2008-12-05
Just as a matter of interest. Would booting from Live CD and chrooting to the problem distro be any use? Which keyboard would that use?
Cheers, Mike

---

### Post by falcon61102 on 2008-12-05
> **nickski said:**
> Yea you are right, i wasn't sure though thank you for correcting me...

No worries.

---

### Post by Icebear on 2008-12-06
I think the default language changer is both alt keys

so at the login prompt try that and then type

also at the login goto option and click language

choose english
(I do not if that will change the keyboard though)

---

