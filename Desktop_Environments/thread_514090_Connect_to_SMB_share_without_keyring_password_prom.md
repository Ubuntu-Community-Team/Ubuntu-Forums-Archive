---
title: "Connect to SMB share without keyring password prompt?"
date: 2007-07-31
forum: Desktop Environments
---

### Post by wkulecz on 2007-07-31
I'm trying to move my wife from windows 2000 to Ubuntu 7.04 after her MB died and my attempt to "restore" the original drives most recent backup to a fresh w2k install on the replacement failed.

I've got the three main things she uses the computer for working fine -- Email (Thunderbird, was easy to drag and drop her profile folder from the broken windows system to Ubuntu), Web browsing (Mozilla), and photo viewing -- what is built into Gnome works great for browsing individual images or doing a slide show of a directory.

Here is the issue, the photos are on a Ubuntu 6.06 file server that had been automatically mapped as W2K network drives upon boot.   But under 7.04 I've made desktop icons to double-click which opens the shares and while the "windows password" is retrieved auto magically, before it does so, I need to type in the keyring pass phrase so I'm back to zero needing to type a password to connect the first time.  Anyway to eliminate this prompt?

--wally.

---

### Post by wkulecz on 2007-08-01
If there is no solution to this, fantasies of normal windows users switching to Ubuntu just ain't gonna happen!

Single sign-on (login in authorizes all allowed functions) is a non-negotiable requirement for unsophisticated users like my wife. 

She needs to access network shares after logging in without additional passwords.  

When I do my domain login under windows at work ( a rather paranoid networking setup) I have access to every share I'm allowed access to without typing further passwords, although automatic logout is another irritation I have to live with.

--wally.

---

### Post by Vlet on 2007-08-01
[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

---

### Post by wkulecz on 2007-08-01
Thanks, I'll give it a try tonight.

But when she logs in there is no keyring password prompt to connect to the net -- The wifi link (using WEP)  is established and mozilla or thunderbird works fine without the keyring prompt popping up.  Its only when the network share icons on the desktop are clicked to view a remote file that the keyring propt pops up.  It only pops up once per login, but since I used a strong keyring pass phrase (max on the meter graph) she is unlikely to ever be willing to type it in.

--wally.

---

