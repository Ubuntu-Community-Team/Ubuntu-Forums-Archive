---
title: "More members/users with a broken firefox 3.0.11 update?"
date: 2009-06-13
forum: General Help
---

### Post by Soul-Sing on 2009-06-13
I have got a fiefox security update, with comes with a broken xulrunner, so firefox did'n start.
-apt was in pain also.
solution here: 
- ```
xulrunner --register-global
``` when  broken:
- ```
sudo dpkg --configure -a
```
Open synaptic package manager: filter on broken packages: xulrunner
fix broken package/reinstall
When reinstalled, the rest of the firefox update runs ok.

---

### Post by blairm on 2009-06-13
Hi,

An update this morning has broken my firefox as well.
Followed the fix above but it didn't seem to work; maybe I misunderstood it?
Wrote the code in the terminal, removed xulrunner and reinstalled it; still mad no difference.
The filter on broken packages showed nothing.
Running Jaunty.
Really would like to return to using firefox; don't feel as comfortable with Opera or Konqueror. 
Does anyone know of a deb of the previous version? Or will I need to compile it from source? 

Cheers,

Blair

---

### Post by trecool999 on 2009-06-13
> **blairm said:**
> Hi,

An update this morning has broken my firefox as well.
Followed the fix above but it didn't seem to work; maybe I misunderstood it?
Wrote the code in the terminal, removed xulrunner and reinstalled it; still mad no difference.
The filter on broken packages showed nothing.
Running Jaunty.
Really would like to return to using firefox; don't feel as comfortable with Opera or Konqueror. 
Does anyone know of a deb of the previous version? Or will I need to compile it from source? 

Cheers,

Blair

Try simply using Synaptic to reinstall Firefox. Does it work after that?

---

### Post by blairm on 2009-06-13
Thanks for reply.

Tried that a couple of times with no luck; when I try to stay firefox I get the firefox icon in the task bar saying starting firefox browser, but after about 10 seconds it gives up.

Cheers,

Blair

---

### Post by merlinus on 2009-06-13
I found there was more than one profile in my .mozilla/firefox directory.  Getting rid of one of them solved the problem.

---

### Post by trecool999 on 2009-06-13
> **blairm said:**
> Thanks for reply.

Tried that a couple of times with no luck; when I try to stay firefox I get the firefox icon in the task bar saying starting firefox browser, but after about 10 seconds it gives up.

Cheers,

Blair

Did you do a complete removal or just the normal removal?

---

### Post by blairm on 2009-06-13
Thanks Merlin,

Just had a look in .mozilla; looks like I have general and profile 0 (details below).
I tried removing profile 0 and it made no difference, so I put it back in the profiles.ini.

Trecool: Was a complete removal and reinstallation. 

Blair

.firefox has
 
- refhrako.default
- pluginreg.dat
- profiles.ini

profiles.ini has:

- [General]
StartWithLastProfile=1

- [Profile0]
Name=default
IsRelative=1
Path=refhrako.default

---

### Post by merlinus on 2009-06-13
Perhaps your only recourse is to save your bookmarks, completely remove .mozilla directory, and reinstall firefox from Add/Remove or synaptic.

---

### Post by blairm on 2009-06-13
May need to do that; a quick question though - if I completely remove mozilla directory, will that kill everything I have in sunbird as well?

Mozilla contains extensions, firefox, sunbird and appreg (not sure what that is, and I'm unable to open it to find out).
Not a dealbreaker if I do have to save all the sunbird entries, but would like to know before wiping the mozilla directory.

Cheers,

Blair

---

### Post by merlinus on 2009-06-13
You could save the entire extensions subdirectory, .sqlite and .dat  and .db  and .ini files.

Here's another idea:  backup your .default directory as well.  If firefox works after the reinstall, then you can copy it back and not lose anything.

---

### Post by blairm on 2009-06-13
OK, still not working. Have just;

- deleted .mozilla
- completely uninstalled firefox
- reinstalled firefox

The problem remains as it was; When I try to start the browser I get the message in the task bar that the browser is starting but it gives up after a few seconds.

What's the next step? Should I try getting the source from the firefox site and compiling? 
Think I've only compiled a couple of programs in the several years I've used linux, so it would at the very least be a learning experience:)

Blair

---

### Post by blairm on 2009-06-13
Sorry, unintentional double post.

Blair

---

### Post by majamba on 2009-06-13
or you could try firefox-3.5

aptitude install firefox-3.5

---

### Post by albinootje on 2009-06-13
> **leoquant said:**
> I have got a fiefox security update, with comes with a broken xulrunner, so firefox did'n start.
-apt was in pain also.

Hmmm, which release was that ? 

I updated my Jaunty desktop last night, and apt-get and Firefox didn't complain at all.
Tonight at work I updated some Hardy desktops and apt-get didn't complain at all.

---

### Post by blairm on 2009-06-13
Thanks for the suggestion Majamba - I just installed 3.5 and the issue remained the same.

Makes me wonder whether it's a hardware issue, but it doesn't seem likely since it's all pretty standard - 3.0Ghz intel core 2 duo, a gigabyte mobo and a 4850 graphics card.

On the verge of backing up everything and doing a reinstall, but would really prefer to avoid that if I can.

Also wonder whether I'm the only one in this position; my computer was working fine a few hours ago.
Firefox stopped immediately after the update, so I'm guessing the update probably caused the problem.

Is there a way to wind back an update?

Blair

---

### Post by albinootje on 2009-06-13
> **blairm said:**
> 
The problem remains as it was; When I try to start the browser I get the message in the task bar that the browser is starting but it gives up after a few seconds.

What happens if you try to start Firefox with the profile manager in a terminal ?
```

firefox -P

```
> 
What's the next step? Should I try getting the source from the firefox site and compiling? 

No. That will not help you to find the cause of your current problem, and will be a looooooong waste of time.

---

### Post by blairm on 2009-06-13
Think we're making some progress.

Followed albinootje's advice and entered sudo firefox -P in the terminal, A box titled firefox - choose user profile came up.
There were no profiles, so I created a default one.
 
If I click the start firefox button in the choose user profile box I can start firefox and it seems to work.

However, trying to start firefox from applications-internet-firefox gives the same behaviour I've been having for the past couple of hours - that is, the note in the task bar that firefox is starting but after a couple of seconds it gives up.

Blair

---

### Post by blairm on 2009-06-14
For what it's worth, I've solved my problem re being unable to open Firefox: used chown to change ownership of the .mozilla directory, which was only able to be accessed by root.
Thanks everyone for your help, and I hope this may be of some help to anyone else having problems.
Songbird is still knackered and the problem appears to be a different one there, but that's a whole new thread!

Blair

Right, seems the issue is related to permissions.
After some experimentation I tried running  firefox from the terminal with the command sudo firefox  and it worked.
Next, I restarted the machine. When I tried to start firefox via applications-internet-firefox the choose user profile box came up, but it was blank.
I tried to create a profile but got the following error message:


Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]

However, not entirely sure how to change the file permision: tried doing so by highlighting .mozilla in the file browser and going to properties - permissions. Didn't work. 

Still searching for an answer: looking on the bright side, I've learned more about firefox today than I have in 10 years of using it:D

Blair

---

