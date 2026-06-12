---
title: "I'd like to re-enable the scroll bars in the Unity desktop"
date: 2011-10-09
forum: Desktop Environments
---

### Post by Silverflyer on 2011-10-09
to replace the mac like scroll bars I have now in Macbuntu.  I am running 11.04 with Macbuntu on the Classic desktop.  Is this possible without screwing everything up?

Thank you.

---

### Post by Silverflyer on 2011-10-09
This is what is looks like now, I would like to remain just like this, without the big ugly blue scroll bar.

[URL="http://imageshack.us/photo/my-images/521/screenshotdxz.png/"]
[/URL]

---

### Post by Copper Bezel on 2011-10-09
Check if the package overlay-scrollbar is still installed. If it is, I *think* running this should fix it:

```
echo "export LIBOVERLAY_SCROLLBAR=1" | sudo tee /etc/X11/Xsession.d/80overlayscrollbars> /dev/null
```

There are a couple of ways to disable the new scrollbars, and I don't know which way the MacBuntu script uses. Trouble is, I'm not certain whether or not the command above works - I've seen it with the value set to 0 to disable the scrollbars, but I don't have a file called 80overlayscrollbar at all, and they appear for me.

Edit: And I don't have a value set for "$LIBOVERLAY_SCROLLBAR" when I use echo on it, either. = /

---

### Post by Silverflyer on 2011-10-09
Before I go ahead and do that, is there a quick easy way to undo it if it breaks something?

I am a Linux noob, so please go easy on me.

---

### Post by Copper Bezel on 2011-10-09
= ) No problem. 

Installing the package overlay-scrollbar definitely won't break anything and can be reverted by removing the package. The other command, frankly, I don't know how it works. It comes from [_Tux Garage_]("http://www.tuxgarage.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html"), but there's no explanation of what's actually happening on the backend. It shouldn't break anything, but I wouldn't try it without checking if the overlay scrollbar package is still installed first.

You also might try switching to a different theme and seeing if it's something specified in the GTK ("Window Control") theme itself. If the scrollbars switch back when you switch the theme, we can figure out how they've done that, too.

So check those two things first - no chance of breaking anything with those.

---

### Post by Krytarik on 2011-10-09
> **Copper Bezel said:**
> The other command, frankly, I don't know how it works. It comes from [_Tux Garage_]("http://www.tuxgarage.com/2011/04/disable-overlay-scrollbars-in-ubuntu.html"), but there's no explanation of what's actually happening on the backend.
The file "/etc/X11/Xsession.d/80overlayscrollbars" isn't there by default. Creating those is intended to override the default setting, which is 'Overlay Scrollbars enabled'. So, if you want to revert that later, you can just remove that file again. (Just added this note to our post.)

Setting the value of "LIBOVERLAY_SCROLLBAR" to "1" through that file is possible, but as the default is 'Overlay Scrollbars enabled' anyway, it effectively won't change anything.

So +1 for checking if the package "overlay-scrollbar" is installed, and if default themes like "Ambiance" would use Overlay Scrollbars. But I'm quite sure the culprit for that lies in Macbuntu's theme settings. So, if you eventually need to head this way, try outcommenting the following line in the top of the file "/usr/share/themes/Macbuntu/gtk-2.0/gtkrc" and see how it goes:
```
include "scrollbar.rc"
```Note: I'm guessing Macbuntu installs its theme system-wide, into the above stated directory; if not, look out for "~/.themes" in your home directory. --- The funny thing, after checking its installer script, it apparently installs its theme into both of those directories. :D

Regards.

---

### Post by Silverflyer on 2011-10-09
well, if Synaptic package manager is the place to check to see if it is installed, this is what I got.

I am not sure how to outcomment something, is it the same as deleting that line in the text file?

---

### Post by Krytarik on 2011-10-09
> **Silverflyer said:**
> well, if Synaptic package manager is the place to check to see if it is installed, this is what I got.
Ok, check.

> **Silverflyer said:**
> I am not sure how to outcomment something.
Damn it, I was afraid of this, but I didn't know how to word the introducing sentence to make a code like this not contradict it :P :
```
# include "scrollbar.rc"
```

---

### Post by Silverflyer on 2011-10-09
I can open "/usr/share/themes/Macbuntu/gtk-2.0/gtkrc" and read it, but I can not edit it.

The odd thing is that the window that opens when I browse the file system, has the scroll bars from Unity, and not the Macbuntu scroll bars.

---

### Post by Krytarik on 2011-10-09
> **Silverflyer said:**
> I can open "/usr/share/themes/Macbuntu/gtk-2.0/gtkrc" and read it, but I can not edit it.
Ok, yet another obstacle ;) , run this instead:
```
gksudo gedit /usr/share/themes/Macbuntu/gtk-2.0/gtkrc
```
And have a look at this guide later:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

> **Silverflyer said:**
> The odd thing is that the window that opens when I browse the file system, has the scroll bars from Unity, and not the Macbuntu scroll bars.
Hmm, indeed unexpected; but it's still the same overall theme?

---

### Post by Copper Bezel on 2011-10-09
Silverflyer, can you confirm whether or not you see the Unity scrollbars in gedit, the text editor Krytarik just suggested using as well? There are a number of applications that don't support the new overlay scrollbars, and  I just noticed that Synaptic is one of them. Nautilus, gedit, and the Ubuntu Software Center all support them, but Synaptic, Banshee, and I think Firefox do not.

---

### Post by Silverflyer on 2011-10-09
I actually just had that thought myself, and was investigating it.  There are elements of the UI that do indeed use the new scroll bars.  Ubuntu Software Center being one of them, as are the file system windows.  I guess that leaves me with no options.  Bummer but I guess I can live with it.

Thanks for the help.

---

