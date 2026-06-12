---
title: "Changing Windows - loses focus"
date: 2011-05-07
forum: Desktop Environments
---

### Post by lcdrovers on 2011-05-07
This is quite a strange problem. I've just recently upgraded to 11.04, and to make a long story short, I didn't like Unity, and wanted to go back to GNOME. Now, because I'm an idiot and didn't notice the option to boot into the "Ubuntu Classic" desktop, I thought it would be a good idea to ```
sudo apt-get purge unity*
```

Words cannot express how much I facepalmed when I realized what I had done. Luckily, though, I was able to get the Ubuntu Classic (GNOME) desktop to load, and everything seems to work fine, even compiz. The problem I have is that when I use Alt+Tab in any capacity, the window appears to lose focus, as even when a window has focus on it, when I click anything or use the keyboard, it doesn't show any change until I minimize and restore the window. If I click on the application on the bottom bar, this problem does not occur. Here are some screenshots to show you what I'm talking about (I realize they're a bit fuzzy; my screen's resolution is really huge and there were some problems when scaling down the images):
[IMG]http://i.imgur.com/Aj1db.png[/IMG]
The above is when I Alt+Tabbed to gedit from Chrome. I then spammed the keyboard, but nothing was shown on the window, until I minimized gedit and restored it, showing this:
[IMG]http://i.imgur.com/diVKH.png[/IMG]
As you can see, it doesn't show any of the text I input until I minimized and restored the window. Here's another example with Chrome:
[IMG]http://i.imgur.com/C8tao.png[/IMG]
I Alt+Tabbed to Chrome, then pressed Ctrl+T to open a New Tab, but it didn't show any change in the window (notice, however, that it shows "New Tab" in the titlebar at the bottom of the screen). After minimizing and restoring Chrome, it showed:
[IMG]http://i.imgur.com/453fD.jpg[/IMG]

I've also been unable to change the order of application windows in the bar at the bottom of the screen by moving their titlebars around, as I was able to do previously on the GNOME desktop before upgrading. I don't know whether that's because I purged Unity, or because of the same thing that's messing up Alt+Tab.

I have no clue what is wrong, and I'd appreciate any help I can get, because it gets really annoying have to click on the application to switch to it, rather than just using Alt+Tab.

EDIT: The images are displaying really strangely, and I don't know how to fix that, so do forgive me for stretching your screen. Is there a form of hide tags on these forums?

EDIT2: Fixed.

---

### Post by Copper Bezel on 2011-05-07
For the images, if you don't want to use GIMP, try gthumb - cropping and resizing are pretty straightforward, although the "edit" mode is annoyingly hidden (as the E key has to be pressed to show the tool pane.)

Now, to clarify, you're saying that the windows you tab to *are* in fact focused (in that they take the text input) but they're not refreshing to show that any change has happened until you minimize and restore them?

This is a little obvious, but did you check to see what you actually removed with that command? It's possible that something you needed got removed along with the things you didn't. I really wouldn't know beyond that - I've never really seen a window "stuck" like that, let alone seen forcing the window to remap fix it.

And you said you're using Compiz rather than Metacity, right?

---

### Post by lcdrovers on 2011-05-07
I fixed the images, although I realize they're still pretty huge, sorry for that.

> Now, to clarify, you're saying that the windows you tab to are in fact focused (in that they take the text input) but they're not refreshing to show that any change has happened until you minimize and restore them?
That is precisely what is occuring, yes.

> This is a little obvious, but did you check to see what you actually removed with that command? It's possible that something you needed got removed along with the things you didn't. I really wouldn't know beyond that - I've never really seen a window "stuck" like that, let alone seen forcing the window to remap fix it.
I don't know how I would view what I removed with that command; I don't know what is installed by default in the Unity that comes with the upgrade, and I don't believe there is a "history" viewer or something in synaptic, or any way to view what precisely I removed with the use of that command.

> And you said you're using Compiz rather than Metacity, right?
This is quite peculiar. To check this, I ran fusion-icon (which I already had installed), and it said I was using metacity. Using fusion-icon, I changed the window manager to compiz, then I restarted. Even when using compiz over metacity, the same effect remained.

---

### Post by Copper Bezel on 2011-05-07
Yeah, I would have expected that it would happen with one or the other, but not both.

> I don't know how I would view what I removed with that command; I don't know what is installed by default in the Unity that comes with the upgrade, and I don't believe there is a "history" viewer or something in synaptic, or any way to view what precisely I removed with the use of that command.

Actually, there is one in Synaptic's File menu, but it only applies to changes made *within* Synaptic. You do, however, have this file: /var/log/apt/history.log . If the changes happened before the start date, you can navigate to that folder to access older logs. It's probably best if we take a look at that.

---

### Post by lcdrovers on 2011-05-07
I believe I've found the relevant information:
```
Start-Date: 2011-04-30  11:27:55
Commandline: apt-get purge unity*
Purge: ubuntu-desktop:amd64 (1.220), unity:amd64 (3.8.10-0ubuntu2), junit4:amd64 (4.8.2-2), libunity4:amd64 (3.8.4-0ubuntu1), evolution-indicator:amd64 (0.2.14-0ubuntu4), libnb-java4-java:amd64 (6.9-0ubuntu2), junit:amd64 (3.8.2-4), unity-common:amd64 (3.8.10-0ubuntu2), vim-latexsuite:amd64 (20100129-2), libnb-platform-devel-java:amd64 (6.9-0ubuntu2), empathy:amd64 (2.34.0-0ubuntu3), unity-place-applications:amd64 (0.2.46-0ubuntu3), libunity-misc0:amd64 (0.2.1-0ubuntu2), unity-place-files:amd64 (0.5.46-0ubuntu5), ruby1.8:amd64 (1.8.7.302-2), libnb-ide13-java:amd64 (6.9-0ubuntu2), ruby:amd64 (4.5), libnb-apisupport2-java:amd64 (6.9-0ubuntu2), vim-gnome:amd64 (7.3.035+hg~8fdc12103333-1ubuntu7), netbeans:amd64 (6.9-0ubuntu2), unity-asset-pool:amd64 (0.8.20-0ubuntu2), libruby1.8:amd64 (1.8.7.302-2), vim-addon-manager:amd64 (0.4.3), libnb-platform12-java:amd64 (6.9-0ubuntu2)
End-Date: 2011-04-30  11:28:47
```

I don't know the significance of any of these packages, so I don't know how effective it will be to reinstall any of them. Do you suggest reinstalling all of them?

---

### Post by Copper Bezel on 2011-05-07
Actually, just try installing the first one, there, ubuntu-desktop, which is a meta-package that installs all the necessary components of the default environment. It'll rake in a number of dependencies, one of which (we hope) will be the one involved.

---

### Post by lcdrovers on 2011-05-07
I installed ubuntu-desktop and restarted, but it didn't appear to change anything.

---

