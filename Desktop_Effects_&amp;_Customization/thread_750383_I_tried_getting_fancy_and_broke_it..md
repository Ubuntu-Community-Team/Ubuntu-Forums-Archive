---
title: "I tried getting fancy and broke it."
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by Jonga on 2008-04-09
Hi folks, this is my first post, until now I've been really enjoying the world of ubuntu and open source software.  Any help would be greatly appreciated.

Ok, so in my efforts to try to get the cube desktop thing going on I think I broke my ubuntu....

I went to visual effects and thought maybe my graphics card (abit amd 64) might be able to handle the 'extra' setting, so I clicked on it and it told me to restart my computer, so I did.   When it came back up my login screen looked like this....

[IMG]http://www.geocities.com/spash66/ubuntulogin.JPG[/IMG]

and when I moved the cursor around I gots me some tracers

[IMG]http://www.geocities.com/spash66/ubuntulogin2.JPG[/IMG]

so I logged in blindly to ubuntu and the desktop looked like this:

[IMG]http://www.geocities.com/spash66/ubuntudesktop.JPG[/IMG]

anyways I right clicked on the desktop to change visual effects back to 'none' mode only to find that it was already there, so just to be sure I restarted my computer and all the same stuff happened.  Then I figure what the heck, I'll give the middle one a try, after all it's already messed, and then I got this....

[IMG]http://www.geocities.com/spash66/graphicproblems.JPG[/IMG]

any ideas?  At this point I'd be happy just to get things back to normal.

I'm sorry if this has already been posted a lot, but I tried doing a search for graphics problems and got quite the list, none of which I could find that related to me.

---

### Post by Martje_001 on 2008-04-09
If you can still see it (:D) go to the restricted drivers manager and disable the driver.

---

### Post by fela on 2008-04-09
> **Martje_001 said:**
> If you can still see it (:D) go to the restricted drivers manager and disable the driver.

i was gonna say enable the driver. Maybe your right though.

---

### Post by russo.mic on 2008-04-09
Well,  My first recomendation is to ALWAYS backup your xorg.conf before making any changes!
goto a failsafe terminal and punch in this:

sudo dpkg-reconfigure -phigh xserver-xorg

follow the instructions and select the correct options and such.  That will get your X server back to default.  We'll work on 3d accel after that point.  

Let us know if you get it going!

Russo

---

### Post by Martje_001 on 2008-04-10
> **fela said:**
> i was gonna say enable the driver. Maybe your right though.
I think it went wrong when he/she enabled the driver ;).

---

### Post by Jonga on 2008-04-10
yeah, I did manage to get things back to somewhat normal.  I was able to get the failsafe prompt before, but for some reason it wasn't letting me into it this time, so I finally managed to muddle my way through the haze to disable the driver, and when I restarted I could actually see what was going on.  I also don't think i originally installed the amd 64 bit version of ubuntu, I was going to do a reinstall with that now (I don't have anything important on here) that I got it on disk.  Thanks for info.  I think maybe I'll go do a bit of reading before I go and start clicking on random settings (although that is half the fun).

---

### Post by fela on 2008-04-11
> **russo.mic said:**
> Well,  My first recomendation is to ALWAYS backup your xorg.conf before making any changes!

Well yeah, that's a good idea...but once i ended up with like 400 backup copies of xorg.conf :)

that's why when I edit it (mind you this is not a good idea) I DO NOT take a backup copy! i'm fed up of backups everywhere, clogging up my disk... ***_[COLOR="Red"]BUT IF YOU ARE A NEWBIE OR IF YOU JUST WANT TO FEEL SAFE THAT YOUR SYSTEM ISN'T GONNA BREAK ANY TIME SOON, PLEASE DO BACKUP YOUR XORG CONFIG FILE BEFORE EDITING IT!!!!!![/COLOR]_***

---

### Post by Jonga on 2008-04-11
Well, I got my computer running again smoothly, in the high graphics mode without it wigging out even.  I've actually learned a good bit through all this poking around.  Even reinstalling was a bit tough until I figured out how to change the boot priority on  my computer.  Now I'm gonna try to go figure out this cube stuff, I was reading this little bit how to make it operational in ubuntu 7.04 but maybe thats different in 7.10 as I could not find the enable desktop effects button for the life of me.

"Ubuntu 7.04 comes with some quite nifty desktop effects, these can be enabled by clicking System on the top panel and selecting Desktop Effects on the Preferences menu.

When the desktop effects window launches click the Enable Desktop Effects button, make sure that both options below the button are ticked and click Close.

You can now start using the desktop effects. To switch to another desktop (in the process, using the desktop cube), click Ctrl + Alt and the left or right keys, clicking the up and down keys shows all the desktops in a long horizontal area across the screen.

The desktop effects are based on compiz and make working with Ubuntu a lot nicer and you can show off in front of everyone, it will certainly catch some peoples eyes."

---

### Post by fela on 2008-04-11
> **Jonga said:**
> Well, I got my computer running again smoothly, in the high graphics mode without it wigging out even.  I've actually learned a good bit through all this poking around.  Even reinstalling was a bit tough until I figured out how to change the boot priority on  my computer.  Now I'm gonna try to go figure out this cube stuff, I was reading this little bit how to make it operational in ubuntu 7.04 but maybe thats different in 7.10 as I could not find the enable desktop effects button for the life of me.

I realized by trial and error (at least for my problem) when it said all that s**t about low graphics mode, all i had to do was ```
sudo apt-get install linux-restricted-modules-`uname -r`
``` in terminal, restart, select the kernel that kept booting into vesa, and it should work fine.
For the cube, install compizconfig-settings-manager thru apt-get. Then system > preferences > advanced desktop effects then enable 'Cube' and 'Rotate Cube'. Disable desktop wall when it asks (so you can enable cube instead). There is also cube reflection which is quite nice.

EDIT: the cube thingy the way i told you only works in gutsy or later.

---

### Post by Jonga on 2008-04-11
Sweet it worked, my desktop's starting to look wicked.  Time to go see what else I can break.:-P

---

### Post by russo.mic on 2008-04-11
nothing personal,  fela,  I think it's quite irresponsible to recommend or inadvertently recommend people make changes to xorg without backing up.  if your only complaint is your disk gets clogged by a file an average of a few kilobytes, may i recommend the command rm, poss. with sudo in the front...?

The point is, for newbies esp.  who are going to want compiz and all these fun things they shouldn't feel afraid to try and set them up that there going to break there system.  If all you have to do is instruct them to cp over xorg with a backup you made a few minutes ago, everyone can rest a bit at ease.  Usually I keep one backup, called xorg.conf.bkup, and only keep my latest working copy.  

Not to stand on a soapbox, but please, backup your xorg.

Russo

---

### Post by fela on 2008-04-11
> **russo.mic said:**
> nothing personal,  fela,  I think it's quite irresponsible to recommend or inadvertently recommend people make changes to xorg without backing up.  if your only complaint is your disk gets clogged by a file an average of a few kilobytes, may i recommend the command rm, poss. with sudo in the front...?

The point is, for newbies esp.  who are going to want compiz and all these fun things they shouldn't feel afraid to try and set them up that there going to break there system.  If all you have to do is instruct them to cp over xorg with a backup you made a few minutes ago, everyone can rest a bit at ease.  Usually I keep one backup, called xorg.conf.bkup, and only keep my latest working copy.  

Not to stand on a soapbox, but please, backup your xorg.

Russo

I didn't reccomend it, i was just saying that is what i do (as the only changes i make to /etc/X11/xorg.conf are changes that i can correct, as i know the syntax of it). Once again, this ***_[COLOR="Red"]IS NOT RECCOMENDED IF YOU DO NOT FEEL LIKE BREAKING YOUR SYSTEM...[/COLOR]_***

do i make myself clearer now? ;)

---

### Post by fela on 2008-04-11
thanks for the advice, i have editied my previous post.

---

### Post by russo.mic on 2008-04-14
Rock'in.

Russo

---

