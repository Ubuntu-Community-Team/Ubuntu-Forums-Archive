---
title: "Nautilus Action: QR Code to Clipboard Tutorial"
date: 2011-06-30
forum: Desktop Environments
---

### Post by BkkBonanza on 2011-06-30
I've created a quick and easy way to copy QR Codes to Clipboard.
Useful for pasting URL or BitCoin addresses into wherever...

Create a small script and make it executable,

nano barclip
chmod +x barclip

Paste this into barclip
```

#!/bin/bash
zbarimg -q --raw "$1" |xclip -selection c

```

You need two small packages for the QR decode and clipboard,
**sudo apt-get install zbar-tools xclip**

If you don't have Nautilus Actions then install that (very useful),
**sudo apt-get install nautilus-actions**

This gives you a nice gui tool for creating Actions to embed in the menus or mouse right click. 
It shows up on the menu System, Preferences.

Open Nautilus Actions, create a new Action.
For "Context Label" put "**Read QR Code to Clipboard**".

On the Command tab enter the path to your **/path/to/barclip** script.
For parameters enter **%f**.

On the Mimetypes tab, remove the "*" line and add the image types you want to match, say "**image/png**" and "**image/jpeg**".
This makes the item only show up for those file types (regardless of filename extension).

Click "**Save**" for the action.

Test it out. Let's say you see a QR code on the web. 
Drag it onto your desktop, right click it and choose "Read QR Code to Clipboard".

Go to some text entry field and right click, Paste. 
You should see the QR data pasted.

[IMG]http://chart.apis.google.com/chart?cht=qr&chs=120x120&chl=18yX7wW6ia219ebNZ57HCznXa98SUGPmop+[/IMG] Hint, Hint.

Hope this is useful for someone.

---

### Post by cnlohr on 2011-08-02
I was really happy to see ZBar did QR Codes, so happy I made this whole process much, much simpler with my new tool.  I made a little thing that hides up on the dock, when you click it, it searches the screen for QR Codes, sends them to ZBar, and overlays an outline with text telling you what it says... It also lets you copy any of the codes to the clipboard.

Anyone want to help me package-ify it?

[http://cnlohr.blogspot.com/2011/08/desktop-qr-code-reader-for-ubuntu.html](http://cnlohr.blogspot.com/2011/08/desktop-qr-code-reader-for-ubuntu.html)

---

