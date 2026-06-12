---
title: "Ubuntu 11.04 &quot;Pink Screen&quot;"
date: 2011-06-12
forum: Desktop Environments
---

### Post by Ecaz on 2011-06-12
I just installed Ubuntu 11.04 from my USB drive. 
The installation went perfect but when I restarted my PC to log in all I could see was a pink screen.
Here is an image,
[Pink Screen Img 1]("http://ecazs.net/dump/2011-06-12%2017.18.24.jpg")

And if you look at this image,
[Pink Screen Img 2]("http://ecazs.net/dump/2011-06-12%2017.18.39.jpg")
at the very top you can see how there is a thin line where the colors differ from the pink, I can see my mouse move up there, so it's almost like it's a pink layer on top of the desktop.

I tried to restart it again and I got the same pink screen but this time it was flickering intensively, white to pink.

I don't know what to do :(

---

### Post by Ecaz on 2011-06-12
I have Radeon HD6870 if it's to any help.

---

### Post by wildmanne39 on 2011-06-12
> **Ecaz said:**
> I just installed Ubuntu 11.04 from my USB drive. 
The installation went perfect but when I restarted my PC to log in all I could see was a pink screen.
Here is an image,
[Pink Screen Img 1]("http://ecazs.net/dump/2011-06-12%2017.18.24.jpg")

And if you look at this image,
[Pink Screen Img 2]("http://ecazs.net/dump/2011-06-12%2017.18.39.jpg")
at the very top you can see how there is a thin line where the colors differ from the pink, I can see my mouse move up there, so it's almost like it's a pink layer on top of the desktop.

I tried to restart it again and I got the same pink screen but this time it was flickering intensively, white to pink.

I don't know what to do :(
Hi is your system booting all the way or is it hanging at boot? If not booting look at this link.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Ecaz on 2011-06-13
It's booting because I can move the mouse at the very top of that pink screen. However if I press <Ctrl><Alt><F1> I just get a black screen and then the computer restarts by itself.

I tried pressing shift during boot but nothing happened so I guess I'll try that.

I tried running it directly from my USB, it only got the loading screen of Ubuntu then it crashed...

---

### Post by mswift on 2011-06-13
That pink screen, is that before or after the boot loader menu?

---

### Post by Ecaz on 2011-06-13
OK, here.

I chose to start with Ubuntu in the boot instead of Windows 7.
I get to the Ubuntu loading screen, a text that reads Ubuntu and then a couple of dots underneath to show the loading progress.

And normally where the log in screen would be I have a pink/purple overlay on the screen, I can still see my mouse at the very top of the screen but I can't do anything.

I just re-installed it using a CD, I tried the "Try it first" feature and that worked perfectly but when I installed it and on the first boot I get the same freaking problem. 
Except this time, it's flickering like hell.

---

### Post by mswift on 2011-06-13
OK.
When you boot your pc, press e (for edit) 
when you see the grub bootloader menu.

Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place.

Press Ctl+x to boot.

---

### Post by Ecaz on 2011-06-13
Ok I did and I got a black screen and it started loading a bunch of stuff then it stopped after awhile and nothing more happened.

I could do Ctrl Alt F1 on there though.

---

### Post by mswift on 2011-06-13
> I could do Ctrl Alt F1 on there though.

Did you try logging in and running gdm or startx ?

---

### Post by Ecaz on 2011-06-13
> **mswift said:**
> Did you try logging in and running gdm or startx ?

I logged in but I don't know what gdm or startx is :S

---

### Post by mswift on 2011-06-13
> I logged in but I don't know what gdm or startx is :S


No bother. 

Type

```
sudo gdm
```

Or

```
sudo startx
```

---

### Post by Ecaz on 2011-06-13
If I do gdm i get

Failed to acquire org.gnome.Displaymanager 

and

Could not acquire name; bailing out

Startx gives me a bunch of stuff but i did notice this

Failed to load module fglrx module does not exist
Chipset : amd radeon hd 6800 series chipid. 0x6738 requires KMS 
Screens found but none have a usable configuration.

Fatal server error 
no screens found

Those where all marked as EE

---

### Post by mswift on 2011-06-13
If you have a working internet, you can try installing 
the fglrx Amd graphics driver.

```
sudo apt-get install fglrx
```

Then restart and try again.

---

### Post by Ecaz on 2011-06-13
I tried, can't really remember what it said but something about the package being obsolete or that it could only be access from another source :S

---

### Post by mswift on 2011-06-13
That's bad, it means your internet is not working.

You could try booting with the vesa driver enabled:

```
sudo pico /etc/X11/xorg.conf

```

then type 
Device "vesa"

and exit pico with Ctrl+x (anser yes to save the file.

Then type sudo startx again.

---

### Post by Ecaz on 2011-06-13
It says Device isn't a valid keyword in this section and then it tells me i have parse error in that file

---

### Post by mswift on 2011-06-13
I'm sorry, I messed that up. It's been years I had to fiddle in xorg.conf.

Here is how your xorg.conf should look like:

```
Section "Device"
        Driver      "vesa"
EndSection

```

---

### Post by Ecaz on 2011-06-13
Now it says that line 3 needs an identifier line

---

### Post by mswift on 2011-06-13
That's strange.

Please type

```
sudo dpkg-reconfigure -phigh xserver-xorg
```


Then please paste the content of your xorg.conf here.

---

### Post by Ecaz on 2011-06-13
It says xorg is an unknown option

---

### Post by mswift on 2011-06-13
Sorry, I give up.
The problem is that your graphic card is very new and thus not very god supported yet.

Please read [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
for further instructions how to enable fglrx. 

Good luck.

---

### Post by Ecaz on 2011-06-13
How come it works on the LiveCD then?

---

### Post by mswift on 2011-06-13
That is the one thing I've been wondering since
I read your thread.

How on earth was he able to install this thing.:confused:

---

### Post by Ecaz on 2011-06-13
> **mswift said:**
> 
How on earth was he able to install this thing.:confused:

Mighty weird, but I did read somewhere that the current Linux Kernel doesn't have "built-in" drivers for the HD 6800 series

---

### Post by wildmanne39 on 2011-06-13
> **mswift said:**
> That is the one thing I've been wondering since
I read your thread.

How on earth was he able to install this thing.:confused:
Hi, I am sure it is because when you run it from the cd it has a opensource drive it uses for video, then when you boot you have to install one, if you follow the link I gave you in my earlier post it might get you going, it is for people with your problem.

---

### Post by Ecaz on 2011-06-13
I can't follow that link because I only have one computer and I don't feel like writing down everything by hand.

---

### Post by vikram5 on 2011-09-28
I had a similar problem for my  Radeon 6450 card, but it worked fine for the previous version of this driver: "AMD Catalyst™ 11.8 Proprietary Linux x86 Display Driver". Here are the steps to download and install it:


[LIST]
[*]Download the AMD Catalyst™ 11.8 Proprietary Linux x86 Display Driver
[/LIST]
```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-8-x86.x86_64.run
```

If you don't have 'wget', install it by
```
sudo apt-get install wget
```  


[LIST]
[*]Make it executable, if not already
[/LIST]
```
chmod +x ati-driver-installer-11-8-x86.x86_64.run
```


[LIST]
[*]Run it and follow on-screen instructions to install the driver
[/LIST]
```
sudo ./ati-driver-installer-11-8-x86.x86_64.run
```

If you can not even get the command prompt, follow instructions posted by "[mswift]("http://ubuntuforums.org/member.php?u=109039")"

[LIST=1]
[*]When you boot your pc, press e (for edit) when you see the grub bootloader menu.
[*]Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place.
[*]Press Ctl+x to boot.
[/LIST]

Hope this helps!

---

