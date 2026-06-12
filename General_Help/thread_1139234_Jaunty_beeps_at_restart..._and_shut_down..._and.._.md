---
title: "Jaunty beeps at restart... and shut down... and.. MAKE IT STOP!!"
date: 2009-04-26
forum: General Help
---

### Post by higashi on 2009-04-26
Title says it all. my computer makes these hideous beeps when i try restarting or shutting down or anything like that... can i disable this? how?

---

### Post by |Mitch| on 2009-04-26
System/Preferences/Sound

---

### Post by higashi on 2009-04-26
Thanks

---

### Post by id10twork on 2009-04-26
sorry to latch on to your thread, but my jaunty does that, and so did my old machine. going into sound does not have any settings to make it stop. any more suggestions?

---

### Post by w3wsrmn on 2009-04-26
> **id10twork said:**
> sorry to latch on to your thread, but my jaunty does that, and so did my old machine. going into sound does not have any settings to make it stop. any more suggestions?

You can unload the PC speaker module with
```
modprobe -r pcspkr
```And add the following line to **/etc/modprobe.d/blacklist.conf** to prevent the module from ever loading
```
 blacklist pcspkr
```

---

### Post by |Mitch| on 2009-04-26
...

---

### Post by higashi on 2009-04-27
i just went to system>prefferences>sound , went to the sounds tab and unchecked "play alert sound"

---

### Post by id10twork on 2009-04-27
> **higashi said:**
> i just went to system>prefferences>sound , went to the sounds tab and unchecked "play alert sound"

mine's unchecked... the only thing i have checked is the top one "play alerts and sound effects" because no sounds will play if i don't have it checked

---

### Post by id10twork on 2009-04-27
> **w3wsrmn said:**
> You can unload the PC speaker module with
```
modprobe -r pcspkr
```And add the following line to **/etc/modprobe.d/blacklist.conf** to prevent the module from ever loading
```
 blacklist pcspkr
```

what exactly is this going to do? it looks like it may work but i'd like more info first. is it to remove the inside speaker? would i just be able to do it thru setup on my boot menu?

---

### Post by josel777 on 2009-04-27
> **w3wsrmn said:**
> You can unload the PC speaker module with
```
modprobe -r pcspkr
```And add the following line to **/etc/modprobe.d/blacklist.conf** to prevent the module from ever loading
```
 blacklist pcspkr
```


I have had this problem since 8.10 (Intrepid). 

Blacklisting pcspkr ```
 blacklist pcspkr
``` doesn't fix the problem for me. However, ```
modprobe -r pcspkr
``` does. It is very frustrating.

---

### Post by higashi on 2009-04-27
nevermind, mine still beeps. im gunna try this blacklist thing..
i guess i'll find out next time i shutdown/restart

---

### Post by Brian_the_King on 2009-04-27
This is what worked on my system..

From another thread on this forum



> **tangibleorange said:**
> OK well to disable the beeps you can try these two commands (one after the other):

```
sudo rmmod pcspkr
```and then this:

```
echo 'blacklist pcspkr' | sudo tee -a /etc/modprobe.d/blacklist
```Hopefully you will now be beep-free! If your system fails to shutdown, another way to shut down is to run this command:

```
sudo shutdown -h now
```Make sure you save any work BEFORE using that command, as it will immediately begin the shutdown process.

Good luck!

---

### Post by farlander762 on 2009-04-27
I looked on another thread and found that there is a much easier solution than blacklisting anything.  

[http://ubuntuforums.org/showthread.php?t=1139490&highlight=beep]("http://ubuntuforums.org/showthread.php?t=1139490&highlight=beep")

Just turn it off.  [COLOR="Red"]System -> Preferences > Power Management -> General -> Extras -> Sound notification.[/COLOR] 

This beep is hellish.

***Well that didn't work.....***

---

### Post by higashi on 2009-04-27
> ***Well that didn't work.....***

so.. it.. doesnt work? O.o

---

### Post by id10twork on 2009-04-27
> **Brian_the_King said:**
> This is what worked on my system..

From another thread on this forum

THANK YOU!!! This worked great... the other blacklist code that the other person posted did not work for me... i'm so happy the beeping has stopped, i used to leave my volume down low just so when i turned off my computer the beep would be as loud lol:-D

---

### Post by reality1011 on 2009-04-27
what about "xset b off" ?


simple terminal void beeping

---

### Post by freonchill on 2009-04-27
why is the "sound error option" under "power settings" rather than under sound?!

this does NOT fix the problem for me.

im weary of completely disabling my pc speaker, but i guess i really dont use it much...

tried "xset b off" in a terminal and then rebooted - BEEP

PS: ill try to modprobe tomorrow after work and post back 

modprobe fixed the problem... hopefully it wont come back

then off to find the suspend/hibernate problem...

---

### Post by SonicSteve on 2009-04-28
The black list worked perfectly! Thanks no more anoying squawk beep.

---

### Post by damis648 on 2009-04-28
The blacklist item is not a command, it is a line that must be added to /etc/modprobe.d/blacklist.conf in order to stop the module. To do so:
```
sudo rmmod pcspkr
```
If that removes the beep, then continue:
```
sudo cp /etc/modprobe.d/blacklist.conf /etc/modprobe.d/blacklist.conf.bak
sudo echo "blacklist pcspkr" >> /etc/modprobe.d/blacklist
```

---

### Post by higashi on 2009-04-29
i get this error

> me@my-desktop:~$ sudo rmmod pcspkr
[sudo] password: 
ERROR: Module pcspkr does not exist in /proc/modules


---

### Post by 84loops on 2009-04-29
my computer does that too, it's a dell. So, I just went into the BIOS and disabled PC speaker. Make sure you leave onboard audio enabled, or if you have a PCI audio card make sure that still enabled.

---

### Post by DhulKarnain on 2009-04-29
> **w3wsrmn said:**
> You can unload the PC speaker module with
```
modprobe -r pcspkr
```And add the following line to **/etc/modprobe.d/blacklist.conf** to prevent the module from ever loading
```
 blacklist pcspkr
```

Thank you.
This method worked for my toshiba a300d and its highly irritating loud beep.
It's a lifesaver when rebooting at 2 a.m. and the rest of the family is asleep.

---

### Post by higashi on 2009-04-29
Where can i find the BIOS? :\

---

### Post by rainwalker on 2009-04-29
> **w3wsrmn said:**
> And add the following line to **/etc/modprobe.d/blacklist.conf** to prevent the module from ever loading
```
 blacklist pcspkr
```

Worked for me too :)
My question is, why did it change from playing the log out sound to the beeping noise?

---

### Post by danielgc.com on 2009-04-29
> **higashi said:**
> Where can i find the BIOS? :\

that depends on your computer model... can you tell us? Basically you press a key before it loads Ubuntu

---

### Post by SILLAT on 2009-05-07
> **Brian_the_King said:**
> This is what worked on my system..

From another thread on this forum

I Dont mean to run in on anyones post but gotta say the following commands worked for me.
Thanks for the fix that annoying beep before shutdown is now gone

---

### Post by alex.rayu on 2009-05-23
Is that kinds normal that the users should be wrenching their necks figuring out how to removed that? Did not seem to bother the developers?

---

### Post by ssdt on 2009-07-31
I reported a bug in lauchpad about this. Ubuntu community should send out an update to stop this beep, it's really annoying and I feel like it's going to do something bad to the computer like it's going into some blue screen of death.

---

### Post by vex21 on 2009-08-02
Hi everyone, 

I also have a problem with an irritating beep sound at restart. I've read this thread but it didn't help so I googled around a bit and although I'm only about half-way through with solving this issue now, I'm going to share it anyway as it may give a nudge to someone else who knows Ubuntu better than I do.

For the record, I'm using Jaunty Jackalope (2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux) on HP Pavilion dv3600.

Now, first of all I found out that it wasn't the integrated PC speaker that produced the sound at restart because when I plugged my headphones in, the restart beep could be heard from the headphones. So it must have been a sound card issue. I tried all the attempts at blocking the PC speaker suggested in this thread anyway just to be sure, but it didn't help.

The second thing I discovered was that the irritating sound also occurred when I started a terminal window in Gnome and did something that invokes an alert, e.g. pressing backspace when there's nothing else to erase on the line or pressing tab key to show options where there are no options available. This could be amended quite easily in:

> System -> Preferences -> Soundwhere you can disable the "Play alert sounds" checkbox (another way may be going to terminal menu "Edit -> Profile preferences" and unchecking "Terminal bell" on the General tab, I didn't try it though).

Nevertheless, the beep at restart remained. I tried switching to non-graphical terminal (I think there are five of them, pick one using CTRL + ALT + F1 to F5) to see if the alert beep sound was there. It was (again holding the backspace when there's nothing to delete causes the alert beep). 

I solved this by setting the length of terminal bell sound to zero:

```
setterm -blength 0
```This worked for the current session of the non-graphical terminal only but putting this line at the end of 

```
~/.bashrc
```file did it for every next login. 

Having turned the alert bell off, I tried shutting (or restarting) the computer down from the non-graphical terminal with the graphical session still turned on (to go back to the graphical session press CTRL + ALT + F7) and the annoying beep sound was heard again.

So I tried logging out of the graphical environment, then switching to a non-graphical terminal (e.g. CTRL + ALT + F5) and shutting the computer down from the terminal. The beep was gone. Thus I discovered that 

> when you log out of the graphical desktop environment to the graphical welcome login screen and choose to shut down or restart from here, the bothersome beep sound isn't produced.
That's all I managed to find out in my spare time. It made my life a bit easier when shutting the laptop down in a public place, but it doesn't solve why there's the beep sound when shutting the computer down from the desktop environment. 

Hopefully, this might help someone. And if anybody knows if there's a way to get rid of the beep when closing the X session, please let me know.

Cheers.

---

### Post by weishigoname on 2009-10-28
made it ,sound good ,thanks

---

### Post by milensinan on 2009-10-28
same here.
and not just 'on restart'.
for instance, when trying to install a package (flock or any other program) on terminal, it incredibly strates to beeeeep hundreds times until the setup ends which takes few minutes, so i can't even listen to music i just shut the whole sound !

---

### Post by scouser73 on 2009-10-28
To permanently disable it, you need to add a line line to [B]/etc/modprobe.d/blacklist.
[/B]
**echo "blacklist pcspkr" | sudo tee -a /etc/modprobe.d/blacklist**

When you reboot your computer the system beep should be disabled everywhere.

---

### Post by Uncle Spellbinder on 2009-10-28
I hated that beep, but just learned to live with it. But after installing Karmic, I was quite surprised to hear silence on shutdown, restart and boot.

---

### Post by Pasea on 2009-10-28
> **Brian_the_King said:**
> This is what worked on my system..

From another thread on this forum

This worked great for me! Thanks!!

---

