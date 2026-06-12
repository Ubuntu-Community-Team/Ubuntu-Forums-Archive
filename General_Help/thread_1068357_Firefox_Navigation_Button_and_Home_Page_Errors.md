---
title: "Firefox Navigation Button and Home Page Errors"
date: 2009-02-12
forum: General Help
---

### Post by BJ_Covert_Action on 2009-02-12
Howdy All,

Last night I logged onto Ubuntu and was quickly prompted with an upgrade request. Being a diligent updater of my system, I selected all of the upgrades offered including what appeared to be a reinstall or update to Firefox 3.0. I installed the upgrades successfully to my knowledge. After the upgrading process, I piddled around on my system for a while attempting to learn more about the ports on my system and security in general.

Long story short, today I log on and notice that when I start Firefox the back, forward, upside down carret, and refresh buttons on my navigation toolbar don't work. This may have been the case last night but I did not notice. Firefox also refuses to properly load my homepage when it starts. I have checked and reset my preferences using Firefox's preferences GUI numerous times to still have it fail at loading my proper startup page (which is Google). 

Well I did some Googling on the subject and found out that a file called localstore.rdf can get corrupted, leading to the toolbar problem, and needs to be deleted from time to time. So, I deleted it, and nothing changed. I went so far as to uninstall firefox entirely and reinstall it via Synaptic Package Manager. Still the exact same problems occur. 

So this has left me a little dumbfounded as to how Firefox can not only launch improperly, but also manage to be uninstalled, reinstalled fresh, and still fail to launch properly. Any ideas?

For reference, other things I did last night on my computer prior to my discovery of this glitch included:

- editing the avahi-daemon startup file to disable automatic loading.
- downloading and installing nmap and zenmap and using both the front  end  and the console to port scan my local IP for open ports
- repetitive use of the netstat command to find out further information about services running on my computer
- changing permissions to my Home folder 
----Owner: Create and delete files
----Group: Create and delete files
----Others: Access Files (only)

- all of the above tasks required various sudo logins since most of them were administrative tasks

Any idea why any of this might have caused a Firefox error?

I hope this helps. If anyone needs more information please just tell me what to post and how to find it.

Thanks in Advance,
Brady C. Jackson

:popcorn:

---

### Post by BJ_Covert_Action on 2009-02-12
Anyone?

---

### Post by BJ_Covert_Action on 2009-02-13
Update: 

Error Console after firefox start is outputting the following:

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.6/components/libpyloader.so

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.6/components/pyabout.py

Error: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/firefox-3.0.6/components/nsBrowserGlue.js :: bg__initPlaces :: line 449"  data: no]
Source File: file:///usr/lib/firefox-3.0.6/components/nsBrowserGlue.js
Line: 449

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x8007000e (NS_ERROR_OUT_OF_MEMORY) [nsIDocShellHistory.useGlobalHistory]"  nsresult: "0x8007000e (NS_ERROR_OUT_OF_MEMORY)"  location: "JS frame :: chrome://browser/content/browser.js :: prepareForStartup :: line 763"  data: no]

Does that help any?

---

### Post by LiamWilson on 2009-02-13
This may seem like a bit of a dumb answer, but did your try uninstalling it then re installing firefox?

---

### Post by BJ_Covert_Action on 2009-02-13
Yeah, I did a full removal through Synaptic (including dependencies) and reinstalled Firefox 3.0.6. I tried that three times and it never changed (which seems odd to me, tells me something is not getting deleted).

Anyways, last night I tried tactic two and did a full removal and installed Firefox 2 instead. Firefox 2 seems to be running peachy keen so I will take that as a successful fix since I kind of preferred 2.0 over 3.0 anyways. 

Nonetheless, I would still be interested in hearing if anyone else has any idea what might have caused this. If you don't want to keep the thread going feel free to message me on here.

---

### Post by abrooke18 on 2009-02-14
I had a similar problem - the only solution was to delete the old Firefox 3 profile and profile.ini file, then restart Firefox, which create a new profile.

This procedure deletes all your data, but it fixes the problem!

---

### Post by gurrier on 2009-02-21
I've had exactly the same issue and all my bookmarks also vanished.
I think I may have had some issues in the leadup to this profile corruption which showed Firefox still hanging as a process from time to time.

Anyway I managed to get my bookmarks toolbar and "Organise Bookmarks" to show my bookmarks by doing the following...

1) Find your profile folder by looking for a hidden directory under
ls ~/.mozilla/firefox/
e.g. for me...
~/.mozilla/firefox/saxqgn8t.default 

2) then look in this folder for any files beginning with places.sqlite* and rename them.
e.g. for me...
cd ~/.mozilla/firefox/saxqgn8t.default
mv places.sqlite places.sqlite.old
mv places.sqlite-journal places.sqlite-journal.old
you may also find some of these (I did not)
mv places.sqlite.corrupt places.sqlite.corrupt.old

3) Check under the bookmarkbackups subfolder
e.g. for me...
ls -al ~/.mozilla/firefox/saxqgn8t.default/bookmarkbackups/
If any of the recent files are zero bytes in size, delete them and then restart Firefox

4) Hey presto, bookmarks back!!!!

Now I need to fine out how to get my addons to update.  I'm seeing the same warnings in the Error Console in Firefox (Tools menu).

[I]Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.6/components/libpyloader.so

Failed to load XPCOM component: /usr/lib/xulrunner-1.9.0.6/components/pyabout.py [/I]

---

### Post by gurrier on 2009-02-21
Ok, I noticed an error in the Firefox "Error Console" which indicated a permissions error so I ran Firefox as root to try to install the problematic addons 

sudo firefox

That worked but my bookmarks disapeared again.

So I repeated the steps above again and this time I found a new file in the bookmarkbackups folder (see above) and removed that.
(Note that it starts with a capital "B" and also is missing the first hyphen of the previous files which is a little odd.  It also has root ownership.)

[email]me@pc:~/.mozilla/firefox/saxqgn8t.defaul[/email]t$ ls -al bookmarkbackups/
total 296
drwx------ 2 me me  4096 2009-02-22 01:55 .
drwx------ 8 me me  4096 2009-02-22 01:58 ..
-rw------- 1 me me 48615 2009-02-11 22:19 bookmarks-2009-02-11.json
-rw------- 1 me me 48615 2009-02-13 01:47 bookmarks-2009-02-13.json
-rw------- 1 me me 48615 2009-02-14 14:50 bookmarks-2009-02-14.json
-rw------- 1 me me 48615 2009-02-15 16:20 bookmarks-2009-02-15.json
-rw------- 1 me me 48137 2009-02-22 01:06 bookmarks-2009-02-22.json
-rwx------ 1 root root 46014 2009-02-22 01:55 Bookmarks 2009-02-22.json

Anyway, I think I'm back in the saddle now.
Hope this gives you some leads.

---

### Post by tua79344 on 2009-02-22
I have the same problem as OP. Reinstalled several times, no help.

Youtube videos no longer play right either, and the search bar in the top righr  doesn't work.

---

### Post by BJ_Covert_Action on 2009-03-03
Well the best solution I was able to come up with was to wipe Firefox 3 off my system entirely. Then I installed firefox 2.0 (old school) and it started working perfectly. I always kinda liked 2.0 better than 3.0 anyways so I think I will stick with it for now, but thanks for the advice everyone, it helped me learn a lot about firefox :)

Cheers,
Brady

---

### Post by Arrorn on 2009-05-04
Thanks so much gurrier my firefox was showing up blank and your fix gave me my bookmarks back...

---

