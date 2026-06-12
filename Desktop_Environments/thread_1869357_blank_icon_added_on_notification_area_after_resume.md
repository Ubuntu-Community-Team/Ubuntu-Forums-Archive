---
title: "blank icon added on notification area after resume since ugrade"
date: 2011-10-25
forum: Desktop Environments
---

### Post by digit_al on 2011-10-25
Hello,

I am using lubuntu since 11.4 and it was working perfectly fine until I did the upgrade to 11.10.

Since then, each time I resume from suspend (close/open lid of the laptop), a blank icon is added in the notification area.

So far, I was unable to find the cause of it, either by myself, or trying to search on the web for a similar problem.

The problem is annoying, because I might end up with more than 10 blank icons...

The solution I found so far to resolve the issue (appart from logoff/logon), is to remove the notification area applet from the panel, and to add it again.

Any idea what is causing this ?

Thanks a lot in advance for any help.
Digit.

---

### Post by dingo on 2011-10-26
I have the same problem on my eeepc with a fresh install of lubuntu 11.10. 

There are two bugs filed about this problem. You may want to add a comment to one or both of them confirming that you have the problem also.  

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/880010]("https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/880010")

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878]("https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878")

By the way, restarting the panel removes the empty space:

```
lxpanelctl restart
```

---

### Post by digit_al on 2011-10-27
Thanks dingo,

I will follow the issues closely on launchpad.

I tried to register to report the issue on my Acer AS1410, but I never received the email from launchpad... will retry tomorrow.

Thanks again.

---

### Post by croque on 2011-10-28
I believe this is related to the battery icon which is controlled by the xfce4 power manager. When I set the power manager to never show the icon...I do not get the extra space added after every suspend (on a freshly installed and updated Lubuntu 11.10 eeepc 1005ha).

Try this. First get rid of the extra space (if any) by resetting the panel.
```
lxpanelctl restart
```Then open the XFCE Power Manager.
```
xfce4-power-manager-settings

```Under 'System tray icon' select 'Never show icon' and click Close.

Now try suspending the computer and see if that fixes it.

---

### Post by digit_al on 2011-10-28
I confirm it fix the issue for me.
But it's also annoying to not have this icon :(

---

### Post by amjjawad on 2011-10-28
> **dingo said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/880010](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/880010)

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878)


Apparently, these two bugs are effecting Laptops ONLY. Too bad I don't have a laptop to produce it. I just did a fresh install for Lubutnu 11.10 and did couple of Suspend but everything is fine. I even added the Power Manager Icon but everything is fine.

I was wondering if users who got that bug whether they did update and upgrade their systems?

---

### Post by amjjawad on 2011-10-28
> **croque said:**
> I believe this is related to the battery icon which is controlled by the xfce4 power manager. When I set the power manager to never show the icon...I do not get the extra space added after every suspend (on a freshly installed and updated Lubuntu 11.10 eeepc 1005ha).

Try this. First get rid of the extra space (if any) by resetting the panel.
```
lxpanelctl restart
```Then open the XFCE Power Manager.
```
xfce4-power-manager-settings

```Under 'System tray icon' select 'Never show icon' and click Close.

Now try suspending the computer and see if that fixes it.

Could you please try that on your laptop while it's on battery not plugged to the A/C power?

Waiting for your feedback :)

---

### Post by croque on 2011-10-28
On battery power it still works as it should. No extra space in the tray after 3 suspends and resumes.

---

### Post by amjjawad on 2011-10-28
> **croque said:**
> On battery power it still works as it should. No extra space in the tray after 3 suspends and resumes.

So, as per your workaround, even on battery, there is no more extra space? that's good :) but of course the icon must be removed, right?

---

### Post by croque on 2011-10-28
Yes...as far as I can tell (based on my only Lubuntu laptop)...if the battery icon is present, the extra space will be there after a suspend/resume. If the icon is not there, no additional space is added after suspend/resume.

More evidence: I looked at all the screenshots showing this problem on ubuntuforums and over on launchpad...they all have the battery icon present.

So yes...it seems to be a work-around, but not really a fix, because the battery icon is helpful on a laptop.

---

### Post by amjjawad on 2011-10-28
> **croque said:**
> Yes...as far as I can tell (based on my only Lubuntu laptop)...if the battery icon is present, the extra space will be there after a suspend/resume. If the icon is not there, no additional space is added after suspend/resume.

More evidence: I looked at all the screenshots showing this problem on ubuntuforums and over on launchpad...they all have the battery icon present.

So yes...it seems to be a work-around, but not really a fix, because the battery icon is helpful on a laptop.

Ok, thanks for the explanation :)
Could you please post on the bug reports about your work-around until the devs find a fix?

---

### Post by croque on 2011-10-28
Done.

Hopefully, the devs will consider this bug to be a priority. It's the kind of thing that might discourage people from using Lubuntu on their laptops. 

I know I was reluctant to install Lubuntu on my other laptops because of this bug...but now I'm going for it. :D

---

### Post by Bazon on 2011-10-29
> **croque said:**
> I believe this is related to the battery icon which is controlled by the xfce4 power manager. When I set the power manager to never show the icon...I do not get the extra space added after every suspend (on a freshly installed and updated Lubuntu 11.10 eeepc 1005ha).

Try this. First get rid of the extra space (if any) by resetting the panel.
```
lxpanelctl restart
```Then open the XFCE Power Manager.
```
xfce4-power-manager-settings

```Under 'System tray icon' select 'Never show icon' and click Close.

Now try suspending the computer and see if that fixes it.

Aargh! I don't have such a setting in my xfce4-power-manager-settings! (see screenshot. "Bildschirm sperren im Ruhezustand/Standby" means /lock screen on suspend/hilbernate".)

Is there another way to access the setting of the tray icon?

---

### Post by Bazon on 2011-10-29
Oops, there **is** this setting, now I found it!
*(I was blind because I was not looking for a dropdowm menu but a selectable list...)*

Switching the battery monitor off is not so bad, as there is a LXDE panel applet doing mostly the same thing. :-)

In order to still access the power settings, you can [this]("http://ubuntuforums.org/showpost.php?p=11383983&postcount=4"):

> **amjjawad said:**
> 
From LXTerminal, please run:

```
sudo leafpad /usr/share/applications/xfce4-power-manager-settings.desktop
```

Replace this line:

```
OnlyShowIn=XFCE;
```

with

```
#OnlyShowIn=XFCE;
```

Save, Exit and check your Menu > Preferences

---

### Post by amjjawad on 2011-10-29
> **Bazon said:**
> Oops, there **is** this setting, now I found it!
*(I was blind because I was not looking for a dropdowm menu but a selectable list...)*

Switching the battery monitor off is not so bad, as there is a LXDE panel applet doing mostly the same thing. :-)

In order to still access the power settings, you can [this]("http://ubuntuforums.org/showpost.php?p=11383983&postcount=4"):

One of the things I'd LOVE to see in Lubuntu 12.04 is these settings to be my default in the Menu and one doesn't have to do all that :)
I'm trying to find some time to write my list on this thread: [http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)

---

### Post by bs5765 on 2011-11-21
I "fixed" it by using an alias to fix the panel for me without having to type out the long command everytime. Coming out of Suspend, I open a terminal and type "fixpan" (without quotes) and my panels automagically fix themselves!

To get this effect, open a terminal and paste the following:

```
leafpad ~/.bash_aliases
```

Now paste the next line into leafpad:

```
alias fixpan='lxpanelctl restart'
```

Close leafpad and save. Close and reopen the terminal. Now you can type "fixpan" and it will fix your panel.

---

### Post by amjjawad on 2011-11-27
> **bs5765 said:**
> I "fixed" it by using an alias to fix the panel for me without having to type out the long command everytime. Coming out of Suspend, I open a terminal and type "fixpan" (without quotes) and my panels automagically fix themselves!

To get this effect, open a terminal and paste the following:

```
leafpad ~/.bash_aliases
```Now paste the next line into leafpad:

```
alias fixpan='lxpanelctl restart'
```Close leafpad and save. Close and reopen the terminal. Now you can type "fixpan" and it will fix your panel.

Hi everyone,

Could someone please confirm whether the above workaround is able to fix the issue or not?

Thanks!

---

### Post by croque on 2011-11-27
> **amjjawad said:**
> Hi everyone,

Could someone please confirm whether the above workaround is able to fix the issue or not?

Thanks!

This doesn't actually fix the issue...but it makes it easier to reset the panel after a suspend to get rid of the added blank space. You would still have to type the command every time you wanted to get rid of the extra space.

---

### Post by amjjawad on 2011-11-27
> **croque said:**
> This doesn't actually fix the issue...but it makes it easier to reset the panel after a suspend to get rid of the added blank space. You would still have to type the command every time you wanted to get rid of the extra space.

Thanks a lot for the confirmation :)

---

### Post by erchinoald on 2011-12-15
Has anyone found a fix for this, rather than the workarounds outlined above? Experiencing the same issue and it's quite annoying - Lubuntu 11.10 on a Samsung NC10. Cheers.

---

### Post by amjjawad on 2011-12-15
> **erchinoald said:**
> Has anyone found a fix for this, rather than the workarounds outlined above? Experiencing the same issue and it's quite annoying - Lubuntu 11.10 on a Samsung NC10. Cheers.

Hi,

Have you checked the reported bug(s) on Launchpad? Developers don't read/look at the forum but they do read and look at Launchpad :)

---

### Post by erchinoald on 2011-12-15
> **amjjawad said:**
> Hi,

Have you checked the reported bug(s) on Launchpad? Developers don't read/look at the forum but they do read and look at Launchpad :)
Sorry, I've just looked now. This report appears to be where the action is: [https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/846878) ...but unfortunately there does not appear to be any solution yet. I'm not sure if at this stage it's worth adding anything to that or if I should just wait for it to be resolved?

---

### Post by amjjawad on 2011-12-15
> **erchinoald said:**
> I'm not sure if at this stage it's worth adding anything to that or if I should just wait for it to be resolved?

Anything like what? :)
If you have something that will help to fix the issue then definitely go ahead and add that to the report, otherwise you need to wait :)

---

### Post by erchinoald on 2011-12-17
> **amjjawad said:**
> Anything like what? :)
If you have something that will help to fix the issue then definitely go ahead and add that to the report, otherwise you need to wait :)
Anything such as 'I'm having the issue as well on an NC10'. So I suppose no, I shall continue to wait... Thanks.

EDIT: I followed these instructions on the bug report as a workaround:

> As mentioned further up:

Clean up the Panel
lxpanelctl restart

In xfce4-power-manager
Set "System Tray Icon" to the "Never Show Icon"

Then install the non default batter monitor

sudo apt-get install xfce4-battery-plugin

And add it to your panel
...however the new battery monitor doesn't work and just says that my battery is 100% all the time. But now I can't seem to get the original xfce4-power-manager back as I selected 'never show icon'. I presume I'm missing something basic, how can I get the regular (broken) one back?

---

### Post by amjjawad on 2011-12-17
> **erchinoald said:**
> Anything such as 'I'm having the issue as well on an NC10'. So I suppose no, I shall continue to wait... Thanks.

If you are not the one who reported that bug but that bug affect you too then you can simple click on "This bug affects 6 people. Does this bug affect you?" and leave a comment if you like.

> EDIT: I followed these instructions on the bug report as a workaround...however the new battery monitor doesn't work and just says that my battery is 100% all the time. But now I can't seem to get the original xfce4-power-manager back as I selected 'never show icon'. I presume I'm missing something basic, how can I get the regular (broken) one back?

I'm currently on Lubuntu 11.04 (doing some tests) and I need to restart but I have to leave the house and go to the clinic so will check it later. In the meantime, you can remove the applet from LXPanel and re-add it, logout or restart then check whether it's back or not.

---

### Post by amjjawad on 2011-12-17
@erchinoald

Check this thread from the beginning, I think the workaround is mentioned there somewhere. Sorry again but I must go!

---

### Post by erchinoald on 2011-12-17
Thanks, I got back to it now - I just had to navigate to the settings screen via terminal.

Frustratingly, all of this has caused me a new problem. Now whenever I return from suspend, I am asked to enter my password on a weird xscreensaver 5.14 login screen. It doesn't look like a normal login screen, and in any case I have screen locking switched off! :mad: Linux can be so trying for newcomers...

---

### Post by amjjawad on 2011-12-17
> **erchinoald said:**
> Thanks, I got back to it now - I just had to navigate to the settings screen via terminal.

Glad you managed that :)

> Frustratingly, all of this has caused me a new problem. Now whenever I return from suspend, I am asked to enter my password on a weird xscreensaver 5.14 login screen. It doesn't look like a normal login screen, and in any case I have screen locking switched off! :mad: Linux can be so trying for newcomers...

I don't Suspend at all so I have no problems.

Since you are newcomer, please read this: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

It has nothing to do with your issue but it will enlighten your path :)

---

### Post by ogilvierothchild on 2012-02-15
Here is my work-around

In a terminal shell, type:
> 
sudo mkdir -p /usr/local/bin
gksudo gedit /usr/local/bin/lxpanel-reset.sh


Now in that editor window, paste the following:
> #!/bin/sh

# only kill panel on current X11 DISPLAY
kill `ps e -Clxpanel  | grep "DISPLAY=$DISPLAY" | awk '{print $1}'`

# restart
cd ; nohup lxpanel -p LXDE &


Save the file end exit the editor.  Back at the terminal shell prompt, type:
> 
sudo chmod a+rx /usr/local/bin/lxpanel-reset.sh


Open a new shell, you should be able to type "lxpanel-reset.sh" and the lxpanel should restart on command.

Now, we want a button on the toolbar to do this for us, so it's jsut a single click. So in a terminal shell, type:

> 
mkdir -p ~/.local/share/applications
gedit ~/.local/share/applications/lxpanel-reset.desktop


Now in that file, paste in the following
> 
[Desktop Entry]
Categories=Utility;GTK;
Comment=Kill lxpanel and restart with LXDE profile
Exec=/usr/local/bin/lxpanel-reset.sh
Icon=reload
Name=LXPanel Restart
NoDisplay=false
StartupNotify=false
Terminal=false
Type=Application


Save that, and now the "lxpanel reset" program shows up in the main LXDE menu under "Accessories".  Logout and login to be sure.

Now on the lxpanel, right click, goto "Panel Settings", click the "Panel Applets" tab, click "+ Add" , find and click "Application Launch Bar", click  the "+ Add" button at the bottom, now back in "Panel Applets" the new Application Launch Bar is at the bottom of the list. Click on it, then click the "Edit" button on the side.  A new window pops up (you might have to move the "panel preferences" window to the bottom of the screen to get at the new window).  

In the new window (Application Launch Bar) click the small triangle to expand that submenu list.  Scroll down to "LXPanel Restart" and click it, then in the middle of that window click the "+ Add" button.  Then click "Close" at the bottom.

Now back in "panel preferences", you can click that "Application Launch Bar" (last entry in the "panel applets" list), and use the "Up" / "Down" buttons to position it.

Now, if your system tray goes wonky, just click that lxpanel reset icon and it will reset it.

I almost didn't use LXDE at all because of this issue, but I find clicking that button takes a fraction of a second, so doing that 10x a day is not a chore; i hardly notice it.

---

### Post by Andrew York on 2012-02-24
A half-decent workaround I've found it to automatically restart your panel on resume. I added a script to /etc/pm/sleep.d called reset_panel:
 
```
#!/bin/bash
case "$1" in
   suspend|hibernate)
      #do nothing
   ;;
   resume|thaw)
      sleep 5 && lxpanelctl restart
   ;;
   *)
      exit 1
   ;;
esac
exit 0

```
You gotta add the 'sleep' part, I suspect 'cause the icon movement happens after this script executes.

(I more or less copied a script I found in the same directory, called restore_brightness, which I think is a Toshiba thing)

Using Lubuntu 11.10 on a Toshiba r835, very pleased so far. System has yet to crash, everything works out of the box. Lots of little tweaks to get Lubuntu juuuust how I like it, of course.

EDIT: I had to refine this script a little, as described here: [http://askubuntu.com/questions/107276/how-can-i-get-a-script-to-always-run-on-resume-in-lubuntu](http://askubuntu.com/questions/107276/how-can-i-get-a-script-to-always-run-on-resume-in-lubuntu)

The improved script:
```

#!/bin/bash
case "$1" in
   suspend|hibernate)
      #do nothing
   ;;
   resume|thaw)
      export DISPLAY=:0 #What does this do? Are there side effects?
      sleep 5 && lxpanelctl restart & #Delayed so the battery icon can finish wrecking shop.
   ;;
   *)
      exit 1
   ;;
esac
exit 0

```

---

### Post by rathpberries on 2012-10-16
I used your step-by-step method and just made a button for myself as well. Google brought me here, just fyi. I also branched off from your idea and made a Play/Pause button up there too, awesome!

---

### Post by kwiadnyana on 2012-12-11
> **ogilvierothchild said:**
> Here is my work-around

In a terminal shell, type:


Now in that editor window, paste the following:


Save the file end exit the editor.  Back at the terminal shell prompt, type:


Open a new shell, you should be able to type "lxpanel-reset.sh" and the lxpanel should restart on command.

Now, we want a button on the toolbar to do this for us, so it's jsut a single click. So in a terminal shell, type:



Now in that file, paste in the following


Save that, and now the "lxpanel reset" program shows up in the main LXDE menu under "Accessories".  Logout and login to be sure.

Now on the lxpanel, right click, goto "Panel Settings", click the "Panel Applets" tab, click "+ Add" , find and click "Application Launch Bar", click  the "+ Add" button at the bottom, now back in "Panel Applets" the new Application Launch Bar is at the bottom of the list. Click on it, then click the "Edit" button on the side.  A new window pops up (you might have to move the "panel preferences" window to the bottom of the screen to get at the new window).  

In the new window (Application Launch Bar) click the small triangle to expand that submenu list.  Scroll down to "LXPanel Restart" and click it, then in the middle of that window click the "+ Add" button.  Then click "Close" at the bottom.

Now back in "panel preferences", you can click that "Application Launch Bar" (last entry in the "panel applets" list), and use the "Up" / "Down" buttons to position it.

Now, if your system tray goes wonky, just click that lxpanel reset icon and it will reset it.

I almost didn't use LXDE at all because of this issue, but I find clicking that button takes a fraction of a second, so doing that 10x a day is not a chore; i hardly notice it.
This is the best!!! It solves other problems (like the entire task bar going out to lunch after suspend -- I Put a shortcut on the desktop, double clicking it brings the task bar back to work).

SUPER!

THANKS!!!

---

