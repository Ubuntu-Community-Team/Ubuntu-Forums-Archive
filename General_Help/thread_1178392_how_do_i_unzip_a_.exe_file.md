---
title: "how do i unzip a .exe file?"
date: 2009-06-04
forum: General Help
---

### Post by jtmedin on 2009-06-04
I have a windows .exe file which i believe is created by zip. Would like to get the directories & files in the .exe file. Anyone got any ideas? TIA

---

### Post by spcwingo on 2009-06-04
Not sure about Linux native, but I use WinRAR to extract these...it usually just starts the process (extracts it from the self-extracting archive).  After that I use unshield and cabextract to finish 'em off from the terminal.  I haven't tried unrar from the terminal for this, but I'll get back to you and let you know if works or not.

---

### Post by spcwingo on 2009-06-04
No dice with unrar.

---

### Post by Soul-Sing on 2009-06-04
Is this question related to wine and ubuntu?
Is it a native windows programm you want to run?

---

### Post by Yellow Pasque on 2009-06-04
Run the .exe in WINE?

---

### Post by Topsiho on 2009-06-04
What makes you think the .exe file is a compressed file? From it's extension it is an executable file for Windows, and not compressed. Compressed files have other extensions, such as .zip or .gz or so. See man gzip in a terminal for more information on zipped files and how to unzip them.

Topsiho

---

### Post by Legace on 2009-06-04
> **jtmedin said:**
> I have a windows .exe file which i believe is created by zip. Would like to get the directories & files in the .exe file. Anyone got any ideas? TIA

Not all .exe's are extractable. Are you sure this .exe is extractable?

---

### Post by jtmedin on 2009-06-04
Its a driver for windows that i need the files for ndiswrapper.

---

### Post by Tibuda on 2009-06-04
> **Topsiho said:**
> What makes you think the .exe file is a compressed file? From it's extension it is an executable file for Windows, and not compressed. Compressed files have other extensions, such as .zip or .gz or so. See man gzip in a terminal for more information on zipped files and how to unzip them.

Topsiho

No, there are some extractable exes , which you can open with winzip/winrar in Windows or file-roller in ubuntu. I beliebe you need to install cabextract to be able to open it with file-roller, if it is extractable, as Legace asked.

---

### Post by michy99 on 2009-06-04
Try```
unzip nameoffile.exe
```Replace nameoffile.exe with the actual filename.

---

### Post by Topsiho on 2009-06-04
Though I did not read all of it, you might find your answer here:

[http://ubuntuforums.org/showthread.php?t=479009](http://ubuntuforums.org/showthread.php?t=479009)

Makes me remark that you should first investigate yourself whether your question was asked before on this forum.

:)

Topsiho

---

### Post by danggrianto on 2009-06-04
i thought .exe is an executable binary files. isn't the purpose of making .exe files is to 'hide' the programs from user?

---

### Post by Topsiho on 2009-06-04
See also: [http://ubuntuforums.org/archive/index.php/t-591533.html](http://ubuntuforums.org/archive/index.php/t-591533.html)

Topsiho

---

### Post by Topsiho on 2009-06-04
Seems that danielrmt is right, I learned something today, so today is not wasted :)

Topsiho

---

