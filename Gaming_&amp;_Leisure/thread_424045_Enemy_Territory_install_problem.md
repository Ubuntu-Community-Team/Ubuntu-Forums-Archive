---
title: "Enemy Territory install problem"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by Focus Fate on 2007-04-26
Hey, I'm new to Ubuntu and linux in general and although I am learning a bit I am still pretty dull about installing things. I DLed the installer for Enemy Territory for Linux and it's a .run, upon double clicking I get gedit telling me this:

Could not open the file /home/gregory/Desktop/et-linux-2.60.x86.run.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

I tried to pick another character coding from the drop down but it did not work. I am really completely in the dark here so I'm sorry if this is a common problem or realativly simple to fix, but I searched the forums and found no answer.

I am on Feisty 64bit and would really appreciate any help :)

---

### Post by cogadh on 2007-04-26
Don't double click it, do this in a terminal:
```
username@ubuntu:~$ cd Desktop
username@ubuntu:~/Desktop$ sh et-linux-2.60.x86.run
```

A .run file is shell script and can only be run (AFAIK) from a terminal.

---

### Post by lakersforce on 2007-04-26
Since you are on a the amd64 you might also want to run this line:

```
sudo apt-get install ia32-libs
```

---

### Post by Focus Fate on 2007-04-26
Thanks for the help! It worked like a charm (after I went in and tweaked the write access) Now all I gotta do is get it to play sound and I'll be on my way :-D

---

