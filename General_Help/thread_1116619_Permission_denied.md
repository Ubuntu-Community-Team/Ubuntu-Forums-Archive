---
title: "Permission denied?"
date: 2009-04-05
forum: General Help
---

### Post by Onemajorflaw on 2009-04-05
Hello,

     I just opened up terminal and typed in ~/.bashrc and it said that permission was denied. I tried accessing my "lost+found" folder and it said the same thing. Anyone know why and have a solution to my problem? Thanks!

---

### Post by lisati on 2009-04-05
Sometimes, as a safety precaution, you need "root" privileges to edit or browse files, especially so for system files. The usual way to temporarily grant yourself such privileges within Ubuntu is to prefix the command you're using with "sudo".

---

### Post by _Purple_ on 2009-04-05
You need to use sudo as this requires root privilege. If you are trying to see it in text mode, you should place the name of the text editor as well.
Type the following command in terminal:

```
sudo nano ~/.bashrc
```

It will prompt you to enter your password, then hit enter. Instead of nano, you can choose any other text editor.

---

### Post by jocko on 2009-04-05
> **Onemajorflaw said:**
> Hello,

     I just opened up terminal and typed in ~/.bashrc and it said that permission was denied. I tried accessing my "lost+found" folder and it said the same thing. Anyone know why and have a solution to my problem? Thanks!~/.bashrc is not an executable file, which is why you get an error when you try to **run** it (which is what you do if you just type the file name).
Are you sure you didn't mean to edit the file?
In that case, you first type the name of the application you want to edit it with (i.e gedit, kate, nano, vim...) and then the name of the file as argument for that application, i.e the command:
```
gedit ~/.bashrc
```
will open your ~/.bashrc in gedit.
The "lost+found" folder is a system folder which is only there in case a file system check would find lost files. The permissions on that folder allows only root to view it's content, as root is the only one that is supposed to deal with file system repair.

---

### Post by jocko on 2009-04-05
> **_Purple_ said:**
> You need to use sudo as this requires root privilege. If you are trying to see it in text mode, you should place the name of the text editor as well.
Type the following command in terminal:

```
[COLOR=Red]**sudo**[/COLOR] nano ~/.bashrc
```It will prompt you to enter your password, then hit enter. Instead of nano, you can choose any other text editor.
**NEVER, NEVER, NEVER** use sudo to edit a file that belongs to a normal user. That may change it's permissions, which will make the user unable to access the file. The ~.bashrc file must be owned by the user who owns the directory it's in.

---

### Post by apmcd47 on 2009-04-05
> **Onemajorflaw said:**
> Hello,

     I just opened up terminal and typed in ~/.bashrc and it said that permission was denied. I tried accessing my "lost+found" folder and it said the same thing. Anyone know why and have a solution to my problem? Thanks!

Okay, did you type ```
~/.bashrc
```or did you type something like ```
more ~/.bashrc
```or ```
vi ~/.bashrc
```
which the other posters seem to think you typed?

If the first one, then you are trying to execute your .bashrc file. The contents of the .bashrc file are executed when you start a new instance of bash, to set up your environment (such as modifying your PATH or setting the repository for CVS. You really only need to run your .bashrc file again if you have modified it and want bash to make use of the modifications.
Try instead one of the following:
```
. ~/.bashrc
source ~/.bashrc
```

As for Lost+found - you don't need to look in there unless your filesystem has had problems. fsck puts recovered files in there. If you need to look in there use a shell running as root (konsole has one under the sessions menu, or type *sudo bash* or *gksu nautilus* or the equivalent for konqueror/dolphin) **but be careful, you will be running as root!**

Andrew

---

### Post by Onemajorflaw on 2009-04-05
Wow! Thanks for the help everyone! I literally installed Ubuntu an hour ago and I'm just running through some tutorials to try to familiarize myself with my new OS. Thanks again!

---

### Post by Cresho on 2009-04-05
YA!  It's like windows.  ONce you figure out where is the "stuff", you will be fine and will never want to EVER look at windows again....EVER!  I been a convert for a few years now and I recently kicked windows.

---

### Post by Iowan on 2009-04-05
> **Cresho said:**
> YA!  It's like windows.NAAAAA!!!  Don't even...):P

---

### Post by Cresho on 2009-04-05
> **Iowan said:**
> NAAAAA!!!  Don't even...):P

Let me rephrase it.  It's like riding a bicycle.

---

### Post by axelroo on 2009-04-05
Just for future reference as you discover Ubuntu and Linux in general, if you ever download an actual executable binary such as nVidia's Driver Installer or any other .bin file, you'll need to change its attributes to executable before you run it or you will get permission denied.  You can do this from the prompt using: "sudo chmod a+x file.bin". Have fun

---

