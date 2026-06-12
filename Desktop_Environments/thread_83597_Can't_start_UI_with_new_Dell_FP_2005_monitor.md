---
title: "Can't start UI with new Dell FP 2005 monitor"
date: 2005-10-29
forum: Desktop Environments
---

### Post by staticten on 2005-10-29
hi, i just bought a new monitor and i can't seem to get to the log in UI part of Ubuntu. I don't have my old monitor anymore. My new Dell FP2005 widescreen can support up to 1680x1050 resolution. What can i do? thanks.

i'm basically clueless right now.

thanks again and hope to hear from this community.

---

### Post by codejunkie on 2005-10-29
[quote=staticten]hi, i just bought a new monitor and i can't seem to get to the log in UI part of Ubuntu. I don't have my old monitor anymore. My new Dell FP2005 widescreen can support up to 1680x1050 resolution. What can i do? thanks.

i'm basically clueless right now.

thanks again and hope to hear from this community.[/quote]
you could try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```  this will reconfigure the xserver they way the installer did.

---

### Post by staticten on 2005-10-29
thanks codejunkie, 

but, what exactly or how do i do this, with this code?

i'm not really an expert yet, just new to Linux. (about a month)

thanks....

have a great day!

---

### Post by staticten on 2005-10-29
what's really happening is, 

i start the computer, Grub starts and ofcourse i choose Ubuntu 5.04

then it actually got to all the loading text part of it, when it says Ubuntu starting, 
However, when it gets to the log-in part, nothing is showing up on my screen, i'm assuming it doesn't recognize/support or not configured for my new monitor, so i can't even get in....

thanks, and I love Ubuntu

:-)

---

### Post by codejunkie on 2005-10-29
[quote=staticten]what's really happening is, 

i start the computer, Grub starts and ofcourse i choose Ubuntu 5.04

then it actually got to all the loading text part of it, when it says Ubuntu starting, 
However, when it gets to the log-in part, nothing is showing up on my screen, i'm assuming it doesn't recognize/support or not configured for my new monitor, so i can't even get in....

thanks, and I love Ubuntu

:-)[/quote] let me see if im understanding this correctly it's not even showing anything just a blackscreen right, if so then try hitting ctrl+alt+F1 when you get to the black screen this should bring you to a text based terminal where you can login using your username&password once you've logged in enter
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by staticten on 2005-10-29
hi codejunkie, 

i just tried doing that, but hitting ctrl+alt+F1 doesn't do anything, or won't even bring me to the text based terminal...so i can't log in and enter the code you've given.

?

---

### Post by codejunkie on 2005-10-29
[quote=staticten]hi codejunkie, 

i just tried doing that, but hitting ctrl+alt+F1 doesn't do anything, or won't even bring me to the text based terminal...so i can't log in and enter the code you've given.

?[/quote]
well im a little lost on this one,  so im taking a wild guess here if your using the the dvi connector on your video card, i remember reading somewhere on the forum that some people couldn't get there monitor working using the dvi connector on some video cards, if your using the dvi connecter you might want to search the forum on enabling the dvi connector on your video card or try a dvi to vga adapter and use the vga output on your video card. if your already using the vga connector you could try using the ubuntu live cd and see if that recognizes your monitor if it does you could copy the /etc/X11/xorg.conf file from the live cd to a usb thumbdrive and copy it over to your install, other than that i don't really know what else to do.

---

### Post by staticten on 2005-10-29
thanks dude, 

i'll try that and in the worst case, i'll probably just try to intall 5.10, if it'll let me do it.....

i already have Grub, when i install a 5.10 over my 5.04, should i include another grub, or should i just leave it as is?

??

but yeah, thanks again.

---

### Post by codejunkie on 2005-10-30
[quote=staticten]thanks dude, 

i'll try that and in the worst case, i'll probably just try to intall 5.10, if it'll let me do it.....

i already have Grub, when i install a 5.10 over my 5.04, should i include another grub, or should i just leave it as is?

??

but yeah, thanks again.[/quote]
if your planning on upgrading to breezy the installer will make the changes to grub so you shouldn't have to make any changes to it.

---

### Post by staticten on 2005-10-30
cool, thanks!

---

