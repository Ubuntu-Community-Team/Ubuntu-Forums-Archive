---
title: "Getting started with gaming on Linux"
date: 2014-09-08
forum: Gaming &amp; Leisure
---

### Post by rolfUser on 2014-09-08
I was interested in using emulators to play games on my PC. So I went on Google and found this:

[http://linuxconfig.org/linux-dosbox-simulator-and-free-dos-games](http://linuxconfig.org/linux-dosbox-simulator-and-free-dos-games)

So it says I have to install "dosbox" and Wine in order to get started. The commands given did not work, so I changed them a bit like this:
```
[COLOR=#333333][FONT=Courier New]sudo apt-get install dosbox[/FONT][/COLOR]
```
```
[COLOR=#333333][FONT=Courier New]sudo apt-get install unrar unzip wine[/FONT][/COLOR]
```

So here's the problem. Hopefully someone would know what to make of this. 
I tried installing Doom 2. Here's what I get:

[ATTACH=CONFIG]256267[/ATTACH]

So ..... how do I log in? Should I just try something else? I don't know.

---

### Post by R33D3M33R on 2014-09-08
Blindly pasting commands into the command line may lead to a hacked system. To try out Doom, install chocolate-doom from the repository.

---

### Post by mooreted on 2014-09-08
Install Steam, you will find over 800 Linux games. As stated: don't randomly follow directions online, you're going to get yourself in trouble.

---

### Post by bizhat on 2014-09-09
First your download failed..  You need to find another source for Doom game. Make sure you download from trusted source, many include malware, virus etc.. with free downloads (mostly illegal downloads). I am not sure if doom 2 is paid or not, too old game, i think i played it in 1997 (maybe doom 1) along with below 100kb dangerous dave.

It is better install playonlinux

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

This software is available in Ubuntu Software center. Then you can use it to install DOS/Windows games. Check some youtube video on how to use PlayOnLinux. I have installed Quack3 yesterday and it worked properly on PlayOnLinux.

---

### Post by kostkon on 2014-09-09
Also, since you have already installed unrar, you can just double-click on the to open it with the archive manager.

---

### Post by rolfUser on 2014-09-13
Sorry if I kept anyone waiting for a response.
I went with PlayOnLinux and was impressed with everything I saw.
I tried installing a Sonic Fan Remix. It's almost done, but now it is asking me 

How much memory does your graphics board have?

Is it referring to my RAM? Is it referring to my SWAP partition?
My RAM is a 4GB DDR3 System Memory.
I understand that swap can be as high as 8gb in this case.
So.... should I just put 4096?

[ATTACH=CONFIG]256435[/ATTACH]

---

### Post by bizhat on 2014-09-13
It is asking about graphics card memory. It never asked me anything like that during few windows games i have installed on playonlinux. Not sure if it is specific to that game. All games i installed are from setup.exe i have, not the games listed in payonlinux as supported,

---

### Post by rolfUser on 2014-09-13
I went on Google about checking my graphics card memory
 [http://ubuntuforums.org/showthread.php?t=780900](http://ubuntuforums.org/showthread.php?t=780900)

---

### Post by rolfUser on 2014-09-13
> **rolfUser said:**
> Sorry if I kept anyone waiting for a response.
I went with PlayOnLinux and was impressed with everything I saw.
I tried installing a Sonic Fan Remix. It's almost done, but now it is asking me 

How much memory does your graphics board have?

Is it referring to my RAM? Is it referring to my SWAP partition?
My RAM is a 4GB DDR3 System Memory.
I understand that swap can be as high as 8gb in this case.
So.... should I just put 4096?

[ATTACH=CONFIG]256435[/ATTACH]

So referring back to this question in the quote above, what would work?

[ATTACH=CONFIG]256436[/ATTACH][ATTACH=CONFIG]256437[/ATTACH]

---

### Post by bizhat on 2014-09-14
Please post result of following commands

```

lshw -C Video
glxinfo | grep OpenGL

```

No need to take screenshot, you can copy and paste. Select text, right-click, select copy.

---

### Post by rolfUser on 2014-09-14
> **bizhat said:**
> Please post result of following commands

```

lshw -C Video
glxinfo | grep OpenGL

```

No need to take screenshot, you can copy and paste. Select text, right-click, select copy.

Bear in mind that I am still just a novice with Ubuntu.
```
lshw -C Video
```

outputs:
[ATTACH=CONFIG]256449[/ATTACH]

Followed by:
```
glxinfo | grep OpenGL
```
Which outputs:
[ATTACH=CONFIG]256450[/ATTACH]

But if I close and enter:
```
lshw -C Video glxinfo | grep OpenGL
```
I get:
[ATTACH=CONFIG]256451[/ATTACH]

I don't understand. Please explain.

---

### Post by bizhat on 2014-09-15
> **rolfUser said:**
> I don't understand. Please explain.

```

lshw -C Video

```

command shows what video card you have. 

```

glxinfo | grep OpenGL

```

command shows which driver software you are using.

Your graphics card is Radeon HD 8330, i googled to find information about this graphics card, i can't find much information like how much memory it got etc.. Most graphics card have its own memory. For example my Graphics card [Radeon HD 5670]("http://www.amd.com/en-gb/products/graphics/desktop/5000/5670") have 512 MB of memory.

Just found this

[http://www.techpowerup.com/gpudb/2205/radeon-hd-8330-igp.html](http://www.techpowerup.com/gpudb/2205/radeon-hd-8330-igp.html)

It says memory is shared between system memory, so this card have no dedicated memory. In that case, i think memory is set in BIOS (not sure). Check if you have option to set video memory in bios, if not set some random amount (below 256 MB) and see if that works.

---

### Post by rolfUser on 2014-09-21
Thanks everyone for your help. It looks like I learned a few important things. 
I have to move on now.

---

