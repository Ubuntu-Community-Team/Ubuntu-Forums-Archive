---
title: "Boot screen and startup"
date: 2015-06-06
forum: Desktop Environments
---

### Post by RobGoss on 2015-06-06
Hello everyone I'm currently using  Ubuntu 14.04, I wanted to know if you could tell me why and how I can get rid of the distortion when I start up my machine. What I mean is just before my computer reaches the login screen I see a distorted background and it stays this way for a few seconds before I can login... 

I'm using the default  environment  from Ubuntu.. Almost forgot I have a different background for my lock screen and my desktop. Thanks so much

---

### Post by Bashing-om on 2015-06-06
RobGoss; Hi !

You can tell grub to use a different resolution.
Here is what I have done :
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900

```
By editing " /etc/default/grub " .
Where I have set a higher resolution, 1600x900. for my display, and for what my display supports. Heed the warning ; "note that you can use only modes which your graphic card supports via VBE" !

Else you can check the display settings that the GUI is using, That resolution is safe to use in grub also.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-06
Thanks for the fast reply.

So I need to edit the grub file and make these changes? I don't want to mess things up seeing everything is running great.

What are the recommended [COLOR=#000000]resolution for grub? and Is this why I getting the distorted startup. Can you tell me why this is happening is it because the lock screen had a different [/COLOR][COLOR=#000000]resolution from the desktop?[/COLOR]

---

### Post by RobGoss on 2015-06-06
This is what I see in my grub file do I need to change the GFXMODE=640x480  to something higher?

```
# The resolution used on graphical terminal# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480 
```

---

### Post by Bashing-om on 2015-06-06
RobGoss; Yes indeed.

That is the place to make the edit. Always make a backup of any file you are editing ! Never can tell what might happen, and with that backup you can revert.

As to the resolution that you can use in grub; as advised by the comment:
reboot to the grub menu; 'c' key for a (C)ommand line interface.
Observe the result of grub command:
```

vbeinfo

```

Else you can use the native resolution the the GUI uses; That info should be available in "system Settings" -> display.

Be careful and know what the supported resolutions are. We do not want to damage the monitor by overdriving it !

As to:
> 
Can you tell me why this is happening is it because the lock screen had a different resolution from the desktop?

I would not think this is a factor, as grub runs before the operating system is started; and, if I am not mistaken grub uses a different driver than that of the GUI .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-06
Ok so i changed this

```

[COLOR=#000000][FONT=Ubuntu Mono]# The resolution used on graphical terminal# note that you can use only modes which your graphic card supports via VBE[/FONT][/COLOR]# you can see them in real GRUB with the command `vbeinfo' [COLOR=#000000][FONT=Ubuntu Mono]#GRUB_GFXMODE=640x480[/FONT][/COLOR] 
``` 


To This
```

[COLOR=#000000][FONT=Ubuntu Mono]# The resolution used on graphical terminal# note that you can use only modes which your graphic card supports via VBE[/FONT][/COLOR]# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1900x900
```


But it still looks really bad after start up am I doing something wrong?

---

### Post by Bashing-om on 2015-06-06
RobGoss; Hey !

Process of learning:
> 
[color=red]#[/color]GRUB_GFXMODE=1900x900

1st you are certain that "1900x900" is a valid resolution, yes ? I can not stress enough.
Then we have that silly little '#" that makes the line into a "comment" with the '#' character the line will not be parsed.

So in the text editor remove that comment character. and and and
Once the file is saved, to propagate the change to the operating system run terminal command:
```

sudo update-grub

```
( as the advisory states at the head of the file ).

OK, how now does the splash screen look when rebooting ?

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-06
> **Bashing-om said:**
> RobGoss; Hey !

Process of learning:

1st you are certain that "1900x900" is a valid resolution, yes ? I can not stress enough.
Then we have that silly little '#" that makes the line into a "comment" with the '#' character the line will not be parsed.

So in the text editor remove that comment character. and and and
Once the file is saved, to propagate the change to the operating system run terminal command:
```

sudo update-grub

```
( as the advisory states at the head of the file ).

OK, how now does the splash screen look when rebooting ?[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]




I use this command to edit my Grub file
```
sudo gedit /etc/default/grub &#8211;  
```

After doing so I changed the resolution to 1900 by 900, Then I saved the changes, Are you saying I have to **remove the '#" ** from my Grub file then save my changes? Sorry I'm a bit lost :)


You said: [COLOR=#000000]OK, how now does the splash screen look when rebooting ?[/COLOR]

[COLOR=#000000]After updating the grub it seems like the distorted image that was all scrambled and multi colors is the now the same images I'm using on my desktop but less [/COLOR][COLOR=#000000] distortion.[/COLOR]

---

### Post by ajgreeny on 2015-06-06
Did you also run **sudo update-grub** which is needed for the edit to take effect?

---

### Post by Bashing-om on 2015-06-06
RobGoss; Well ...

In my mode of instruction:
This is a no no !
> 
sudo gedit /etc/default/grub

With a graphical application one uses the graphical elevator "gksudo" rather than the textual 'sudo' : ( gksudo is also now depreciated - but can be used, as pkexec is now the new boy on the block ) . - undesired side effects -
You may have to install 'gksudo" :
```

sudo apt-get install gksu

```
see:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

And yes, you have the right of the procedure. 
remove the comment character at the start of that line (in your text editor);
save the file and exit back to terminal:
and then execute:
```

sudo update-grub

```
to propagate the change.

[INDENT][INDENT]as we make haste
[INDENT][INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-06
> **ajgreeny said:**
> Did you also run **sudo update-grub** which is needed for the edit to take effect?

Yes I did after it was recommend but it still looks kind of distorted not sure why I'm sure I'm missing something. Thanks

---

### Post by RobGoss on 2015-06-06
Let me get this straight 

**First:** You want me to edit my Grub file correct and remove the **# from this line **[COLOR=#000000][FONT=Ubuntu Mono]#GRUB_GFXMODE=1900x900 correct[/FONT][/COLOR]? what's the best way to edit this and save my changes.

**Second:** You want me to run this command from my terminal:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install gksu[/FONT][/COLOR] 
```

**Third: **You want me to run this update command from the terminal:
```
 **sudo update-grub **
```


Then I need to restart my machine to see the changes correct? Sorry but I just want to make sure, Thanks so much for your time.

---

### Post by Bashing-om on 2015-06-06
RobGoss; Humm ...

Not at all sure of what you have going on here as:
You say
> 
I'm using the default environment from Ubuntu..
I have a different background for my lock screen and my desktop.

After updating the grub it seems like the distorted image that was all scrambled and multi colors is the now the same images I'm using on my desktop but less distortion.


Which begs the question, are you using a custom image for grub's splash screen AND if so what means have you employed to set the image ?

Are we going to
[INDENT][INDENT][INDENT]go ahunt'n 
[/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-06
> **Bashing-om said:**
> RobGoss; Humm ...

Not at all sure of what you have going on here as:
You say


Which begs the question, are you using a custom image for grub's splash screen AND if so what means have you employed to set the image ?

Are we going to[INDENT][INDENT][INDENT]go ahunt'n 
[/INDENT]
[/INDENT]
[/INDENT]



As far as I know I'm not using any custom image for the grub splash screen. I am using a custom image for my desktop background and a custom image for the login screen.

After rebooting it seems a little better I just have a little distortion at the bottom of the splash screen now by I still did not remove the **# from the grub file yet.**

---

### Post by Bashing-om on 2015-06-06
RobGoss; Well ..


To attain admin authority to use a graphical application, I am the more comfortable with the legacy "gksudo" .
This utility is no longer installed by default on later releases of ubuntu, as "pkexec" is now the preferred way. I am aware that one has to do some setting up of 'pkexec' to make it apply to text editors and as such I would rather use 'gksudo' .
so if you run:
```

gksudo gedit /etc/default/grub

```
and the system tells you it can not comply. Then install the suite that includes the gksudo tool:
```

sudo apt-get install gksu

```
OR one can check and see if it is already installed:
```

dpkg -l gksu

```
IF it is you will get this result:
> 
sysop@1404mini:~$ dpkg -l gksu
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  gksu           2.0.2-6ubunt amd64        graphical frontend to su
sysop@1404mini:~$


SO; we do:
1) gksudo gedit /etc/default/grub and remove the '#' character at the start of line "#GRUB_GFXMODE=1900x900"
2) Save the file and exit back to terminal
3) execute terminal command " sudo update-grub "
4) reboot to see the effect.
-------------------
Now if there is still a problem
a) change the resolution to some other
or
b) see what image you are using, if it is compatible with what grub expects and what means you are using to set up a custom splash image.
-----------------------

Keep in mind
[INDENT][INDENT][INDENT]we will be with you 'til the end
[/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-06
Will do my friend thank you I will let you know how it goes.

---

### Post by RobGoss on 2015-06-06
How do you determine were the grub background images are located.

---

### Post by Bashing-om on 2015-06-06
RobGoss; Well;

Could be in a number of places; most generally :
```

sysop@1404mini:~$ ls -al /usr/share/images/desktop-base/desktop-grub.png
lrwxrwxrwx 1 root root 30 May 19  2013 /usr/share/images/desktop-base/desktop-grub.png -> /etc/alternatives/desktop-grub
sysop@1404mini:~$

sysop@1404mini:~$ ls -al /etc/alternatives/desktop-grub
lrwxrwxrwx 1 root root 43 May 19  2013 /etc/alternatives/desktop-grub -> /usr/share/images/desktop-base/joy-grub.png
sysop@1404mini:~$

```
For the tutorial to have a custom splash screen:
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
is a good guide. There are many others.
If ya want to get indepth - multiple installs; fancy displays:
see
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Is the better that I am aware of.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2015-06-06
This page explains Grub background images and the locations where they might be.

[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

See "Image Priority" section.

By default, Grub does not use a background image. A user has to put one in an appropriate location.

---

### Post by RobGoss on 2015-06-06
Hello and thanks, But I was looking in my Grub file and notice this at the end of the file

export GRUB_COLOR_NORMAL="light-gray/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"
#export GRUB_MENU_PICTURE="/home/robert/Pictures/Wallpapercorrectsize/ubuntu_logo_wallpaper_by_a48maverick-d6nfcpm.png"

Correct me if I'm wrong but it looks like the grub splash is displaying multi images and that would explain the distorted images be displayed. Because when the splash screen is loading I can see a number of images I have saved in my wallpaper folder and picture folder. Am I correct? How would I change that path to show just one background image.

---

### Post by Bashing-om on 2015-06-06
RobGoss; Hey;

Looks as if you have been following old documentation that no longer applies.
See :
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)
"GRUB 1.99 and later
The following guidance for setting the background image is for GRUB 2 version found in Ubuntu 11.04, Natty Narwhal and later."

For the correct procedure. Revert all other means you are employing to obtain a splash image.

[INDENT][INDENT]just what I think
[INDENT][INDENT][INDENT]do it by-the-book
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Dennis N on 2015-06-06
I will just add this final thought to the thread, and then be on my way:

In post #1, you said:

"What I mean is just be for I computer reaches the login screen I see a distorted background and it stays this way for a few seconds"

I think you may be referring to the Plymouth boot splash, not the Grub background. The Grub background is only behind the menu.

---

### Post by RobGoss on 2015-06-06
> **Dennis N said:**
> I will just add this final thought to the thread, and then be on my way:

In post #1, you said:

"What I mean is just be for I computer reaches the login screen I see a distorted background and it stays this way for a few seconds"

I think you may be referring to the Plymouth boot splash, not the Grub background. The Grub background is only behind the menu.


So is this a **Grub** issue or **Plymouth boot splash** issue? because now I'm confused because I'm trying to follow the Grub tutorial that was shared here but now you're saying it might not be the Grub splash screen.....

---

### Post by RobGoss on 2015-06-07
Bump

---

### Post by Dennis N on 2015-06-07
IMO, If you see this distorted image _while the grub menu is being displayed on the screen_, then the grub background is the likely suspect. If you see this distored image _after the grub menu_, the Plymouth boot splash is a likely suspect. Your statement that I quoted suggested the latter.

_Boot Process Stages:_

[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)

Based on my understanding, after you select an OS from the grub menu, the kernel for that selection is booted and it takes over, starts init and you system gets going. It's during all this startup activity that the Plymouth boot splash would run, up to starting the login screen.

I have had problems with the Plymouth boot splash having the wrong resolution, I have seen weird psychedelic color distortion on the booth splash which disappears when the login screen is reached - that was on an old AMD system with old Nvidia Graphics I was once trying to resurrect. Never figured out how to fix that. We used to call it Psychedelic Ubuntu. That system is now deceased. 

I'm not an expert on startup problems; just pointing out where it might be.

---

### Post by RobGoss on 2015-06-07
> **Dennis N said:**
> IMO, If you see this distorted image _while the grub menu is being displayed on the screen_, then the grub background is the likely suspect. If you see this distored image _after the grub menu_, the Plymouth boot splash is a likely suspect. Your statement that I quoted suggested the latter.

_Boot Process Stages:_

[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)

Based on my understanding, after you select an OS from the grub menu, the kernel for that selection is booted and it takes over, starts init and you system gets going. It's during all this startup activity that the Plymouth boot splash would run, up to starting the login screen.

I have had problems with the Plymouth boot splash having the wrong resolution, I have seen weird psychedelic color distortion on the booth splash which disappears when the login screen is reached - that was on an old AMD system with old Nvidia Graphics I was once trying to resurrect. Never figured out how to fix that. We used to call it Psychedelic Ubuntu. That system is now deceased. 

I'm not an expert on startup problems; just pointing out where it might be.

Well I'm still learning Linux so with that said, I'm new also and I don't know to much about the grub menu. When I startup my machine it just loads up my Ubuntu system. I don't see any Grub menu am I missing something? I don't know how to access it ether. Thanks

---

### Post by Bashing-om on 2015-06-07
RobGoss; Morning .

We are all at some point on this learning curve that is linux . The boot process is a particular interest to me, and it is a constant learning process. There is a lot going on to boot up that kernel and desktop.

In a direct response:
> 
When I startup my machine it just loads up my Ubuntu system I don't see any Grub menu am I missing something? I don't know how to access it ether.

Nope, you are not by default missing anything. With only one instance of ubuntu installed by default the boot menu will not be displayed. In such an instance of a single install to gain access to the grub menu, when booting up as soon as the bios screen clears depress and hold the right-shift- key -> grub menu (MBR partitioning) ((UEFI systems it is the escape key).

So let us try and identify at what stage you see the distortion. Is this distortion before the grub menu, or after when the booting kernel is selected ?

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-07
> **Bashing-om said:**
> RobGoss; Morning .

We are all at some point on this learning curve that is linux . The boot process is a particular interest to me, and it is a constant learning process. There is a lot going on to boot up that kernel and desktop.

In a direct response:

Nope, you are not by default missing anything. With only one instance of ubuntu installed by default the boot menu will not be displayed. In such an instance of a single install to gain access to the grub menu, when booting up as soon as the bios screen clears depress and hold the right-shift- key -> grub menu (MBR partitioning) ((UEFI systems it is the escape key).

So let us try and identify at what stage you see the distortion. Is this distortion before the grub menu, or after when the booting kernel is selected ?[INDENT][INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]
[/INDENT]



Hello Bashing, I'm a little confused, I don't select any [COLOR=#000000]kernel at boot up, I just press the start up button on my machine and after that it boots up to my login screen but! before it reaches that is when I see the distorted screen. Sorry if I'm a bit confusing but the grub topic has thrown me off.....


Is this the Grub menu that you're talking about
[www.]("http://robgoss.com/images/ubuntu_11.04-grub2.png")[/COLOR][robgoss.com/images/ubuntu_11.04-grub2.png]("http://robgoss.com/images/ubuntu_11.04-grub2.png")

If it is I don't see this at startup and that's not were the distortion is. It's the screen just before the login screen appears were you enter your pass word.[B]


This is what the screen look like when it appears. 
[/B][http://robgoss.com/images/distorted.jpg](http://robgoss.com/images/distorted.jpg)

---

### Post by Bashing-om on 2015-06-07
RobGoss; Yeah ;

That is the screen that you want to tey and boot to. as advised in the default configuration with a single instance of linux installed the boot menu will not be displayed. To get to this menu in the older systems one must get grub's attention.
Grub looks for any key to be depressed within a certain time frame after bios hands off to grub, "any" key is generally told to be the shift key(s).
Reboot and as soon as the bios screen clears depress a key, the grub menu should appear.
Boot to this grub menu. Is the distortion prior to the menu ? When you press enter - with the top entry in the kernel list selected (asterisk) do you now get this distortion ?

[INDENT][INDENT]who what when and why
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-07
I did press the shift key and hold it then the Grub menu appeared after that I choose the first option to boot Ubuntu after that when my system loads i get that distorted screen  before I login.



 but I'm not sure what to do at this point

---

### Post by Bashing-om on 2015-06-07
RobGoss; Good ;

Ok with the grub menu displayed it is your option which kernel to boot with.
The booting kernel can be selected by the keyboard arrow keys to move up/down the list OR choose "advanced" to be able to select other options. Just place the cursor to the choice and hit the enter key. Generally one wants to boot the latest kernel ( the one with the highest version number) . You can not hurt anything by selecting different options, see what happens. Playing with a "recovery" kernel will be an eye opener.

When booting from a selected kernel from the grub menu, is the distortion still present ?

Just remember to always shut the system down cleanly !

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-07
After trying to follow your instructions which was GREAT by the way and much appreciated.  I was able to access the Grub menu there were a few options and the first one was to boot up Ubuntu, The others was Advanced option which I did choose that as well. No matter which one I choose when trying to boot up the I got the distorted view.....

---

### Post by RobGoss on 2015-06-07
First of all I use a** dual monitor setup **sorry I did not mention that not sure if it would have help this discussion, and after watching my machine booting up a few times I notice there was something yellow displaying in the distorted screen. 

I have theses yellow sticky's pined to my second screen, well I notice when my machine booted up I can also see those yellow sticky's booting up on my** first monitor** so that made me think why am I also seeing those yellow sticky's  all distorted on my first monitor.

So I disconnected my **second monitor** and try booting up my machine again and guess what? no distorted screen after booting up with only one monitor everything look ok. So it looks as tho it's something to do with my dual setup screen.  

This has been driving me nuts since yesterday. Any ideas?

---

### Post by Bashing-om on 2015-06-07
RobGoss; Well ..

Yeah dual monitors do set things in a different light.
I have no experience with dual monitors, so now we fly by the seat of out pants, see what we can learn.

Presently all I can think of is to see what is set in System Settings -> display . Are both monitors the same manufacturer ? Such that both will use the same settings ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-07
Yes there're the same identical monitors brand setting and all. I am wondering if I could maybe turn one off and turn it on when needed with out unplugging it.

---

### Post by Bashing-om on 2015-06-07
RobGoss; Sheeeshh ...

Do not really know about turning on the monitor later, years ago that was a bad practice due to a possible power spike on the power supply blowing capacitors. Do not know if that still applies . Dennis ?

[INDENT][INDENT]If I knew it all
[INDENT][INDENT][INDENT]I would not be me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-07
I guess I'll have to do my homework hey man I want to thank you guys so much for all the help you guys are GREAT. I think this is a whole new topic :)

At least I know now what is causing it. It was not a total failure

---

### Post by Bashing-om on 2015-06-07
RobGoss; Hey ;

I got another thought. power all down, and swap the monitor cables. See if the problem moves with the cables .

The topic, I think, remains the same; just a change in direction.

[INDENT][INDENT]stranger things have been known to happen
[/INDENT][/INDENT]

---

### Post by RobGoss on 2015-06-07
I'll give it a try can't hurt nothing....

---

### Post by RobGoss on 2015-06-07
> **Bashing-om said:**
> RobGoss; Hey ;

I got another thought. power all down, and swap the monitor cables. See if the problem moves with the cables .

The topic, I think, remains the same; just a change in direction.
[INDENT][INDENT]stranger things have been known to happen
[/INDENT]
[/INDENT]



So I swapped the monitor cables and no changes the only way I can get rid of the distortion is to unplug one monitor, so I did until I can find a fix for this effecting my startup.

---

### Post by Bashing-om on 2015-06-07
RobGoss; K ;

Next thought up, is to check " /etc/X11/Xorg.conf " . As the monitors are identical, the settings for screen 0 and screen 1 should be the same in that file.

[INDENT][INDENT]as I continue pondering on along
[/INDENT][/INDENT]

---

