---
title: "how to know if my home folder is encrypted?"
date: 2010-07-13
forum: Desktop Environments
---

### Post by rizos on 2010-07-13
i can't remember if i choose encrypt my home folder when i first install ubuntu.


is there a way to know if it's encrypted?

thanx.

---

### Post by Dart00 on 2010-07-14
Option A:
1. Fire up your duelboot Windows system
2. Install some freeware that will let you mount and browse whatever file system you installed.
3. Try to browse it, see what you find.
- Can you even access the drive?
- Can you see any folder structure?
- Can you open any of your pics or MP3s?

If 1 or all 3 of those are false its a good assumption its encrypted.

Option B:
1. Take out the harddrive of your computer.
2. Plug it into another computer, or a USB adapter
3. Try to browse it, see what you find.
- Can you even access the drive?
- Can you see any folder structure?
- Can you open any of your pics or MP3s?

If 1 or all 3 of those are false its a good assumption its encrypted.

Hope this helps.

---

### Post by C.S.Cameron on 2010-07-14
Option C:
1. Make a bootable flash drive with usb-creator.
2. Boot with it and try to open your home folder.

---

### Post by rizos on 2010-07-14
thanx for answering...


it seems all this options are a bit more complex of what i thought.


there is no command line to know this?...

---

### Post by TaTaE on 2010-07-16
why don't you try this command in your terminal

```
# mount | grep *yourusername*
```

and you will see from the output if your home dir is encrypted.

---

### Post by rizos on 2010-07-16
there is no output

---

### Post by TaTaE on 2010-07-17
I hope you understood my poor english, the word ***yourusername*** was meant to be replaced by your username.

and when you copy that command above, make sure to remove the # sign.

---

### Post by rizos on 2010-07-19
taht worked very well...


thanx a lot...


# was the mistake...


and yes it's encrypted

it says ecrpytfs...

---

