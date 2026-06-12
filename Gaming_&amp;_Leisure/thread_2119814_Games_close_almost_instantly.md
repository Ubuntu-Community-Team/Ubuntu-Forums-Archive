---
title: "Games close almost instantly?"
date: 2013-02-24
forum: Gaming &amp; Leisure
---

### Post by mvdonofrio on 2013-02-24
Okay, so I'm fairly new to this whole idea of Linux and Ubuntu, but I'm not terribly helpless when it comes to computers in general. Despite this, I'm having an issue with launching any kind of game. I downloaded and installed both Amnesia: The Dark Descent, and Bastion. For both games, give or take 10 seconds after it launches and the games start to load, they just close and there's no error message or anything telling me why exactly this is happening. Has anyone run into any issues like this or have any idea how to fix it? I've heard great things about both games and would be sorely disappointed if this problem cannot be resolved. Thanks in advance!

---

### Post by Perfect Storm on 2013-02-25
Welcome to the ubuntuforums :KS

We need a bit more information than that to help you.
Which Ubuntu version do you have? And is it 32-bit or 64-bit?
Also the specifications of you computer (RAM, Video card, etc.)
How did you install these games? (steam, ubuntu software center, manual download/install).

---

### Post by myromance123 on 2013-02-25
I have a feeling you haven't installed your graphics drivers yet? If you haven't installed any graphics drivers, it's safe to assume Ubuntu is using the Open Source driver for your card whether it be AMD/ATi or Nvidia (which could be the reason why your games aren't able to run).

The Open Source drivers are not up to par with the proprietary drivers yet, meaning less performance or sometimes inability to play the game.
[B]
---------------------------
NOTE: before trying to install the drivers like below, please update Ubuntu and do the following to keep yourself safe from experiencing problems later on.

Open a Terminal and input this:
sudo apt-get install linux-headers-generic

Hit enter, and when it asks for your password just put it in and hit Enter again. It may ask [Y/n], just hit "y" and Enter again. Now you're ready to follow the below instructions.
---------------------------[/B]

In Ubuntu's Dash, search for System Settings. On the top right select the "Additional Drivers" tab.

If you're using an AMD/ATi card, make sure that you have fglrx-updates or I think it's now called post-release driver selected. Then hit Apply Changes and restart your computer.

If you're using an Nvidia card, make sure you have the 310 drivers selected (will be called experimental-310, you can try experimental-304 too). Then hit Apply Changes and restart your computer.

If you're using an Intel Integrated graphics card, then you shouldn't have to do anything. It should already be installed automatically.

Hopefully this helps you, but this might not be the issue you're having either. I personally use the Nvidia 310 experimental drivers, and can play all my games at 1080p with full settings.

If you could help list your graphics card Vendor Name and model that would be great (e.g Nvidia GTX 680 or AMD/ATi HD7970).

P.S: If you don't know how to find the Terminal, just open Ubuntu's Dash and search for 'Terminal' without the quotes.

---

### Post by mvdonofrio on 2013-02-25
Sorry for being vague about the details of my hardware/software but I'm running 32 bit 12.04 Ubuntu and I'm not sure how to find my graphics card vendor name and model so if you could point me in the direction for that I could tell you.

Oh and I manually downloaded and installed both games if that helps!

AND I went through the get install linux headers generic process with the terminal but afterwards the additional drivers tab was empty?

---

### Post by myromance123 on 2013-02-25
Alright, this sounds like you might be using an older AMD/ATi card. Which is why no driver is appearing in the Additional Drivers tab.

Just to be sure, open a Terminal and enter this:
```
sudo lspci | grep -i vga
```

This should return what graphics card you have. Paste the output here so we can try and further help you.

---

### Post by mvdonofrio on 2013-02-25
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by myromance123 on 2013-02-25
Are you perhaps using a laptop/notebook/netbook?

Your output shows that you're using an Intel Integrated Graphics solution. This card doesn't have the power to play most games. However, you should at least be able to play Bastion (this is just my assumption however).

Since it's an Intel card, this means that your drivers are already automatically installed. 

What resolution are you running your screen at? From other forums, anyone using this integrated solution has to run everything as low as possible to get their games running.

Are there any 2D games you have that you can test? 

Are you able to run glxgears? Open a terminal and type:
```
glxgears
```

Do 3 colored gears appear?

---

### Post by nwalkey on 2013-02-25
You try launching it from terminal? And +1 for checking that you have the right graphics driver.

---

### Post by mvdonofrio on 2013-02-26
Honestly I'm not sure how to launch it from the terminal but I could try if you could point me in the right direction for that lol but I'll try running glxgears when I get home in about 20 minutes

---

### Post by mvdonofrio on 2013-02-26
i ran glxgears and the 3 colored gears did appear if that helps

---

### Post by Portaro on 2013-02-26
*i ran glxgears and the 3 colored gears did appear if that helps*

if you have the 3 D colored gears its mean that you have a 3d aceleration provided by default graphic drivers.

But the output of this command also give to yout the FPS result of your config an example->

302 frames in 5.0 seconds = 60.305 FPS
301 frames in 5.0 seconds = 60.014 FPS
301 frames in 5.0 seconds = 60.014 FPS
284 frames in 5.0 seconds = 56.626 FPS
301 frames in 5.0 seconds = 60.007 FPS
300 frames in 5.0 seconds = 59.977 FPS
301 frames in 5.0 seconds = 60.055 FPS
301 frames in 5.0 seconds = 59.931 FPS
300 frames in 5.0 seconds = 59.893 FPS


if you have a less FPS maybe your config cant run some games, or games work with slowly image.

If you can try launch games by terminal for example i have the game warzone2100 if i have  a problem of closed GUI i open my terminal and put the command
warzone2100 if the image GUI close the terminal give to me any reason for this.

And finally i have some problems with xubuntu and Lubuntu with my older ATI (non-maintained proprietary driver for linux) Radeon 9250 PRO, i have a problem with games and 3d aceleration, the only solution for me to solve problem its very simple install mesa-utils.

You can find the solution i mentioned here->

[http://ubuntuforums.org/showthread.php?t=2089840](http://ubuntuforums.org/showthread.php?t=2089840)

I can solve that problem on my both pcs one desk and other laptop, in two i have same problem.

It can be possible that you have a similar problem like me.

---

### Post by mvdonofrio on 2013-02-26
310 frames in 5.0 seconds = 61.881 FPS
309 frames in 5.0 seconds = 61.678 FPS
309 frames in 5.0 seconds = 61.675 FPS
309 frames in 5.0 seconds = 61.678 FPS
309 frames in 5.0 seconds = 61.677 FPS
309 frames in 5.0 seconds = 61.677 FP 

thats the output of glxgears but how exactly do i go about running bastion from the terminal?

---

### Post by myromance123 on 2013-02-27
**----------------------------------------------**
EDIT: From the linked thread, you can also try opening a Terminal and installing this first. It might just solve your problems in one go:
```
sudo apt-get install libtxc-dxtn-s2tc0
```
**----------------------------------------------**

Check out this guy's post: [link]("http://ubuntuforums.org/showthread.php?p=11992661")

Looks like this is a normal issue with Intel cards and S3TC textures. You can try his method to fix the game, it might just work. If it doesn't, then down below I've outlined some ways you can run Bastion through the Terminal.

I've been trying to figure out where your game might be installed, but since you're using the USC I can't be sure. Which is why I can't give you a direct command to enter into the Terminal to run Bastion with.

From that thread, there seems to be two places it can be installed in:
```
 /usr/local/games
```

Or:
```
/opt/Bastion/
```

You can try and look into these folders to check if Bastion is there. Just open your Home folder, and on the left is a location called Filesystem. From there, you can look into /opt or /usr.

To run executables, you'd normally do this:
```
./name_of_executable
```

So, if you manage to find Bastion's executable, you can type the "./" into a Terminal and just drag the executable onto that same Terminal. It'll give you a long command, and by hitting Enter it should run.

---

