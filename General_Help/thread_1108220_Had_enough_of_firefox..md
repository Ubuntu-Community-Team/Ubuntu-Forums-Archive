---
title: "Had enough of firefox."
date: 2009-03-27
forum: General Help
---

### Post by hey2222 on 2009-03-27
Okay, well ever since I went to 8.04 firefox has been acting odd. I've reinstalled countless numbers of times, but no luck.I thought "I'll get over it" but I can't take it anymore. Firefox has been closing/crashing (I'm not sure) itself unexpectedly all the time. Research for homework, close. Reading the news, close. Listening to music, close. Opening firefox to the homepage, close. I've had enough and I cant put up with it any more. Someone help me!

---

### Post by cosine352 on 2009-03-27
try to run it through terminal  and look for error massage. It can give some idea of what is going wrong. 

In terminal
> firefox

---

### Post by kanikilu on 2009-03-27
Have you tried running Firefox in safe mode?

[http://kb.mozillazine.org/Safe_mode](http://kb.mozillazine.org/Safe_mode)

Have you tried creating a new profile? I don't think reinstalling Firefox will do this by default. Close any existing Firefox windows and then run ```
firefox -profilemanger
``` from a terminal (or ALT+F2).

[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)

If neither of those help, I think people are going to need a lot more detail than you gave in your first post. For instance:

- You mentioned you are on 8.04, is that 32 or 64 bit?
- What, if any plugins or add-ons do you use in FF?
- Does this seem to happen with sites that use a particular plugin or technology (e.g. Flash, the "Silverlight-for-linux" equivalent, etc.)?
- Does this seem to happen with any particular sites? In other words, is it reproducible or "random"?  If so, which ones?
- Does the problem "go away" for a while after clearing your browser cache?

If it's just well-and-truly randomly crashing, that's going to be very hard to troubleshoot, so definitely see if you can find some sort of a pattern.

Also, I'm not sure, but you might find something useful in your logs (/var/log/). I'd probably check debug, messages, syslog, and Xorg.0.log for good measure...

Good luck.

---

### Post by glotz on 2009-03-27
Firefox never, ever crashed for me. Do you have the crappy adobe flash plugin? It's notorious for causing such problems.

---

### Post by hey2222 on 2009-03-27
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:6383): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6383): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

I have no idea what the error means. As for addons the only thing i installed is noscript and flashplugin-nonfree.

---

### Post by kanikilu on 2009-03-27
There's a very similar-sounding bug report here:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/221668](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/221668)

They seem to think it has something to do with flash, so try disabling that plugin (or just run Firefox in safe mode) and see what happens...

---

### Post by TenPlus1 on 2009-03-27
You could always give Opera a try and see how that works out for you:

[www.opera.com](www.opera.com)

---

### Post by hey2222 on 2009-03-27
Installed Opera, and everything works perfectly. Although, getting use to a new browser will be somewhat difficult it beats crashing every 30sec - 5 mins. Thanks for the advice, and thanks for the help guys.

---

### Post by Slim Odds on 2009-03-27
> **hey2222 said:**
> Installed Opera, and everything works perfectly. Although, getting use to a new browser will be somewhat difficult it beats crashing every 30sec - 5 mins.....

Understand your frustration, but remember, there are tons of people using it without problems. It usually turns out to be a plugin or something unusual when problems like this happen.

---

### Post by trot2millah on 2009-03-27
You could also try the Epiphany browser, it was made specifically for GNOME and is built from Firefox.  It's simpler than Opera, but from my experiences Opera looks terrible in GNOME and Epiphany was a solid browser.

---

### Post by dj722000 on 2009-03-27
Well I agree with hey2222, I did an update and now my Firefox is acting all crazy for the past week. It went to full screen that I cant seem to get out of, I can click on tools, but nothing happens, if I click anything in the drop menu for tools like plug ins, nothing happens and it constantly flashes at me. That is really annoying. Sometimes it will flash between current screen and previous screen if im clicking on links to read stuff. Cant seem to get nowheres. The only way I can get it to do anything is to restart it, but then its only for a short time and back to being all funky again. Funny thing is, I have it on my laptop and updated that to, but that one is alright. Since the last update, Epiphany is acting a little goofy too. Like something didnt get installed right from the update. Any ideas.

---

### Post by rmockler on 2009-03-27
I'm amazed that I don't see more reference on the the forum to the Seamonkey browser.  I always install it immediately with every new release of Ubuntu that I install.  Then when Firefox decides to act funky, I just switch over to Seamonkey and life is back to normal.  Seamonkey doesn't do all that Firefox does, but what it does is done right. It also includes a great pop3 email client as part of the package.  Bookmarks are compatible with Firefox, so just export them from Firefox and import them into Seamonkey and away you go.  Seamonkey has a small set of extensions and some neat themes.  Give it a try, you'll hardly see any difference from Firefox except it works.  You can find Seamonkey in Synaptic.

---

### Post by cosine352 on 2009-03-31
> **rmockler said:**
> I'm amazed that I don't see more reference on the the forum to the Seamonkey browser.  I always install it immediately with every new release of Ubuntu that I install.  Then when Firefox decides to act funky, I just switch over to Seamonkey and life is back to normal.  Seamonkey doesn't do all that Firefox does, but what it does is done right. It also includes a great pop3 email client as part of the package.  Bookmarks are compatible with Firefox, so just export them from Firefox and import them into Seamonkey and away you go.  Seamonkey has a small set of extensions and some neat themes.  Give it a try, you'll hardly see any difference from Firefox except it works.  You can find Seamonkey in Synaptic.

go Seamonkey. It is also good for editing the html files.

---

### Post by dcstar on 2009-03-31
> **hey2222 said:**
> Okay, well ever since I went to 8.04 firefox has been acting odd. I've reinstalled countless numbers of times, but no luck.I thought "I'll get over it" but I can't take it anymore. Firefox has been closing/crashing (I'm not sure) itself unexpectedly all the time. Research for homework, close. Reading the news, close. Listening to music, close. Opening firefox to the homepage, close. I've had enough and I cant put up with it any more. Someone help me!

Simply close Firefox and rename the .mozilla folder that contains the (probably) corrupted profile.

Restart Firefox and a fresh profile will be created, if it suddenly works correctly you can then import the bookmarks from the old profile folder.

---

