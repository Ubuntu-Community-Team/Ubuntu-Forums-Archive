---
title: "How to read .pdb files"
date: 2006-10-02
forum: Desktop Environments
---

### Post by noparking on 2006-10-02
How can I read my e-books in .pdb format.I'm looking for something like ''iSilo'' in other OS.

---

### Post by skymt on 2006-10-02
I use a terminal command, I don't know of any GUI way to do it.```
txt2pdbdoc -d file.pdb file.txt
```That command will convert file.pdb to plain text.

You need to install txt2pdbdoc first. Read [this](https://help.ubuntu.com/community/Repositories/Ubuntu), and activate the Universe repository. Then run this command:```
sudo aptitude install txt2pdbdoc
```

---

### Post by noparking on 2006-10-03
Thank you. Any other suggestions?

---

### Post by skymt on 2006-10-03
No, that's it. I just wrote a little GUI for txt2pdbdoc, though. It's attached. Save it to your desktop, open a terminal, and do this:```
gunzip guipdb.gz
sudo mv guipdb /usr/local/bin/
```Then you can run it as "guipdb".

When you run it, you get a file open dialog. If you open a .pdb file, it will convert it to .txt. If you open a .txt file, it'll go the other way. It won't work if you don't install txt2pdbdoc.

Let me know if that doesn't work.

---

### Post by noparking on 2006-10-03
Thanks again.Your script works well with simple text and pdb files.Unfortunately I have to deal with some more complex pdb files with hyperlinks and tables. app.20 MB. 

I couldn't get iSilo work with wine. Maybe I'll read these files in vmware under Ubuntu with the other OS...Until linux community solve the problem.

---

### Post by wecjason on 2007-10-02
Go to this site [http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

Install ies4linux

Then see this  [http://www.zarski.com/index.php?/archives/48-iSilo-plug-in-for-Linux-users.html](http://www.zarski.com/index.php?/archives/48-iSilo-plug-in-for-Linux-users.html)

The installation of isilo reader is similar to the isiloX

Download [isilo4.01]("http://www.isilo.com/download/dl/iSilo401W32Setup.exe") setup file for Windows, then key in the following command

switched over to the directory where you download isilo

[B]WINEPREFIXcreate=~/.ies4linux/ie6 wine iSilo401W32Setup.exe

[/B]This will popup the install for iSiloX. Just complete the install wizard like you would on Windows.

You can access the isilo on Desktop just like windows

---

### Post by jamarsa on 2007-10-02
For .pdb, do you mean specifically iSilo format, or are you generic (PalmDoc Book for example)?

If the later, have a look at FBreader ([http://www.fbreader.org](http://www.fbreader.org)), a book reader intended originally for PDAs, but I think available also for linux desktops. It does support some .pdb formats, except, unfortunately, iSilo. I use it in my Zaurus.

---

### Post by heinig on 2007-10-21
I just got iSilo working under wine w/o any trouble.  
I'm using version 4.32 (iSilo) and Gutsy.

---

