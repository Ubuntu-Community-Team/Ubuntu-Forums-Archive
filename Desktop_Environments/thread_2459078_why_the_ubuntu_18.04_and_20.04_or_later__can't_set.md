---
title: "why the ubuntu 18.04 and 20.04 or later  can't set a password for a compress archive?"
date: 2021-03-10
forum: Desktop Environments
---

### Post by yk0vpusdf85mz4tks on 2021-03-10
why the ubuntu 18.04 and 20.04 can't set a password for a compress archive?
why can't set a password ? 
and all the 18.04 and the later version don't set a password for any compress archive ?
there isn't a set passwrod item?

---

### Post by ajgreeny on 2021-03-10
It is very easy to create a password protected compressed archive but you need to ensure you have an appropriate compression package installed.

I'm not on my Xubuntu machine at the moment (using Android) but I always install p7zip package which is the one that I believe gives me that password ability.

---

### Post by yk0vpusdf85mz4tks on 2021-03-11
when i right click a file ,select the compress item ,then it isn't see a set password dialogue .
it likes beblow (the screenshot can't be post). where is the psaaword setting items?

---

### Post by spjackson on 2021-03-11
The answer depends on which file manager you are using.

I use Ubuntu Studio 20.04 (which is based on Xubuntu) so the default file manager is Thunar. With Thunar, you can right-click on (say) a folder and select Create Archive from the Pop-up menu. Choose an archive type that supports password protection, e.g. .7z, .zip. Click "Other Options" and enter a password.

It sounds like you are using the default file manager in Ubuntu which is Nautilus. I can't see an obvious way to do a similar thing in Nautilus currently. According to[ this article]("http://https://askubuntu.com/questions/1037290/create-zip-file-with-password-protection-in-ubuntu-18-04") you need to start Archive Manager, select New Archive and the password box is under "Other Options" as above. This works when running from the live 20.04 Ubuntu iso so should work for you.

---

### Post by ajgreeny on 2021-03-11
> **spjackson said:**
> The answer depends on which file manager you are using.

I use Ubuntu Studio 20.04 (which is based on Xubuntu) so the default file manager is Thunar. With Thunar, you can right-click on (say) a folder and select Create Archive from the Pop-up menu. Choose an archive type that supports password protection, e.g. .7z, .zip. Click "Other Options" and enter a password.

It sounds like you are using the default file manager in Ubuntu which is Nautilus. I can't see an obvious way to do a similar thing in Nautilus currently. According to[ this article]("http://https://askubuntu.com/questions/1037290/create-zip-file-with-password-protection-in-ubuntu-18-04") you need to start Archive Manager, select New Archive and the password box is under "Other Options" as above. This works when running from the live 20.04 Ubuntu iso so should work for you.
You may well be right about that but I do not use Ubuntu as I find many things in gnome DE unusable.  

I know a lot of the uses to which I put thunar, including about 20 custom actions invoked from right click on files or folders, are available in nautilus, aka files, only by installing extension packages.  You may argue that thunar also has some of these but as far as I'm aware the most useful ones, eg thunar-archive-plugin, are installed automatically.

Alternatively, you could see if adding thunar or another file manager to Ubuntu allows you to utilise a right click to create a password protected archive.

---

