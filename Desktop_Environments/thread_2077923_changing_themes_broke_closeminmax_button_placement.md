---
title: "changing themes broke close/min/max button placement"
date: 2012-10-29
forum: Desktop Environments
---

### Post by gamblor01 on 2012-10-29
I recently upgraded this system to 12.10 from 12.04.  I always use the default close/min/max button on the left side of the window.  After installing 12.10 I decided to play around with my window theme to see if anything had changed that I wanted to move to (currently I am using radiance).

While cycling through the themes I noticed that the close/min/max buttons moved to the right side of the windows.  That's fine -- I have had this problem in the past so I simply checked in both gconf-editor and dconf-editor and found the system wrong in dconf-editor.

I fixed the settings in dconf-editor but oddly enough it worked for all windows ***EXCEPT*** Chromium still doesn't seem to work.  I have attached a screenshot that proves the settings in both gconf and dconf are correct.  You can actually see that the buttons are properly set for both of those windows, but Chromium is still on the right.

Any ideas?

---

### Post by Frogs Hair on 2012-10-29
I know Chrome has the option to use the GTK title bar or the Chrome theme title bar. If using a Chrome theme the buttons appear on the right. You can check this in browser settings > appearance .

---

### Post by grahammechanical on 2012-10-29
And there was I wondering why Chromium now had its buttons on the right. We have to tick the box Use system title bars and borders.

---

### Post by gamblor01 on 2012-10-29
> **Frogs Hair said:**
> I know Chrome has the option to use the GTK title bar or the Chrome theme title bar. If using a Chrome theme the buttons appear on the right. You can check this in browser settings > appearance .

Thanks for the reply but I don't think this statement is accurate.  I have been using Chromium for a while now (since 11.04) and I can assure you that even with a theme set the buttons have *ALWAYS* been on the left side.  I can take a screenshot of my 12.10 system at home and post it -- unless Chromium just recently made this change.  I will check when I get home tonight.

Switching to use the GTK title bar DOES move them to the left, but disabling that option moves them back to the right and it should not -- at least that is not how it has worked for like 2 years, and that is not how my desktop at home works (though again, I will check tonight).

Just FYI you can right-click directly on the title bar and toggle the GTK title bar on and off.  You don't have to go through menu > settings > appearance.  ;)


Assuming my home system still functions the "correct" way and Chromium hasn't changed this to enforce the buttons on the right when a theme is active and non-GTK title bars are used...any other ideas what to check?

Thanks!

---

### Post by Frogs Hair on 2012-10-29
I am aware of the right click. I use _Chrome_ and the button position in when using the The Chrome theme title bar has (Always) been on the right since 11.10.That is why I wrote Chrome not Chromium . Chromium from the repository is modified for Ubuntu.

---

### Post by gamblor01 on 2012-10-29
> **Frogs Hair said:**
> I am aware of the right click. I use _Chrome_ and the button position in when using the The Chrome theme title bar has (Always) been on the right since 11.10.That is why I wrote Chrome not Chromium . Chromium from the repository is modified for Ubuntu.

This is really strange but it seems like they must have just implemented this for Chromium as well.  I just checked on my home system and it's on the right side now too.  :(


Seems like a bug to me as it is not following the default layout any longer.  I swear this is something that just changed.  I have been using 11.04, 11.10, 12.04, and 12.10 -- this is something that just happened over this weekend for me.  They have always been on the left.

I guess I can report it against the chromium-browser package and see what they say.  Thanks!

---

