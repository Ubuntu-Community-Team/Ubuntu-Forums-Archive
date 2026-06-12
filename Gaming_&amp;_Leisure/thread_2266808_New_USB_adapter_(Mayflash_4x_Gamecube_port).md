---
title: "New USB adapter (Mayflash 4x Gamecube port)"
date: 2015-02-25
forum: Gaming &amp; Leisure
---

### Post by vap1485 on 2015-02-25
Greetings all. The other day I ordered a PC/WII U gamecube controler adapter. The way it works is it lets you plug gamecube controlers through a USB port. 

in terminal, when I type lsusb it comes up as
Bus 003 Device 006: ID 0079:1843 DragonRise Inc. 


I'm using Ubuntu 14.04 x64

I have Dolphin Wii U emulator and other SNES emulators and none of them recognize the controler. All that happens is that the mouse moves around when I move the joystick.

[http://www.play-asia.com/gamecube-controller-adapter-for-wii-u-pc-usb-paOS-13-49-en-70-8h2n.html?ref=froogle&gclid=CLHXqdPI_cMCFUMV7AodTTEAaA](http://www.play-asia.com/gamecube-controller-adapter-for-wii-u-pc-usb-paOS-13-49-en-70-8h2n.html?ref=froogle&gclid=CLHXqdPI_cMCFUMV7AodTTEAaA)

[IMG]http://4u.pacn.ws/640/ly/gamecube-controller-adapter-for-wii-u-pc-usb-395375.2.jpg[/IMG]

---

### Post by vap1485 on 2015-03-03
anyone...?

---

### Post by Vladlenin5000 on 2015-03-03
Unsupported as of today.

---

### Post by Seph_Reed on 2015-11-02
So I've found this adapter code and installed it, but there is literally zero output upon running the file it makes.
[https://github.com/ToadKing/wii-u-gc-adapter](https://github.com/ToadKing/wii-u-gc-adapter)



**For those who want to get as far as I have**
*download libusb if you don't have it already (probably):[ http://sourceforge.net/projects/libusb/files/]("http://sourceforge.net/projects/libusb/files/")
*There's a file called INSTALL.  It's a text file with details on how to install it.
*Then download the adapter.  [https://github.com/ToadKing/wii-u-gc-adapter/archive/master.zip](https://github.com/ToadKing/wii-u-gc-adapter/archive/master.zip)
*Once you've unzipped it, open terminal and navigate to the folder it's in and run make.  It's readme has installation directions.
*You'll end up making an executable called `./wii-u-gc-adapter` which you can run.
*Before you run the executable you have to edit ~/.bashrc  
*There's a file called SDL_gamecontroller.txt which tells you what to do.  Use `sudo nano ~/.bashrc` to edit the file.


[SIZE=3]From here, I can't figure it out.
[SIZE=2]
If I run ./wii-u-gc-adapter in  PC mode, nothing happens.
If I run it in WiiU mode I get an error detailed here:
[https://github.com/ToadKing/wii-u-gc-adapter/issues/21](https://github.com/ToadKing/wii-u-gc-adapter/issues/21)


The entirety of the code for this is one small C file:
[https://github.com/ToadKing/wii-u-gc-adapter/blob/master/wii-u-gc-adapter.c](https://github.com/ToadKing/wii-u-gc-adapter/blob/master/wii-u-gc-adapter.c) 
So I imagine it shouldn't be too difficult to fix.  But I'm pretty foreign to the whole thing.

Any Help would be greatly appreciated.
[/SIZE]
[/SIZE]

---

### Post by Seph_Reed on 2015-11-02
So I dug around in the wii-u-gc-adapter code for a bit.

I was getting an error message, that didn't say much.  So I modded the code to give me the error code, and then again to give me the error name:
[TABLE="class: memname"]
[TR]
[TD]libusb_error_name [/TD]
           [TD]([/TD]
           [TD="class: paramtype"]int 
[/TD]
           [TD="class: paramname"]*error_code*[/TD]
[TD])[/TD]
           [TD][/TD]
[/TR]
[/TABLE]


The Error?

Insufficient priveledges.

So I ran sudo ./wii-u-gc-adapter.

Everything works.  I feel dumb.  Ish.  Smart enough to find my dumb, too dumb to not have to be smart.

---

### Post by isaac19 on 2016-03-25
I tried to run the make in the folder, but I got the following error message. Please help.

Package libusb-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libusb-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libusb-1.0' found
cc -c -o wii-u-gc-adapter.o wii-u-gc-adapter.c -Wall -Wextra -pedantic -Wno-format -std=c99   -O2
wii-u-gc-adapter.c:21:20: fatal error: libusb.h: No such file or directory
 #include <libusb.h>
                    ^
compilation terminated.
Makefile:16: recipe for target 'wii-u-gc-adapter.o' failed
make: *** [wii-u-gc-adapter.o] Error 1

---

