---
title: "Bootsplash images"
date: 2009-01-28
forum: General Help
---

### Post by Bankai56 on 2009-01-28
I wanted to install a picture in the Grub directory to let it look cooler.:D
How do you do that ?
I am new sorry.
And how do i install a diffrent bootupscreen for Ubuntu
Thx
Bankai

---

### Post by UbuntuNerd on 2009-01-28
just be careful you can damage things.
[https://wiki.ubuntu.com/Artwork/Incoming/Hardy/Alternate/Grub]("https://wiki.ubuntu.com/Artwork/Incoming/Hardy/Alternate/Grub")

---

### Post by Bankai56 on 2009-01-29
Ok i did that and nothing happend.:?:?:?
how do i check the drive ubuntu is installed on the (hd0,0)?

---

### Post by UbuntuNerd on 2009-01-29
try this
[HTML]sudo fdisk -l[/HTML]
also look in this page
[http://ubuntuforums.org/showthread.php?t=510972]("http://ubuntuforums.org/showthread.php?t=510972")

---

### Post by Bankai56 on 2009-01-29
ok i tried that and this came i have no idea what to do now.
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8683    69746166    7  HPFS/NTFS
/dev/sda2            8684       13073    35262675    f  W95 Ext'd (LBA)
/dev/sda3           13074       14529    11695320   83  Linux
/dev/sda4           14530       14593      514080   82  Linux swap / Solaris
/dev/sda5            8684       13073    35262643+   7  HPFS/NTFS
I found something called startup manager and i am trying to do it with that.
Just want to know what the above means for the future :D
THX

---

### Post by Bankai56 on 2009-01-29
Ok Startup manager did nothing good. Didn't work. Know i dont even have a looding screen of Ubuntu 8.10. I only see so somands running down the screen and then Ubuntu is loaded. Know i need a lot of help.
The way you told me to do it workes fine in Ubuntu 8.04. But since i have 8.10 it doesn't work anymore.
Any ideas?
Thx:D

---

### Post by LinuxGuy1234 on 2009-01-29
> **Bankai56 said:**
> And how do i install a diffrent bootupscreen for Ubuntu
Thx
Bankai

First, press Alt+F2, then type xterm in the text box, then press Enter.
Now do:
```
sudo apt-get install libusplash-dev build-essential libbogl-dev
```
then press Enter. Enter your password if prompted.
Say Y, then let apt-get do it's work.
Now use your favorite graphics program to make a PNG the size of your monitor, at least 256 colors (GIMP can do this, so does Kolourpaint).
Then do this in the xterm:
```
pngtousplash yourimagefile.png > yourusplash.c
gcc -I/usr/include/usplash -I/usr/include/bogl -o yourusplash.o -fPIC -c yourusplash.c
gcc -shared -Wl,-soname,usplash-artwork.so yourusplash.so -o yourusplash.so
sudo mkdir -p /usr/local/lib/usplash/
sudo cp yourusplash.so /usr/local/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourusplash.so 55
# select your usplash here after typing this command then pressing enter:
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)
```

Long, I know...

---

### Post by Bankai56 on 2009-01-30
Sorry i just broke my left hand so typing is a bit difficult :)
is there a faster way because cant copy into exterm and typing hurts.
[http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html)
I tried that and know have a totaly ugly splash ad i was aimingg to chnag thegrub menu when i coos betwen dxp linx

---

### Post by LinuxGuy1234 on 2009-01-31
> **Bankai56 said:**
> Sorry i just broke my left hand so typing is a bit difficult :)
is there a faster way because cant copy into exterm and typing hurts.
[http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html)
I tried that and know have a totaly ugly splash ad i was aimingg to chnag thegrub menu when i coos betwen dxp linx

Try substituting "xterm" for "konsole" or "gnome-terminal".

---

### Post by Bankai56 on 2009-01-31
ok i did that but i forgot to change the yousplashimage.png an now that it doesnt have a splashimages it just shows the text how do i reverse that.
And one more qeustion.
How do you come up with all these commands? For me most of them look like mummbojumbo:D:D
Do you learn them by heart or do you just know them?
Thx

---

### Post by LinuxGuy1234 on 2009-02-01
> **Bankai56 said:**
> ok i did that but i forgot to change the yousplashimage.png an now that it doesnt have a splashimages it just shows the text how do i reverse that.
And one more qeustion.
How do you come up with all these commands? For me most of them look like mummbojumbo:D:D
Do you learn them by heart or do you just know them?
Thx

1. ```
sudo update-alternatives --config usplash-artwork.so

```
2. I dunno... I'll explain.
**sudo** is the program in Ubuntu to get administrator status. **gcc** is the C compiler of the **GNU Compiler Collection**.
**pngtousplash** converts a PNG file to a usplash-enabled .c file, which is then compiled into a shared library.
**cp** CoPies files.
**mkdir** MaKes DIRectories.
**dpkg-reconfigure** reconfigures a piece of software.
**update-alternates** alters symlinks to help you pick your best software, eg. vi could execute nvi or vim.

---

### Post by Bankai56 on 2009-02-02
The repair worked and i tried to install the theme again. but it didnt work .
Here is what i wrote.
```
pngtousplash /home/alwin/Desktop/Stuff/sourcetheme/chrometext_1024_768.png > yourusplash.c
gcc -I/usr/include/usplash -I/usr/include/bogl -o yourusplash.o -fPIC -c yourusplash.c
gcc -shared -Wl,-soname,usplash-artwork.so yourusplash.so -o yourusplash.so
sudo mkdir -p /usr/local/lib/usplash/
sudo cp yourusplash.so /usr/local/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourusplash.so 55
# select your usplash here after typing this command then pressing enter:
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)


alwin@Sleeping-Forest:~$ sudo update-alternatives --config usplash-artwork.so
[sudo] password for alwin: 

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
alwin@Sleeping-Forest:~$ pngtousplash /home/alwin/Desktop/Stuff/sourcetheme/chrometext_1024_768.png > yourusplash.c
alwin@Sleeping-Forest:~$ gcc -I/usr/include/usplash -I/usr/include/bogl -o yourusplash.o -fPIC -c yourusplash.c
alwin@Sleeping-Forest:~$ gcc -shared -Wl,-soname,usplash-artwork.so yourusplash.so -o yourusplash.so
gcc: yourusplash.so: No such file or directory
alwin@Sleeping-Forest:~$ sudo mkdir -p /usr/local/lib/usplash/
alwin@Sleeping-Forest:~$ sudo cp yourusplash.so /usr/local/lib/usplash
cp: cannot stat `yourusplash.so': No such file or directory
alwin@Sleeping-Forest:~$ sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourusplash.so 55
alwin@Sleeping-Forest:~$ # select your usplash here after typing this command then pressing enter:
alwin@Sleeping-Forest:~$ sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
alwin@Sleeping-Forest:~$ sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-11.27 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-11.27 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic          
 *  fglrx (8.543)...                                                            fglrx (8.543): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

```
The first part is just what i copied into the terminal. 
I hope you recognise whats wrong i dont see a damn thing :D

---

### Post by LinuxGuy1234 on 2009-02-02
> **Bankai56 said:**
> The repair worked and i tried to install the theme again. but it didnt work .
Here is what i wrote.
```
pngtousplash /home/alwin/Desktop/Stuff/sourcetheme/chrometext_1024_768.png > yourusplash.c
gcc -I/usr/include/usplash -I/usr/include/bogl -o yourusplash.o -fPIC -c yourusplash.c
gcc -shared -Wl,-soname,usplash-artwork.so yourusplash.so -o yourusplash.so
sudo mkdir -p /usr/local/lib/usplash/
sudo cp yourusplash.so /usr/local/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourusplash.so 55
# select your usplash here after typing this command then pressing enter:
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-$(uname -r)


alwin@Sleeping-Forest:~$ sudo update-alternatives --config usplash-artwork.so
[sudo] password for alwin: 

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
alwin@Sleeping-Forest:~$ pngtousplash /home/alwin/Desktop/Stuff/sourcetheme/chrometext_1024_768.png > yourusplash.c
alwin@Sleeping-Forest:~$ gcc -I/usr/include/usplash -I/usr/include/bogl -o yourusplash.o -fPIC -c yourusplash.c
alwin@Sleeping-Forest:~$ gcc -shared -Wl,-soname,usplash-artwork.so yourusplash.so -o yourusplash.so
gcc: yourusplash.so: No such file or directory
alwin@Sleeping-Forest:~$ sudo mkdir -p /usr/local/lib/usplash/
alwin@Sleeping-Forest:~$ sudo cp yourusplash.so /usr/local/lib/usplash
cp: cannot stat `yourusplash.so': No such file or directory
alwin@Sleeping-Forest:~$ sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/local/lib/usplash/yourusplash.so 55
alwin@Sleeping-Forest:~$ # select your usplash here after typing this command then pressing enter:
alwin@Sleeping-Forest:~$ sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
alwin@Sleeping-Forest:~$ sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-11.27 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-11.27 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-11-generic          
 *  fglrx (8.543)...                                                            fglrx (8.543): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

```
The first part is just what i copied into the terminal. 
I hope you recognise whats wrong i dont see a damn thing :D

Typo here:
```
alwin@Sleeping-Forest:~$ gcc -shared -Wl,-soname,usplash-artwork.so yourusplash.so -o yourusplash.so
```
Fixed command:
```
gcc -shared -Wl,-soname,usplash-artwork.so -o yourusplash.so yourusplash.o
```

---

### Post by Bankai56 on 2009-02-03
Sorry that i bother, but i just had to reinstall ubuntu and does this still apply?

---

### Post by LinuxGuy1234 on 2009-02-08
> **Bankai56 said:**
> Sorry that i bother, but i just had to reinstall ubuntu and does this still apply?

yes.

---

### Post by LinuxGuy1234 on 2009-02-08
> **pmicheal said:**
> I'm sorry, but I can't understand the whole procedure discussed in previous posts :(

I want to change the boot screen with my company's logo. Is there any step by step guide to achieve this. Thanks in advance. :)

What bootscreen? GRUB splashscreen or Ubuntu splashscreen?

---

### Post by johnjohn2 on 2009-02-08
> **LinuxGuy1234 said:**
> What bootscreen? GRUB splashscreen or Ubuntu splashscreen?

Startup manager works for me

---

