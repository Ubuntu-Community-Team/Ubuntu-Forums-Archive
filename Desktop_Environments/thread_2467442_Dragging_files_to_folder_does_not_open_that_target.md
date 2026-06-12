---
title: "Dragging files to folder does not open that targeted folder (Ubuntu 20.04)"
date: 2021-09-26
forum: Desktop Environments
---

### Post by ramster2 on 2021-09-26
Hello,
When I [COLOR=#232629][FONT=-apple-system]dragged a file onto another folder icon, the target folder used to open to display its contents, at which point you could release the file, and have it moved to that particular folder. (Ubuntu 16)
Now that I am using Ubuntu 20.04, it does not do that anymore. How do I fix this?[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-09-27
Which file manager are you using? I've never seen this behaviour in any file manager on any OS....

---

### Post by ajgreeny on 2021-09-27
> **ramster2 said:**
> Hello,
When I [COLOR=#232629][FONT=-apple-system]dragged a file onto another folder icon, the target folder used to open to display its contents,[COLOR="#FF0000"] at which point you could release the file, and have it moved to that particular folder.[/COLOR] (Ubuntu 16)
Now that I am using Ubuntu 20.04, it does not do that anymore. How do I fix this?[/FONT][/COLOR]
I do not understand what you mean by the section I have marked in red.
What do you mean by "release the file"? And why, after dragging it to another folder, do you still have to move it to that folder after its release?

What you're saying makes no sense to me.

---

### Post by speartip on 2021-09-27
I understand what the OP is saying. I've never done that before, but just tried it now on Ubuntu 20.04 and it works fine. Just drag the file onto the Folder Icon & the File appears in the Folder. The folder doesn't open to reveal it's contents, but it still works.

---

### Post by ramster2 on 2021-09-27
The file does appear in the target folder after you drag into it, but you have to open that folder manually to see its content.

In Ubuntu 16, the target folder opens automatically when you hover a file on top of it.
How do I make it like that? I want to be able to hover a file on top of a folder, and have that folder automatically open to reveal all of its content.

---

### Post by speartip on 2021-09-27
I'm not sure you can. The behavior that you are looking for appears to have been a bug in 16.04, see here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1301083](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1301083) What you're seeing now is normal behavior in Nautilus.

---

### Post by ramster2 on 2021-09-27
Ah OK, I thought it was one of the features. It was quite helpful for me.
 
I read something about this line **[COLOR=#990000][SIZE=3][FONT=ui-monospace]gsettings set org.gnome.nautilus.preferences open-folder-on-dnd-hover true[/FONT][/SIZE][/COLOR]** to turn that setting on & off. But it was for Ubuntu 16.
I am not sure if it's going to work on the 20.04. I am really not good on linux. But thank you for your help.[COLOR=#232629][FONT=ui-monospace]
[/FONT][/COLOR]

---

### Post by tea for one on 2021-09-27
I did not know that this dragging feature even existed, so I did a little test.

The setting should indeed work in 20.04.

You may have to open two nautilus windows side by side for ease of use.

One window for the source and the second window as target.

I used [COLOR="#0000FF"]dconf-editor[/COLOR] rather than the terminal to change the setting, simply because it was already installed.

---

### Post by T6&amp;sfpER35% on 2021-09-29
i'm confused too , the way i see it , the difference is **1 click**, instead of hovering...
idk, maybe i don't get it

---

### Post by deadflowr on 2021-09-29
> **3nd said:**
> i'm confused too , the way i see it , the difference is **1 click**, instead of hovering...
idk, maybe i don't get it

Old behavior was drag a file (or folder) and hover it over a folder and it would open to the hovered over folder.
New behavior is  drag a file and hover over folder will stay in current directory, and if you release the file it'll go into the hovered over folder without opening that hovered over folder.
I guess the new behavior makes sense if you need to drag  multiple different files or folders to multiple different sub-folders.
Whereas the old behavior would have been detrimental to do that, as it would keep opening the sub-folders.

An example would be, say you dropped a bunch of photos into the Pictures folder, but you want to sort those into specific sub-folders.
The old behavior would mean every time you dragged one photo (or multiple files) into the destined sub-folder, it would open to the folder.
it would be a pain to have to deal with that if you wanted to moved many files into many different folders.


But on the flipside, I can see where users would prefer the old behavior and let the hover open to the hovered over folder.
It was really helpful if you wanted to drag a file down several levels, which the new behavior cannot do.

It's a difference in button presses really as the old behavior would allow you to hold onto the file and once you drag it over a folder that folder would open.
So just one button press could move a file very far down the file path if wanted.

Luckily the gsettings/dconf setting works and is a safe and quick workaround.

Does that make any sense?

---

### Post by T6&amp;sfpER35% on 2021-09-29
yup makes sense now ... i never knew that . I just open the folder tree and drag and release (copy/paste) where i want it and thats that .
thanks for explaining :smile:

---

### Post by deadflowr on 2021-09-29
I've been hit by both behaviors at the wrong time, so...

If you're fast and accurate you can drop files into sub-folders using the old behavior without the sub-folder opening.
But key there is fast and accurate, it does have a slight delay before opening but you need to be quick about it.
I guess users who prefer the old behavior already know this, and well, have an issue with the change.
I can sympathize.

---

### Post by ajgreeny on 2021-09-29
Interestingly, and I admit going off at a bit of a tangent here, I seldom drag and drop files using the file manager but use the context menu I get from the custom actions available in thunar, Xubuntu's file manager.
A right click on file or files points to a script in my home
```
#!/bin/sh
[ 0 -eq $# ] && exit
dst=$(zenity --title='Where to move' --file-selection --directory) || exit
/bin/mv -n -- "$@" "$dst"
```
which moves those files to any folder in my home that I navigate to.
I use a very similar script to copy files into other folders as well; another great time-saver.

It is something I use a great deal and I think it a hugely time-saving method of moving or copying files from folder to folder.
I've used Xubuntu and its custom actions for so long now that I don't know if such methods are available in the other DE versions but my betting is that something similar must be.

---

