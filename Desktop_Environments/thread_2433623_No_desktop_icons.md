---
title: "No desktop icons"
date: 2019-12-22
forum: Desktop Environments
---

### Post by jasonmili on 2019-12-22
My system is Ubuntu 18.04.3 LTS with the default (Ubuntu) Desktop. I have been through many updates, and (since I don't remember when) I have never had desktop icons. However, all other users' desktops are absolutely normal, and new users also have icons. This has become irritating now, and I want to take my desktop icons back. Furthermore, when I right click on Desktop I do not get all options other users get, but I only get the following: "1) Change background, 2) Screen Settings, 3) Settings" whereas in other users they get "1) New Folder, 2) Paste, 3) Select All, 4) Open Terminal" and 2-3 more options too. So, something is clearly not working correctly on the desktop... Probably the app responsible for drawing it, along with right click options?

I have already tried many things, none of which worked, and that's why I am here:

1) Tried gnome-tweaks --> Desktop --> Show Icons
2) Tried dconf reset, alongside other commands described here: [https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](https://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears) (even though that is not my problem exactly, because on my user Dash appears normally, Activities appear normally, only Desktop Icons do not show)
3) Tried moving all files from inside the "Desktop" folder in another directory, outside Desktop, rebooted, and still when I additionally create a file inside the Desktop folder, it doesn't appear on my visible desktop.

---

### Post by CatKiller on 2019-12-22
18.04 uses Gnome rather than Unity. Gnome isn't capable (any more) of having icons on the desktop. You need to install an extension to get that functionality. I believe the extension is called "desktop icons."

---

### Post by deadflowr on 2019-12-22
> **CatKiller said:**
> 18.04 uses Gnome rather than Unity. Gnome isn't capable (any more) of having icons on the desktop. You need to install an extension to get that functionality. I believe the extension is called "desktop icons."

18.04 still can have icons.
It's a change to new nautilus file manager that removes the ability.
Which only came with Ubuntu 19.(well either release, as I cannot remember which 19.04 or 19.10)

The issue seems to be something particular to the user's settings more than a system issue.

> Furthermore, when I right click on Desktop I do not get all options other users get, but I only get the following: . I
What does that mean? 
I cannot tell if it means you see nothing or if more info was supposed to be posted but wasn't.

Sorry can't help much atm as i'm baffled as well.
Something is stuck in my head about what's happening.
But I cannot remember what.
It is familiar, though.

I think the last time someone had an issue much like this they just created a new user and moved their files over to the new users home.
(And by move I mean only move the non-hidden folders like Videos and Pictures and Documents, etc etc.
Since user configurations settings are in the hidden folders, moving those would probably just move the problems as well)
Of course this is not a particularly useful or helpful approach, but it's an option.

---

### Post by Dennis N on 2019-12-22
> 18.04 still can have icons. It's a change to new nautilus file manager that removes the ability. Which only came with Ubuntu 19.(well either release, as I cannot remember which 19.04 or 19.10)

_Some observations:_

Ubuntu 19.04 and 19.10 can also display Desktop icons. I put a file in the Desktop folder and it also appears as an icon on the Desktop itself. I checked this in both releases. The Extension "Desktop Icons" could be what enables this*, but Desktop Icons display even with the extension switch turned OFF (but extension still installed), so I'm not sure. I didn't explore this further*.

One thing that's useful is that the extension enables the Trash and Home Folder Icons on the Desktop, and you can turn those (but not file icons) on and off from its configuration options. So it has this going for it. Also, the extension allows changing the size of icons.

* tested later, and found it's necessary

---

### Post by jasonmili on 2019-12-22
> **deadflowr said:**
> 
What does that mean? 
I cannot tell if it means you see nothing or if more info was supposed to be posted but wasn't.


You are absolutely right, I am sorry, it was cut off somehow. Here is what I wanted to say: "1) Change background, 2) Screen Settings, 3) Settings" whereas in other users they get "1) New Folder, 2) Paste, 3) Select All, 4) Open Terminal" and 2-3 more options too. So, something is clearly not working correctly on the desktop... Probably the app responsible for drawing it, along with right click options?

Also, moving to a new user (which indeed shows desktop icons, I have tested that) is not an option for me, as I have important settings for many user-configured apps to preserve.

---

### Post by Dennis N on 2019-12-24
> Here is what I wanted to say: "1) Change background, 2) Screen Settings, 3) Settings" whereas in other users they get "1) New Folder, 2) Paste, 3) Select All, 4) Open Terminal" and 2-3 more options too. So, something is clearly not working correctly on the desktop... Probably the app responsible for drawing it, along with right click options?

No, the menu choices are different because of the "Desktop Icons" gnome-extension. The users with the 5 additional options have it installed, but the user with just 3 options doesn't have it installed.

The attached images &#8681; show menu with and without the extension (and without the extension, NO desktop icons will display).

---

### Post by jasonmili on 2019-12-24
I can't see how to install it, though. Locating various tutorials through the internet, I have found that I needed to install gnome-shell-extension-desktop-icons but this package is said by apt to be "unable to be traced". Which is kind of logical I guess, since I have Ubuntu 18.04.3 LTS, not 19-series. So, how do I install/enable this extension on my OS, then? (I have also installed gnome-shell-extensions)

Actually, now that I have done my research, it seems that on Ubuntu 18.04 there is still the old version of Nautilus installed by default, which should provide desktop icons. So, my guess is that on my system, this is broken. How can I view what might be wrong with the desktop icons from Nautilus?

---

### Post by vanadium on 2019-12-24
In Ubuntu 18.04.3, it is still the file manager "Nautilus" that provides desktop icons. So do not look into installing an extension, but into ways to turn desktop icons on, or to first have nautilus setup such that it takes care of the desktop. As I do not have 18.04 myself, I cannot be more specific at this time.

---

### Post by Dennis N on 2019-12-24
Sorry - post #6 relates to Ubuntu 19.04 or 19.10.  In Ubuntu 18.04, one can turn them off and on using the **dconf-editor** utility. In dconf-editor, Navigate to org > gnome > desktop > background and look for show-desktop-icons at the bottom (screenshot). This also changes the desktop menu. Menu screenshots (icons on and icons off) attached.

---

### Post by jasonmili on 2019-12-24
Unfortunately this didn't work. It was already on, tried setting it to off, rebooting, setting back on, rebooting, again the same situation... What's wrong with my user's Nautilus?

---

### Post by mörgæs on 2019-12-26
If adding desktop icons and other kinds of customisations are important then I suggest that you choose Xubuntu rather than Ubuntu next time you install.
Not that is solves your problem now but it prevents future ones.

---

