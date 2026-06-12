---
title: "what does this error mean? XFCE"
date: 2007-08-08
forum: Desktop Environments
---

### Post by kystorms on 2007-08-08
I have loaded xubuntu and it runs fairly well... but

when i log into it from sessions - 

I get the following:

could not look up internet address for lisac-desktop.
This will prevent Xfce from operating correctly.
It may be possible to correct the problem by adding
lisac-desktop to the file /etc/hosts on your system.
Now I do notice that after leave on program * none in particular* i get a bit of a "ghost" picture of what ever was on the last open window when i try to open a new program in xfce.
I hope someone can tell me how to take care of this error, and hope that if i do... that will stop this from happening.

Also, does xubuntu need alot of power? I have 160. GB HD, 1.5 GB memory 1.5 Ghz.

thanks
:confused:

---

### Post by dougfractal on 2007-08-08
sudo gedit /etc/host
> 127.0.0.1 localhost lisac-desktop
127.0.1.1 lisac-desktop

> Also, does xubuntu need alot of power? I have 160. GB HD, 1.5 GB memory 1.5 Ghz.You could run xubuntu on 128MB ram and 400Mhz , although I would recommend 256MB and 1Ghz.

> Now I do notice that after leave on program * none in particular* i get a bit of a "ghost" picture of what ever was on the last open window when i try to open a new program in xfce.  Have you install compiz? as that is strange.

---

### Post by fwojciec on 2007-08-08
Your xfce is slow because of this error.

You have to edit your /etc/hosts file so that it looks more or less like this:

> 127.0.0.1      localhost        toshiba

Replace "toshiba" with whatever you named your computer - basically just add the actual host name to the file.

That should take care of your problem.

---

