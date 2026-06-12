---
title: "First Ubuntu install, coupla problems"
date: 2006-10-01
forum: Desktop Environments
---

### Post by except on 2006-10-01
Hi there!

I just installed ubuntu edgy AMD 64 for my Intel E6600 running on an MSI motherboard with an Asus Nvidia video card.
I havn't tried linux for years, and I thought it would be interesting to get it running and see what this community's been up to. I mostly use autocad and photoshop, so its no real use to me yet, hence the edgy install, to try out all the new stuff.
After installing I cannot seem to do the following:

1) Change my default os to windows
2) Change the resolution of the screen to 1280x1024
3) Get internet to work


1: I tried finidng the boot-admin tool, but if I type it into the console or shell (as suggested by the help) it can't find it. According to the help it is supposed to be in applications - system tools, but there's no such thing. When I try to gedit the menu.lst file, it says I do not have permission to do so, eventhough as far as I know, ubuntu only gave me one user name/password when installing, and I wouldnt know what the root password would be.

2: Seems like the driver is not detecting the display properly. What should I do?

3: Every time I enter my ip/gateway info, press Ok and try to connect, it doesn't work. And when I enter the settings agin, the gateway box is empty.

And additional question:
Will windows XP run slower because ubuntu is installed? I wouldn't think so, but in another thread that seems to be common knowledge?

Also, those neat 3D interface tricks, how do I access them? I've ssen videos of great interfaces on ubuntu (xgl?) but they don;t seem to be enabled by default.

Thanks for all you help.

---

### Post by rbprogrammer on 2006-10-01
when you say you want to have the default OS to be windows, do you mean load up windows automatically without having to do anything?  

if so, i would just go into liunx and change in /boot/grub/menu.lst the "default" option.  this is assuming you use grub as the bootloader. for me, its around line 14 and there is even a timeout option right after it.

as for the resolution problem, i had to install the package 915resolution but that may only work for certain Intel graphic cards.  sorry if that doesnt help.

and for getting the internet to work, that would be more complicated.  for me at school i had to get an IP address, DNS addresses, and some other stuff for the internet to work. but at home, i just have to turn on my wireless device in my laptop and click connect.

but i'm sure just changing the menu.lst file would help you for that one problem.

---

### Post by offramp13 on 2006-10-01
1. To edit the menu.lst file, do this:
```
sudo gedit /boot/grub/menu.lst
```
the password should be the one you use to log in.

2. To change the screen resolution do this:
```
sudo dpkg-reconfigure xserver-xorg
```
and follow through the steps, towards the end it asks you what resolutions you want, again the pasword is what you use to log in.

3. I dont know exactly what you mean about your network problems, some more info might help.

And about fancy themes, XGL/Compiz looks pretty sweet, but is kind of a pain to install. I would recomend using automatix bleeder if you are a noob still.

---

### Post by except on 2006-10-01
Thank you guys but,

the boot problem,
like I said, I do not have permission to change the menu.lst. It doesn't ask me for a password or user name. I just log in using my preconfigured user/pass I entered when I installed ubuntu. It won't let me save the file.

the internet problem:
it's not knowing the setting that's the problem. It's that the gateway setting clears itself. Obvisouly without a gateway it won't work.

---

### Post by except on 2006-10-01
Ok, I managed to change the menu.lst, same way i treid before, but it allowed me to save this time.
The resolution thing however went wrong. I did what you suggested and reconfigured X, but now, when I start up, I indeed get the login screen in 1280x1024, but after entering username and password, the screen turns black and after a second or two the login screen comes back up, as if nothing happened. I can't do anything anymore except going into a fail-safe terminal.

---

### Post by except on 2006-10-02
Bumpyness

---

### Post by offramp13 on 2006-10-02
i would suggest running ```
sudo dpkg-reconfigure xserver-xorg
``` again (you can do so from the failsafe terminal), and you have an nVidia card so choose either nv or nvidia, i had a similar problem a while back. I used vesa, then once in ubuntu i installed all of my graphics drivers and then popped open my xorg.conf file and changed it to say nvidia. also if you are spat out to a command line, you might be able to go into the graphic interface if you type ```
startx
``` it wont fix your problem, but it will atleast get you into ubuntu. sorry if i cant help! if you have any other questions/problems feel free to ask.

---

