---
title: "sudo from the GUI"
date: 2006-05-07
forum: Desktop Environments
---

### Post by VK2XCI on 2006-05-07
G'day all, 
I'm having trouble with the concept of "no root account". I'm certainly not a newbie to Linux, which is probably part of the problem! I've had Ubuntu running all of 1 hour, having "converted" from Mandrake.

I'm trying to move a couple of files from where I downloaded them  in /home/vk2xci/temp to /user/share/backgrounds. The File manager tells me I don't have permission, as it should. Now, given the past behavior, I thought ot should have asked me for sudo password?

Perhaps I'm missing something VERY basic here?

---

### Post by Sutekh on 2006-05-07
Well you can either copy them from the terminal
```
sudo cp /home/vk2xci/temp/<some file> /usr/share/backgrounds/
```
which will prompt for your sudo password.

Or open Nautilus as root, with
```
gksudo nautilus
```
which wil open a dialog asking for your password, then you can browse using Nautilus as root.

---

### Post by VK2XCI on 2006-05-07
Many thanks Sutekh,

This is obviously going to take some getting used to.!

---

### Post by ComplexNumber on 2006-05-07
[quote=VK2XCI]G'day all, 
I'm having trouble with the concept of "no root account". I'm certainly not a newbie to Linux, which is probably part of the problem! I've had Ubuntu running all of 1 hour, having "converted" from Mandrake.

I'm trying to move a couple of files from where I downloaded them  in /home/vk2xci/temp to /user/share/backgrounds. The File manager tells me I don't have permission, as it should. Now, given the past behavior, I thought ot should have asked me for sudo password?

Perhaps I'm missing something VERY basic here?[/quote] install a program called gexec [here]("http://gnomefiles.org/app.php?soft_id=678"). its a really basic program so it very few dependencies (just gtk, gksudo, libgksudo, libgksudoui). to install it, just type "make"...."make install".
i find it quite useful, but i'm not entirely certain if its good for a newbie.

---

### Post by Sutekh on 2006-05-07
No problem.  I assure you it gets much easier, if you stick at it.  Plus you already have some Linux exp under you belt.

---

### Post by VK2XCI on 2006-05-07
[QUOTE=ComplexNumber]install a program called gexec [here]("http://gnomefiles.org/app.php?soft_id=678"). its a really basic program so it very few dependencies (just gtk, gksudo, libgksudo, libgksudoui). to install it, just type "./configure"...."make"...."make install".
i find it quite useful, but i'm not entirely certain if its good for a newbie.[/QUOTE]

Good Stuff,
I was going to suggest a "Run as Root" shortcut, but that'll do nicely!

I really do miss the root account, I wonder at the rationale behind the approach :confused:

---

### Post by tennvols_69 on 2006-05-07
ubuntu has a root account but you must set the password. to do this hit ctrl+alt+f1 then login with your user password. at the # type sudo su
then passwd  you will now be prompted to  set a password.  once you do this you can do 1 of 2 things hit ctrl+alt+f7 to get back to gdm and you can now use terminal when it askes for password this will be what you set by the above means. to get into genome  with root  you must drop to command line and type sudo /etc/init.d/gdm stop  after gdm has stopped you can now do startx will will bring you into gnome  under root user.  to get out i always drop back to command line then do sudo /etc/init.d/gdm stop then sudo /etc/init.d/gdm start to bring you back to the normal user login.

---

### Post by VK2XCI on 2006-05-08
[QUOTE=tennvols_69]ubuntu has a root account but you must set the password. to do this hit ctrl+alt+f1 then login with your user password. at the # type sudo su
then passwd  you will now be prompted to  set a password.  once you do this you can do 1 of 2 things hit ctrl+alt+f7 to get back to gdm and you can now use terminal when it askes for password this will be what you set by the above means. to get into genome  with root  you must drop to command line and type sudo /etc/init.d/gdm stop  after gdm has stopped you can now do startx will will bring you into gnome  under root user.  to get out i always drop back to command line then do sudo /etc/init.d/gdm stop then sudo /etc/init.d/gdm start to bring you back to the normal user login.[/QUOTE]

Man, how convoluted is that?:eek: 
Thank you. I can see how it works. I guess that setting up a "normal" root account is going to break something... probably the gui by the sound of things? I may have to look for another Debian based Distro :(

---

### Post by aysiu on 2006-05-08
[QUOTE=VK2XCI]
I really do miss the root account, I wonder at the rationale behind the approach :confused:[/QUOTE] Read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

It has the rationale, *and* it explains how to set up a traditional root account if you wish to do so.

---

### Post by VK2XCI on 2006-05-08
[QUOTE=aysiu]Read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

It has the rationale, *and* it explains how to set up a traditional root account if you wish to do so.[/QUOTE]

Thank you aysiu,

I have read and understood! I don't have to agree tho!

Why the dire warning in bold caps not to do GUI root login?  Is there a real problem or simply a "policy" matter?

---

### Post by aysiu on 2006-05-08
[QUOTE=VK2XCI]
I have read and understood! I don't have to agree tho![/quote] No, you don't. But that's the rationale. And I think it covers both pros and cons of the *sudo* model.

> 
Why the dire warning in bold caps not to do GUI root login?  Is there a real problem or simply a "policy" matter? It's a real problem. You should never log in as root graphically.

---

