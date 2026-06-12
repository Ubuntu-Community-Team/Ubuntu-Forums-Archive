---
title: "Remove Ubuntu logo from screen"
date: 2014-05-30
forum: Desktop Environments
---

### Post by yamel3 on 2014-05-30
Okay, I admit the title is just click bait.

I can't figure out how to remove the words 'ubuntu 14.04 LTS' from my desktop. Changing wallpapers doesn't make it go away. It's only present on the unity desktop. It's a tiny nag, but I just want it to be clean.

Thanks for any advice you can provide!

---

### Post by mcduck on 2014-05-30
That sounds like a strange problem. Could you perhaps give a screenshot of what it looks like?

---

### Post by yamel3 on 2014-05-30
Sure. You mean, everyone doesn't have this in the bottom left corner of the screen? It wasn't there in 13.10 on my last laptop.

[ATTACH=CONFIG]253605[/ATTACH]

Thanks!

---

### Post by kansasnoob on 2014-05-30
I only get that on the login screen, are you using lightdm?

---

### Post by deadflowr on 2014-05-30
I gave this title a more proper title.

---

### Post by yamel3 on 2014-05-30
I think so. At least, I see in the Synaptic Package Manager that lightdm is installed.

---

### Post by mcduck on 2014-05-30
> **mcduck said:**
> That sounds like a strange problem. Could you perhaps give a screenshot of what it looks like?

Yeah,that looks like the text LightDM overlays on the background in the login screen, but it's definitely not supposed to be there once you get to the desktop. If it would disappear when changing a wallpaper I'd count it as some kind of graphics glitch, but since it stays even after that it must be something else.

Also from what I can see in the small screenshot it *doesn't* have the dot grid that's also part of the LightDM overlay, which makes things even more strange. :o

---

### Post by yamel3 on 2014-05-30
Right. The dot grid goes away on login.

---

### Post by bapoumba on 2014-05-30
Does it still appear if you make up a new user ?

---

### Post by yamel3 on 2014-05-30
> **bapoumba said:**
> Does it still appear if you make up a new user ?

Just created a 'guest' user and the logo text appears on that account, too.

---

### Post by bapoumba on 2014-05-30
> **yamel3 said:**
> Just created a 'guest' user and the logo text appears on that account, too.

Hmm, is this an upgrade or a fresh install ? Which Ubuntu flavor are you using ?

---

### Post by mcduck on 2014-05-30
I wonder if it has something to do with the new lock screen mechanism. What happens if you remove the logo text from the lock screen:
```
gsettings set com.canonical.unity-greeter logo ""
```
try locking the screen and unlocking again after running the command. Does it make any difference?

To reset the value back to default you can just run this:
```
gsettings reset com.canonical.unity-greeter logo
```
(Either way I'm not sure how the unity-greeter could possibly end drawing the logo while on desktop, but at least that's something to try...)

edit: Actually, no matter what's causing it, since we know what file is used to draw that, there's a easy way to hide the problem. Just renaming the image file would remove it from login screen *and* the desktop. Although I'm not really into hiding symptoms instead of fixing the actual problems, as there probably is something else broken and that might cause other issues outside of just the most visible one... But in case nothing else works, running "*sudo mv /usr/share/unity-greeter/logo.png /usr/share/unity-greeter/logo.png.backup*" should at least get the text off the desktop.

---

### Post by papibe on 2014-05-30
Hi yamel3.

Could you open a terminal, run this command, and post back the output (you can copy/paste the text)?
```
find /etc/lightdm/ -type f -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

---

### Post by yamel3 on 2014-05-30
> **bapoumba said:**
> Hmm, is this an upgrade or a fresh install ? Which Ubuntu flavor are you using ?

This is a fresh install on a new laptop. ~3 weeks old, basic Unity. I do have the XFCE environment installed, as well, but this logo does not appear when I log into it.

---

### Post by yamel3 on 2014-05-30
> **mcduck said:**
> I wonder if it has something to do with the new lock screen mechanism. What happens if you remove the logo text from the lock screen:
```
gsettings set com.canonical.unity-greeter logo ""
```
try locking the screen and unlocking again after running the command. Does it make any difference?

To reset the value back to default you can just run this:
```
gsettings reset com.canonical.unity-greeter logo
```
(Either way I'm not sure how the unity-greeter could possibly end drawing the logo while on desktop, but at least that's something to try...)

edit: Actually, no matter what's causing it, since we know what file is used to draw that, there's a easy way to hide the problem. Just renaming the image file would remove it from login screen *and* the desktop. Although I'm not really into hiding symptoms instead of fixing the actual problems, as there probably is something else broken and that might cause other issues outside of just the most visible one... But in case nothing else works, running "*sudo mv /usr/share/unity-greeter/logo.png /usr/share/unity-greeter/logo.png.backup*" should at least get the text off the desktop.

Okay, this makes it a little crazier. I ran that first script and locked the screen. The logo was not on the lock screen. I logged back in and there it was on the desktop. I logged out and there it was on the login screen. Your idea to rename the file would surely work, but now I'm just really curious to know why it's doing this.

Thanks!

---

### Post by yamel3 on 2014-05-30
> **papibe said:**
> Hi yamel3.

Could you open a terminal, run this command, and post back the output (you can copy/paste the text)?
```
find /etc/lightdm/ -type f -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```
Regards.

Here's what I get. I don't know what it's trying to tell me, though.
```
     1    #
     2    # User accounts configuration
     3    #
     4    # NOTE: If you have AccountsService installed on your system, then LightDM will
     5    # use this instead and these settings will be ignored
     6    #
     7    # minimum-uid = Minimum UID required to be shown in greeter
     8    # hidden-users = Users that are not shown to the user
     9    # hidden-shells = Shells that indicate a user cannot login
    10    #
    11    [UserAccounts]
    12    minimum-uid=500
    13    hidden-users=nobody nobody4 noaccess
    14    hidden-shells=/bin/false /usr/sbin/nologin


```

Hope that helps. Thanks!

---

### Post by grumblebum2 on 2014-05-31
This logo appears when I stop nautilus from drawing the desktop.
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] **gsettings get org.gnome.desktop.background show-desktop-icons**
false
```

Reset to default...
```
gsettings reset org.gnome.desktop.background show-desktop-icons
```

---

