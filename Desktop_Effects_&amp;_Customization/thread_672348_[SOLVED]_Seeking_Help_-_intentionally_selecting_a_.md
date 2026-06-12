---
title: "[SOLVED] Seeking Help - intentionally selecting a different root theme?"
date: 2008-01-19
forum: Desktop Effects &amp; Customization
---

### Post by dustigroove on 2008-01-19
To preface: I have searched through the forums and looked for the answer to my question and there are a ton of "How to get your root theme to match your user theme" threads... I want the *opposite*, but with the ability to choose the theme root uses.

Basically I am looking to intentionally select a different theme for programs run as root. Any advice on how this can be accomplished?

---

### Post by rune0077 on 2008-01-19
Just a guess 'coz I've never tried it:

- Make a root account
- Log in as root
- Change the settings/appearances as you like

Can't see why that shouldn't work.

---

### Post by aysiu on 2008-01-19
> **rune0077 said:**
> Just a guess 'coz I've never tried it:

- Make a root account
- Log in as root
- Change the settings/appearances as you like

Can't see why that shouldn't work.
It might be possible if you run the command ```
gksudo gnome-appearance-properties
``` after Alt-F2 or in [the terminal](http://www.psychocats.net/ubuntu/terminal).

---

### Post by dustigroove on 2008-01-19
Thank you both for your suggestions, much appreciated. Unfortunately I was not able to select the theme used by root when logged in under my account with either suggestion.

Logging in as root allows me to change the theme as root, but reverts back when logged in as myself.

Trying to run the appearance program through gksudo when in my account throws up a nag that it can't run because there is an existing occurrence, settings will not be saved, yada-yada.

Any other things to try?

Thanks again!

---

### Post by rune0077 on 2008-01-19
Okay, let's try combining the two suggestions. Now that you have a root password, open a terminal and type 

```
su
```

Feed it your root password. Then:

```
gnome-appearance-properties
```

Well, it's worth a shot.

---

### Post by mik01aj on 2008-01-19
su doesn't work in ubuntu by default, you should type sudo -i instead ;>

And one more thing - you can start an X session without 'creating' a root account - just log out, press control-alt-f1, login as usual, then do this:
```
sudo -i
[type your password]
killall gdm
startx
```Well, maybe it's not the most 'elegant' solution but it works for me. :)

---

### Post by rune0077 on 2008-01-19
su works fine as soon as you have established a root password (which is the case here).

---

### Post by dustigroove on 2008-01-19
Just to reiterate, launching 'gnome-appearance-properties' while in an open session will not allow for a change of the root theme as there already is a settings manager instance open for the current user. The program opens after receiving the warning attached, and shows the theme that I selected when I had logged in as root, however the selected theme is not used. Something in the currently running appearance settings manager is overriding the root selection.

So changing the theme logged in as root does not work. Changing the theme by launching the appearance program via gksudo or under su also does not work. Grrrr... there has to be some way to do this, otherwise there would not be so many posts to do the opposite.

Perhaps I need to select a theme that is my home directory and not in /usr/share/themes/? Will fiddle some more now and check back in a bit...

---

### Post by aysiu on 2008-01-19
Try ```
gksudo gconf-editor
``` and going to Apps > Metacity > General > theme

---

### Post by rune0077 on 2008-01-19
Hmm, what happens if you kill the gnome-settings-manager? I'm betting it would crash your desktop or simply start right back up again, but even so, might give it a try. If killing the process won't work, maybe just try to stop it without shutting it down (all this is doable through the System Monitor). 

Or perhaps you just have to do it "the hard way", meaning "gksu nautilus" then go to theme-folder your root is currently using and replace it with the one you'll want to use (which would of course permanently delete the old theme, though, so don't do this if you want it back or available later on).

---

### Post by dustigroove on 2008-01-20
> **aysiu said:**
> Try ```
gksudo gconf-editor
``` and going to Apps > Metacity > General > theme

Thanks Aysiu and rune, unfortunately still no dice.

So far I've learned four main things (1) is that if you kill the gnome-settings-daemon or select a theme from your home directory while logged in as yourself, root owned apps will go back to the same default, grey gtk theme every time no matter what theme was selected by root.  (2) the gnome-settings-daemon restarts automatically and when it does it refreshes all window theming, applying the currently selected user theme to both user and root owned windows - unless said theme is located in your home directory in which case the cheery grey default theme just gets refreshed. and finally (3)... my head really hurts from digging around in my system to tweak this little customization that I want to make.

Soooo... I'll chip away at this again tomorrow as time permits. Thanks again guys.

Cheers

---

### Post by aysiu on 2008-01-20
You mentioned the outcome of killing the gnome-settings-daemon.

What happened when you changed the root theme with gconf-editor?

---

### Post by dustigroove on 2008-01-21
Nothing changed unfortunately when I made the gconf changes. I might be on a fruitless search... from searching around it appears this is a hard coded default when the system cannot find a proper theme. This is apparently what happens when a user selects a theme contained in their home directory - it doesn't so much use root's theme as it falls back to no theme because it is not properly aware of the theme directory.

Some interesting reading (well, perhaps only to me) within the bug report comments here:
[https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/24280](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/24280)

As I'm stubborn I'll persist with trying to find a solution, unfortunately I'm just a little less optimistic about it.

Cheers.

---

### Post by rune0077 on 2008-01-21
Do you think the only problem is the theme being in your home folder? Then you should just try moving the theme:

alt+F2
gksu nautilus

and move the theme from your home folder to /usr/share/themes

---

### Post by dustigroove on 2008-01-21
> **rune0077 said:**
> Do you think the only problem is the theme being in your home folder? Then you should just try moving the theme:

alt+F2
gksu nautilus

and move the theme from your home folder to /usr/share/themes

Unfortunately this is not what I am trying to do. I want the used theme to be the one in the users home directory and any non-user themed applications (the ones that default back to the ugly grey gtk theme when opened as su) to use a different theme. Making them all the same is trivial, making the themes different but *customizable* is what is proving difficult.

Cheers

---

### Post by aysiu on 2008-01-21
> **dustigroove said:**
> Unfortunately this is not what I am trying to do. I want the used theme to be the one in the users home directory and any non-user themed applications (the ones that default back to the ugly grey gtk theme when opened as su) to use a different theme. Making them all the same is trivial, making the themes different but *customizable* is what is proving difficult.

Cheers
rune0077 isn't saying to use the same theme. rune0077 is saying that the theme you're trying to choose should be in a universally available (not user-specific) location.

---

### Post by dustigroove on 2008-01-22
> **aysiu said:**
> rune0077 isn't saying to use the same theme. rune0077 is saying that the theme you're trying to choose should be in a universally available (not user-specific) location.

My mistake, I had interpreted his comment differently. I have tried setting the theme to something globally available as well as located in my local themes folder. Neither allows me to choose to theme windows opened as su.

It appears this [used to be feasible]("http://lifehacker.com/software/linux-tip/re+theme-your-sudo-applications-263153.php") under the gnome-theme-manager (it could be run as user or as su and would theme windows accordingly) but now with the gnome-appearance-properties utility it does not seem to function the same way.

From all my reading on this, it really seems that the separate theming was more of a side-effect than an intended "feature", and is now being fixed... too bad, I think that it would be a nice option to have.

---

