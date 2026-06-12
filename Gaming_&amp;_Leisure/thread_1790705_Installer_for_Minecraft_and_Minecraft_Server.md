---
title: "Installer for Minecraft and Minecraft Server"
date: 2011-06-25
forum: Gaming &amp; Leisure
---

### Post by KoolPenguin on 2011-06-25
Here is a front end to Minecraft that I whipped up.  My son was asking if there was a way to install it easily without having to go to the terminal for him and his friends, so this is what I came up with.

[IMG]http://dl.dropbox.com/u/31531443/craftyguiscreenshot2.png[/IMG]

I have tested it on Ubuntu and Kubuntu and it works great. It requires kommander-kde3 and gksu... Minecraft requires Java.  Give it a try.

Ps. I use the AdFly service, you will get to the download link after that.

I do have a website at [www.ShrewdsWorld.com]("http://www.shrewdsworld.com") that I am working on and I'm in the process of moving all my projects to google code.

[Download Shrewd's Crafty GUI here...]("http://adf.ly/1uqIc")

Thanks

--

Chris

---

### Post by KoolPenguin on 2011-07-01
I have just released the next version of Shrewd's Crafty GUI for Minecraft, version .25b... A new feature to install mods has been added.

Please check my website for more information and download link.

[http://www.shrewdsworld.com]("http://www.shrewdsworld.com")

Thanks

--
Chris

---

### Post by Dangertux on 2011-07-01
You officially are one of the coolest dads on the face of the planet. No , seriously wish my dad would have done stuff like that for me when I was a kid. Then again I wouldn't have had to figure it out and might be sans a very lucrative job :-) 

Nonetheless nice work :-)

---

### Post by KoolPenguin on 2011-07-01
> **Dangertux said:**
> You officially are one of the coolest dads on the face of the planet. No , seriously wish my dad would have done stuff like that for me when I was a kid. Then again I wouldn't have had to figure it out and might be sans a very lucrative job :-) 

Nonetheless nice work :-)

Thanks... I just hope it helps out others who have trouble installing Minecraft and the mods.

Best
--
Chris

---

### Post by El3mentGamer on 2011-07-07
Im not very "ubuntu smart" ... do you think you could explain how to install it? All i have is a plain folder with random scripts in it.

---

### Post by KoolPenguin on 2011-07-08
> **El3mentGamer said:**
> Im not very "ubuntu smart" ... do you think you could explain how to install it? All i have is a plain folder with random scripts in it.

Open a terminal and do the following...

To install java, at terminal command prompt enter:

sudo apt-get install sun-java6-jre sun-java6-plugin

Please make sure these are install before using this program:

sudo apt-get install kommander-kde3 gksu fastjar

To install, goto the directory you placed 'Shrewd's Crafty GUI' in and at terminal command prompt:

sudo ./setup.sh' from terminal

Will create a shortcut on the desktop to start the program after installed.

Best
--
Chris

---

### Post by El3mentGamer on 2011-07-08
I've installed both the java and kommander things.

When i type in the "sudo ./setup.sh" code in a new-opened terminal i get this error.
> brandon@brandon-HP-Pavilion-dv6500-Notebook-PC:~$ sudo ./setup.sh
[sudo] password for brandon: 
sudo: ./setup.sh: command not foundWhen i type the code in a the setup.sh terminal popup i get this error.
> @----------------------------------------@
@      Shrewd's Crafty GUI Setup         @
@            Version .10a                @
@----------------------------------------@


What would you like to do?

1. Install Shrewd's Crafty GUI
2. Uninstall Shrewd's Crafty GUI
3. Exit
sudo ./setup.sh
/home/brandon/Downloads/shrewds-crafty-gui-25b/setup.sh: line 132: [: too many arguments
/home/brandon/Downloads/shrewds-crafty-gui-25b/setup.sh: line 137: [: too many arguments
/home/brandon/Downloads/shrewds-crafty-gui-25b/setup.sh: line 142: [: too many arguments
Invalid choice
What am i doing wrong? How do i fix it >:sad:

---

### Post by KoolPenguin on 2011-07-08
> **El3mentGamer said:**
> I've installed both the java and kommander things.

When i type in the "sudo ./setup.sh" code in a new-opened terminal i get this error.
When i type the code in a the setup.sh terminal popup i get this error.
What am i doing wrong? How do i fix it >:sad:

try "sudo chmod +x ./setup.sh" to make it executable, then "sudo ./setup.sh" to run it.

Best
--
Chris

---

### Post by El3mentGamer on 2011-07-08
This thing is ticking me off and your program seems very interesting and helpful and i really want minecraft mods. You say you accept donations? What if i make i deal with you? Because im about as aggrivated as can be... 

If i donate to you, is there any way you could make an installation video tutorial, or do a teamviewer type thing to control my computer and do it for me.

Idk if i'm doing something wrong or if the program/ubuntu is preventing it.

Please and thanks,
Brandon.

---

### Post by KoolPenguin on 2011-07-08
> **El3mentGamer said:**
> This thing is ticking me off and your program seems very interesting and helpful and i really want minecraft mods. You say you accept donations? What if i make i deal with you? Because im about as aggrivated as can be... 

If i donate to you, is there any way you could make an installation video tutorial, or do a teamviewer type thing to control my computer and do it for me.

Idk if i'm doing something wrong or if the program/ubuntu is preventing it.

Please and thanks,
Brandon.

I was going to do videos for my projects so I'll see if I can put something together tomorrow and post it on my website. Most likely later in the day/evening tomorrow.

What version of Ubuntu and environment are you using?

Best
--
Chris

---

### Post by El3mentGamer on 2011-07-08
11.04 and i just continuously keep on getting the "Too many Arguments" Error.

I already have Minecraft installed, would that matter? I planned on uninstalling with your program and the re-installing it.

---

### Post by KoolPenguin on 2011-07-09
> **El3mentGamer said:**
> 11.04 and i just continuously keep on getting the "Too many Arguments" Error.

I already have Minecraft installed, would that matter? I planned on uninstalling with your program and the re-installing it.

Not sure why you are getting those errors.

Make sure you backup your world saves before removing Minecraft!

If your Minecraft is located in .minecraft then my program should have no problem removing it.

Download archive from here and place it on your Desktop (makes it more simple):

[http://shrewds-crafty-gui.googlecode.com/files/shrewds-crafty-gui-25b.tar.gz]("http://shrewds-crafty-gui.googlecode.com/files/shrewds-crafty-gui-25b.tar.gz")

Try the following step by step (copy and paste in terminal):

```
sudo apt-get install kommander-kde3 gksu fastjar zip unzip tar
```
```
cd Desktop
```
```
tar -zxvf shrewds-crafty-gui-25b.tar.gz
```
```
cd shrewds-crafty-gui-25b
```
```
sudo chmod +x setup.sh
```
```
sudo ./setup.sh
```

Now you should see the install options.  After your install it there will be a shortcut on your desktop.

Hope this helps. I was going to do a vid but I can't find my mic (think one of the kids took it). So it would be with no voice instructions.

Best
--
Chris

---

### Post by El3mentGamer on 2011-07-09
Thank you very much sir! I GREATLY appreciate your effort to manually help and individual 'customer'. I will be donating to you ASAP! My paypal is currently being renewed do to an ebay scandel attempt.. long and annoying process. But you are a HUGE help! THANK YOU VVEERRRYY MUCH.

---

### Post by KoolPenguin on 2011-07-09
> **El3mentGamer said:**
> Thank you very much sir! I GREATLY appreciate your effort to manually help and individual 'customer'. I will be donating to you ASAP! My paypal is currently being renewed do to an ebay scandel attempt.. long and annoying process. But you are a HUGE help! THANK YOU VVEERRRYY MUCH.

Your welcome.  Just remember to make sure that you check the mods you would like to install first for conflicts with other mods and the Minecraft version they support.  Some mods will not install if they are not archived with the correct directory structure for Minecraft.  I have a list of some mods on my website that I verified to work with my mod installer.

Best
--
Chris

---

### Post by sansa dude on 2011-07-11
Great application! Thank you. Works perfectly when you follow the instructions from your earlier post. Its good to have a simple way of installing minecraft with the icons for the game. The way I had it working before wasn't very good. Thanks again! :D

---

### Post by KoolPenguin on 2011-07-12
> **sansa dude said:**
> Great application! Thank you. Works perfectly when you follow the instructions from your earlier post. Its good to have a simple way of installing minecraft with the icons for the game. The way I had it working before wasn't very good. Thanks again! :D

No problem.  I hope it helps out others as well.:)

Best
--
Chris

---

### Post by roololing on 2011-07-14
This is an amazingly useful application, good work! The mod installer and server options are particularly handy. Before this, I always had to go on Windows 7 to play Minecraft. Thank you for all of the effort you put into this!

---

### Post by KoolPenguin on 2011-07-16
> **roololing said:**
> This is an amazingly useful application, good work! The mod installer and server options are particularly handy. Before this, I always had to go on Windows 7 to play Minecraft. Thank you for all of the effort you put into this!

Good to here.

I am also working on making the mod install function better as one can still have problems if the mod is not for the correct Minecraft version, etc.

Best
--
Chris

---

### Post by KoolPenguin on 2011-07-16
Looking for suggestions on how to improve this project.  What would you like to see added or changed?  Please leave suggestions here or on my website.

Contributions in code, graphics, etc are always welcome!

Thanks
--
Chris

---

### Post by roololing on 2011-07-18
Maybe a button to create a shortcut to Minecraft on the desktop or in the launcher?

And maybe in the future it could even have skin and texture pack editors.

EDIT: Oh, and a button that takes out your save files, uninstalls & reinstalls the minecraft.jar, and puts the save files back in.

---

### Post by ELD on 2011-07-20
I ran the setup and no shortcut to be found anywhere?

Why does it need to be run as root?

---

### Post by KoolPenguin on 2011-07-21
> **ELD said:**
> I ran the setup and no shortcut to be found anywhere?

Why does it need to be run as root?

Root is required to install the script launchers.  This will place a menu entry and enable you to launch it from a terminal as well.  Try running setup again with sudo and re-installing.

Best
--
Chis

---

### Post by KoolPenguin on 2011-07-21
I made a video of the Windows version of my project.

[Click here for a video preview of upcoming release]("http://youtu.be/qpNAzaIoKhk")

Best
--
Chris

---

### Post by ELD on 2011-07-21
I did run it as root, i was just asking why because you didn't note anywhere i can see that it added launchers to /
 
Was no error message or anything, odd, anyways thanks but i decided just to use the main Minecraft jar for now.

---

### Post by KoolPenguin on 2011-07-21
> **roololing said:**
> Maybe a button to create a shortcut to Minecraft on the desktop or in the launcher?

And maybe in the future it could even have skin and texture pack editors.

EDIT: Oh, and a button that takes out your save files, uninstalls & reinstalls the minecraft.jar, and puts the save files back in.

re: desktop shortcut; Already does, atleast you should see one. :)

re: skin & texture editor; There is a skin editor online and texture pack edits are done with paint programs, such as gimp.

re: re-install minecraft/keep saves; sounds good! Will look into it.

Best
--
Chris

---

### Post by KoolPenguin on 2011-07-22
> **ELD said:**
> I did run it as root, i was just asking why because you didn't note anywhere i can see that it added launchers to /
 
Was no error message or anything, odd, anyways thanks but i decided just to use the main Minecraft jar for now.

Whatever works for you.  Please let me know what happened when you ran the setup.sh file as root so I can look into fixing it.  It should of put a shortcut on your desktop as well as a menu entry.

Best
--
Chris

---

### Post by Cpierce on 2011-07-28
Chris, This really worked well, so thank you. When will you have the windows version available ? Would love to have that for my boy !

---

### Post by KoolPenguin on 2011-07-29
> **Cpierce said:**
> Chris, This really worked well, so thank you. When will you have the windows version available ? Would love to have that for my boy !

Glad it helped you out and the windows version will be available sometime in the next few weeks.

Best
--
Chris

---

### Post by Cpierce on 2011-07-29
Great ! I will be waiting. Thanks again for all the hard work.

---

### Post by Cpierce on 2011-08-30
Chris, I keep checking, any news on the windows version ?

---

### Post by KoolPenguin on 2011-09-07
> **Cpierce said:**
> Chris, I keep checking, any news on the windows version ?

Sorry for the late reply.  I haven't been well the past few weeks but getting better. I should be able to start working on it again shortly. It was almost finished so not much left to do.

Best
--
Chris

---

### Post by TheShadowFog on 2011-09-07
You sir. Are a genius. :popcorn:

---

