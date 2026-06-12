---
title: "Where is my volume button?"
date: 2017-11-03
forum: Desktop Environments
---

### Post by shersk on 2017-11-03
I have searched the internet for answers, and there are many people with ideas of how to tinker with Xubuntu, but I want to know how Xubuntu developers envisaged it. How should the audio volume button be installed?

Xubuntu 17.10, Pulseaudio 10.0, XFCE 4.12.

---

### Post by Autodave on 2017-11-03
It should have been there when you installed Xubuntu: in the top right corner. At least in 16.04 that is where it is.

---

### Post by Autodave on 2017-11-03
Try going into the upper panel and right clicking on it. From the drop down menu click on Panel and then Add New Items. Scroll down to Indicator Plugin and install that. You should have your volume indicator/changer now.

---

### Post by sprinterdriver on 2017-11-03
Maybe you somehow have managed to removed the "indicator plugin" from the panel.
To check: Right-click upper right corner --> Panel --> Panel preferences --> Items.

---

### Post by shersk on 2017-11-03
I have now tried adding the Indicator Plugin as described in previous posts. What it did was add an indicator for Thunderbird (which I don't use). But there still is no audio volume button or indicator. I didn't have it in 17.04 and 16.04. Can't remember when I last had volume indicator. It's a long time ago. But I did have it under Xubuntu perhaps around 2013.

I should add that this is a known issue (i.e. "bug", "problem") with Xubuntu which can be found by searching online. I am asking for the official solution.

---

### Post by Autodave on 2017-11-03
Have you been upgrading to the next release(s) or doing clean installs?

---

### Post by oldos2er on 2017-11-03
Do you have xfce4-volumed installed?

---

### Post by shersk on 2017-11-03
> [COLOR=#000000]Have you been upgrading to the next release(s) or doing clean installs?[/COLOR]
I have been upgrading. From 16.04 to 17.04. Then from 17.04 to 17.10.

> [COLOR=#000000]Do you have xfce4-volumed installed?[/COLOR][COLOR=#000000]
Yes, and it is the newest version.[/COLOR]

---

### Post by Autodave on 2017-11-03
Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD. I have never had any luck upgrading to e new version. I learned long ago to do fresh installs.

For now, I would install a fresh installation of 16.04. Or, live with what you have and do a fresh install of 18.04 when it comes available next year.

I have 13 machines (some VERY old and some brand new) and have no problem on any of them. All run Xubuntu 16.04.

---

### Post by shersk on 2017-11-03
I see your point. Given that my computer works well in most other respects, I think I'll just wait for 18.04. 

Do you think this problem would have been fixed in a rolling release distro like Arch Linux? Or would it have been the same or even more prone to such problems? According to distrowatch.com, Manjaro is really catching on, and I might try it out (live usb), but perhaps Ubuntu's clean install method is better in terms of cleaning out individual tampering issues.

My sound problem might well be due to some tampering. For example, I did some things to make the subwoofer work (laptop), using HDAJackRetask.

---

### Post by VMC on 2017-11-03
Go to settings 'Xfce Panel Switch' Click save current configuration. Then click on others like Redmond, Xubuntu Modern. If the volume reappears, then reapply your saved configuration and see if it sticks. Make sure its not 'hidden' under panel items 'Notification Area'. I've also had issue with the volume changing icons.

---

