---
title: "(firefox:1787): GLib-WARNING **: g_set_prgname() called multiple times"
date: 2009-12-08
forum: Desktop Environments
---

### Post by m42h31 on 2009-12-08
my firefox can't open with clicking it's icon on ubuntu 9.10. but i run it on terminal by typing firefox %u i found this error :
(firefox:1787): GLib-WARNING **: g_set_prgname() called multiple times

it just run well if i run with sudo 
any solution to solve this problem?

---

### Post by m42h31 on 2009-12-25
is there no solution ??

---

### Post by 5ulo on 2009-12-25
the same here

---

### Post by Weevil on 2009-12-29
I have to click the firefox icon in my panel twice, first time gets shut down again for some reason. Same error as you guys in terminal.



Hmz... this post says it gets fixed by removing the .mozilla folder from your homefolder. I'll give it a try.

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=536197&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=536197&forumId=1)

---

### Post by rdewit on 2009-12-29
> **Weevil said:**
> 
Hmz... this post says it gets fixed by removing the .mozilla folder from your homefolder. I'll give it a try.


Hi, you **do** realise that you will **lose all your Firefox settings** (including bookmarks and addons) when you remove your .mozilla folder? 
It might be safer to rename it to .mozilla.bak for example.

---

### Post by falconindy on 2009-12-29
If it's that big of a deal to you, run it as:
```
firefox 2>/dev/null
```
They're just warnings though. No harm done.

---

### Post by bennig on 2010-01-06
If I launch firefox it doesn't open. Also the firefox icon is missing.

First I tried reinstalling firefox through synaptic, that didn't work.

I tried launching it through terminal, I got this error: 

  GLib-WARNING **: g_set_prgname() called multiple times

I tried reinstalling libglib2.0-0, no change, then forcing libglib2.0-0 to run as version 2.22.2 instead of the latest version 2.22.3 - the error message went away, but firefox still didn't start.

After googling that I found this thread. Tried all 3 "solutions" in the thread.

I ran it as sudo, it didn't start, but gave no error.
I renamed my .mozilla folder, got the same error.
I ran it with "firefox 2>/dev/null" got the same error.

I still cannot get firefox to start. Has anyone been able to fix this issue?

---

### Post by bennig on 2010-01-07
Anyone?

---

### Post by mugs on 2010-01-09
This worked for me: I removed xulrunner-headless-1.9.2 and now Firefox starts

---

### Post by Bashar &quot; on 2010-01-14
i'm facing the same issue now with thunderbird but my problem is worse

i start it then it shows:
(thunderbird-bin:2702): GLib-WARNING **: g_set_prgname() called multiple times

few minutes of work it Segfaults (Segmentation Fault)

of course deleting .mozilla and .mozilla-thunderbird will delete the entire profiles and this is not an acceptable solution at all


and i don't have xulrunner-headless

---

### Post by mugs on 2010-01-14
Do you have any of the moblin programs installed?

---

### Post by Bashar &quot; on 2010-01-14
no its fresh 9.10 installation then i copied my profile from my previous 8.10 installation

both TB 2.x

---

### Post by Bashar &quot; on 2010-01-14
> **mugs said:**
> Do you have any of the moblin programs installed?

just to confirm how do i dentify if i have any of moblin softwares installed?

---

### Post by kovi on 2010-01-15
Uninstalling Miro player ([http://www.getmiro.com/](http://www.getmiro.com/)) solved the problem for me.

---

### Post by amadib on 2010-01-18
I'm having this issue as well.

---

### Post by Sqeaky_TheTrulyOpen on 2010-01-19
I too am having this issue and removing the .mozilla folder did not correct it, and I do not have xulrunner-headless installed.

---

### Post by ie@fromru.com on 2010-01-20
It happened after Firebug 1.5 update. I started FF by running "firefox -safe-mode" in command line and disabled Firebug 1.5 add-on, only after that I managed to run FF as usual.

---

### Post by pkts2 on 2010-02-03
Fixed!. Instead of deleting the whole .mozilla folder found out that the offending file is actually "compatibility.ini".

Not sure what this file does but renaming it does the trick.

---

### Post by m_a_r_k_y on 2010-02-10
[http://ubuntuforums.org/showthread.php?t=1362942](http://ubuntuforums.org/showthread.php?t=1362942)

---

### Post by calamar_ on 2010-02-14
Finally I found out a better solution to this problem I was having as well.

Just go to the profile folder under your ~/.mozilla/firefox/... There you'll see 3 files named like extensions.something

I tried first removing the three of them and it worked.

I wondered first if the problem could be with any of the extensions I got installed or updated. That's why I got there.

Anyway, I deleted then just the file "extensions.ini" and it worked too. So, try your own and let us know.

Thanks all.
Alex

---

### Post by SirGe on 2010-02-16
I had the same problem. The messages ((firefox-bin:22382): GLib-WARNING **: g_set_prgname() called multiple times) appear to be an unrelated symptom. Prism seems to be the issue.

Part of the apparent reason for many different proposed solutions is that once I successfully start firefox in safe mode (i.e. with -safe-mode), it restarts fine without any additional options. Once. If I stop it and try to start it again, it fails without any additional messages.

None of the above proposed cures fixed the problem in my case.

By a tedious process of alimination, I identified the trigger as prism: if I disable it, I have no problems, if I re-enable it, I bring the problem back. This extension is not particularly useful: it enables you to create prism launchers from Firefox, but you can do the same by editing XML files...

My versions: FF 3.6.2pre, prism 1.0b3 (from [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu):](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu):) I _really_ wanted tear-off tabs :)

This helped me realize just how much I depend in firefox working properly on my desktop - loads of thanks to all the Mozilla developers!

HTH

---

### Post by harpoonz on 2010-02-19
Thanks for doing the legwork SirGe!  I was getting the same message until I disabled Prism.

---

### Post by sambatyon.abulafia on 2010-02-20
OK guys, I took the time to disable all the add ons and enable them one by one until the bug show itself. At the end, the add on which was causing all the problems was greasemonkey.

---

### Post by ben2talk on 2010-02-20
> **Weevil said:**
> I have to click the firefox icon in my panel twice, first time gets shut down again for some reason. Same error as you guys in terminal.



Hmz... this post says it gets fixed by removing the .mozilla folder from your homefolder. I'll give it a try.

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=536197&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?locale=en-US&comments_parentId=536197&forumId=1)

I think this is a problem in the file 'compatability.ini'. I have multiple profiles, so I opened /home/ben/.mozilla and clicked the magnifying glass, entered 'compatibility.ini' and deleted them all.

Firefox started perfectly - but only one time.

So, I edited 'compatability.ini' to read as follows:

[Compatibility]
LastVersion=3.6_20100124075447/20100124075447
LastOSABI=Linux_x86-gcc3
LastPlatformDir=/usr/lib/firefox
LastAppDir=/usr/lib/firefox

Then I saved it, and made it READ ONLY - then copied and pasted it into each of the profile folders.

Now I can launch Firefox normally, and this file isn't rewritten in a way that stops it launching ;)

---

### Post by shellehs on 2010-02-25
@ben2talk  thanks, it works 4 me~~

---

### Post by pho3nixf1re on 2010-02-25
i was having the same issue. in the compatibility.ini file i changed

```

[Compatibility]
LastVersion=3.6_20100218182626/20100218182626
LastOSABI=Linux_x86_64-gcc3
LastPlatformDir=/usr/lib/firefox-3.6
LastAppDir=/usr/lib/firefox-3.6

```

to

```

[Compatibility]
LastVersion=3.6_20100218182626/20100218182626
LastOSABI=Linux_x86_64-gcc3
LastPlatformDir=/usr/lib/firefox
LastAppDir=/usr/lib/firefox

```

notice the difference in the platform and app dir settings.

be sure to change the file to read only, otherwise firefox will overwrite the fix.

---

### Post by pho3nixf1re on 2010-02-25
WARNING! changing the directories like i did removed all my extensions. will post back if i can figure out what happened. at least firefox works. good thing firefox isn't my main browser anymore ;)

---

### Post by Arkitekt on 2010-02-26
> **sambatyon.abulafia said:**
> OK guys, I took the time to disable all the add ons and enable them one by one until the bug show itself. At the end, the add on which was causing all the problems was greasemonkey.

I also discovered this, but the reason it is causing a problem with 3.6 is because greasemonkey seems to not auto-update when a new version comes out, most of us have pre-3.6 versions. I myself had a version from January of 2009. Looks like in 0.8.3 greasemonkey added a 3.6 compatibility flag. Updating manually from the add-ons website to 0.8.20100211.5 fixed this issue for me. 

I fixed my GLib warnings by downgrading libglib2.0-0 and libglib2.0-data to 2.22.1-0ubuntu1, the newest one from karmic-updates (2.22.3-0ubuntu1) seems to be unstable. For those wondering how to do this, in synaptic highlight the package and under the package menu on the toolbar select force version (CTRL-E).

Hope this solves this for everyone.

---

### Post by Deathspawn on 2010-03-02
> **SirGe said:**
> I had the same problem. The messages ((firefox-bin:22382): GLib-WARNING **: g_set_prgname() called multiple times) appear to be an unrelated symptom. Prism seems to be the issue.

Part of the apparent reason for many different proposed solutions is that once I successfully start firefox in safe mode (i.e. with -safe-mode), it restarts fine without any additional options. Once. If I stop it and try to start it again, it fails without any additional messages.

None of the above proposed cures fixed the problem in my case.

By a tedious process of alimination, I identified the trigger as prism: if I disable it, I have no problems, if I re-enable it, I bring the problem back. This extension is not particularly useful: it enables you to create prism launchers from Firefox, but you can do the same by editing XML files...

My versions: FF 3.6.2pre, prism 1.0b3 (from [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu):](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu):) I _really_ wanted tear-off tabs :)

This helped me realize just how much I depend in firefox working properly on my desktop - loads of thanks to all the Mozilla developers!

HTH

Yep. Seems correct. Just installed prism and shortly after, it failed to start. Did the firefox -safe-mode and shut off all add-ons and it popped up fine. Though, I do notice when starting it in Terminal, it still throws up these errors:

> spawn@quernerium:~$ firefox

(firefox-bin:27247): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",

(firefox-bin:27247): GLib-WARNING **: g_set_prgname() called multiple times

But it starts.

---

### Post by LouPirlu on 2010-04-01
same problem, firefox 3.6 doesn't start (I see "Starting Firefox Web Browser" on the taskbar for a while, then disappears and nothing happens). Launching from the terminal I get the GLib warning.

launching in safe mode and **disabling GreaseMonkey** solved the Firefox-doesn't-open problem (but I still got the GLib warning), and **downgrading the package libglib** to 2.22.2 solved the warning (but again ffx didn't start). They seem to be two different issues.

---

### Post by watchpocket on 2010-04-09
> **LouPirlu said:**
> . . . and **downgrading the package libglib** to 2.22.2 solved the warning (but again ffx didn't start). They seem to be two different issues.

I did this.

It helped a Firefox problem I was having, but for several weeks now my Update Manager still shows (as recommended updates) version 2.22.3 for both libglib2.0-0 and libglib2.0-data.

Do I need them for anything, since I'm currently running 2.22.2?

How does one get them out of the Update Manager?  Synaptic has nothing newer for them than 2.22.3.  

I have to uncheck them every time I install updates.  One of these days I'll probably end up installing them accidentally, along with other updates.

Suggestions, please.

---

### Post by mugs on 2010-04-09
Highlight those packages and then go to Package on the menu bar and check lock version.  Then it will show up under a category of pinned and you wont accidentally update it in the future.

---

### Post by DOMiller on 2010-04-12
Have this error when starting Thunderbird, followed by segmentation error, similar to Bashar, except segmentation error comes immediately, before T'bird opens.

Tried ALL of the ideas mentioned in this forum; nothing makes a difference.

No problem with FireFox.

Any new ideas?

---

### Post by DOMiller on 2010-04-13
> **DOMiller said:**
> Have this error when starting Thunderbird, followed by segmentation error, similar to Bashar, except segmentation error comes immediately, before T'bird opens.

Tried ALL of the ideas mentioned in this forum; nothing makes a difference.

No problem with FireFox.

Any new ideas?

Found the basic cause and solution:

I had previously installed, and had been using, the latest Version of T'bird (3).  Subsequently, Update Manager reverted to an older version (2).  *Apparently*, it didn't revert the dependents, though, and the combination of old T'bird and new dependents caused the problem.  Again installing the latest version from [http://getthunderbird.com](http://getthunderbird.com) resolved the issue (the Glib warning still appears, but no segmentation fault, and T'bird opens and runs normally).  Installation instructions can be found here:  [B][http://tinyurl.com/instTB3](http://tinyurl.com/instTB3) 
[/B]If TB3 had been installed previously, as in my case, the latter 1.5 steps on migration are not needed.

---

### Post by dogeatery on 2010-09-07
This problem began occurring for me immediately after I installed Prism in Linux Mint 8.  Prism now installs an extension in Firefox.  I opened Firefox in safe mode and disabled the Prism extension and Firefox immediately began working like normal.

Anyone know how this will affect Prism?

---

