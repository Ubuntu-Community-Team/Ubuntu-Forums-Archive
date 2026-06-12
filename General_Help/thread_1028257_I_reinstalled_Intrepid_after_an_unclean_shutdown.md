---
title: "I reinstalled Intrepid after an unclean shutdown"
date: 2009-01-02
forum: General Help
---

### Post by lionfox on 2009-01-02
I reinstalled intrepid after an unclean shutdown, because i did not know how to enter the maintainance shell to do a manual fsdsk when the automatic one kept freezing at 6 percent.

When I did a guided install and had ubuntu take up the whole hard disk, the process went fine and completed, or so I thought. Now it will not boot and just says grub, there is no graphic menu. Ubuntu is my only OS.

What do I do to get ubuntu to boot? I'm new to linux, but not computers.

how do i get grub to boot my OS?

---

### Post by caljohnsmith on 2009-01-02
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. 

If you don't have internet connectivity when using the Live CD, instead right-click [this link]("http://home.comcast.net/~ubuntu_grub/boot_info_script.txt") to the script in your web browser, choose "Save link as...", save the "boot_info_script.txt" file, transfer it to your Ubuntu desktop on the Live CD via USB stick, floppy, or however you want to do it, and then run:
```
sudo bash ~/Desktop/boot_info_script.txt
```
The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by lionfox on 2009-01-03
thanks, I appreciate the help and I will try it as soon as I can.

---

