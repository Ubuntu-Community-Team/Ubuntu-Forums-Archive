---
title: "Mupen64 HELP!!!"
date: 2009-02-11
forum: Gaming &amp; Leisure
---

### Post by abunt2 on 2009-02-11
Here are the instructions I got for installing Mupen64
Step 1: Go here and download the Linux version.
Step 2: Go to wherever you downloaded it to and extract it wherever you want it.
Step 3: Go to the directory and double click Mupen64 with the blue cog diamond icon thing above it. Hurrah! It should run.
Step 4: Now click "options" and try out some of the audio and input settings until you find ones that work for your setup.
Step 5: Click "open rom" and point it at a rom.

here is my problem: I just got a new computer running ubuntu (first linux os Ive used) and I followed step 1 step 2 and step 3 perfectly, but when I double click the Mupen64 with the blue cog diamond icon thing above it, a thing pops up that says: Couldn't display "/home/abunt2/Downloaded Games/mupen64".
There is no application installed for this file type
Please help! and yes, I definitely downloaded the linux version, Im not that stupid ;)

Ive already tried googling and searching the forums here for help, but to no avail. 
Thanks in advance!:)

---

### Post by hessiess on 2009-02-12
set the file to exectible ;)

```
chmod +x /path/to/file
```

---

### Post by donkyhotay on 2009-02-12
The post above is correct, if you are uncomfortable with the CLI and want a GUI method right-click on the file, select properties, go to the permissions tab, checkmark "allow executing file as program", close the properties window then try doubleclicking the icon again.

---

