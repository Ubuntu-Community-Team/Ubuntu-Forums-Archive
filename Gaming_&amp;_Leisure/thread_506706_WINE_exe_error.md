---
title: "WINE exe error"
date: 2007-07-22
forum: Gaming &amp; Leisure
---

### Post by insanity54 on 2007-07-22
Hello, 

I just installed Battlefield 1942 with wine on Dapper.

Before you say, "Battlefield dosn't work with wine", Let me say first, "I know."

I have this problem with just about every .exe file I come across, some websites say it is a bug, but it obviously is a precaution for preventing malware from being run.

the error occurs when I try to run BF1942.exe or any .exe

```
Cannot open BF1942.exe

The filename "BF1942.exe" indicates that the file is of
 type "executable". The contents of the file indicate that the
 file is of type "DOS/Windows executable". If you open this file,
 the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or
 recieved the file from a trusted source. To open the file,
 rename the file to the correct extention for "DOS/Windows
 executable", then open the file normally. Alternatively, use the
 Open With menu to choose a specific application for the file.

```

I have been searching high and low for a answer to this problem, one website suggested to chmod the file to 755, which I did, and nothing happened.  the file .exe itself does not do the error, but a link file to it does. 

Also I read that it is a bug and can be fixed by changing the .exe to .EXE I did this and the same thing happened.

My question, is- How can I tell my system i trust the file and run the file?

---

### Post by hikaricore on 2007-07-22
Exactly how are you trying to run this executable?

Like from a command line you should be typing:
> wine BF1942.exe

From the directory the file is located in.

---

### Post by duncan.hawthorne on 2007-08-04
yes running from terminal works, but how do you make it work for just double clicking on the file in nautilus (which is where the error appears)?
this is just some system precaution that i want to turn off

---

### Post by Cappy on 2007-08-05
Right click, click "open with other application", Click "use a custom command" at the bottom, type in "wine" LOWERCASE
*hit okay or apply or whatever*

You may need to right click the file, goto properties, click the "Open With" tab, and click "wine" to make it happen everytime.

---

### Post by duncan.hawthorne on 2007-08-05
yes you can go into that menu and type open with wine everytime but wine doesnt stay in the "open with" menu. so you have to type everytime.
i guess when you go into that menu it is treating it as a dos/exe again, or something.
But this misses the actual issue, which is that we should be able to turn off this warning error. other files have this warning error too, eg png renamed as jpg. I dont need to be warned. How do you turn off the warning and make it open automatically with what you want it to?
As a strange fix it appears that renaming the exe seems to make it work. or renaming the extension (eg removing it). or even renaming the exe then renaming it back. What is going on?

---

### Post by Cappy on 2007-08-05
change directory to ~/.local/share/mime/packages
and open
Override.xml

Remove the very end that says
```

</mime-info>

```
Add a line on the end that says
```

<mime-type type="application/x-extension-windows"><comment>Windows executable</comment><glob pattern="*.exe"/></mime-type></mime-info>

```

Save it and it should work.

The reason that there is an error message by-default is so that any program launching an "exe" would not run automatically without the user's permission.

You can find more information on shared-mime-info at your local library.

---

### Post by duncan.hawthorne on 2007-08-05
thank you, i'll try it this evening :D

---

