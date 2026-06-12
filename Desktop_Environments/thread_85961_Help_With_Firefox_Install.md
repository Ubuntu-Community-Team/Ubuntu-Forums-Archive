---
title: "Help With Firefox Install"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-03
I am suffering from a slow firefox and want to do the "fix" as noted in the Ubuntu Wiki, but the level of specificity is not high enough for a newb...

what is a "libstdc++5"     ---how do I find and where do i install it?   If I don't need to back up any bookmarks is there an easier way to install the newer firefox?

Thanks

---

### Post by aysiu on 2005-11-03
First of all, read this:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Then:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by Georgie-o on 2005-11-03
I read the stuff and a couple of basic problems remain.   When I download Firefox its named "...RC1"   not "b2" as noted in the instructions so when I type it I get:

e@ubuntu:~$ sudo cp firefox-1.5b2.tar.gz /opt/
cp: cannot stat `firefox-1.5b2.tar.gz': No such file or directory

And I'm still not sure what that "libstdc++5" stuff means?  Something I need to do prior to installing??

---

### Post by aysiu on 2005-11-03
Okay. Forget about those instructions.
Just double-click the .tar.gz (the equivalent of .zip in Windows)
Click on the Extract button
Extract the files to your desktop.
Open the new folder (unzipped)
Double-click on the file called *firefox*
When asked whether you want to Run in Terminal, Display, Cancel, or Run, select *Run*.

This is all graphical--no command-line.

---

### Post by Georgie-o on 2005-11-03
Alright, I'm getting somewhere now..sort of.  I did like you said and it opend the correct version..great!!!  But after I closed it, I could only find the old version 1.0.7.  Was this not installed?  maybe just run off of the desktop?  How do I find it, shortcut to it? and unistall the other??

Stick with me here, I think we can get through this together...

---

### Post by aysiu on 2005-11-03
Okay... this is why it's a good idea to stick with the Firefox that comes with Ubuntu (the one that can be updated to 1.0.7)--it's fully integrated with the rest of the system. Right now, the version you just "installed" is really not installed at all. It's just a launcher in a folder that contains just about everything.

There are two things you have to do to integrate it with the rest of your apps. The first works just fine. The second... well, I haven't gotten it to work correctly, but it should work... theoretically.

1. Put it in the right path so that it's recognized as an application. My favorite place is /usr/local/bin. So open up a **Run** dialogue and type ```
gksudo nautilus
``` then enter your sudo password. Go to /usr/local/bin and move your new Firefox 1.5 folder to there. For the sake of simplicity, you may want to rename it firefox, so that it ends up being /usr/local/bin/firefox with the executable being at /usr/local/bin/firefox/firefox. To override the old version, open a new window (still gksudo nautilus) and go to /usr/bin. Then drag the /usr/local/bin/firefox/firefox icon to /usr/bin/ and select "make link" or "link here." It'll ask if you want to replace firefox. Say "yes." Now when you type ```
firefox
``` as a command, it'll use your new Firefox.

2. Now the part that theoretically works but hasn't for me: associating the libraries with the new Firefox (this is good for multimedia plugins and such). Same deal (gksudo nautilus) but make a symlink (what we did before with the "make link") from the /usr/lib/mozilla-firefox/plugins folder to /usr/local/bin/firefox/plugins so that essentially when you're clicking on /usr/local/bin/firefox/plugins, you're really going to /usr/lib/mozilla-firefox/plugins. Does that make sense?

This last part screwed me up, really. So now I have to use Epiphany for viewing Apple trailers and pages with Flash on them. Why do you want Firefox 1.5? 1.0.7 isn't working for you?

By the way, if you've ever wondered why most instructions for Ubuntu and Linux in general are given by command-line commands, this post is why! It's a lot easier to say "copy and paste these commands in" than to try to explain "click here, drag that," etc.

---

### Post by Georgie-o on 2005-11-04
Your the Man!

I could not get it to work exactly...The part where I had the problem was when I moved the new launcher to the existing bin (and replaced it) I could not get that to work as a launcher ( it ran nothing)  so I put in back in the usr/local/bin/firefox/firefox and just made custom lauchers on my tool bar.  It seems to work well.  1.5 is MUCH faster than the previous version.  The only problem is a deadlink in the pulldown menu and the old version is still installed.  Should I go to the ADD/Remove programs and take it off?  will that ruin anything?  Thanks for your help I have actually learned a lot about making this stuff work.  Your help is much appreciated.


G

---

### Post by aysiu on 2005-11-04
I wouldn't take the old one out unless you're running low on hard drive space. There's really no reason to. The key to making the /usr/bin/firefox work is to make it a link (*alias* in Mac, *shortcut* in Windows) to the *actual* file, which is /usr/local/bin/firefox/firefox. Well, if it works, it works.

---

