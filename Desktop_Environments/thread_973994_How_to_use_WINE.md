---
title: "How to use WINE"
date: 2008-11-07
forum: Desktop Environments
---

### Post by raunhar on 2008-11-07
I have just installed ubuntu 8.04 .
Also I installed WINE through software Sources--> third party software along with the key.
No error was displayed.
Now how do i check if it has been installed and how do I use it.

Thanks in advance

---

### Post by prshah on 2008-11-07
> **raunhar said:**
> I have just installed ubuntu 8.04 .
Also I installed WINE through software Sources--> third party software along with the key.


Open a terminal (Applications, Accessories, Terminal) and give the command ```
wine --version
```

That will show you the version installed, or give an error message if it's not installed.

To use it, browse to the Windows program you want to use, then right-click the (.exe) file and select "Open with Wine Windows Program Loader"

---

### Post by raunhar on 2008-11-08
Thanks for the reply.
I tried it , but it showed, no WINE installed.

So i again did the process, it showed copying files, and complete.
Then i went to Update manager, but no wine was showing there.
I again went to terminal.
there again it showed no WINE installed.

---

### Post by kostkon on 2008-11-08
You can check if it is installed in *Synaptic*. Search for it and see if it is checked as installed.

Alternatively, you can give the following in a terminal
```
apt-cache policy wine
```

---

### Post by raunhar on 2008-11-08
Thanks, I was able to install it.

just another question:
Do i need to have windows to run the programms.
I need to use Dreamweaver and paintshop pro .

Do I run the installation file of these programs.

---

### Post by rpavic on 2008-11-08
You don't have to have windows installed, just run the setup files for Dreamweaver and PS.

---

### Post by raunhar on 2008-11-08
Thanks a lot for the quick reply.

---

