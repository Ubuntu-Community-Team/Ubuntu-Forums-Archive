---
title: "Disable Hot Corner Gnome Shell"
date: 2011-07-26
forum: Desktop Environments
---

### Post by MARP1961 on 2011-07-26
I think Gnome Shell is fantastic; but one thing has really annoyed me! The 'Hot Corner' at the top left of the screen launches the Overview Screen. This is fine in itself, but seems pointless when a click of the mouse on the 'Activities' tab or hitting the Superkey (Windows Key)on the keyboard does the same thing. Also when clicking near the top left corner it is very easy to inadvertently activate this hot corner which is annoying when you are in the middle of doing something.

I looked for a Gnome 3 extension to disable it but couldn't find one that works. 

Googling around has revealed a fix for this. See the post below:

---

### Post by MARP1961 on 2011-10-22
Just to update this information:

Now that Oneiric Ocelot is out, the line of code that needs to be altered to **disable the 'hot corner' in Gnome Shell** is in a different hidden folder. I have made a video showing you how to do this in 11.10. I wish someone smarter would write an extension for this to make the fix unnecessary.

Anyway, check this video out:
[http://www.youtube.com/watch?v=Xc1CpeIet6c]("http://www.youtube.com/watch?v=Xc1CpeIet6c")

 or the instructions on this website: [http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button]("http://askubuntu.com/questions/5573/how-do-you-disable-the-automatic-activation-of-gnome-shell-activities-button")

---

### Post by maizyRu on 2012-03-20
That extension helps me.

Installation:

```

mkdir -p ~/.local/share/gnome-shell/extensions
cd ~/.local/share/gnome-shell/extensions
git clone https://github.com/Ahrak/gnome-shell-extension-disable-hot-corners.git

```

Then activate it in gnome-tweak-tool

(Tested on Linux Mint 12 based on Ubuntu 11.10, GNOME Shell 3.2.2.1)

---

### Post by MARP1961 on 2012-03-20
**All Gnome Shell Users**
There** is** now an extension for this which only involves a couple of clicks. Navigate to the Gnome Shell Extensions Website and look through the 14 or so pages!

[https://extensions.gnome.org/#page=2&shell_version=3.2.1](https://extensions.gnome.org/#page=2&shell_version=3.2.1)

---

### Post by rpremuz on 2012-03-21
> **MARP1961 said:**
> 
[...] Navigate to the Gnome Shell Extensions Website and look through the 14 or so pages!

[https://extensions.gnome.org/#page=2&shell_version=3.2.1](https://extensions.gnome.org/#page=2&shell_version=3.2.1)

This is a funny instruction :-) Why didn't you provide the link to an extension?

I'd suggest the following extension:
[https://extensions.gnome.org/extension/100/remove-activies/](https://extensions.gnome.org/extension/100/remove-activies/)
(yes, it has a spelling mistake in the name).

---

