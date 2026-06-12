---
title: "D key (alone) shows desktop over Xrdp"
date: 2010-10-13
forum: Desktop Environments
---

### Post by ecadman on 2010-10-13
PROBLEM
While connecting over Xrdp, hitting the "D" key alone hides all my windows and shows the desktop. This is problematic since I often wish to type words containing at least one "D" in it. In case anyone else is having this problem, I've wrestled through it and offer this help.

I'm using Ubuntu 10.10 Maverick Meercat and connecting via Xrdp. I only have this problem when connecting remotely.

APPARENT CAUSE
I don't pretend to know for sure, but the problem appears to be that the remote connection is flubbing Metacity's "<Super>d" binding for the "show desktop" command. More precisely, the string "<Super>" doesn't appear to be functioning for me. If I change <Super> to <Ctrl>, I can use Ctrl + D to show desktop, and I can then type the letter D without it hiding every window from me. 

Further evidence <Super> isn't working for me, if I change Metacity's "panel_run_dialog" global key binding from "<Alt>F2" to "<Super>F2" I bring up the run dialog by hitting F2 alone.

WORKAROUND
Change the system's "show desktop" keystroke. Here are the steps.

1) Alt+F2
2) gconf-editor
3) /->app->metacity->global_keybindings
4) Change the assigned keystroke for show_desktop from "<Super>d" to "<Ctrl>d" or "<Ctrl><Alt>d" or "disabled"

If someone finds this worthy of submitting a bug ticket, please let me know so I can follow it. Thanks.

Ed

---

### Post by zdea on 2010-10-15
I also have this problem on a vanilla install, which to me means that either xrdp or the terminal server client is broken, I would wager it's xrdp. Bummer too because this is the best way to work with VM's in my book.

---

### Post by haihovu on 2010-10-24
I got the exact same problem when upgraded to maverick recently, after resolving a host of other problems with xrdp. It seems xrdp is not getting a lot of attention in the regression process, since there was a problem with demonic short cuts in xrdp in 10.04 as well ([http://ubuntuforums.org/showthread.php?t=1471770](http://ubuntuforums.org/showthread.php?t=1471770)).
 
Thanks for posting your work around, it works perfectly (though I elected to disable the show desktop shortcut). I'd like to raise a bug report but I don't know how the Ubuntu bug report system work, yet.

---

### Post by laperouse on 2010-11-15
Astonished that not many more people have hit the problem.

As I understand, it is a keyboard mapping issue when connecting to a Ubuntu machine (which has xrdp installed) with RDP.

Once connected, hitting the key <d> (note lower case) minimizes all active windows and shows the desktop. Hitting the key again restores the windows, but you will not be able to enter the letter "d" in any application. Slightly limiting...

I found that going to System->Preferences->Keyboard Shortcuts lists the mappings, although using a somewhat obscure "key language" which I am not familiar with. However, if you scroll to the bottom, you will find this entry:

<hide all normal windows and show the desktop -> D>

(note here the uppercase "D"). This is the culprit. Change the mapping to, say, <Alt><d> (lower case), close and the problem should be solved!

Now what this has done is to create a file under your home directory (I will represent that by the usual ~):

~/.gconf/apps/metacity/global_keybindings/%gconf.xml

and the new mapping is stored in that XML file.

It appears to be an error in the default keyboard mappings. They might be in the X11 configuration, but I could not devote more time to look into this further.

Cheers to all. HTH.

---

### Post by heathman001 on 2010-11-23
Thanks laperouse, this issue was driving me crazy. Your solution worked perfectly.

---

### Post by purevirtual on 2010-11-27
Thank you for the workaround!

---

### Post by Nemo_bis on 2011-02-18
I had the same problem; the strange thing is that it's like the "Windows" key was always considered pressed, but it happens only with the d key. Since I had just changed my .xmodmap file (which worked correctly on Ubuntu 9.10) I checked it but it was correct.
Anyway, I've adopted this workaround...

---

### Post by AtesComp on 2011-03-02
Also being plagued by the inane and obtuse use of the "d" key via remote login, I troweled  upon the black earth a little deeper.

Using "gconftool-2", I traveled down the structured tree to light upon the branch "/apps/metacity/global_keybindings" and found the "show_desktop" item. Lo, the value appears as "<Super>d".  With apparent resolve, the poorly designed program is left bewildered as to the use of "<Super>" and randomly decide for itself to apparently ignore "<Super>" and select the "d" key. Unbeknownst to the astute end-user, the lowly "d" key has suddenly become his bane forevermore.

I protest! An error I say! I banish thee to the deepest pit of hell!
Changing this does not one any good fortune, sudo or not!

To correct heinous error, edit the swine of a file "/var/lib/gconf/debian.defaults/%gconf-tree.xml" and set the "show_desktop"s stringvalue to "Disabled" or whatever your humble preference. A trick upon this treat is to actually make entry of the word "Disabled" as it contains a "d". The astute reader shall quickly note the use of the "delete" key on "&lt;Super&gt", enter "isable", and use the existing "d".  No longer shall each user need concern themselves with prior given solutions henceforth.

My given solution requires a logout/login.

Live well hence forth for all user logins thereafter. I fare thee anon. ):P

---

### Post by fradsham on 2011-03-02
> **ecadman said:**
> PROBLEM
While connecting over Xrdp, hitting the "D" key alone hides all my windows and shows the desktop. This is problematic since I often wish to type words containing at least one "D" in it. In case anyone else is having this problem, I've wrestled through it and offer this help.
 
I'm using Ubuntu 10.10 Maverick Meercat and connecting via Xrdp. I only have this problem when connecting remotely.
 
APPARENT CAUSE
I don't pretend to know for sure, but the problem appears to be that the remote connection is flubbing Metacity's "<Super>d" binding for the "show desktop" command. More precisely, the string "<Super>" doesn't appear to be functioning for me. If I change <Super> to <Ctrl>, I can use Ctrl + D to show desktop, and I can then type the letter D without it hiding every window from me. 
 
Further evidence <Super> isn't working for me, if I change Metacity's "panel_run_dialog" global key binding from "<Alt>F2" to "<Super>F2" I bring up the run dialog by hitting F2 alone.
 
WORKAROUND
Change the system's "show desktop" keystroke. Here are the steps.
 
1) Alt+F2
2) gconf-editor
3) /->app->metacity->global_keybindings
4) Change the assigned keystroke for show_desktop from "<Super>d" to "<Ctrl>d" or "<Ctrl><Alt>d" or "disabled"
 
If someone finds this worthy of submitting a bug ticket, please let me know so I can follow it. Thanks.
 
Ed
 
 
I have to say, that although the solution is not obvious, it worked perfectly for me. I am on a Windows 7 laptop and remoting into a desktop running Ubuntu 10.10 standard desktop install.
 
thank-you for the solution.

---

### Post by stivy on 2011-03-09
I was having the same problem with the pressing the 'd' key and it minimizing my windows. I fixed it by using the work around that ecadman posted.

I am still having some other issues which I think are related to the Super issue. When I am in the file browser and double click on something it closes all of my file windows. If I ctrl+left click to select multiple items it closes all of my file browser windows. If shift+left click I am fine but if use shift+up arrow or shift+down arrow it closes all of my file browser windows. It is very annoying when trying to copy files around or even trying to open a file.

Has anyone else had this issue as well?

---

### Post by dude4linux on 2011-03-19
Yes, I have the problem also.  Fresh install of 10.10.  Trying to remote access using rdesktop.  Finally found this thread, but haven't yet tried one of the suggestions.

---

### Post by freshman66 on 2011-03-24
Same here. Anbody found a solution to the doubleclick problem?

---

### Post by Keamas on 2011-05-24
> **ecadman said:**
> PROBLEM
While connecting over Xrdp, hitting the "D" key alone hides all my windows and shows the desktop. This is problematic since I often wish to type words containing at least one "D" in it. In case anyone else is having this problem, I've wrestled through it and offer this help.

I'm using Ubuntu 10.10 Maverick Meercat and connecting via Xrdp. I only have this problem when connecting remotely.

APPARENT CAUSE
I don't pretend to know for sure, but the problem appears to be that the remote connection is flubbing Metacity's "<Super>d" binding for the "show desktop" command. More precisely, the string "<Super>" doesn't appear to be functioning for me. If I change <Super> to <Ctrl>, I can use Ctrl + D to show desktop, and I can then type the letter D without it hiding every window from me. 

Further evidence <Super> isn't working for me, if I change Metacity's "panel_run_dialog" global key binding from "<Alt>F2" to "<Super>F2" I bring up the run dialog by hitting F2 alone.

WORKAROUND
Change the system's "show desktop" keystroke. Here are the steps.

1) Alt+F2
2) gconf-editor
3) /->app->metacity->global_keybindings
4) Change the assigned keystroke for show_desktop from "<Super>d" to "<Ctrl>d" or "<Ctrl><Alt>d" or "disabled"

If someone finds this worthy of submitting a bug ticket, please let me know so I can follow it. Thanks.

Ed

Can I set this option for all users on the mashine ?

---

### Post by Monery on 2011-09-07
I have installed the minimum Gnome GUI on Ubuntu 11.04 server for various reasons, but I am having this problem with both rdesktop on my Linux Mint Laptop as well as the Win 7 Pro Remote Desktop software.

---

### Post by phweda on 2011-09-22
> **ecadman said:**
> PROBLEM
While connecting over Xrdp, hitting the "D" key alone hides all my windows and shows the desktop. This is problematic since I often wish to type words containing at least one "D" in it. In case anyone else is having this problem, I've wrestled through it and offer this help.
 
I'm using Ubuntu 10.10 Maverick Meercat and connecting via Xrdp. I only have this problem when connecting remotely.
 
APPARENT CAUSE
I don't pretend to know for sure, but the problem appears to be that the remote connection is flubbing Metacity's "<Super>d" binding for the "show desktop" command. More precisely, the string "<Super>" doesn't appear to be functioning for me. If I change <Super> to <Ctrl>, I can use Ctrl + D to show desktop, and I can then type the letter D without it hiding every window from me. 
 
Further evidence <Super> isn't working for me, if I change Metacity's "panel_run_dialog" global key binding from "<Alt>F2" to "<Super>F2" I bring up the run dialog by hitting F2 alone.
 
WORKAROUND
Change the system's "show desktop" keystroke. Here are the steps.
 
1) Alt+F2
2) gconf-editor
3) /->app->metacity->global_keybindings
4) Change the assigned keystroke for show_desktop from "<Super>d" to "<Ctrl>d" or "<Ctrl><Alt>d" or "disabled"
 
If someone finds this worthy of submitting a bug ticket, please let me know so I can follow it. Thanks.
 
Ed
 
Still there in 11.04. Thanks Ed for the workaround. BTW couldn't do this fix remotely cause of the 'd' in 'gconf-editor' ;)

---

### Post by captainentropy on 2011-11-10
Just encountered this nonsense too using remote desktop. However, it only appeared when I made a second vnc connection (~$vncserver ---> *servername:2*). 
 
The key mappings are found under System->Preferences->Keyboard Shortcuts just like laperouse said. I changed the mapping to something absurd since I'll never use it. 
 
No need for complicated workarounds: System->Preferences->Keyboard Shortcuts
 
Thanks where the fix is.
 
Note, this only started happening after an upgrade to 10.10. The keymap in the servername:1 connection did NOT have the same problem mapping. I'm guessing this is some kind of bug...

---

### Post by bell1996 on 2011-12-10
This solved my problem. Just mapped the "hide all windows" from "d" to "ALT-D".

---

### Post by ericinwisconsin on 2011-12-15
I had the same issue with a server running 11.10. Since I don't have physical access to the device, it was a major pain. Especially since "d" is in the word "admin". It made using Firefox (remotely) to access a website very frustrating.

Thanks for the workaround!

---

### Post by Xfool on 2012-03-30
> **AtesComp said:**
> Also being plagued by the inane and obtuse use of the "d" key via remote login, I troweled  upon the black earth a little deeper.

Using "gconftool-2", I traveled down the structured tree to light upon the branch "/apps/metacity/global_keybindings" and found the "show_desktop" item. Lo, the value appears as "<Super>d".  With apparent resolve, the poorly designed program is left bewildered as to the use of "<Super>" and randomly decide for itself to apparently ignore "<Super>" and select the "d" key. Unbeknownst to the astute end-user, the lowly "d" key has suddenly become his bane forevermore.

I protest! An error I say! I banish thee to the deepest pit of hell!
Changing this does not one any good fortune, sudo or not!

To correct heinous error, edit the swine of a file "/var/lib/gconf/debian.defaults/%gconf-tree.xml" and set the "show_desktop"s stringvalue to "Disabled" or whatever your humble preference. A trick upon this treat is to actually make entry of the word "Disabled" as it contains a "d". The astute reader shall quickly note the use of the "delete" key on "&lt;Super&gt", enter "isable", and use the existing "d".  No longer shall each user need concern themselves with prior given solutions henceforth.

My given solution requires a logout/login.

Live well hence forth for all user logins thereafter. I fare thee anon. ):P

Dude! That works!

---

### Post by memius on 2012-04-30
i have the same problem, but i'm not logged in remotely.

i'm simply running ubuntu 11.10 on my home machine.

does this mean someone _else_ is remotely logged in?

---

### Post by JJake on 2012-08-06
> **AtesComp said:**
> To correct heinous error, edit the swine of a file "/var/lib/gconf/debian.defaults/%gconf-tree.xml" and set the "show_desktop"s stringvalue to "Disabled" or whatever your humble preference. A trick upon this treat is to actually make entry of the word "Disabled" as it contains a "d". The astute reader shall quickly note the use of the "delete" key on "&lt;Super&gt", enter "isable", and use the existing "d".  No longer shall each user need concern themselves with prior given solutions henceforth.

My given solution requires a logout/login.

This solution worked for me when the others did not.  Thank you for posting this!

---

