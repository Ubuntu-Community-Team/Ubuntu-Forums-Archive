---
title: "Trying to understand .zip files in Ubuntu"
date: 2013-04-30
forum: Gaming &amp; Leisure
---

### Post by opieisop on 2013-04-30
I am new to linux and Ubuntu ( 2 days new ). I am trying to get Minecraft to work with a set of modpacks my friend sent me. He sent me a .zip file that I think does not work in linux unless I have proper software ( is this correct ? ). So I installed Krusader using the Ubuntu Software center. I located the file that was sent to me in the left window of the program, I opend the .minecraft.zip folder and inside it was the folder I need to replace my current folder with. ( .minecraft is the name of the folder being moved/replaced ). I went up one level in the right window in order to place the new .minecraft folder in the correct spot. It gave me a popup ( as expected ) telling me that there was already a folder with that name. Now I was looking for an overwrite option but I did not find one. There was an option to write it alongside ( paraphrasing ) another folder but I did not know exactly what that meant so I pressed cancel and simply deleted the old .minecraft folder in the right window. Then I tried to move the folder on the left window to the right just like before. It bean to move the folders, it seemed to be working until I got a popup error. After looking at it I can see that all but 3 folders were moved to the new destination. The remaining 3 all give me the same error. This is a ss of what is happening. Any information or guidance on what this means would be appreciated. 

[IMG]http://i.imgur.com/WcQJVBd.png?1[/IMG]

---

### Post by schragge on 2013-04-30
I'm not sure, but the problem may be square brackets in the file name. They are part of shell's [glob]("http://en.wikipedia.org/wiki/Glob_%28programming%29") syntax, and may be wrongly interpreted if passed by Krusader to shell unquoted. Try to rename files before unpacking.

---

### Post by coldraven on 2013-04-30
You don't need Krusader just double click the zip file to open it..

---

### Post by opieisop on 2013-04-30
schragge - I will try that, hope it works for me. Thank you for responding.

coldraven - At first I looked in the folder and did not see the file. It was as if it didn't download. I did not use terminal to do this I used the " Home Folder " icon. I figured perhaps .zip is not seen by linux/ubuntu and I would need another program. So I got this file manager program you see. Thank you for responding.

---

### Post by schragge on 2013-04-30
You did not see it because file names starting in a dot are hidden. In Nautilus, you can press **Ctrl**+**H** to show them. I guess pressing **Alt**+**.** in Dolphin (KDE file manager) does the same.

---

### Post by oldrocker99 on 2013-04-30
To make sure that you can open any kind of compressed file, just open a terminal and type

sudo apt-get install p7zip-full p7zip-rar

It will ask for your password (but not show when you type it), then download and install the files. Those two packages will let you open ANYTHING.

---

