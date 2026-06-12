---
title: "Asus Driver install"
date: 2008-12-12
forum: General Help
---

### Post by headbuster on 2008-12-12
Hello!
I am new to Ubuntu and would like to know how to install the drivers because I can't use the internet...and listen to music for example.
I have a CD and there is a Linux folder in which there is a Audio and LAN folder. I extract the file in the LAN folder and read the readme but can't manage to install the drivers.
Here is the readme
```
<Requirements>

  - kernel source tree (supported versions 2.4.x or 2.6.x)
  - compiler/binutils for kernel compilation

<Quick installation>
	Unpack the tarball :
		tar vzxf RTL8168B_8100E_linuxdrv_vxx.zip

	Change to the directory:
		cd RTL8168B_8100E

	Use the installation script:
		./build RTL8168B (or RTL8100E)


<Normal install with proper kernel settings>

  Unpack the tarball :
	tar vzxf RTL8168B_8100E_linuxdrv_vxx.zip

  Change to the directory:
	cd RTL8168B_8100E

  If you are running the target kernel, then you should be
  able to do :

	make clean modules	(as root or with sudo)
	mv ./src/rtl_ethernet.o ./srcr/RTL8168B.o (or ./src/RTL8100E.o)
	make install
	depmod -a
```

I try quick install but when I get to ./build RTL8168B and press enter in the terminal...I get lots of errors like no such file or directory...can't create something Error 1 Error 2 and others.
So could you please guide me how to install them and is there a way to isntall them without the terminal
Thanks.

---

### Post by headbuster on 2008-12-12
Come on guys!
Help please :S

---

