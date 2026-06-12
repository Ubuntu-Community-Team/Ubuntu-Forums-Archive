---
title: "How to instal Ubuntu on Dell XPS L501"
date: 2011-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by category_1 on 2011-01-15
Dear All,

I have just purchased a new Dell XPS L501 laptop with Windows 7 installed by Dell.

I would like to install Ubuntu 10.04 onto the laptop as a dual boot with Windows 7 and have prepared a USB with the installation software.

My first attempt to install Ubuntu failed. As the installation begun initialising, an error message appeared on a command line on an otherwise blank screen, and was along the lines of - Installation failed as live drive was not found.

Please could anyone help me install Ubuntu on a Dell laptop with easy to follow instructions? (as very much the novice) and make me aware of any trouble I should expect when dual booting a Dell laptop? as quite a few came up when search about this.

Thank you for your time.
Kind regards,
Yas

---

### Post by stanz on 2011-01-16
Check BIOS if usb is enabled.
I prefer using a CDRom for easy testing & install.
You can search for very detailed instruct's here. _Which I'd advise_-since your dual booting with ms!

Also- I'm guessing win7 is already installed and working?
Remember, Dell and win7 have some kind of backup program that messes with grub [or changes
the whole mbr] and will leave you bootless at the next reboot. 

I searched and found some helpful info- both here on the forum and grub2 wiki, and together with
my handy cdrom, it all worked out. 
Post back your progress here or [here]("https://answers.launchpad.net/ubuntu")!!
enjoy

---

### Post by category_1 on 2011-01-17
Thanks stanz for a reply.
 
Yes, I was able to select a usb boot option on the boot menu after which I got the error message.
 
I am extremely interested in the link for a detailed instruct on installing ubuntu, unfortunately the link is not on your post. Please can you send it again?
 
Thanks for informing about interference by Dell backup programme. The Dell backup software popped up when using the laptop on the last occasion. Does that mean I will not be able to boot the next time I restart? I will give it a test of course, but what can I do to fix this issue?
 
Cheers,
Yas

---

### Post by stanz on 2011-01-17
[FONT=Book Antiqua]_Ubuntu instructions for installation:_[/FONT] 
[http://www.ubuntulinux.org/desktop/get-ubuntu/download](http://www.ubuntulinux.org/desktop/get-ubuntu/download)

[FONT=Book Antiqua]_FYI & handy info, when it happens!_[/FONT]
[FONT=Book Antiqua]These links are from posts-here on the forum-that have helped me  understand what was happening and how to fix it.
You will notice  different methods to approach this fix, choose what applies![/FONT]
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

> [COLOR=Red]***Dell & HP have software that writes into the MBR that corrupts grub2:***[/COLOR][http://ubuntuforums.org/showpost.php?p=9304503&postcount=11](http://ubuntuforums.org/showpost.php?p=9304503&postcount=11) {Many Links}
[http://ubuntuforums.org/showpost.php?p=9756863&postcount=31](http://ubuntuforums.org/showpost.php?p=9756863&postcount=31)

[FONT=Book Antiqua]_Recovery Help Documents:_[/FONT] 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I hope this is a help! Please post your progress!
Have fun....:popcorn:

---

### Post by stanz on 2011-01-17
I forgot to ask about the error--concerning BIOS & the USB.
Do you have working CdRom--as option?

---

