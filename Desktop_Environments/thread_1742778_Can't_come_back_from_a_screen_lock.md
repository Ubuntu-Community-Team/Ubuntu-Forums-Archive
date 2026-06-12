---
title: "Can't come back from a screen lock"
date: 2011-04-29
forum: Desktop Environments
---

### Post by th1rt3en on 2011-04-29
Living with others, I've made it a habit to lock my laptop if I walk away from it (Ctrl+Alt+L), but with the recent upgrade to 11.4 I've run into a problem: when I go to unlock my laptop it just gives me a black screen instead of the "enter your password" menu. All I get is the mouse.

The only work around I have for this is to log into a TTY and then restart the laptop. 

In case it's significant, the exact process I go through is as follows: Lock my screen (Ctrl+Alt+L), close the laptop lid (power management is set to just blank the screen instead of suspend), walk away for 10+ minutes, open lid, and then I run into my error.

I would also be more than happy to do my part and submit an error report through launchpad, but I have no idea what package this would fall under. If anybody knows what package is responsible for locking the screen or how I can find out I would appreciate the information.

---

### Post by th1rt3en on 2011-04-29
Wait, scratch what I just said. I don't think it's the screen lock that's the issue. Since I encountered the error I stopped locking the screen and just started closing the laptop lid. Same thing happened, only it was whatever screen I had left off on before.

In this case it was my alarm clock; I set it to go off at 4:30am around midnight, closed the lid, then went to sleep. My alarm went off just fine, but when I opened the lid to turn it off it still read the same time as it did when I closed it (midnight) and all I had was mouse function, nothing else worked.

So the problem, then, must have something to do with the screen being blanked when I close the lid.

---

### Post by mpace965 on 2011-04-30
I'm having a similar problem when I close my lid. Except I don't even get a mouse.

---

### Post by manzdagratiano on 2011-04-30
There is an existing bug report for such issues - Bug #762918:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762918](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/762918)
It seems to have a wide range of symptoms related to the screensaver and locking. You do not need to reboot the machine however. Just log into tty1 and issue 'sudo pkill X', which will restart the X server, and you will happily see gdm restarting. It is annoying but one can live with it.

---

### Post by mpace965 on 2011-04-30
Ok tried ```
sudo pkill X
``` and resumed session, tried Suspend, and the same thing happened as before.

---

### Post by th1rt3en on 2011-04-30
> **manzdagratiano said:**
> Just log into tty1 and issue 'sudo pkill X', which will restart the X server, and you will happily see gdm restarting. It is annoying but one can live with it.

This workaround works great, much better than the primitive one I was using before. Certainly manageable until it's fixed in the future. Thanks for the link to the bug report too by the way. I'm marking this thread as solved.

---

### Post by manzdagratiano on 2011-04-30
You are welcome... glad to be of help!
My X does not freeze after a suspend, only after idling with screensaver enabled, though some people have reported freezes after locking. Until this issue is fixed, killing X whenever there is an issue is the only workaround it seems.

---

### Post by Krytarik on 2011-04-30
How about replacing it by xscreensaver in the meantime?:
[http://ubuntuforums.org/showthread.php?p=10385503#post10385503](http://ubuntuforums.org/showthread.php?p=10385503#post10385503)

Greetings.

---

### Post by kyleflan on 2011-04-30
I tried Krytarik's suggestion. However, instead of freezing on a black screen, it freezes on a screen shot. The mouse cursor moves but I'm not able to click anything. The keyboard also appears not to be working.

---

### Post by Krytarik on 2011-04-30
> **kyleflan said:**
> I tried Krytarik's suggestion. However, instead of freezing on a black screen, it freezes on a screen shot. The mouse cursor moves but I'm not able to click anything. The keyboard also appears not to be working.
That is completely unrelated to the screensaver/lock feature, and would happen with gnome-screensaver, too. What type of screenshot were you trying to do then? Both may be video driver related, what card/chip do you have, what driver are you running?

---

### Post by abhiramcr on 2011-05-28
Hi!
I have a problem something similar too. I have an a Semperon 1800-32bit on a Gigabyte M61-SME-S2 motherboard. Recently, I updated the graphics driver for the on-board NVidia GeForcr6100 and started using Ubuntu11.04 with the Unity. 
Ever since, there's this problem. When the screen locks out after the set time, a blank white screen is all that is displayed. Not even mouse movements are recognized. I initially saw no option to log-in back and was a bit confused (I actually was doing a system-reset). But just a try to ctrl-Alt-Del and keying in my password let me through. I guess the problem is to do with the screen lock window that never pops up when the display goes to sleep.
Maybe, it's not really necessary to do the xkill at all... :) just enter the password and see if you're able to log-in again... hope that helps.

Also, appreciate knowing if this is any bug that's alive in the database. I checked a couple of them, but wasn't sure whether i'm close to those.

Thanks in advance. :)
-abhi

Update after 3 hrs of original post: seems like it's all the issue with the screensaver thingie. Let me wait for the bugfix mentioned up above in this thread. :)

---

### Post by petoro on 2011-06-20
Same problem here, I have an Intel X3100 Graphics Card, and I get sporadic freezes when I come back from a period of inactivity.

In this page:

[http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)

They say that the linux kernel should be upgraded from 2.6.38 to 2.6.39.0 to solve this.  And they give instructions for doing it.

Is it advisable to make this upgrade?

Or is it better to wait for the automatic upgrade when the new kernel is ready for Ubuntu 11.04 Natty Narwhal?

Thanks

---

### Post by Krytarik on 2011-06-20
@petoro: Yeah, why not give it a try! Your currently used kernel will keep installed, and you can choose it at the boot menu (you may need to press the Shift key upon boot to make it appear).

---

### Post by petoro on 2011-06-20
> **Krytarik said:**
> @petoro: Yeah, why not give it a try! Your currently used kernel will keep installed, and you can choose it at the boot menu (you may need to press the Shift key upon boot to make it appear).


Thanks Krytarik for the advice.

The problem is that I don't have Grub.  Natty is the only SO I have installed in my computer.

---

### Post by Krytarik on 2011-06-20
> **petoro said:**
> 
The problem is that I don't have Grub.  Natty is the only SO I have installed in my computer.
Believe me, you *have* Grub2 installed. It's just because Ubuntu is your only OS that you don't get the boot menu appear by default. You just need to press the Shift key upon boot to make it appear, like I said.

---

### Post by petoro on 2011-06-20
Thanks again,


I will wait a little bit for Canonical to make the automatic update of the Kernel.

In case they don't, I will make the upgrade myself.

I will inform you then.


Have a good day/night.


Petoro

---

### Post by petoro on 2011-07-21
Eureka!


I think that comment #82 by Aitor Guevara in launchpad has solved my freezes too.

[https://bugs.launchpad.net/acpi/+bug/762918/comments/82](https://bugs.launchpad.net/acpi/+bug/762918/comments/82)

At least I've been without freezes for more than 50+ hours, after applying his very simple guidelines.

Let's hope that not much people has bought another computer thinking this was a hardware problem.  And let's hope this is a definitive repair.

The solution is also here:

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

It works for me, although I have an Intel 3100 graphics card instead of an AMD one.

I didn't have to install compizconfig-settings-manager as indicates in this last link because I had it installed already.

So, this simple things are what I had to do:

Press the Window Logo button <Super> and type 'Compiz'. Launch the settings manager and navigate to 'OpenGL' plugin. Disable the 'Sync to VBlank' option and reboot your PC.


Hope this helps,


Josechu

---

### Post by am_i_registered on 2012-01-17
Hi all, I'm writing a reply, although it's marked as solved, since the thread describes exactly my problem and the solutions provided does not work...

I have exactly the same problem with [th1rt3en]("http://ubuntuforums.org/member.php?u=1222743") the user who opened this tread.

When, my screensaver kicks in, the screen gets black but the mouse is visible. I can move the mouse, but the screen remains black and the lock screen menu is not showing. Actually, the lock screen menu does not activate itself (by pressing Alt+Ctrl+Delete and then Enter, I'm logging out). When logging in again, unity's behavior is strange, all windows maximize to the top of the screen and thus most menus are hidden behind the global menu bar. Rebooting restores unity to normal until screensaver kick in again...

Everything was working ok until today.... 

It sounds to me like a bug of gnome-screensaver... BUT:

After a lot of googling for a solution with no results, I tried removing the gnome-screensaver using the terminal:
```
sudo apt-get remove gnome-screensaver
```After rebooting I clicked the lock screen menu in the global menu, which did nothing - I was expecting the menu to disappear after the removal of gnome-screensaver, but doing nothing it's ok and since unity's behavior was back to normal I decided to live without it...

After a while my screensaver kicked in :P 
Moving my mouse stopped it... but no lock screen... I double checked and gnome-screensaver is not installed :guitar:
I tried to lock the screen using the key combination Alt+Ctrl+L and a pop-up windows appeared with the following message:
> Couldn't execute command: gnome-screensaver-command --lock
Verify that this is a valid command.Any ideas???

BTW: I'm using 11.10 x64

---

### Post by am_i_registered on 2012-01-17
Problem solved!

I deleted xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```

and rebooted the machine.

:lolflag:

---

### Post by edanto on 2012-01-21
Thanks for posting the tip.  I have the same problem, but don't understand the implications of deleting xorg.conf - could something go wrong if I do that?

I tried the solution [http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html) (Disable the 'Sync to VBlank' option)

but my screen is still staying black after I try and resume.  Eager to try deleting xorg.conf in case it fixes the problem, but I'm very much a novice and would be cautious of making things worse!

---

### Post by am_i_registered on 2012-01-21
> **edanto said:**
> Thanks for posting the tip.  I have the same problem, but don't understand the implications of deleting xorg.conf - could something go wrong if I do that?

I tried the solution [http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html) (Disable the 'Sync to VBlank' option)

but my screen is still staying black after I try and resume.  Eager to try deleting xorg.conf in case it fixes the problem, but I'm very much a novice and would be cautious of making things worse!

Hi, unless you have created a customized xorg.conf, which you would like to keep... there is no problem deleting the xorg.conf, since ubuntu will create a new one on next boot.

You could also, rename it and keep it with another name in case you need to restore it.
Try this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

and then:

```
sudo rm /etc/X11/xorg.conf
```

finally:
```
sudo reboot
```

I hope this will solve your issue... it's very annoying!

---

### Post by edanto on 2012-01-21
Ah - thank you very much for the explanation.

In my case, there isn't an xorg.conf file in that directory though.

```
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
```

hmmm, where next?!

---

### Post by am_i_registered on 2012-01-21
> **edanto said:**
> Ah - thank you very much for the explanation.

In my case, there isn't an xorg.conf file in that directory though.

```
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
```hmmm, where next?!

Try to create a new user and login. Let me know if the problem is still there...

---

### Post by edanto on 2012-01-21
No, unfortunately that didn't help.

One thing that was different when I made a test User account was when I logged in as the test user, there were a bunch of updates ready to install.  In my main account, when I go to System Info, it just hangs on 'checking for updates'

When I left the test account for while, logged in, and came back to the computer the screen was just black and wouldn't wake.  I think I could barely make out the shape of some windows on the screen, incredibly dim - if that helps at all in the diagnosis.

---

### Post by am_i_registered on 2012-01-21
> **edanto said:**
> No, unfortunately that didn't help.

One thing that was different when I made a test User account was when I logged in as the test user, there were a bunch of updates ready to install.  In my main account, when I go to System Info, it just hangs on 'checking for updates'

When I left the test account for while, logged in, and came back to the computer the screen was just black and wouldn't wake.  I think I could barely make out the shape of some windows on the screen, incredibly dim - if that helps at all in the diagnosis.

At least now we know it's not something related to your user's settings.

for the updates open a terminal and try this:

```
sudo apt-get update
sudo apt-get upgrade
```

did you try to reset unity? if not give it a try:

Open tty1 by pressing Ctrl+Alt+F1 and login, then type:

```
sudo unity --reset
```

If I think of smth else, i'll write...

Let me know if the above works...

---

### Post by Nikolai D. on 2012-10-17
Hi ppl :)

i have installed xfce desktop and mate desktop ad gnome-shell the third to test them. On my 12.04 64bit. And i had freezing lock screen. The white-transparent one with the moving mouse. The remove xscreensaver and the disable opengl sync to v black setting in compiz did not help me.

But the Unity reset command helped me.

Thanks,
Nikolai

---

