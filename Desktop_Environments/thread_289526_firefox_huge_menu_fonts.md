---
title: "firefox: huge menu fonts?"
date: 2006-10-31
forum: Desktop Environments
---

### Post by kawazu on 2006-10-31
Folks,

installed xubuntu 6.10 on my notebook yesterday and things work out well so far (made a switch from debian unstable...), except for one thing bugging me: Though most of the GTK2 - applications in the XFCE environment adhere to the global (desktop) font and theme settings, Firefox doesn't. 

Please have a look at the file attached. For now, it seems that no matter what I do, the firefox menu font always is more or less 2 pixels larger than the font in the rest of the applications.

Two short questions:
- Why? :o
- How can I get this changed?

What I tried so far, after looking through various ubuntu forums:
- dpkg-reconfigure fontconfig-config to enable autohinter and subpixel-hinting, disable bitmapped fonts;
- firefox about:config to enable xft stuff.

Anything else I forgot about this?

Thanks in advance for any hints!
Cheers,
Kris

---

### Post by souki on 2006-10-31
do you have a ".fonts.conf" in your home directory ?
if so, try to remove it, and restart your session

---

### Post by kawazu on 2006-10-31
Hi there, and at first thanks a lot for your hint. :)


> **souki said:**
> do you have a ".fonts.conf" in your home directory ?
if so, try to remove it, and restart your session

no. :( all I found is .fonts.cache-1 and .fontconfig - removing both and starting all over again so far didn't change anything.

---

### Post by dagnabit dang doohickey on 2006-10-31
How about trying this:
In your Font preference pane, change the application font size to anything other than what it is now, then close the pane. Open it up again and change it back to the size that you desire.

I ran into a situation with an app, I forget which one, where the app was not behaving properly according to how a *default* pref was set. So, I toggled the prefs check box, closed, and toggled back. That did the trick.

While this tip won't hurt to try, it's pretty much a shot in the dark. For a more heavy-handed firefox approach, you can mess with userChrome.css as this user did:
[http://www.ubuntuforums.org/showpost.php?p=1259120&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1259120&postcount=6)

---

### Post by kawazu on 2006-10-31
Hi there;

and also thanks for the hint... 

> **dagnabit dang doohickey said:**
> How about trying this:
In you Font preference pane, change the application font size to anything other than what it is now, then close the pane. Open it up again and change it back to the size that you desire....


Tried that, as well. For what I see, indeed the Firefox menu font changes as I switch global font size, but it always stays drastically bigger than, in example, the menu font in Thunderbird. :confused:

---

### Post by dagnabit dang doohickey on 2006-10-31
I've never used a Firefox theme and don't know if they're easily editable, but assuming you're using one, maybe that's where this problem is originating. Just a guess.

---

### Post by Klaudio on 2006-10-31
Hi,
have you already edited your /.mozilla/.../*profilename*/chrome/userChrome.css file?

There is a section where you find:

> * Make menu items in particular 15 pt instead of the default size:
 *
 * menupopup > * {
 *   font-size: 15pt !important
 * }
 */
/*

Maybe you have to look for another tag to copy and paste in this file (google helps you).

See you.

See you.

---

### Post by kawazu on 2006-10-31
Folks;

and first, thanks a lot for your hint. It seems, though, that an XFCE-specific error sort of messed things up (whyever this is to happen): I created a new user profile just to learn that, by default, everything is fine, all applications share the same font size.

However, the very moment I activate the "enable sub-pixel hinting" within the XFCE theme configuration tool, this seems to get messed up - beyond repair: Deactivating this doesn't switch the behaviour "back to old" but rather leaves most of the GTK2 fonts way too small (whyever this doesn't affect Firefox still is not clear to me). I had to remove most of the XFCE configuration in my $HOME to get over this... :/

Anyhow, thanks for all the hints :)
Bye,
Kris

---

