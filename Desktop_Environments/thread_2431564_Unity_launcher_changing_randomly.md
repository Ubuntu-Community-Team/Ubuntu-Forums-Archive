---
title: "Unity launcher changing randomly"
date: 2019-11-18
forum: Desktop Environments
---

### Post by vin944 on 2019-11-18
I have installed Ubuntu 19.04 on an Intel NUC and the weirdest stuff just happens.  It reboots randomly with no set pattern I can see.  So I back dated to 18.04 to no avail.  Same nonsense.  I've checked logs, etc but I will write off the rebooting as a NUC issue.  

But I have such a peculiar Ubuntu issue that I cannot seem to find any reference to.  Once Ubuntu boots up the launcher bar is where it should be and on the top.  After a while it decides that it is time to turn into a tab which is accessible by clicking the "Activities" button at the top left.  This is both in 19.04 and 18.04.  Don't get me wrong, I like the new "TAB" style launcher I'm just wondering what is going on, lol.  Why does it boot up with the standard bar and then whenever it decides it's time, it changes to the "TAB" bar, lol?

Here are a couple of screenshots for you to look at.

Thanks.

---

### Post by CatKiller on 2019-11-18
I don't use Gnome and I didn't use Unity, so I can't help with your issue, but I can tell you that Ubuntu stopped using Unity by default with 18.04 and switched to Gnome instead. So, unless you've specifically installed Unity, you're using Gnome. Perhaps knowing that it's a Gnome problem rather than a Unity problem will help you to find solutions.

---

### Post by deadflowr on 2019-11-18
Not unity.
That's gnome shell.
gnome shell is the new default desktop for Ubuntu.

Not sure if it's relevant. but I do see you have an open window in the second image in the top workspace
(You see it in that tiny portion the shows in the right side.)
Does the behavior persist if no windows are open anywhere?

---

### Post by vin944 on 2019-11-18
For whatever reason I'm thinking Unity but in fact it is Gnome, thanks.  I do see the open window and there is no relationship to the launcher problem.  It does the same thing regardless of what may be open at the time.  

I don't really see the launcher as a problem though I'm just wondering why it changes and why I have never seen it before except on the NUC?  For the life of me I can't figure out how or why the launcher bar turns itself into a tab like that, lol.  I have another machine with Ubuntu 18.04 and it's never done that.  

The reboot problem I'm sure is with the NUC and I'm living with that.  However after reboot, the launcher is a normal bar and then after x hours it changes to a hidden "TAB" bar all by itself, lol.  I never see that change, it only does it when I'm not at the computer.  The first time I saw this was on 19.04 and thought maybe my reboot problem was 19.04 related.  So I ordered a new 128G HDD and proceeded to install 18.04.  I didn't want to clog up the original HDD because it was a challenge to get Myth installed.  I did get it installed and figured I would try to debug the reboot issue by getting a new HDD and install 18.04.  This is probably 4 months ago now.  The reboot issue and secondly the launcher changing remained.  I haven't been able to find and documentation about this TAB launcher so I'm puzzled by that.

Has anyone seen this behavior or for that matter experienced the TAB launcher like the one in the second pic?

Thanks for your replies,

---

### Post by Frogs Hair on 2019-11-18
The second picture used to be the default view when the activities tab was selected though I can't account for the difference from the first picture.

---

### Post by nicholascousar on 2019-11-19
Same thing happened to me. I don't have any pictures of my old enviroment, but I'm certain the dash/dock used to cover the entire width of the screen instead of just partially in the center. What's more frustrating though is that the volume down media key no longer works since this update.

---

### Post by mc4man on 2019-11-19
Your 1st screen is the default launcher for gnome-shell in an ubuntu session. I believe it's 'produced' via a built-in extension provided by Ubuntu. (for a ubuntu session
The 2nd is what would be seen in gnome-shell without Ubuntu's  extension, typically in a gnome-session.
Never heard of this happening during a session though..

(- next time it happens do this to check session
```
env |grep GDMS
```
Also see what happpens if you restart gnome-shell
Alt+F2 > type in r  then press enter key

---

### Post by vin944 on 2019-11-20
So it is morning now and the NUC has reboot itself leaving me at the default launcher bar.  Sometime today it will switch to the gnome-session launcher bar (TAB style).  
I ran all the commands you suggested and took 3 screenshots.  1st screenshot is before any commands, 2nd is after the grep command and 3rd is before restarting the session.  
After restart the session looks the same as the first screenshot.  Thanks for taking a shot at this.

---

### Post by vin944 on 2019-11-20
Update to my last post.  After a few hours the TAB launcher showed up.  I repeat the above steps and when I did a restart the default launcher came back.  
1st screenshot, magically appearing TAB launcher,
2nd screenshot, ran the grep command and did a restart, back to default launcher.  

Is there a command to get the TAB launcher (1st screenshot) back?

Thanks

---

### Post by mc4man on 2019-11-23
> **vin944 said:**
> Update to my last post.  After a few hours the TAB launcher showed up.  I repeat the above steps and when I did a restart the default launcher came back.  
1st screenshot, magically appearing TAB launcher,
2nd screenshot, ran the grep command and did a restart, back to default launcher.  

Is there a command to get the TAB launcher (1st screenshot) back?

Thanks

Not sure about 18.04, certainly in 19.04+ the dock in screen 1 (orig. post) is from the gnome-shell-extension-ubuntu-dock package.  So if you want the 'dock' as in the orig. screen 2 then remove that package and log out/in.

```
sudo apt purge gnome-shell-extension-ubuntu-dock
``` 
As to why the extension is failing mid session, no idea & somewhat a moot point if you don't want it. (though may be systemic of a bigger issue?? 
You could run this & look for any interesting lines that aren't a JS WARNING:
```
journalctl -r  |grep ubuntu-dock
```

---

### Post by vin944 on 2019-11-23
I saw this behavior in both 18.04 and 19.04.  I started with 19.04 and had this reboot issue plague my NUC like I've never seen.  So I got a new HDD to eliminate at least that part of the equation.  I rolled back to 18.04 and same chaotic rebooting, no pattern at all.  The only thing I can pin point is that it has never reboots when I am actually using it.  So I agree that a larger systemic issue exists but my expertise is not enough to dig it out.  (Good thing firefox lets you restore session, lol).   I'm an Elec. Engineer and have used Unix extensively so I'm pretty good on the command line.  

I ran the journalctl command and it spit out quite a bit so i piped to wc and got this: 621    6100   69834.  Lots of stuff there I can't make alot of sense out of.  Majority of lines are:  Nov 23 18:03:35 vin-NUC8i5BEH gnome-software[2397]: no app for changed [email]ubuntu-dock@ubuntu.com[/email]

I will remove the ubuntu-dock and see how that goes.  Why would they include 2 different docking schemes with the installs?   I like the tab dock quite a bit actually.   I'll let you know how that goes.

Thanks for the code and your help!

---

### Post by vin944 on 2019-11-23
I went to remove the dock with the purge command but got nervous when I saw Ubuntu-destop was going to be removed, lol  Here is the output I saw,

vin@vin-NUC8i5BEH:~$ sudo apt purge gnome-shell-extension-ubuntu-dock
[sudo] password for vin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-shell-extension-ubuntu-dock* ubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 174 not upgraded.
After this operation, 687 kB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

Is it OK to remove the ubuntu-desktop

Thanks

---

### Post by CatKiller on 2019-11-23
> **vin944 said:**
> 
Is it OK to remove the ubuntu-desktop
Yes. It's not really a package. It's a meta-package that depends on all the default software (so you can install it all at once). Since you'll no longer have all of the default software, you can no longer have that package either. 

It's probably worth reinstalling it before you upgrade to the next version of Ubuntu, just in case.

---

### Post by vin944 on 2019-11-24
> **mc4man said:**
> Not sure about 18.04, certainly in 19.04+ the dock in screen 1 (orig. post) is from the gnome-shell-extension-ubuntu-dock package.  So if you want the 'dock' as in the orig. screen 2 then remove that package and log out/in.

```
sudo apt purge gnome-shell-extension-ubuntu-dock
``` 
As to why the extension is failing mid session, no idea & somewhat a moot point if you don't want it. (though may be systemic of a bigger issue?? 
You could run this & look for any interesting lines that aren't a JS WARNING:
```
journalctl -r  |grep ubuntu-dock
```

I went ahead with purging the ubuntu dock and reboot.  All looks good now with the TAB launcher seeming to be the default.  Looks like the end of that mystery.  And I've got my favorite launcher now.  

I wonder if that may be the problem with my NUC and the chaotic rebooting.  I used the NUC most of the evening to ffmpeg edit a 22 minute video.  All was perfect while I was using the machine.  Then this morning when I got up, it had reboot itself (which didn't surprise me) but all of my .bash_history was gone.  Luckily because I used so many different ffmpeg commands, I made a ffmpeg history text file with history | grep ffmpeg > ffmpeg.history.txt.   Normally I wouldn't do that but for some reason I thought I should.  Good thing, so I can work with those commands today.  

Anyway after seeing that my history was not saved I figured might as well do the purge.   I will keep you posted to see if the ubuntu-dock purge had anything to do with the rebooting issue.  Thanks for your help ):P

---

### Post by vin944 on 2019-11-25
It is the next day and it has rebooted again overnight.  Maybe I will  start a different post under the correct heading.  Got the launcher  fixed and I appreciate the help.  Thanks all.

---

