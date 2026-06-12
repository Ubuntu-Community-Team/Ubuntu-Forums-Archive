---
title: "My Dell Camera"
date: 2009-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jordanoff11121 on 2009-06-27
I have Dell Inspiron 1545. 
I have disk with drivers for my camera, but autorun doesnt works. Setup.exe doesnt works too.

What can i do to fix my camera?

Please write step by step, i'm newbie :)

---

### Post by Secrest on 2009-06-27
You mean you have a camera that you want to work with your dell right?  Have you just tried plugging your camera up to the dell and letting everything run like its supposed to?  Most cameras are plug and play with ubuntu so there is no reason to try and use your disk to install anything.  Plug the camera up using your usb cable and make sure your camera is turned on.  A program will pop up letting you transfer your pics to your dell.  Let me know how it goes.

---

### Post by oddeyed on 2009-06-28
Hello jordanoff11121, I have the same laptop as you. I am unsure if you mean a digital camera which you take photos with out in the wild, or a Webcam build into the laptop. Because the title says 'Dell Camera' I will assume you mean a Webcam.
 
 As a complete newbie, you could be forgiven for not knowing that anything ".exe" is generally Windows only. There is a way to run _some_ Windows programs in Ubuntu or Linux, its called 'WINE', try [http://www.winehq.org]("http://www.winehq.org/"). I doubt that your Webcam program from Windows would work though, as Webcams are managed VERY differently on Ubuntu than Windows.
 
A brief primer on drivers for Ubuntu or Linux: Rather than install drivers individually, you tend to upgrade the 'Kernel' (Linux itself) to the latest version, and that will usually come with most of the hardware (bits and pieces like webcam) support that you need (obviously, there are some exceptions that make the rule). As long as you install updates, your camera should just work by itself.

A better way to do it would be to simply install the webcam application that comes available with Ubuntu by default. To do this, you will have to use the 'Add/Remove...' program that is at the bottom of the 'Applications' menu. As you asked, step-by-step instructions ensue...


[LIST]
[*]Open it by going Applications -> Add/Remove...
[*]Change the drop-down menu that says 'Canonical-maintained applications' to 'All Open Source applications'.
[*]Type in the text box 'Cheese' and wait for the results.
[*]Tick the box next to 'Cheese Webcam Booth'.
[*]Click 'Apply Changes' which is in the lower-right corner of the window, then click 'Apply'.
[*]Enter your password when prompted.
[*]Wait for all the installing to finish itself. It will all automatically download, extract and set itself up. Don't be surprised if it downloads more than 1 file, sometimes in Ubuntu programs 'depend' on other programs.
[*]When it is finished, you may want to make it so you only install the applications from the Ubuntu sponsors (Canonical) in future. So, when it is done, click 'Add/Remove more progams' and then change the drop down menu back to 'Canonical-maintained applications'. This step is optional.
[*]Then, close it, and go Applications -> Graphics -> Cheese Webcam Booth. It should open and detect the webcam, and you will be able to take photos and have fun and cool effects with it as well. This program is quite easy to use, so experiment a bit and have fun.
[/LIST]
 Hope this helps, and if you meant a digital camera from the wild... then this was all pointless. ;) Enjoy the magical world of Ubuntu, and I hope the extra info I gave you was helpful too. ):P

---

