---
title: "A litle help please."
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by Veevose on 2007-10-08
Hey i am veevo and i am new to Ubuntu and i am starting to figure it out. It is fun and nice to use ubuntu but i have some plroblems of understanding how to install games with Wine.
I just want to download the Steam and Install the CSS. that is what i need for now.
I understand that steam.msi file is not good and i cant find any other one to use.
So if it is someone there to make time explaining me please let me know.
Sorry to open a new post!

---

### Post by Sockerdrickan on 2007-10-08
? it is "good"

wine start SteamInstall.msi

---

### Post by Veevose on 2007-10-08
well i cant even open wine: I have it here at applications but thats it.. it apperas to me as a folder ... i cant open it as a running program.??:(

---

### Post by cogadh on 2007-10-08
Wine is not an application, it is a compatability layer that allows Windows executables to run in Linux. You just need to do what Tux0r said in a terminal.

Also, you might want to check out the "Stuff I've learned about Wine" link in my sig, it might help you out with using Wine for the first time.

---

### Post by Veevose on 2007-10-08
dude i think i am either too stupid or either very stupid.
I have read your last post and its very good explained but.
Still i downloaded the steamintall.msi file from theyr website and tryed to open it with wine from wine>aplication>add aplication.. and nothing it dosent see that file on my desktop.
OR.. how should i open it... i mean man.. i know i am new and probably very anoying but i realy want to make this work, and others more maybe:P

---

### Post by cogadh on 2007-10-08
You don't use the "Add Application" function to install it. Open a terminal, cd to the directory where you saved the Steam install package and run this:
```
wine start steaminstall.msi
```
The Add Application function is for creating custom Wine profiles for applications that have already been installed via Wine.

---

### Post by Veevose on 2007-10-08
Here is the reply of what you suggested me:
vivi@Techno:~$ wine start steaminstall.msi
fixme:exec:SHELL_execute flags ignored: 0x00000500
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: File not found

and the file was on desktop

---

### Post by cogadh on 2007-10-08
Did you change directories to the desktop before you ran it? By default, a terminal opens in your home directory, not the desktop directory.
```
cd ~/Desktop
wine start steaminstall.msi
```

---

### Post by Veevose on 2007-10-08
ok that works.. thanks.
Now i have another problem.. you know how it is..
It runs steam and when it gets to 26% update it says that another copy of steam is running.. and steam is shutting down.

---

### Post by cogadh on 2007-10-08
Okay, this is a common problem. Do this in the terminal:
```
cd ~/.wine/drive_c/Program\ Files/Steam/
nice -n 19 wine steamTmp.exe SelfUpdate "Steam.exe" 14
```

EDIT - Also, I highly recommend you check out the Steam entry in Wine's Application Database, it will explain everything you need to install and run it correctly:
[http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

### Post by Veevose on 2007-10-08
There you go.. thank you dude thank you very much.
do you have any id or something from where i can contact you if i have any problem.. if offcourse that is ok with you.
I am saying this because i love this OS and i realy want to learn how to use it.

---

### Post by cogadh on 2007-10-08
Just use the forums for any help you might need, there are many of us lurking around here who can help you out. Most of 'em are way better than me at this stuff.

---

### Post by Veevose on 2007-10-08
allright thank you mate and sorry for the spam,.

---

