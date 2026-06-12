---
title: "Netbook Remix Option - Mini-9"
date: 2009-08-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Olmy on 2009-08-21
I've got my mini-9 going with 9.04 desktop (after ditching XP) and all is well except that some windows (mostly options, but some apps as well) are too big for the screen and can (sometimes) get themselves into an awful mess so it's impossible to close them.

I know that there is a work around by switching off visual effects and using alt-click to grab them and move but it's messy.

First question is does the NBR get over this?

I'd quite like to try it anyway and I understand that it can be installed as an add on with a mode switch to go back to the normal desktop?

I've also heard that this can cause problems when trying to go back to desktop.

Does anyone have experience and some definitive instructions?

Thanks.

---

### Post by snowpine on 2009-08-21
Hi Olmy, the package you want is called maximus. It is the component of Netbook Remix that automatically maximizes all windows to take advantage of the limited screen size. You will still need to use Alt+drag for some windows, but maybe a little less than now... Good luck!

---

### Post by Olmy on 2009-08-21
Thanks snowpine, does this package do anything else but maximise the windows in the normal way?

My experience is that hitting the maximise button on the normal desktop makes things worse, if anything - that's when I end up being unable to close them.

I'd still like to hear if anyone has got a system which can switch between NBR and normal desktop....

---

### Post by snowpine on 2009-08-21
You can install ubuntu-netbook-remix if you really want to, it will give you all of the netbook packages (including maximus). You will still need to alt-drag certain windows though. Ubuntu has done a pretty good job making their interface small-screen friendly. But with apps, it is really up to the developer of each application; a lot of them are still developing for 1024x768 or larger screens. Maybe you should try netbook remix as a live CD/USB before you install, see whether it is actually the solution you are looking for. Personally, I've gotten pretty good at Alt+drag and don't really think about it any more. :)

---

### Post by snowpine on 2009-08-21
ps. Netbook does include a desktop-switcher applet that switches from netbook launcher to classic gnome desktop.

---

### Post by jaqrah on 2009-08-21
> **snowpine said:**
> ps. Netbook does include a desktop-switcher applet that switches from netbook launcher to classic gnome desktop.

Very true.  In early versions, the aforementioned applet was very,very buggy.  You might find your mini9 in a sad state of affairs if the applet is still buggy.  I had this happen.  I wound up having to do a clean install.

---

### Post by Olmy on 2009-08-22
> **jaqrah said:**
> Very true.  In early versions, the aforementioned applet was very,very buggy.  You might find your mini9 in a sad state of affairs if the applet is still buggy.  I had this happen.  I wound up having to do a clean install.
This is what I heard.

Does anybody know if said bugs have been dealt with?

---

### Post by Olmy on 2009-08-22
I just tried NBR live.

Worked fine - visual effects off by default but many (NBR specific?) effects were apparent. This means Alt-drag works on big windows.

Desktop switcher worked flawlessly.

Now, I am reluctant to do a clean install as I've now spent some time getting all the stuff I want on my desktop setup (including fixing a nasty sound setup problem).

Found this...
[http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html](http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html)

People were still reporting problems.

Has anybody tried this sort of thing recently?

Related question: Is there any easy way to do a full system backup to USB or something?

(sorry I'm a newbie to ubuntu/linux)

---

### Post by ugm6hr on 2009-08-22
Just to let you know, some application screens require more than the 600 pixels available on the Mini 9: GIMP was a good example in 8.04, but has since changed its layout.

NBR will not change this problem per se.

Nevertheless, during normal use, it is unusual to require settings screens frequently, so I have just used Alt-left drag from time to time.

I installed the NBR directly, and then removed maximus and the netbook-launcher, but that ubuntumini site is a pretty good resourse, so I would be surprised if there were any major flaws with its advice.

As for backups: if you want to just backup your personal data and settings / emails / bookmarks etc, just copy ~/ directory to a USB.  You can also use dpkg to save the list of applications you have installed, or copy all the installation files:
[http://www.uluga.ubuntuforums.org/showthread.php?t=819396](http://www.uluga.ubuntuforums.org/showthread.php?t=819396) (just copy directly to usb rather than a directory in ~/)
[http://www.uluga.ubuntuforums.org/showthread.php?t=261366](http://www.uluga.ubuntuforums.org/showthread.php?t=261366)

---

### Post by jwaclawsky on 2009-08-22
I have a mini 9. Stay away from maximus. It is total crap and unnecessary.  I had two main issues that I wasn't able to configure around. Maximus forced everything to open in full screen, even error and status messages and filled up my 24" display (I usually keep my large display pluggeg into my netbook). And every so often when I closed a window maximus would get control and drive all the other open windows to full screen stacking them one over the other. Then I have to go resize everything. While not too bad in term of effect, but over months it became very annoying. Removing it caused other problems and I had to reinstall Ubuntu (I used it as an opportunity to go from 8.10 to 9.04 and I am happy with the way it is working now).

---

### Post by snowpine on 2009-08-22
> **Olmy said:**
> I just tried NBR live.

Worked fine - visual effects off by default but many (NBR specific?) effects were apparent. This means Alt-drag works on big windows.

Desktop switcher worked flawlessly.

Now, I am reluctant to do a clean install as I've now spent some time getting all the stuff I want on my desktop setup (including fixing a nasty sound setup problem).

Found this...
[http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html](http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html)

People were still reporting problems.

Has anybody tried this sort of thing recently?

Related question: Is there any easy way to do a full system backup to USB or something?

(sorry I'm a newbie to ubuntu/linux)

No need to reinstall to get the netbook remix interface. All of the packages can be added to an existing Ubuntu install.

Check it out: [http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html](http://www.ubuntumini.com/2009/03/installing-ubuntu-netbook-remix-in.html)

As mentioned above, it is not a "cure all" for the "some windows too big for the screen" problem.

---

### Post by jwaclawsky on 2009-08-22
I have been using 9.04 for over a month and I don't have this "some windows too big for the screen" problem. I move around and use my mini 9 netbook on its own, sometimes attached to a 19" monitor and often attached to a 24" monitor. Again beware of maximus ...I found it to be crap and if you have it installed I wouldn't be surprised if it was the source of your problems.

---

### Post by Olmy on 2009-08-23
I've been playing with the live NBR a bit more and found that returning to the desktop via the applet doesn't switch off maximus.

That's no good at all.

I'm not quite sure I want to commit to the launcher, so was thinking that I could use some of the components of NBR to optimise the standard desktop a bit more.

The window picker looks good and could surely be used in the upper panel to replace the lower panel, hence saving me a panel's worth of screen real-estate. The feature of incorporating the window title when it is maximised would also save me space.

But....

Without maximus, the latter feature doesn't work! A maximised window has its title ***and*** the title in the picker. There isn't even a way of stopping the picker from displaying the title of an active, maximised window, so you are stuck with two titles - yuk!

](*,)

---

### Post by ugm6hr on 2009-08-23
If you are looking for a screen real-estate friendly setup on the Mini 9, consider Xfce with a single top panel and autohiding panel.

If you search for my username and xfce4 tag, a thread should appear which details my exploits.

While this can work in Gnome too, the autohide feature in Gnome is less immediate, so annoyed me too much.  On the flip side, autohiding panels in Xfce sometimes fails, so you need to include a "recover panel autohide" button on the panel.

---

### Post by jwaclawsky on 2009-08-23
I am not sure what your exact problem is but if I were you I'd leave that crap maximus behind. It's useless software IMHO. I downloaded 9.04 from [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook) (NO Dell mods and when I did it maximus was not installed although it is in the package selection - hopefully this hasn't changed) and installed in on my mini 9 netbook and it worked just fine for me. I am tying this note with my 19" display plugged-in, external hard drive connected to a USB hub, with a CD burner and keyboard attached to another cascaded hub with a wireless mouse and running Sunbird, Thunderbird, an open office word file, Skype, system monitor and of course firefox with 3 tabs open and all running just fine in each of their windows (and tabs). It operates just like a "normal" desktop for me in this configuration.

---

### Post by Olmy on 2009-08-26
> **Olmy said:**
> Without maximus, the latter feature doesn't work! A maximised window has its title ***and*** the title in the picker. There isn't even a way of stopping the picker from displaying the title of an active, maximised window, so you are stuck with two titles - yuk!
I've just discovered that you can turn off the 'maximise on open' feature of maximus and use it simply to strip the title off maximised windows.

So... what I'd like to try is maximus with the window-picker-applet on the standard desktop - removing the bottom panel...

Can anyone tell me hwo to install these two packages without the whole NBR?

Thanks.

---

### Post by Olmy on 2009-08-26
Cool!

sudo apt-get install window-picker-applet
sudo apt-get install maximus

Use the config editor to set 'no-maximize' in apps->maximus.

Add the window-picker-applet to the top panel - plus the stuff from the bottom panel that I wanted (workspace switcher and show desktop). Delete bottom panel.

Reboot (to start maximus).

Great!

Maximises the use of the screen just as much as the NBR (if I do maximise a window), no auto-maximise of new windows and I don't need to use the NBR app launcher.

:)

---

