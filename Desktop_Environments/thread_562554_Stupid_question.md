---
title: "Stupid question"
date: 2007-09-28
forum: Desktop Environments
---

### Post by zergling on 2007-09-28
Hi everyone,
I open this post because I would like to know how to set a variable permanently.

I was following this instruction :
 
[COLOR="Red"]Running wxWidgets projects[/COLOR]

If when running a wxWidgets app you get an error like:

./a.out: error while loading shared libraries: libwx_gtk2_aui-2.8.so.0: cannot open shared object file: No such file or directory

this means your system does not search for libs in /usr/local/libs (or wherever you installed wxWidgets) by default. To solve this, write 'export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib' on the terminal before opening the executable (from the same terminal). 

UNTIL HERE EVERYTHING IT IS OK!

You can change the LD_LIBRARY_PATH variable permanently to avoid this issue. 

HOW can I set this variable permanently so I do not have to type export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib 
in the terminal all the time?
Bye and thanks in advantage :)

The website is [http://www.wxwidgets.org/wiki/index.php/Compiling_and_getting_started](http://www.wxwidgets.org/wiki/index.php/Compiling_and_getting_started)

---

### Post by llamakc on 2007-09-28
sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf && ldconfig'

It's a great question. The above appends (>>) the path /usr/local/lib to the ld.so.conf file and runs ldconfig to update it (&& ldconfig).

Good question. HTH.

---

### Post by kerry_s on 2007-09-28
you can also add it to the bottom of .bash_profile.

---

### Post by zergling on 2007-09-28
> **llamakc said:**
> sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf && ldconfig'

It's a great question. The above appends (>>) the path /usr/local/lib to the ld.so.conf file and runs ldconfig to update it (&& ldconfig).

Good question. HTH.

Hi, It worked !
Thank you so much :).
From this time one, you are my HERO! :)

Is there any guide to learn all this stuff ?

---

