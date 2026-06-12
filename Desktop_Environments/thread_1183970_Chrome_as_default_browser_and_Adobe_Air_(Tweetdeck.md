---
title: "Chrome as default browser and Adobe Air (Tweetdeck)"
date: 2009-06-10
forum: Desktop Environments
---

### Post by bobbyi on 2009-06-10
I recently set google chrome as my default browser in gnome. 

I did this using the Preferred Applications applet under System->Preferences. I set the browser as "custom" with the command as "/usr/bin/chrome %s".

This seems to be mostly working. For example, if go to System->About Gnome and click any of the links, they open in chrome.

However, if I click links within Tweetdeck (an Adobe Air app), they open in Firefox. I tried reinstalling Air and Tweetdeck and it didn't help. Any idea why it isn't seeing my gnome browser setting?

Another weirdness is that if I do "sudo update-alternatives --config x-www-browser", I get this:
There are 4 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/firefox-3.0
          2    /usr/bin/opera
*+        3    /usr/bin/epiphany-gecko
          4    /usr/bin/konqueror


Note that it claims by current default is ephinany which is not the case.

---

### Post by drazabyss on 2009-06-24
Any update to this would be great.  I have tweetdeck in jaunty and am using the RC of Firefox3.5.  I have default browser and the | sudo update-alternatives --config x-www-browser | browser changed to 3.5, but tweetdeck still open in 3.0

There is a WIN fix that is simply change the default browser due to some strange way tweetdeck through AIR calls on the browser,  That does not seem to translate to ubuntu though.  Any ideas?

---

### Post by paul.maddox on 2009-06-25
I also have this problem. All links in tweetdeck open with Firefox rather than my default browser (Chrome).

:(

---

### Post by rukna on 2009-07-01
Similar issue here. Tweetdeck links open Konqueror, instead of the default FF 3.5

Moreover, I took out Konqueror from the KDE on one of my desktops and now clicking on those links does not do anything.

---

### Post by ChaoticMind on 2009-07-01
Now that firefox 3.5 is released, and you might be using that, a workaround would be to symmlink ln -s /usr/share/<favorite browser> /usr/share/firefox since firefox 3.5 has its own executable (firefox-3.5)

It's ugly, but it works. 

Of course, it can be annoying if you want to launch firefox from terminal or from alt+f2, since it will now open whichever other browser you symmlinked to. (and it's the first link when using tab in terminal or in autocomplete for alt+f2)

---

### Post by rukna on 2009-07-01
> **ChaoticMind said:**
> Now that firefox 3.5 is released, and you might be using that, a workaround would be to symmlink ln -s /usr/share/<favorite browser> /usr/share/firefox since firefox 3.5 has its own executable (firefox-3.5)

It's ugly, but it works. 

Of course, it can be annoying if you want to launch firefox from terminal or from alt+f2, since it will now open whichever other browser you symmlinked to. (and it's the first link when using tab in terminal or in autocomplete for alt+f2)


Did that yesterday when FF 3.5 came out :) Doesn't solve the issue, tho. What you're suggesting would simply have the new version executed. Clicking on the links on tweetdeck or another Adobe Air app still brings up Konqueror for me.

---

### Post by ChaoticMind on 2009-07-01
Weird. Must be that when you installed Tweetdeck (or adobe air?), conqueror was your default, and for some reason that got locked. For me it was firefox, and after I changed it, it's still locked to firefox. 

Try to do symmlink from konqueror's old executable to whatever you want it to open with (likely firefox 3.5) so: sudo ln -s /usr/bin/firefox-3.5 /usr/bin/konqueror (assuming konqueror is the binary name, not sure)

---

### Post by Paperfairy on 2009-07-05
> **ChaoticMind said:**
> Weird. Must be that when you installed Tweetdeck (or adobe air?), conqueror was your default, and for some reason that got locked. For me it was firefox, and after I changed it, it's still locked to firefox. 


Not the case - for me, Opera has been the default, always, and links still open in Firefox as described.

How did the OP get Chrome in Linux? Or is this the mega alpha version?

---

### Post by rukna on 2009-07-05
> **Paperfairy said:**
> How did the OP get Chrome in Linux? Or is this the mega alpha version?

Wine is your friend

---

### Post by ChaoticMind on 2009-07-05
> **Paperfairy said:**
> Not the case - for me, Opera has been the default, always, and links still open in Firefox as described.

How did the OP get Chrome in Linux? Or is this the mega alpha version?

Well, that's a problem isn't it? It's supposed to open links in the default browser, not in Firefox. 


I use Chromium alpha from here: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

I think there is also Google Chrome for linux (developer build) by now as well. (as of ~1 month ago or so?) [http://www.google.com/chrome/intl/en/linux.html](http://www.google.com/chrome/intl/en/linux.html) --> Dev channel.

---

### Post by rukna on 2009-07-13
> **ChaoticMind said:**
> 
Try to do symmlink from konqueror's old executable to whatever you want it to open with (likely firefox 3.5) so: sudo ln -s /usr/bin/firefox-3.5 /usr/bin/konqueror (assuming konqueror is the binary name, not sure)

Uninstalling and re-installing Konqueror did it for me. YMMV, of course.

---

### Post by Alexander Grundner on 2009-07-16
I've been trying to find a fix for this as well. I want Chromium to be the default browser Seesmic opens links in (currently set as the default browser in the GNOME settings). It looks like it's an issue with Adobe AIR rather than with Chromium.

See: [http://getsatisfaction.com/seesmic/topics/twhirl_and_google_chrome](http://getsatisfaction.com/seesmic/topics/twhirl_and_google_chrome)

If anyone finds a way around this, please post.

---

### Post by drazabyss on 2009-07-22
FYI

Follow the instructions in this post and it works like a friggin charm.

[http://blog.andreaolivato.net/open-source/change-adobe-air-apps-default-browser.html](http://blog.andreaolivato.net/open-source/change-adobe-air-apps-default-browser.html)

I downloaded GVIM from A/R for the editing, YMMV

Be sure to run with permissions.

Otherwise, good as gold.  What a relief.  With no updates to the FF3.1 repos until the 9.10 release, I was considering going BACK to 3.1 instead of using the 3.5 Shiretoko just because I click so many links in seesmic and tweetdeck from AIR.

This solves the problem, though.

---

### Post by Alexander Grundner on 2009-07-22
> **drazabyss said:**
> FYI

Follow the instructions in this post and it works like a friggin charm.

[http://blog.andreaolivato.net/open-source/change-adobe-air-apps-default-browser.html](http://blog.andreaolivato.net/open-source/change-adobe-air-apps-default-browser.html)

I downloaded GVIM from A/R for the editing, YMMV

Be sure to run with permissions.

Otherwise, good as gold.  What a relief.  With no updates to the FF3.1 repos until the 9.10 release, I was considering going BACK to 3.1 instead of using the 3.5 Shiretoko just because I click so many links in seesmic and tweetdeck from AIR.

This solves the problem, though.

That's brilliant. Great find!

My edits to the instructions for Ubuntu. Works for me!


**Edit file**
sudo vim /opt/Adobe\ AIR/Versions/1.0/libCore.so

**Jump to line**
:15500

**Use 'a' command to insert text with Vim**

**Look for and change 'firefox' to 'browser' (must remain 7 characters only)**

**Save and quit**
:wq

**Create a symlink for Chromium**
sudo ln -s /usr/bin/chromium-browser /usr/local/bin/browser

---

### Post by jlward4th on 2009-07-27
Rather than hacking the .so file I took care of it this way:
```

cd /usr/local/bin
sudo ln -s /etc/alternatives/x-www-browser firefox

```

---

### Post by mehulved on 2009-08-06
> **jlward4th said:**
> Rather than hacking the .so file I took care of it this way:
```

cd /usr/local/bin
sudo ln -s /etc/alternatives/x-www-browser firefox

```

No that didn't work for me. I had to muck around with the .so file and create the symlink in /usr/local/bin otherwise it wouldn't work. But even now there is a problem in that it opens the a whole new chromium window duplicating all my tabs and opening that url in a new tab.

---

### Post by 5of0 on 2009-08-25
> **Alexander Grundner said:**
> 
My edits to the instructions for Ubuntu. Works for me!
...


Awesome, thanks!  This worked great for me, even opens in the same window.  TweetDeck is so much more usable now! :D

---

### Post by Alexander Grundner on 2009-08-25
I'm glad it helped. However, just be aware the next time an update for Flash is released it will overwrite the libCore.so file you edited (it happened to me about a week ago).

---

### Post by warreno on 2009-09-03
I found an esier way to do this, I think, one that works for me anyway. NOTE that you need to do this with root privs (sudo).

When I looked into the /opt directory, I saw that there were three folders there - one for Adobe AIR, one for TweetDeck, and one for firefox. (The firefox directory was not a symlink. This is marginally troubling and might explain why upgrading your system to Ffox3.5 isn't recognized by TweetDeck, and it still loads Ffox3.)

TweetDeck seems to be hardwired to load /opt/firefox/firefox when opening a URL. But it doesn't actually seem to care if it's really Firefox it loads or not.

Here's the shortened version of what I did. About half of it was guesswork and trial-and-error, but it worked.

1. In /opt, rename the **firefox** directory to something like **ffox**.
2. Create a *new* directory in /opt called **firefox**.
3. Copy the script or symlink to the browser of your choice into the **firefox** folder you just created.
4. Rename that script or symlink **firefox**.

After that, TweetDeck should use the browser you want.

---

### Post by Alexander Grundner on 2009-09-03
> **warreno said:**
> When I looked into the /opt directory, I saw that there were three folders there - one for Adobe AIR, one for TweetDeck, and one for firefox. (The firefox directory was not a symlink. This is marginally troubling and might explain why upgrading your system to Ffox3.5 isn't recognized by TweetDeck, and it still loads Ffox3.)

I like your workaround, but my opt directory doesn't have a firefox directory in there. (Running Ubuntu 9.04)

UPDATE: For fun I tried just adding a symlink in /opt/firefox after I created the directory to see what would happen.

*sudo ln -s /usr/bin/chromium-browser firefox*

Unfortunately, Seesmic opened up the link in Firefox.

---

### Post by warreno on 2009-09-03
> **Alexander Grundner said:**
> I like your workaround, but my opt directory doesn't have a firefox directory in there. (Running Ubuntu 9.04)

Oh. Dang. Nothing named 'firefox' at all?

Well, so much for that. Weird, because I'm running 9.04 as well!

---

### Post by warreno on 2009-09-03
Hey, **Alexander**, can you try it anyway? Maybe it'll work despite the missing firefox directory. Just  make sure the directory and link name are lowercase...

---

### Post by Alexander Grundner on 2009-09-03
> **warreno said:**
> Hey, **Alexander**, can you try it anyway? Maybe it'll work despite the missing firefox directory. Just  make sure the directory and link name are lowercase...

I already tried.

I created an a directory called "firefox" in /opt and then added a symlink called "firefox" pointing to the Chromium browser

My symlink:
*sudo ln -s /usr/bin/chromium-browser firefox*

Unfortunately, I didn't have success with that. I'm curious how and why you have a directory called firefox in /opt. Does anyone else out there see a directory called firefox in /opt currently?

**UPDATE:**
Ha! I figured out another way to do it :)

There's a firefox symlink in /usr/bin/
I renamed it like you suggested to keep it around and then created a new symlink (same command as above) and it works with Tweetdeck and Seesmic!!!

***The catch...** when you want to open Firefox from the menu it will open Chromium. However, since I renamed the original symlink "ffox", I can open up Firefox by calling/running ffox when I need it (or you can just manually change the shortcut properties).*

---

### Post by warreno on 2009-09-04
w00t!* Okay, so now we know a couple ways around this issue. Groovy.

I'm as puzzled as you about the firefox install -- it appears to be a *complete* install -- in /opt. Quite odd. I'm quite sure I didn't consciously or deliberately do anything to put it there. Having redundant binary packages is ... well, redundant, and makes grabbing updates a lot harder.

====

* Yes, I actually typed that. I can't really believe it either.

---

### Post by bod on 2009-09-09
Another solution, thankfully not involving editing binary files!
[http://www.roytanck.com/2009/08/26/getting-adobe-air-to-use-the-default-browser-under-ubuntu/](http://www.roytanck.com/2009/08/26/getting-adobe-air-to-use-the-default-browser-under-ubuntu/)

---

### Post by syed mehdi on 2009-10-26
An easier and cleaner solution will be: edit .bashrc in your home directory and add “export GNOME_DESKTOP_SESSION_ID=Default” to it. Exit Gnome, and come back. After that, all Air apps will use your default launcher.

---

### Post by ahorriblemess on 2009-12-08
I did the same thing. No reason to change anything when you can just create a new file. I made mine in /home/me/.filename.sh (I called it .tweetdeckfix.sh) and put the same thing: 

export GNOME_DESKTOP_SESSION_ID=Default
/opt/TweetDeck/bin/TweetDeck

Saved it, then went back to my home folder, showed hidden files, located the script I created, right clicked it, chose "make executable" then used alt+F2, typed in /home/me/.tweetdeckfix.sh and that was it. 

The first time I did it, I used sudo. It was unnecessary and I couldn't make it executable by right clicking... and I forgot exactly what to use in a chmod command. Plus, Ubuntu has become so much more average-user friendly. I like that.

syed mehdi, I hope you don't mind me reiterating your post. I sort of skimmed through this thread then kept searching until I found the exact same thing written in a bit more detail someplace else online. So just in case anyone else does what I did, maybe they can just stop here.

---

### Post by Czar on 2010-01-11
Looks like my x-www-browser was linked to opera... Here's what I did to fix this Tweetdeck from opening firefox and ignoring Chromium-browser.

> 
czar@kremlin:/usr/local/bin$ sudo ln -s /etc/alternatives/x-www-browser firefox
czar@kremlin:/usr/local/bin$ file /etc/alternatives/x-www-browser
/etc/alternatives/x-www-browser: symbolic link to `/usr/bin/opera'
czar@kremlin:/usr/local/bin$ which chromium-browser 
/usr/bin/chromium-browser
czar@kremlin:/usr/local/bin$ cd /etc/alternatives/
czar@kremlin:/etc/alternatives$ ls -lah |grep x-www-browser 
lrwxrwxrwx   1 root root  14 2009-11-01 05:55 x-www-browser -> /usr/bin/opera
czar@kremlin:/etc/alternatives$ sudo rm x-www-browser 
czar@kremlin:/etc/alternatives$ sudo ln -s /usr/bin/chromium-browser x-www-browser


---

### Post by MunksterMan2 on 2010-01-25
> **Alexander Grundner said:**
> That's brilliant. Great find!

My edits to the instructions for Ubuntu. Works for me!


**Edit file**
sudo vim /opt/Adobe\ AIR/Versions/1.0/libCore.so

**Jump to line**
:15500

**Use 'a' command to insert text with Vim**

**Look for and change 'firefox' to 'browser' (must remain 7 characters only)**

**Save and quit**
:wq

**Create a symlink for Chromium**
sudo ln -s /usr/bin/chromium-browser /usr/local/bin/browser

Worked for me, thanks.

Good to see this bug in adobe air has existed since June.  Way to go adobe :D

---

