---
title: "Alt-Tab No Longer Includes &quot;Home&quot;"
date: 2009-08-01
forum: Desktop Environments
---

### Post by techstop on 2009-08-01
I'm running UNR (Jaunty) on a Dell Mini 9, and am (mostly) very happy. Something that I liked in Intrepid was that when pressing Alt-Tab to switch between windows, there was an icon included for "Home" or the Desktop. It was an easy way to get to various folders, shortcuts, open programs etc.

It seems in Jaunty, Alt-Tab only includes open windows, not Home. How can I get it to revert to the old behaviour where Home is included with Alt-Tab?

I don't want to create a new keyboard shortcut to show the desktop either, I just want the old Alt-Tab behaviour back.

Anyone?

---

### Post by techstop on 2009-08-03
Bump?

---

### Post by Copernicus1234 on 2009-08-03
Do you know what CompizConfig plugin you were using? You probably had a specific setting for it that can easily be set back to the way it was, but question is which plugin it was.

For example, I use Scale plugin connected to the Alt-Tab key and the Ring Switcher connected to the WindowsKey+Tab combination. You probably used something else. Check out the plugins and see if you find which one it was.

---

### Post by techstop on 2009-08-03
> **Copernicus1234 said:**
> Do you know what CompizConfig plugin you were using? You probably had a specific setting for it that can easily be set back to the way it was, but question is which plugin it was.

For example, I use Scale plugin connected to the Alt-Tab key and the Ring Switcher connected to the WindowsKey+Tab combination. You probably used something else. Check out the plugins and see if you find which one it was.

I'm not using Compiz as I'm using UNR which is not compatible.

It's an issue with UNR. I think previously the netbook-launcher was patched to give "Home" or "Desktop" with Alt-Tab, but it's not patched in Jaunty.

---

### Post by approaching on 2009-08-04
so is it that UNR moved to jaunty and now that patch they made doesn't matter? (bump and clarification)

---

### Post by techstop on 2009-08-04
> **approaching said:**
> so is it that UNR moved to jaunty and now that patch they made doesn't matter? (bump and clarification)

From what I can gather, the default is not to include "desktop" in Alt-Tab. In previous distro releases (eg Hardy, Intrepid), this was patched to include the functionality. In Jaunty however, it is not.

See here for example (this applies to Hardy);

[https://wiki.ubuntu.com/UNR/Installation/Hard](https://wiki.ubuntu.com/UNR/Installation/Hard)

> The ppa contains an updated version of metacity which contains some useful patches and bugfixes:

    * Add the desktop to Alt+Tab

I might poke around in gconf-editor when I get home to see if there is an option available.

---

### Post by techstop on 2009-08-12
BUMP! Anyone?

---

### Post by Katalog on 2009-08-12
I don't have an answer (I use UNR also, but don't use the funcitonality you are referring to), but I do have a couple of suggestions. 1. File a bug report requesting they re-introduce the feature and/or 2. submit it as a suggestion on Brainstorm. 

That's the best advice I can give you (and also what I do) - if you can't get an answer, become the squeaky wheel. Chances are if there are enough other people who are as unhappy with this as you are you'll end up getting the grease.

---

