---
title: "Ubuntu won't load,  after using Mate Tweak Tool and switching from Marco to Compiz"
date: 2015-12-22
forum: Desktop Environments
---

### Post by bill23 on 2015-12-22
I have Ubuntu 15.10 Mate, but becarues of a mistake in my using the Mate Tweak Tool and changing froim Marco to Compiz, screwed it up soI can log in but no further. I hve tried the folowing suggesstiont recieved from 'Linuxquestions.org'.


"It sounds like you need to reset to marco from the console. At the grub screen press:

Ctrl + Alt + F1

That will take you to console (tty). You then need to login and run:
Code:
'marco --display=:0 --replace' 

I did that and received thr:


[Invalid MIT-Magic-Cookie-1
keywindow manager error
unable to open X display :0] 

Over at Linuxquestions, it was sugeted  I do the following:

It sounds like you need to reset X. Try the following:

1) Get to another tty CTRL + ALT + F1 (or any of the function keys) and stop X with 
	Code:
	sudo service gdm stop 
2) Make a back up of the X.org config
	Code:
	sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 
2) Reconfigure X with dpkg
	Code:
	sudo dpkg-reconfigure xserver-xorg 
3) Then restart X
	Code:
	sudo service gdm start 
UPDATE: if you don't mind, can you copy and paste the output of this command:
	Code:
	ps -aux | grep dm 
I did not know at the time that my Ubunt Mate used 'lightdm' beut even with the change and my trying it again the result was bupkiss. Tried a suggestion dealing with 'lightdm' its commnad was:


	Code:
	sudo dpkg-reconfigure xserver-xorg-core-lts-vivid
sudo service lightdm start 
As with my other attmts, ti too failed. A few timess fro a fraction of a second I saw  Firefox, Thunderbird and a White square box-like icon with a red X in is center. I was never quick enoug to try and click on Firefox or the 'white' icon.


One of the last suggestions was:  

So you could try mate-wm-recovery
(which my system apparently doesn't have)
or 
	Code:
	gsettings reset org.mate.session.required-components windowmanager 
After entering: , this is what I saw in the terminal window:After entering: _gsettings reset org.mate.session.required-components windowmanager_, this is what I saw in the terminal window:

'No such schema, 'org.sessions.required-components'

'Schema' is a new one for me?

Here is how my partition table looks like:

/dev/sda1 Swap
/dev/sda 2 Extended
/dev/sda 5 Mageia5
/dev/sda 6 Ubuntu
/dev/sda 7 PCLinuxOS
/dev/sda 3 Manjaro

Can I, as a last resort, ovrwrite the Ubunsu in /dev/sda 6 with a fresh installaion using the DVD used with the first installation?  Here si the possible solution as offered by TxLoinghorn,

It would not be necessary to do anything to the partition to install a new OS, or re-install Mate.
Leave the partition as it is. Choose the "Something Else" option during the installation, and choose /dev/sda6 as the / partition. The partition will be re-formatted as part of the installation process.


As has been said, thes was above my pay scale, so when push came to install, I backed away. I did not want to screw up my PC any moire thatn it alraedy was. You see one of my 'brillant ideas, while in terminal mode, I updated Ubuntu and then Upgraded it. I still could noot get it to open but now I could not get Manjaro to open to its login screen.

I am sorry for the length of thes post, but wanted you to know some steps made, and failed. I am hoping someone here may have other ideas? 

bill23

---

### Post by egeezer on 2015-12-25
I recommend the TxLonghorn solution, but with one caution: from the number of typos you are showing here, you may have made some in the terminal - a non-trivial problem, which everyone has at one time or another.  Just be EXTRA cautions of them in the terminal!

---

