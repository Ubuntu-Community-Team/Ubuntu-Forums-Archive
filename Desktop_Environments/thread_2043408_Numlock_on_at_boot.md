---
title: "Numlock on at boot?"
date: 2012-08-16
forum: Desktop Environments
---

### Post by bug67 on 2012-08-16
Recently aquired a laptop with a numeric keypad that I installed Xubuntu on.  Most everything works as it should.  However, when I boot the machine, the numlock does not automatically come on.  I have to turn it on manually every time by hitting the numlock key.

I tried following my own directions here:
[http://ubuntuforums.org/showthread.php?t=1694845](http://ubuntuforums.org/showthread.php?t=1694845)
but when I get to this line:
```
sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
```
I receive this:
```
cp: cannot start '/etc/gdm/Init/Default': No such file or directory
```

I also tried adding numlockx to the startup items but, that didn't work either.

Any idea what I'm doing wrong and how to get the numeric keypad working at boot?

---

### Post by drs305 on 2012-08-16
For Ubuntu, you now put the setting in lightdm.conf:
/etc/lightdm/lightdm.conf
> greeter-setup-script=/usr/bin/numlockx on

Possibly it's the same or equivalent for your flavor.

---

### Post by papibe on 2012-08-16
Hi bug67.

Alternatively, you can check your BIOS, as sometimes you can set it on there.

Just a thought.
Regards.

---

### Post by bug67 on 2012-08-16
> **drs305 said:**
> For Ubuntu, you now put the setting in lightdm.conf:
/etc/lightdm/lightdm.conf


Possibly it's the same or equivalent for your flavor.
When I open /etc/lightdm/lightdm.conf, I see this:
> [SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
No mention of numlockx.  Am I supposed to ad the script you mentioned?

> **papibe said:**
> Hi bug67.

Alternatively, you can check your BIOS, as sometimes you can set it on there.

Just a thought.
Regards.
There is no mention of setting numlock in the BIOS.

---

### Post by drs305 on 2012-08-16
> **bug67 said:**
> When I open /etc/lightdm/lightdm.conf, I see this:

No mention of numlockx.  Am I supposed to ad the script you mentioned?

Yes.

---

### Post by bug67 on 2012-08-16
> **drs305 said:**
> Yes.

Didn't work.  :(

---

### Post by jstauf86 on 2012-10-25
> **drs305 said:**
> For Ubuntu, you now put the setting in lightdm.conf:
/etc/lightdm/lightdm.conf

> 
greeter-setup-script=/usr/bin/numlockx on 

Possibly it's the same or equivalent for your flavor.

Thank you "drs305", 
This worked on Lubuntu 12.04 :guitar:.

---

### Post by gwm on 2012-12-22
Cave!! Take care!!

I went straight in and edited lightdm.conf (without first saving a backup copy) and rebooted. Oh d-dear-dear! said little piglet.

Perhaps I should have first checked where numlockx is located on Ubuntu 12.04. So far I haven't found it. So it appears that this solution will only work for some users.

Well, I pushed buttons until Alt-F4 gave me a login prompt. Then I fetched out a laptop to google for a tutorial on how to drive VIM (only light version of VI with no help files is installed on Ubuntu 12.04). I could have used remove and copy if I'd had a backup. Now I'm back up and working again but I still have to repeatedly rediscover that num lock is off (my wireless keyboard has no lights).

Microsoft have also done this thing of leaving num lock off with Windows 7. What is the motivation for this sage decision? I can't understand why anyone would want it off. Please, can someone teach us?

---

### Post by drpjkurian on 2012-12-22
Hi in KDE (Kubuntu). You can switch on num lock on every start up by tweaking the systen settings. Have a look at the image

---

### Post by gwm on 2012-12-22
I have found numlockx.

From other posts I discovered that one must first install numlockx. I have done this and now the fix given here works fine.

About Microsoft, lets not run the opposition down too much.

The point I am making, is that the whole developer community (many of whom appear to have a foot in more than one camp) seem to have suddenly decided to leave num lock off. I fail to understand the rationale (I hope that's how one spells it).

Thanks for the image. I find no such screen in Standard Ubuntu 12.04 or 12.10, thus showing that developers are by no means unanimous on this subject. Why is it even controvertial?

---

### Post by Byb on 2013-10-20
Disregarding the BIOS setting, ending on a login screen with numlock OFF is the new default behaviour I experienced since my first steps in windows NT in 1998 (NT4 to win8). W9x honoured bios setting and I don't know for NT before NT4.
Maybe a security concern, or if not, a lack of desire for detecting the keyboard layout. Many laptops remain without a separate numpad, not speaking of external ones, and enabling numlock on such keyboards would worry many users.
Useful for desktops, windows has a registry key (current user\..\InitialKeyboardIncators) which behaves this way when set to 2: leave numlock status as is on logout
Setting it for "All Users" makes a near perfect "always on", knowing everybody toggles it on then forget it. A true "always on" would prevent anybody to toggle it off from greeter/login screen.
But this could be another security issue on laptops, as you could not then access to the normal letters of shared keys to type in your password.

Thanks for the tip in this thread guys.

---

