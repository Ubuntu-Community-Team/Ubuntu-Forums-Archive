---
title: "X Server"
date: 2006-02-09
forum: Desktop Environments
---

### Post by gmr310 on 2006-02-09
Firstly, I did do a search and found one unawnsered topic, so im posting for my self. Anyways, I just finnished installing Ubuntu and when ever I start up the computer, it loads up like it should (i think) and then when it gets to the login prompt (text only) it flashes a couple of times, and then an error pops up [IMG]http://imageserver4.textamerica.com/user.images.x/63/IMG_464863/_0209/T520060209065045552.jpg[/IMG]
If i hit "yes" this comes up [IMG]http://imageserver4.textamerica.com/user.images.x/63/IMG_464863/_0209/T52006020906520854.jpg[/IMG]
After those two messages, it goes back to the login, [IMG]http://imageserver4.textamerica.com/user.images.x/63/IMG_464863/_0209/T52006020906532110.jpg[/IMG]
If you have anyideas, that would be greatly apreciated, Thanks!

BTW, dont ask about the computer name... I was bored and couldnt think of anything (and I didnt think anyone else would see it).

---

### Post by localzuk on 2006-02-09
Hi, could you provide us with some more details of your system such as:

what graphics card you have
what your /etc/X11/xorg.conf file looks like?

Cheers

---

### Post by gmr310 on 2006-02-09
I have an ATI 9250 (PCI) and as far as my /etc/X11/xorg.conf, I havent touched it, so what ever the default is... If I was anywhere near my computer I would let you know... but sadly im not

---

### Post by localzuk on 2006-02-10
Every xorg.conf file will be different depending on the card, monitor, keyboard etc... So it would still be mighty useful to see a copy of it.

Login on the terminal and type

```

sudo dpkg-reconfigure xserver-xorg

```

When it asks you questions, choose 'ATI' from the menu of drivers and just agree to the rest.
If this does not work, choose the 'Vesa' driver.

The first option should get the card working properly, the second one however will not provide any acceleration (it will just be a plain SVGA graphics card). It will however provide you with a working graphical desktop.

The other option is to take a look on the forums for other threads regarding ATI graphics cards and problems. In particular I would advise a look at:
[http://ubuntuforums.org/showthread.php?t=75378&highlight=fglrx](http://ubuntuforums.org/showthread.php?t=75378&highlight=fglrx)
as it provides another driver for you to try - this one provided by ATI so *should* work...

---

### Post by gmr310 on 2006-02-10
ok, i tryed the sudo dpkg-reconfigure xserver-xorg thing, and it still didnt work, I think if I take out the pci card, and let it run off of the intigrated it woll work fine, but I didnt have time to try before class this morning, i will update you and let you know...

---

### Post by gmr310 on 2006-02-10
[QUOTE=gmr310]ok, i tryed the sudo dpkg-reconfigure xserver-xorg thing, and it still didnt work, I think if I take out the pci card, and let it run off of the intigrated it woll work fine, but I didnt have time to try before class this morning, i will update you and let you know...[/QUOTE]

Yay for double posting! anyways, so I reinabled the onboard video card in the bios, and now its working fine... sooooooo... i guess at least i got it working. Well, thanks for the help...

Robert
Gmr310

---

