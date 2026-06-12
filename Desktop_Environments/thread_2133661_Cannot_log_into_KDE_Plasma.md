---
title: "Cannot log into KDE Plasma"
date: 2013-04-08
forum: Desktop Environments
---

### Post by CinoxFellpyre on 2013-04-08
Eh that's pretty much title pretty much it. D:

I can run plasma-desktop under a recovery console and that's not really helpful whatsoever, and I can use Lubuntu just fine.

I think there's probably, PROBABLY an issue with the config SOMEHOW. Any thoughts?

---

### Post by CinoxFellpyre on 2013-04-11
Bump for KDE ;-;

---

### Post by dabl on 2013-04-11
Assuming you don't have a full filesystem, usually the login failure is caused by root ownership having previously attached to something inside the user's home folder -- for example "sudo kate" will cause this, when you should be using "kdesudo kate".

One file to review is the ~/.xsession-errors file.  It may or may not point to the cause of the failure to start plasma.

Next, using either a root shell or from a Live CD, at the user's home directory run "ls -la" and take a look at the file .Xauthority in your home folder -- does it have root ownership?  If so, delete it.  Using "ls -la" look at everything at the top level in the user's home folder -- nothing below the top directory should be owned by root.  Next take a look under ~/.kde/share/config, or better yet, just "rm -rf" the config folder under ~/.kde/share/.  Then try another normal login.  You will have lost your customizations, but you should get a default KDE desktop.

---

### Post by CinoxFellpyre on 2013-04-12
I deleted ~/.kde/share/config but it didn't do anything for me.

But I looked through the .xsession-errors file and found something that might help.

```
** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'kfilemodule'.

** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'startkdeinitlock'.

** (zeitgeist-datahub:6302): CRITICAL **: file utils.c: line 118: uncaught error: Error opening file: Permission denied (g-io-error-quark, 14)

** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'kfilemodule'.

** (zeitgeist-datahub:6302): CRITICAL **: file utils.c: line 118: uncaught error: Error opening file: Permission denied (g-io-error-quark, 14)

** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'startkdeinitlock'.

** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'kfilemodule'.

** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'startkdeinitlock'.

** (zeitgeist-datahub:6302): WARNING **: kde-recent-document-provider.vala:160: Couldn't find actor for 'kfilemodule'.


```

---

### Post by dabl on 2013-04-13
I've never seen that issue, but google turned up some hits, including [**[color=green]this[/color]**](http://www.linuxine.com/story/ubuntu-recent-applications-not-being-recorded-unity-home-lens) one.  The first answer shows how to clear recent documents and also prevent new ones from being created.  I would try both of those, and if that doesn't work -- dig deeper and figure out how to totally disable whatever that problematic service is.

I can imagine that using files from a removable device, for example, or files from another user could generate this type of problem -- it appears to relate to files permissions and/or files not found.

---

### Post by CinoxFellpyre on 2013-04-14
I tried a command or two from your link, ~/.local/share/zeitgeist/activity.sqlite zeitgeist-daemon, and I don't even have zeitgeist-daemon.

Maybe if I just do a reinstall of plasma-desktop...I'm gonna try that.

Well that was stupidly convenient. I just removed and reinstalled plasma-desktop and it works now.

---

### Post by dabl on 2013-04-14
After running your system a bit, take another look at ~/.xsession-errors.  If you're still getting warning messages from "zeitgeist-datahub:6302", then it's probably not fixed.  :(

Here's how to remove it:  [http://askubuntu.com/questions/45548/disabling-zeitgeist](http://askubuntu.com/questions/45548/disabling-zeitgeist)

---

### Post by CinoxFellpyre on 2013-04-14
Well after consideration, I figured I already exploded Unity before with Compiz and I like KDE too much, plus zeitgeist is useless and gedit is annoying.

So just removed the thing. The only thing I would miss is the FuriousISO

---

### Post by Gary_Delp on 2013-09-24
A search found this thread, and I tried the reinstall of both plasma-desktop and kubuntu-desktop and now am logging on again and again, when I want to.

To do the uninstall I used ```
sudo apt-get purge plasma-desktop
```
That took out both plasma and kubuntu so I did a ```
sudo apt-get install plasma-desktop kubuntu-desktop
```  It did the trick.

Thanks for your conversation!

---

