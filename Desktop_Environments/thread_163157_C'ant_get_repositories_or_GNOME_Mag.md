---
title: "C'ant get repositories or GNOME Mag"
date: 2006-04-20
forum: Desktop Environments
---

### Post by James King on 2006-04-20
Hi, I'm new to Ubuntu and Linux, and so challenged visually that I can't read the GNOME screen well enough to find GNOOME Mag or get the the high--contrast themes, much less any equivalents to Zoomtext or Dragon Naturally Speakinig, which I have been usiing together very successfully on Winidows XP.  Using the Christopher Negus book, Linux Bible, I was able to install Breezy Badger in a dual boot with Windows XP.  Since i couldn't read the install screens and had to guess that the default choices would work, the resulting GNOME desktop may ot be connected to the Internet or may be corrupted because I can't get the software updates and program packages that Negus shows in his screen shots in his brilliant book.

Is there an easy way for me to fiind GNOME Mag and/or test my Internet connection, and fiind out how to check the overall integrity of my CNOME installatioin?  I have a LiveCD for Ubuntu 5.10 as well as the InstallCD, both downloaded from Ubuntu, and the eleven other Linux distributions, including Live  Knoppix and Live System Rescue Disk, but I can't use any of them without a screen magnifier.  I would greatly appreciate any step-by-step recommendations for getting a magnifier and high-contrst themes.  Thanks for reading this!

James King

---

### Post by Rxke on 2006-04-21
James, you probably won't get a good reply here because you're posting this question in the wrong section...
This is the KDE section, which is quite different than the GNOME one, so I suggest you post your question in ithe GNOME section, where knowledgable people about GNOME will surely help you out.

But for what it's worth: I use GNOME on my laptop, and the thing you are looking for is under the system section (upper bar) there you should see something named like 'assisting technology' (not sure, because I'm dutch) and it opens a window where you have to click the first checkbox. It says you have to log out and log in again for it to start working, then you can go there again and check 'screen reader program' and 'magnify glass' and in-screen keyboard' (again, that's a loose translation)

Oh, and my computer says I have to first install  gnopernicus for it to work enlarged etc. but I seem to vaguely remember it was an option during install which I declined, so maybe it is installed standard...

Hope this helps.

---

### Post by Trajan on 2006-04-22
Hello James,
 The assistive technology support can help you all around. Look for it under
**"System>Preferences>Assistive Technolgy Support"** then click on "Enable Assistive Technologies" (NOTE: You will have to re-login for this to be activated 
Also please be aware that the following packages need to be installed to enable the assistive support: **"gok"** and **"gnopernicus"** for screenreading and magnifying capabilities.).

---

### Post by henriquemaia on 2006-04-22
You can cycle to a lower resolution (getting a bigger text) by pressing "ctrl+alt+shift+keypad +". Maybe you can use this to find the Gnome Mag tool. Using "ctrl+alt+shift+keypad -" you get the reverse.

---

### Post by Rxke on 2006-04-22
You only need to install gok if you want to use the on-screen keyboard, I'm not sure that's needed in this case?

---

### Post by James King on 2006-04-24
Hello Rxke, Trajan, and henriquemaia:      .  

Thanks to all three of you for your very helpful replies to my first post, which was sent to the wrong forum because I'm completely new to Ubuntu and Linux, was writing to you with Zoomtext via Windows XP, and probably hasd installed Breezy incorrectly in a dual-boot system so I couldn't (and still can't) contact the internet through my inistallation of Gnome to get to the repositories to get the, so I can't get the any king of magnifier so I can see well enough to correct my installagion of the downloaded ubuntu CD.  

You three have all helped me greatly to reach my current assumption
that since the Synaptic Package Manager says it cannot get any of the packages that the enaabled Assistive Technology sub-system says I need to get any nagnifier, it must be becausen I can't acces the Internet from my Linux installation even though the dual-boot appears to works fine well, and even though I can easily get on the Internet via the Windows XP installation on the same machine.  You all helped me get the message through Gnome that the repositories were all inaccessible to me.  

[I'll be recommending to the developers of Dapper Dreke and all later versions of ubuntu that they include a magnifier not only in the original install package of Gnome but also at the beginning of the text-based ubuntu installation process -- or at least include an option for a VERY large-print version of White-on-black screens for the initial text-based installation process.]

Following your suggestions I was able to make enoug progress to rule out my unfamiliarity with Gnome as the root cause of my problem.  The root cause probably goes far deeper into the original process or the dual-boot configuration.  So I'll be posting my second request for hep on the Gnome forum (which may also be the wrong place), trying to find out what -- if anything -- is wrong with my Internet connection.

Thanks again.  Your help has proven to me that ubuntu is really a cocmmunity that works for every individusl, no matter how incompetent or diabled, so I want to be a part of it, even if it takes a lot of trial-and-error to make it really work better for me than Windows XP [regardless of whether the Linux movement soon produces anything better than ZoomText v. 9 and Dragon Naturally Speaking Professional V.8].   8).

---

### Post by Rxke on 2006-04-24
yes, the install process is not very clear sometimes whether it was successful or not to acces a network, I clearly remember that gave me lots of headaches using Hoary... (the version before Breezy)

I did see that Dapper, whilst still in beta, seems to have the accessibility files on its CD by default, so if you'd know someone that could burn such a CD for you, it'd be less of a problem to set things up. Good idea about contacting the developers, from what I've read there is actually a lot of work being done to answer accessibility issues, behind the scene by volunteers... I guess the next release (Dapper) will be better in that respect, though I don't remember having read about an option during install, would be nice.

---

### Post by Henrik on 2006-04-25
Hello James,

The scenario you describe is familliar to us and one we have been working to rectify. As the last poster suggests, I would recommend that you move on to the Dapper beta version (download here: [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/)) I would suggest that you get the Live CD version. Dapper is already very stable.

Both a high contrast theme and a magnifier are now installed by default, so they will work withothout the internet working. On the Live CD there is an assistive technology menu. At the very first boot screen (ubuntu logo on black background) you press F5 to get various choices. The text is unforunately a bit small, but the choices are as follows: 

None - Contrast theme - Magnifier - Screen Reader - Keyboard & Mouse modifiers - On-screen Keyboard

So if you selct the second or third choices (using the arrow keys) you should get the contrast theme and magnifier respectively. We would be very interested in hearing your feedback on this on the accessibility mailing list: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility](https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility)

I don't think we can deliver anything that can compete with Dragon Natually Speaking any time soon, but we plan to have very good alternatives (better?) to ZoomText and Jaws in the near future (ie. 6-12months).

Henrik
Ubuntu Accessibility Team

---

### Post by Rxke on 2006-04-25
Henrik, you guys rock.

You do.:cool:

---

