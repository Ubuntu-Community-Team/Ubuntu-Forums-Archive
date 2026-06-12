---
title: "&quot;Extract Here&quot;?"
date: 2007-04-22
forum: Desktop Environments
---

### Post by alexgieg on 2007-04-22
Hi! I have a question. I Ubuntu 6.10, right-clicking a zip (let's say, "filename.zip") file in Nautilus and selecting "Extract Here" would extract the files, well, here, meaning this folder where I (and the zip file) are. But in 7.04 it's creating a folder called "filename.zip_FILES" and extracting the zip contents "there".

I liked the old behavior better, because I deal with A LOT of zip files, and having to now browse inside A LOT of new folders to manually move the files to the parent folder, then delete the useless new folders it creates, isn't fun by any means. Not to mention that the way the option is named is misleading, since the files aren't being extracted "here" as it says they would be.

So, how can I change the behavior of the "Extract Here" option so that it works as it did in 6.10? I hope it's possible... :(

---

### Post by alexgieg on 2007-04-23
No one knows? :(

---

### Post by TwoD on 2007-12-26
I'd love this feature too! It's really annoying when extracting from one disk to another, or even just to the desktop.

It seems like a highly requested feature too, especially by users who come from Windows and look for the convenient WinRar menus.

I've tried several unpacking apps and none of them add this context menu item. (I couldn't even use half of them since I they weren't integrated into Gnome/Nautilus at all, making them completely useless no matter how many filtypes they handle.)

I'd love to be able to extract files to other places than the currenty directory without having to open (and most importantly: **keep track of and close**) the app's window(s) manually.

The built-in archiver gives noting extra when opening the actual program and extracting files. **It doesn't even tell you the completed %**, or give you the option to automatically close after completion... That's why it's much more convenient to simply drag->drop->extract->forget-until-done. It's really all the "full app" can do when extracting by first opening the file anyway, so why not fully integrate that into the gui?

---

### Post by Fire-Reiher on 2007-12-26
This should do the trick:
Open up a terminal and paste the following:
```
gedit ~/.gnome2/nautilus-scripts/"Extract to current folder"
```
Press enter, then paste this in the gedit window and save the file:```

#!/bin/bash
for selected_uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
  file-roller -e $NAUTILUS_SCRIPT_CURRENT_URI $selected_uri
done
```
Now enter this in a terminal:```

chmod +x ~/.gnome2/nautilus-scripts/"Extract to current folder"
```
After that you will need to restart nautilus by logging out and in or typing
```
killall -9 nautilus
``` in a terminal.
After that you should have a new entry called "Scripts" in you nautilus context menu, in there
is the new command.
It supports multiple selections and uses the default gnome unpacker, so it supports every archive type that gnome can handle. It even shows the more or less useful progress bar.

Have fun!

---

### Post by daengbo on 2007-12-27
7.10 appears to have reverted back to the old behavior.

---

### Post by TwoD on 2007-12-27
Fire-Reiher, thanks, but I think you misunderstood what we want. There is already an option to extract the files to the same folder as the archive (which is the only thing I can do with your script too).

We want to be able to extract files to a different folder simply by dragging the archive to the desired location and choose "extract here".

If that is indeed possible with your script, I appologize. I was not able to execute the script other than by right-clicking the file and choosing the nautilus Scripts-menu like you mentioned.

Is it possible to add scripts/commands to the "middle-button-menu" too?

---

