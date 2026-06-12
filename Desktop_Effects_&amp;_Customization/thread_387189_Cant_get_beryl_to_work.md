---
title: "Cant get beryl to work"
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by ebichuhamster on 2007-03-18
I download aquamarine_0.2.0~0beryl1_amd64.deb which is basically idiot proof, but not ebichuhamster-proof.

I get an error message saying : Cannot find dependancies for beryl..amd64

What can i do?

and for my education, whats a dependency and how does it affect me?

Much obliged ! ^_^

---

### Post by Waappu on 2007-03-18
Hi

Select right guide for you from here
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

Add those Beryl repository to sources.list and use apt-get command to install.
That will install all dependency's witch are other packages that Beryl need to run.

---

### Post by ebichuhamster on 2007-03-25
ok ok,, im getting much nearer now i think,,,,Many many thanks to Waappu

in the guide I get to the part "Installing Beryl"

where it tells me to add "sudo apt-get install beryl emerald emerald-themes"

It starts to install but in some point it outputs:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl

This cant be too hard to solve can it?? i mean,, i just have to tell it to look in a specific place right?

In any case, Is this what i have to do? If it is, how do I do it? If it isn't, What do I do now? (in the guide there are no more instructions and i just want some eye candy >.<)

---

### Post by mthaddon on 2007-03-25
So it's saying it can't find that specific package. The packages it (apt-get) can find are determined by the contents of /etc/apt/sources.list. Edit this as root - "sudo gedit /etc/apt/sources.list" (I'm assuming you've done this to add whatever are the appropriate repositories to find beryl). Then you need to do "sudo apt-get update" to update the package database with what packages are available. Then "sudo apt-get install beryl". If you can't find the package, try "sudo apt-cache search beryl". If you can't find it on the list, it's a question of it not being available in the repositories you've configured in your sources.list file.

Also, you can replace all the "apt-get" and "apt-cache" commands above with "aptitude" - it's another program that deals with packages in a slightly more intelligent manner, and can be used a little more flexibly than apt-get and/or apt-cache. Of course, you can also do all this from the GUI - synaptic is the name of the program, and it can be found under System -> Administration.

Good luck, Tom

---

### Post by DoorGunner on 2007-03-25
jdong has a really great thread for getting beryl to to work.

[http://ubuntuforums.org/showthread.php?t=369738](http://ubuntuforums.org/showthread.php?t=369738)

lots of good stuff here.

---

### Post by ebichuhamster on 2007-03-25
>_< OK, I installed beryl!!!  But now i cant see anythinG!!! Maybe its because it's Beta software??? I really hope its just a problem in the setup.......

OK here goes.. I enter 'beryl-manager' into the terminal and then everything goes white.  I press alt+tab and i can see the icons of my current programs, but I can't see anything else. 

Is it that my nvidia GeForce go 6150 isn't installed correctly??? >_<

Agh! I'm so close to the eye candy i can taste it!!!

Million thanks to all who've posted and helped!

---

### Post by Waappu on 2007-03-25
Hi

Use envy to install nvidia driver
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by ebichuhamster on 2007-03-25
At least beryl's working because when i click the lower right corner of the screen, the rotating cube effect happens.

Any suggestions?

---

### Post by Waappu on 2007-03-25
Hi

Try to install nvidia drivers using envy

---

### Post by DoorGunner on 2007-03-25
change xorg to look like this

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"
	Option		"RenderAccel"		 "true"
	Option		"AllowGLXWithComposite"  "true"
	Option 		"AddARGBGLXVisuals" 	 "True"
	Option 		"DisableGLXRootClipping" "True" 
EndSection

---

### Post by ebichuhamster on 2007-03-25
Ok, I used envy.

I used  manual install and it all seemed well until i restarted.  The x server wouldn't load so i wrote "dpkg-reconfigure xserver-xorg" in TT1 and went through all that.  On reboot the X server loaded just fine and I checked to see if the driver was installed, but I couldn't find anything Nvidia related.

Now Beryl's icon appears in the taskbar which i think is good.  So i right click it, go to "Select Window Manager" and select Beryl, but the screen just flashes for a bit and it goes back to Gnome. 

What does this all mean!?

---

### Post by ebichuhamster on 2007-03-25
OK,, sry everybody for the effort up untill now, but im gonna lay off beryl for a week.  I've got a couple of ugly exams.

A million Thanks!

---

### Post by ebichuhamster on 2007-03-30
Ok, did my exams and now i have the time to put ubuntu on the scale.  I think i should get the wireless driver working first, but as i've said before, i can almost taste the eye candy.  

Beryl is installed.  I can access the manager and change options. But when i 'rightclick Beryl Icon>Select Window Manager>Beryl' the screen just flashes and nothing happens.  I would think that the xserver would crash but the option "Launch Fallback window manager if Beryl crashes" set to Gnome.

DoorGunner posted that I should change the xorg configuration, but i dont know how to do this. (im a noob as can be)

Can anyone make a suggestion?

---

### Post by DoorGunner on 2007-03-30
Hey No problem....everyone has to learn.....im still learning lots

what you need to do is 

$sudo gedit /etc/X11/xorg.conf

near the bottom you should see something like this

> Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Driver         "nvidia"

Driver should be "nvidia" not "nv"
Under the nvidia make sure you put the following

> Option		"RenderAccel"		 "true"
	Option		"AllowGLXWithComposite"  "true"
	Option 		"AddARGBGLXVisuals" 	 "True"
	Option 		"DisableGLXRootClipping" "True" 

Just cut and past this right in. It should help your Nvidia Card to react better with Beryl

then you can log out and log back in

you should be able to a 
$glxgears and have decent frames per second rate

What Nvidia card are you running?

---

### Post by ebichuhamster on 2007-03-31
its a ge force go 6150,, 

I think half my problems might be due to this card, because in a previous thread of mine, somebody specifically asked for this exact card when i presented some wierd booting problem..

Anyways, im gonna try and change the xorg.conf as you said.  I'll post results as soon as i can

^_^ Thanks !

---

### Post by ebichuhamster on 2007-03-31
lol ok so i changed that and my xserver wouldnt load on reboot

....I ran this command

> dpkg-reconfigure xserver-xorg

The only reason i know this command is because of all the times i've screwed up the xserver  because of the nvidia drivers.  Anywayzz,,, it seems that this command is a GUI exactly for changing the xorg.conf file,,, so i changed them back to what they were before,,,,,

Dont know exactly whats happening or whats going on, but is it possible that i can just blame my video card ?  

>_<

---

### Post by DoorGunner on 2007-03-31
one of the other things you can do to back up files to the last known working solution.

you could try to do something like this

$sudo cp /etc/X11/xorg.conf  /etc/X11xorg.conf.backup

that will make a backup file named xorg.conf.backup

to recover to back up you could

$sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

My previous suggestion may not work with the albertone drivers. I used the wiki drivers found here [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) . This is not to say that you cannot be successfully with beryl and albertone. If there is a will there is a way.

My suggestion right now is get your drivers working properly. IE you should ensure you have 3d rendering etc and a good fps with out beryl compiz etc. the beryl manager will allow you to step back this way.

Once you have that done go to the beryl thead and follow it [http://www.ubuntuforums.org/showthread.php?t=369738](http://www.ubuntuforums.org/showthread.php?t=369738) jdong is one of the admins here and is quite knowledgeable about beryl and ubuntu. He is a good community resource.

---

