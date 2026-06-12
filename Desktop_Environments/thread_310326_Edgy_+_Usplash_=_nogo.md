---
title: "Edgy + Usplash = nogo"
date: 2006-12-01
forum: Desktop Environments
---

### Post by Saubazi on 2006-12-01
Followed this one:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

(and read several discussions on the forum)
Installed 
usplash-dev
usplash-theme-ubuntu
usplash

packages when it did not work and still does not work.
I am stuck with this ugly splash that I got when I upgraded
to edgy. Closest to new bootsplash I got when I installed
usplash-theme-ubuntu and gave:

sudo update-alternatives --config usplash-artwork.so

When I chose usplash-theme I got a new splash screen - black and
white which said ubuntu on it - no progress bar anything.

When I make myself a new one according to some examples here from 
a png file and I choose such a new usplash with the aforementioned
command - I get this old ugly edgy splash again!?!?

And completely another thing - I had a second IDE disk therefore my 
SATA disk was the third one. Now I removed the second IDE and my SATA
is now the second. However, when I do sudo update-grub it always
changes the root entries to original:
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=UUID=9e4eb642-ce17-4f91-b21e-d464d962bb76 ro quiet splash vga=785
initrd          /initrd.img-2.6.17-10-generic
savedefault
boot

and I need to go everytime and change hd2,0 to hd1,0 - where can I fix this that it won't happen anymore?

---

### Post by x1a4 on 2006-12-21
> **Saubazi said:**
> Followed this one:
and I need to go everytime and change hd2,0 to hd1,0 - where can I fix this that it won't happen anymore?

If you don't have a command line text editor installed 
[indent] run Synaptic and install vim [/indent]

Then: 

1) Open a terminal
2) Run 

su

to enter super user mode

3) Backup the /boot/grup/menu.lst file

cp /boot/grub/menu.lst /boot/grub/menu.lst.bak

4) Using vim open the menu.lst file

vim /boot/grub/menu.lst

5) Place the cursor to the line you wish to change
6) Type the lowercase letter i to switch vim into interactive mode
7) Change (hd2,0) to (hd1,0)
8) Press the Esc (escape) button 
9) Type a colon, : 
10) Type 

wq

to write the file and quit vim

11) Reboot

---

