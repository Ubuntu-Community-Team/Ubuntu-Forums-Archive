---
title: "Desktop blank (image only). No files. No links. Nautilus won't launch."
date: 2009-12-06
forum: Desktop Environments
---

### Post by gregconquest on 2009-12-06
My HTPC has spontaneously rebooted a few times (hardware problem), and after one of these reboots my desktop was blank. The background image was there, but there were no icons, shortcuts, or files on the desktop. I also cannot launch Nautilus. It says "launching" but then after about ten seconds, it's gone. To watch a video, I have to launch VLC first and then browse my drives to find the file I want to play.

Everything else seems to be fine.

How can I "reset" the desktop?

Thank you.
Greg

---

### Post by lidex on 2009-12-06
My first move would be to go into synaptic (system>administration>synaptic package manager) and enter "nautilus" into the search field. Mark "nautilus" and "nautilus data" for re-installation. Apply. Use the Alt+F2 run dialog to restart with command "nautilus"

---

### Post by gregconquest on 2009-12-06
I did exactly as you said, Lidex. (BTW, thanks for the clear directions.) When I tried to launch nautilus, nothing happened. So I opened System Monitor and then clicked on the "Places -- Home Folder" link to launch nautilus. Nautilus appeared in the processes for just a split second ("launching" was its status, I think), then it was gone from the list. At the bottom of the screen, the panel icon still said as usual "Opening Home Folder" with the arrows spinning around for again ten seconds or so, then that was gone too.

I rebooted and it is still the same.

I don't think this is a nautilus issue. I think the desktop or launcher or some-such. And I've just confirmed this.

***If I log out from my problem desktop and then login as another user, I see the three drives on the desktop and nautilus launches fine.***

I've also noticed that in the other account, ***compiz*** and nautilus are running immediately after login. On my account, they are not in the list of processes. This is the case whether I logout and then login to the other account, or if I just switch users. It is almost as if my user preferences have been corrupted and is not launching compiz and nautilus.

Greg

---

### Post by lidex on 2009-12-06
Try starting nautilus from a terminal so we can see the error output. Just bring up the terminal and enter "nautilus" as your command. I had to add compiz to my "startup applications" (system>preferences>startup applications) to get it to run automatically. Not sure how nautilus starts but probably a boot script.

---

### Post by lidex on 2009-12-06
have a look here:
[http://ubuntuforums.org/showpost.php?p=135179&postcount=4]("http://ubuntuforums.org/showpost.php?p=135179&postcount=4")

---

### Post by gregconquest on 2009-12-06
Entering nautilus from terminal I get:
(nautilus:4752): Eel-CRITICAL **: eel_preferences_get_boolean: assertion "preferences_is_initialized ()' failed
... WARNING **: No marshaller for signature of signal 'UploadFinished'
......................................................'DownloadFinished'
......................................................'ShareCreateError'
Initializing nautilus-gdu-extension
Segmentation fault.

I'll check the other thread now.

---

### Post by gregconquest on 2009-12-06
> **lidex said:**
> have a look here:
[http://ubuntuforums.org/showpost.php?p=135179&postcount=4]("http://ubuntuforums.org/showpost.php?p=135179&postcount=4")

Thanks for that link. I tried both of the scripts there, but neither one helped. I tried "killall nautilus" as well, with no results.

There are similarities between the two situations, though. I also cannot right-mouse click on the desktop. Also Epiphany will not launch. Stellarium works fine. Firefox works fine also.

Greg

PS It is midnight here, so I will be slow in replying to this over the next 24 hours. Thank you for the help so far, Lidex.

---

### Post by lidex on 2009-12-06
Try removing
```
~/.gconf/apps/nautilus
```

and rebooting. I recently had some issues with nautilus that were caused by a gvfs update from a third-party repository (PPA). After downgrading those packages all was good.You can go into synaptic and search "gvfs". There should be about 5 related packages. Select one at a time and from "package" menu select "force version", the resulting dialog (if not disabled) will have the version options in a drop-down list. If you can downgrade from there do so - just make sure all are the same version.

Also check for nautilus extensions and shares that differ between your's and working user's.

---

### Post by gregconquest on 2009-12-07
I removed ~/.gconf/apps/nautilus but this did not help. And since this is not limited to nautilus (it is Epiphany too), and I think it is a corruption of my user data, I used Synaptic to reinstall many gnome packages. This also didn't help.

So then I made a new user account, deleted my normal account, deleted the home directory as well, then I recreated it.

Now it is working again, though we'll never know what the specific problem was.

Thanks for the help, Lidex.

Greg

---

### Post by lidex on 2009-12-07
Yeah, that's a headscratcher. I'd kinda like to know what the problem was but glad you're back up all the same. ;)

---

