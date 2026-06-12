---
title: "KSnapShot Weirdness in Kubuntu"
date: 2008-06-29
forum: Desktop Environments
---

### Post by Esau.ie on 2008-06-29
Hey guys! This was posted two years ago, and there was no reply:

hermesrules

 
Join Date: May 2005
Location: Sofia, Bulgaria
Posts: 109
Thanks: 0
Thanked 0 Times in 0 Posts
	
Angry KSnapShot Weirdness in Kubuntu
Hi, all!

I've just upgraded to Edgy, and it does seem awesome. However, there is something else that really troubles me. I am not sure it is specific to Edgy only, but since I am on Edgy now, I decided to post here.

The problem is that all of sudden I get multiple instances of KSnapshot running, and I can't even seem to be able to close them. It is as if a shortcut key is being pressed all the time. I was able to remove ksnapshot, but now instead of it, a Konqueror window pops up with "locate:/ksnapshot" in the address bar. It keeps opening up these windows and nothing else works. I can't close them, I can only press on the power button to restart the computer.

So, I wonder if my system could have been compromised somehow, or if it is perhaps a hardware problem with my keyboard (I am using a Compaq Presario 2100 laptop), so that Kubuntu thinks I am pressing a key all the time.

Does anyone have any suggestions? How can I track the source of this issue?

Thanks in advance for any help!




--------------------------------------------------


I have had the same problem with Hardy Heron v.8.04 running KDE and GNOME on a HP pavilion ze4220 laptop. The laptop is a bit old with some other minor know hardware issues. 

When I first started running GNOME I also had screen capture keep on opening up. I changed the keyboard preferences, removed the keyboard shortcut to take a screenshot and the issue went away. However, the same thing keeps on happening to me in KDE (many instances of Ksnapshot opening up as soon as KDE loads), even though even in KDE I also removed the keyboard shortcuts. 


Any suggestions on what could be causing this?

Thanks in advance.

---

### Post by salemboot on 2008-07-09
I'm getting this on KDE 3.5.9.

Keep pressing Print Screen and you will get this.

I suggest report it as a bug.

KCOP or whatever seems to think it died so it needs to reload it or something i don't really know.

[http://bugs.kde.org/show_bug.cgi?id=139419](http://bugs.kde.org/show_bug.cgi?id=139419)
but they think it was a faulty kvm



I submited a new bug as well.
[http://bugs.kde.org/show_bug.cgi?id=166190](http://bugs.kde.org/show_bug.cgi?id=166190)

---

### Post by salemboot on 2008-07-09
Also turn off the print screen key.


Under Regional & Accessibility / Input Actions
Choose the Preset Actions from the Tree menu
Select PrintScreen

Go to the Command/URL Settings
erase kscreenshot from the command text area

Maybe that will work until they can fix it but it looks as though they they haven't bothered in the past.

---

### Post by elaterite on 2008-10-08
Yes, as salemboot says, disabling the "print screen button" is a good idea, especially when your 92 year old Dad mistakenly leans on it all the time.

There's also a fairly quick fix too. It may take some time as ksnapshot seems to be a resource hog, but even on a slow machine you can eventually reboot (while ksnapshot is going crazy) if you are patient. Go into recovery mode and boot to a prompt. I use Midnight Commander, but use whatever method you choose to delete the directory under 'home' ~/.kde/share/config/session and the file ~/.kde/share/config/ksmserverrc. That will kill the malicious process making ksnapshot go crazy.

---

### Post by atiflz on 2010-05-09
Sorry for reviving this long dead thread.
Kubuntu Karmic and Lucyd still suffer from this problem. I uninstalled ksnapshot and rebooted, in return KDE started to infinitely fork Firefox. So the problem is still valid.

---

### Post by Rob Sherratt on 2011-02-15
[B]_Automating Screen Printing using the PrtScn keyboard button_

[/B]In Kubuntu 10.10, if the PrtScn keyboard button is not assigned, then here's how to configure it:

[LIST]
[*]System Settings -> Shortcuts and Gestures -> Global Keyboard Shortcuts
[*]In the dropdown "KDE Component", select the option "khotkeys"
[*]Select the "PrintScreen" entry so it is highlighted
[*]It may be assigned to "none" as default.  If so the PrtScn button is ignored
[*]Select the "Custom" entry, and touch the spanner icon so it reads "Input..."
[*]On your QWERTY keyboard, press the PrtScn button, and the spanner icon zone will then read "Print"
[*]Exit the System Utilities
[*]Press  the PrtScn button, the program "ksnapshot" will auto-run and grab the  current screen at its native resolution, it shows you a preview, and you can specify where to save the screen image .JPG etc.
[/LIST]

---

