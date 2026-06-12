---
title: "[SOLVED] Starting TeamSpeak client"
date: 2008-06-08
forum: Gaming &amp; Leisure
---

### Post by graabein on 2008-06-08
I've just installed the TeamSpeak client from [here]("http://www.goteamspeak.com/?page=downloads"). I ticked the option to add item to menu but I can't see it, even if I use the Edit Menu option under the System menu.

But I figure I can launch it from the command line. I cd to the correct directory and type **TeamSpeak.bin** but I just get:

```
$ TeamSpeak.bin
bash: TeamSpeak.bin: command not found
```

Here's the contents of the dir:

```
clicense.txt  libborqt-6.9-qt2.3.so  manual      TeamSpeak
client_sdk    libHVDI.so.0.8.0       Readme.txt  TeamSpeak.bin
icon.xpm      libspeex.so.1.0.0      sounds      uninstall.sh
```

The bin-file has the following rights: **-rwxr-xr-x** 

So what am I doing wrong?

---

### Post by Phenax on 2008-06-08
You have to do
./TeamSpeak.bin

The current directory is not in your path (a shell variable that contains all of the directories that you can execute from without typing the absolute path). If you want to execute a file in your current directory you must precede it with a "./" to signify that you are executing it from the current directory.

Although, I just use teamspeak-client from Synaptic - it works fine for me.

---

### Post by graabein on 2008-06-09
Thank you! I knew there was something with a dot but could not remember the slash. 

I'll remove the manually installed client and go with the Synaptic version.

---

