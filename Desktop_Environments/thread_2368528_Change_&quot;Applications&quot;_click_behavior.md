---
title: "Change &quot;Applications&quot; click behavior?"
date: 2017-08-11
forum: Desktop Environments
---

### Post by a.curious.guy on 2017-08-11
I really should be posting this in the new users area but being that it is specific to Gnome 3 I thought Desktop Environments might be more accurate.

I have recently installed Ubuntu 17.04 with the Gnome 3 desktop. There is something that I would like to change. There is an "Applications" button/shortcut/something in the top left. When you click it (or hit the Windows key) it launches a side menu. On that side menu there is a button/icon with 9 dots. If you click that you get the list of Recent Applications (with the option of viewing All Applications). 

Is there a way to have the clicking of the top-left "Applications" (word, not the 9 buttons) launch the list of Recent Applications (or All Applications). Basically I want to have the main Applications button not show the left-side dock.

Is this possible? Is it easily explained to a linux/gnome user? Thank you to anyone that can help.

ACG

---

### Post by Frogs Hair on 2017-08-12
Hello and Welcome


There are extensions that can change behavior in the gnome shell available in the repository. I would start with the standard package and after logging out and back in you can view them in the gnome tweak tool . You can replace the activities button with a standard menu. Dash to dock is a useful extension as well.


```
sudo apt install gnome-shell-extensions 

```

[https://extensions.gnome.org](https://extensions.gnome.org)

---

### Post by again? on 2017-08-12
Adding to Frogs Hair's post, there is an extension that will open the overlay in application view.
You can use Super+s for window spread.
[Start Overlay in Application View]("https://extensions.gnome.org/extension/1198/start-overlay-in-application-view/")

This is a list of some of the extensions I use.
[Dash to Dock]("https://extensions.gnome.org/extension/307/dash-to-dock/")
[CustomCorner]("https://extensions.gnome.org/extension/1037/customcorner/")
[Pixel Saver]("https://extensions.gnome.org/extension/723/pixel-saver/")
[TopIcons Plus]("https://extensions.gnome.org/extension/1031/topicons/")

Desktop with permanent dock and a "Show Applications" launcher at the top.

---

