---
title: "Two Kernels and Serial mouse with wheels"
date: 2005-12-20
forum: General Help
---

### Post by dead poet on 2005-12-20
Hi everybody,
I am from Bangladesh and want to say hello to everybody reading this. As a linux user I've used Redhat and Fedora before but Ubuntu seems to be more user friendly to me except a few glitches. Hence the questions arise :) -

1) Like everyone else with a serial mouse I've gone through the usual "hair-tugging" phase before I figured how to make the mouse work by changing the xorg.cong. The "ttyS0" and "Microsoft" seems ok. But Alas the mouse wheel is not working and I'm very dependent on it. So I need some quick and effective solutions from my friends here. My mouse is a two button scroll wheel mouse serial mouse from A4Tech. The section from xorg.conf looks like this-

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Microsoft"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
        Option          "Buttons"               "5"
EndSection

I added the "Buttons" line cause I read it somewhere. But the wheel still does not work. Making the "Emulate3Buttons" "true" also does not work

2) I have another question for you. I've let the automatic update download and install updates. Now When i'm in the GRUB OS selection screen, I can see two ubuntu kernels. I can log in with the latest with no problems. Does this mean that junks have started to pile up just like windows. Do I need the two kernels. I've installed Ubuntu Breezy Badger with default setup in a 4.5 GB drive. So I'm worried about my disk space.

Thank you for reading this. Any help will be appreciated.

---

### Post by Ocxic on 2005-12-20
i can answer the kernals queston,, there are normally 2, 3 if you include the memtest, one is your normal kernel, the other is the recovery kernel if something goes wrong, if there are more kernels in the menu it's ok, it just means you did an upgrade, or installed a new kernel and it was add to the list. if you don't want to see all of the kernels that are listed, edit you /boot/grub/menu.1st file and COMMENT them out by putting an # in front of the one's you don't want to see, don't delete them from the file just in case. it's not really junk, because when you install a new kernel or upgrade you kernel, the old one still is left behind just in case something happens and you can't boot the new one. if you want to get rid of the older kernel sompletely you'll have to ask someone else, if that's even possible.

---

### Post by dead poet on 2005-12-22
Thanks Ocxic for clarifying the kernel thing. But isn't there anyone who can help me with the mouse wheel thingy? If there is someone with the knowledge, please please do help me out. I'm feeling very uncomfortable without the scrolling function working.

---

