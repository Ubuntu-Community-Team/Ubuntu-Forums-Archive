---
title: "HOWTO: Japanese Input"
date: 2006-01-28
forum: Desktop Environments
---

### Post by rlgc79 on 2006-01-28
Background

I need to type in English, Portuguese and Japanese, and I'd had problems for some time with the combination Japanese+QT (Breezy). 

Solution:

1) Follow the Wiki 
[https://wiki.ubuntu.com/JapaneseInputHowToInBreezy?highlight=%28japanese%29](https://wiki.ubuntu.com/JapaneseInputHowToInBreezy?highlight=%28japanese%29)

You will find that you are unable to type in Japanese in any program that uses the QT library (Kile, kedit etc etc)

2) Go to Synaptic and install qt3-qtconfig (optionally: type "sudo apt-get install qt3-qtconfig" in a terminal session)

Open a terminal session

3) Run "qtconfig"

4) Go to the INTERFACE tab

5) Enable "Enhanced support for languages written right-to-left"

6) In "XIM input style", choose "root"

And now you can type in Japanese (in kile etc ...) \\:D/ 

NOTE: DO NOT CHOOSE "over the spot" as your "XIM input style", because all programs using QT will crash. If you choose this option by mistake, open a terminal session and type

XMODIFIERS="" qtconfig

and switch back to "Root" as your "XIM input style" 

The idea was taken from: [http://www.suse.de/~mfabian/suse-cjk/kde-input-style.html](http://www.suse.de/~mfabian/suse-cjk/kde-input-style.html)

Cheers

---

### Post by hanzj on 2006-01-31
I did as the howto said but I still can't type Japanese in Opera browser and Skype. 

Please advise.

---

### Post by rlgc79 on 2006-01-31
hanzj,

I have just checked skype in 3 different computers; the HOWTO is working well. Note that the japanese text appears in the lower left corner of the application window. Once you press ENTER, the text appears in the application window. 

There is a way to make the text appear on the spot. However, I haven't managed to do it without compiling UIM from the source.  (It was supposed to work when you choose "On the Spot", instead of "Root"...)

---

### Post by disraeli on 2006-03-03
works great on my Kubuntu 5.10 (Breezy) with KDE 3.4.3 ! thanks a lot!
(i only use japanese with Opera and it works soo sweet) :D

---

### Post by muzaki on 2006-03-03
Hi guys,
after doing what you said, i can type japanese character in terminal,firefox,etc.  **BUT** i still cant type it on **Opera** and **Open Office**.Please what should I do:confused: 

note: I`m using ubuntu breezy english edition, default lang is english with japanese keyboard
,I used **Automatix** for update/install Open Office and OPera :rolleyes: Is that the problem??? :confused: 

I`m using anthy as default input way

Everytime I try to type in Open Office,suddenly "Quit Unexpectedly" shows and its quitting

i also did this:  [http://www.ubuntuforums.org/showthread.php?t=76985&highlight=japanese+input](http://www.ubuntuforums.org/showthread.php?t=76985&highlight=japanese+input)
please and thanks in advance

---

### Post by rlgc79 on 2006-03-03
muzaki,

I also have this error message when I try to open japanese files that were created with Microsoft Office. However, if the text is created with Openoffice, there isn't any problem. 

I think this a Linux Openoffice bug, since this problem is not present in the Windows version of Openoffice. I have also found that arrows are not properly printed on  Linux Impress 2.0.1, although it is printed without errors in Windows Openoffice.

Regarding the opera browser, I cannot tell anything, since I only use Firefox...

Best


(Note: I am using the english version of Ubuntu Breezy with an US keyboard)

---

### Post by muzaki on 2006-03-03
thanks so much for fast reply...
but i cant even type in japanese character in OpenOffice...


Ok then if this is a bug, is there any other OO alternative (to type in japanese char?)

---

### Post by rlgc79 on 2006-03-03
Muzaki,

I think you may have broken repositories. Once this happened to me (I could not type japanese). Thus, I reinstalled Ubuntu, installed EasyUbuntu, and proceeded as described by this How-to. Everything works fine now. Now, I can type Japanese in Openoffice.

I am sorry that I don't have better ideas to fix your problem without reinstalling Ubuntu.  

Ps.: Before reinstalling everything, you can test the above approach with vmplayer and an Ubuntu virtual machine (or with QEMU).

---

### Post by muzaki on 2006-03-03
reinstalling would not be my choice i think:( 

I figure out i dont have japanese fonts in OO.

ps. in suse 10.0  i  managed to type japanese in OO ,and i have the jap. fonts,

any comment ? or how to install japanese fonts?

and another noob question, what`s the benefit using QEMU ,you mean to check wether my installation cd is correct or not?

thanks

---

### Post by muzaki on 2006-03-04
update : wow dumb me, at last I could find out my mistake,i just need 2 install japanese font from synaptic
:D :D 
&#12420;&#12387;&#12392;&#12289;&#12431;&#12363;&#12387;&#12383;&#65281;&#65281;&#65281;\\:D/ \\:D/ \\:D/ 
UBUNTU&#12387;&#12390;&#12377;&#12372;&#12356;&#12397;&#65281;

---

### Post by rlgc79 on 2006-03-17
> 
and another noob question, what`s the benefit using QEMU , you mean to check wether my installation cd is correct or not?



Let's say that you can create a new computer "inside" your Ubuntu install.  This "new computer" is just a file for Ubuntu.  You can install Linux, Windows, format the "simulated" hard-disk etc  without losing anything on your computer. If things go wrong, just delete the file. 

It is good way to check things before you change your main OS install, 'cause you can be sure that you won't end up with broken repositores.

Best

---

