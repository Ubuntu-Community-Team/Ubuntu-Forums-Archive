---
title: "Maple 14 Classic Worksheet not working"
date: 2012-02-05
forum: Education &amp; Science
---

### Post by Wraakvol on 2012-02-05
[CENTER][/CENTER]Hi, comrades!

**I'm Wraakvol**, and the Ubuntu universe is completely new to me, since I've installed *Ubuntu 11.10* on my laptop yesterday.:D

First thing I did, I installed Maple 14 on it, 'cause I'm studying on college, and this program is needed. **But I couldn't run the Classic Worksheet**, the one I need. I used the following commands (no one worked for me)::(

> 
maple -cw

xmaple -cw


So, any of you have any ideas, or suggestions?

That's it, I hope your answer!

Wraakvol

---

### Post by Wraakvol on 2012-02-23
Although none of you replied (144 views as I write), I reinstalled Maple 14, once again, and from the terminal I input

> /home/wraakvol/maple14/bin/maple -cw

and nothing happens, although I followed the instructions from the Maple 14 Installation guide and the Readme file. Not even an error. It behave as if I press enter.

I really need to use Classic Worksheet. Please help me.

Ah, one more thing. Does exist a graphic interface of Classic Worksheet for Linux, like the Windows one?

Thanks in advance.

---

### Post by Wraakvol on 2012-02-25
Well, I googled a while, and it seems I'm missing some files. I've just found a guy with similar problems in Fedora. I attach his comment:

> 
maple -cw

died without any error message.

the solution was the installation of a few ancient X11 fonts:

---> Package xorg-x11-fonts-75dpi.noarch 0:7.5-4.fc15 will be installed
---> Package xorg-x11-fonts-ISO8859-1-75dpi.noarch 0:7.5-4.fc15 will be installed
---> Package xorg-x11-fonts-ISO8859-2-75dpi.noarch 0:7.5-4.fc15 will be installed

maybe they are missing from the default Ubuntu install as well 

Now, I need to know what files are missing in my Ubuntu installation, 'cause I've tried to install the ones above, and I got the following:

```

wraakvol@AsgeirrCorp:~$ package install xorg-x11-fonts-75dpi.noarch 0:7.5-4.fc15 
Package xorg-x11-fonts-75dpi.noarch was not found.
wraakvol@AsgeirrCorp:~$ package install xorg-x11-fonts-ISO8859-1-75dpi.noarch 0:7.5-4.fc15
Package xorg-x11-fonts-ISO8859-1-75dpi.noarch was not found.
wraakvol@AsgeirrCorp:~$ package install xorg-x11-fonts-ISO8859-2-75dpi.noarch 0:7.5-4.fc15
Package xorg-x11-fonts-ISO8859-2-75dpi.noarch was not found.

```

So, any ideas?

---

### Post by Wraakvol on 2012-02-26
Hello!

I downloaded those files missing from [here]("http://packages.ubuntu.com/search?keywords=xfonts&searchon=names&suite=oneiric&section=all"), and the program worked fine! :D

I hope this thread helps to anyone who need Maple in his/her machine.

Wraakvol. :popcorn:

---

### Post by PGScooter on 2012-02-26
Wraakvol, I just wanted to say thank you for posting the solution. Many times people get frustrated and upset that no one helped them, but you were better than that and decided to be nice instead of upset. I think this will help others out in the future! Thanks

---

### Post by Wraakvol on 2012-02-27
> **PGScooter said:**
> Wraakvol, I just wanted to say thank you for posting the solution. Many times people get frustrated and upset that no one helped them, but you were better than that and decided to be nice instead of upset. I think this will help others out in the future! Thanks

I was about to get frustrated and get a VM, when I decided to look for help in Mapleprimes.com, those guys who really know about the program itself. And they help me with this problem.

When I realised the solution was tricky, I decided to post it for people who might have the same problem.

So, you're welcome! :P

---

