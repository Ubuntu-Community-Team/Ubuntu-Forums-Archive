---
title: "Install some logic."
date: 2009-04-07
forum: General Help
---

### Post by Phantom_yo on 2009-04-07
Hello,

I'm new to using Ubuntu as my sole OS. So far I've solved problems using previous forum posts which has been great.

I was, however, hoping for an explanation as to *why* my last fix worked. Basically, I installed Gnomad2 for use with my Creative mp3 player. It didn't work at first ("No jukebox found on usb bus") but when I opened it up by typing sudo gnomad2 in the terminal it worked straight away. Could someone explain why it worked this way or push me in the right direction. I want to try and learn properly rather than typing code blindly.

Thanks.

---

### Post by schmidtbag on 2009-04-07
I think its great you want to learn about what you're doing, but I don't think its so great for you to just do something becaue you don't have any idea as to what it is.

But to answer your question, sudo allows any command to be run under root, and therefore you have all privelages.  I'm not sure if gnomad2 is graphical or not, but if you want to run it so it always works, then create a launcher saying "gksu gnomad2".  gksu is basically the same thing as sudo but for graphical programs.

---

### Post by kellemes on 2009-04-07
> **Phantom_yo said:**
> Hello,

I'm new to using Ubuntu as my sole OS. So far I've solved problems using previous forum posts which has been great.

I was, however, hoping for an explanation as to *why* my last fix worked. Basically, I installed Gnomad2 for use with my Creative mp3 player. It didn't work at first ("No jukebox found on usb bus") but when I opened it up by typing sudo gnomad2 in the terminal it worked straight away. Could someone explain why it worked this way or push me in the right direction. I want to try and learn properly rather than typing code blindly.

Thanks.

Strange, an application like this should not be run with super-user privileges.
Please open a terminal window and type (without sudo)..
```
gnomad2
```

Can you post the output you get in the terminal window?

---

### Post by Phantom_yo on 2009-04-08
All it says is...

"PDE device NULL"

opposed to "This is a PDE device" when run with sudo.

---

### Post by ShaunG on 2009-04-08
This is quite odd. It works fine for me when run either as root or not. 

[ASIDE]
It is not without it's bugs however, i find that I must click file->quit to close gnomad2. If I click on the x in the upper right corner gnomad2 crashes and freezes my zen.
[/ASIDE]

---

