---
title: "Error launching browser window: No XBL binding for the browser"
date: 2006-09-04
forum: Desktop Environments
---

### Post by mikko.ohtamaa on 2006-09-04
After killing X with CTRL+ALT+Backspace, Firefox didn't start anymore. Instead, this error dialog pops up

Error launching browser window: No XBL binding for the browser

This could be cured by removing .mozilla directory in your users' home directory and then reinstalling Firefox.

---

### Post by usersock on 2006-11-29
Worked for me. Thanks!

---

### Post by l951b951 on 2007-02-14
I reinstalled firefox using synaptic and it fixed this problem.  I couldn't get to this post to read about it until after reinstalling, so I didn't know to delete .mozilla.  Anyway, reinstalling did the trick without deleting .mozilla.

---

### Post by l951b951 on 2007-02-15
I would like to add additional information regarding this error message.  After rebooting, the first time I tried to open firefox, the same error occurred.  I had to open synaptic and reinstall firefox again.  As I mentioned in my first post, I didn't delete the .mozilla folder, so this may be the culprit.  Any ideas as to why this happens or a way to fix it that won't get rid of all my firefox settings?

---

### Post by Dr_Faustivius on 2007-03-02
found a suggested fix on a mozilla related forum, here is the link:
[http://www.mozilla.com/en-US/firefox/releases/fix-extensions.html](http://www.mozilla.com/en-US/firefox/releases/fix-extensions.html)

It says to rename or remove a folder titled "chrome", searching for this in ubuntu brings up about 10 or 15 folders, all of which do not match the path suggested in the fix. moving or removing the folders will only fix this problem for one iteration of running firefox, then the problem recurs.  Just like the previous fixes this will only work once or twice, then problem will return. Could this be a bug, or need a bump? 

If anybody else has any luck with the posted link, or any other fixes, please post what works, my firefox is compeletly hamstringed and I'm getting sick of using opera.

---

### Post by Dr_Faustivius on 2007-03-02
ok, I've managed to fix this, here is what I did:

terminal: 
sudo aptitude remove firefox
(this will suggest downgrading or upgrading firefox depending on which version you have installed, say yes either way and it should let you load firefox once)

once firefox was open I set my "download statusbar" to be uninstalled and restarted firefox, this worked to let firefox open every time. I'm not too sure if it was just that particular extension, or if there was something else going on, but firefox now opens every time even after upgrading to the latest version (I had to downgrade and then upgrade using aptitude in the terminal)

so, to sum up:
make sure firefox isn't running, even if you can't see it in X
in the terminal, type "sudo aptitude remove firefox" and say yes to its suggested fix
open firefox and remove an extension (for me, download statusbar)
then upgrade firefox (if aptitude downgraded it)

optional: post on this thread and tell us which extension you had to remove, and how many extensions you had installed before you removed it
For me: download statusbar and 4 extensions installed before I removed it

(You may want to try removing extensions one at a time if removing just one doesn't work)
I'm going to try reinstalling download statusbar and see if the problem recurs, will post my results here.

---

### Post by Dr_Faustivius on 2007-03-02
ok, reinstalling download statusbar re-creates the problem, so it must either be that extension or related extensions
I installed fullscreen homestarrunner and the problem didn't come back, so I'm thinking that it must be some specific type of extension that is causing the problem, now it's a matter of deciding wether this is a problem with firefox or ubuntu

---

### Post by Diego- on 2007-03-14
It happened the same to me with the NoScript extension, instead of removing it, what i did is run it in safe mode, and uninstalling the extension there.
```

firefox --safe-mode

```

---

### Post by Neophyte on 2007-03-24
> **Diego- said:**
> It happened the same to me with the NoScript extension, instead of removing it, what i did is run it in safe mode, and uninstalling the extension there.
```

firefox --safe-mode

```

A search and the first hit solves my problem!

Word for word, that fixed it for me!

thanks :guitar:

---

### Post by BobE on 2007-04-18
Today I got the 'No XBL binding..' error msg.  Thx to the info here that it might be extension related I clicked on Tools, then extensions.  NoScript was saying it needed to be updated.  I did that & now Firefox opens like always. :-)

---

### Post by 8rdx on 2007-04-21
I have also solved this problem by updating an extention. For me the extension was 'Adblock Plus' (try it, it's great!).** Also**, I did not start having this problem until Firefox was updated a couple weeks ago. This suggests to me it is a Firefox issue.

:)

---

