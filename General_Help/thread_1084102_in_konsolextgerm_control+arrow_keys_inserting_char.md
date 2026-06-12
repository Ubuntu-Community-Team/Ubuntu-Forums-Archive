---
title: "in konsole/xtgerm control+arrow keys inserting character codes not moving cursor"
date: 2009-03-01
forum: General Help
---

### Post by arch0njw on 2009-03-01
For awhile now (I've been lazy), using the control+arrow keys have been inserting character codes instead of jumping between words.

Anyone have any hints on how to fix this?

control+right:  ;5D
control+left:  ;5C
control+up:  ;5A
control+down:  ;5B

---

### Post by arch0njw on 2009-03-05
Not the best, but there is a "fix" to this.  Apparently this is fixed in Intrepid:

           [I]I had this same problem. I fixed it by copying these lines I found in /etc/inputrc to my existing ~/.inputrc file:
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word[/I]


[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/89235](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/89235)
[https://bugs.launchpad.net/ubuntu/+source/irssi/+bug/104708](https://bugs.launchpad.net/ubuntu/+source/irssi/+bug/104708)
[https://bugs.launchpad.net/ubuntu/+source/vte/+bug/89660](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/89660)

---

### Post by SabreWolfy on 2009-05-01
Thanks -- copying the lines into ~/.inputrc fixed the ctrl-left and ctrl-right arrows not working for me in Ubuntu Jaunty Server too. Seems that these entries in /etc/inputrc are ignored.

In Jaunty non-Server on my desktop machine, ctrl-left and ctrl-right work, even though I don't have a ~/.inputrc. Guess it's reading from /etc/inputrc correctly here.

---

### Post by Thangalin on 2009-07-07
You can fix this in Konsole (version 2.2.2 for KDE 4.2.2) as follows:

[LIST=1]
[*]**Settings » Edit Current Profile » Input » Edit**
[*]Click **Add**
[*]Set **Key Combination** to Left+Ctrl
[*]Set **Output** to **\E[1;5D**
[*]Click **Add**
[*]Set **Key Combination** to Right+Ctrl
[*]Set **Output** to **\E[1;5C**
[/LIST]

Case is sensitive. Pay attention to the backslashes, too. **_\_E[1;5D** is not the same as **e[1;5d**.

Those instructions would only work for the current instance. As soon as you restart Konsole, the changes would revert. Here's what you have to do to make the changes persist:

[LIST=1]
[*]**Settings » Edit Current Profile » Input**
[*]Select xterm (XFree86 4.1)
[*]Click **New...**
[*]Set Description to **Your Bindings**
[*]Click **Add**
[*]Set **Key Combination** to Left+Ctrl
[*]Set **Output** to **\E[1;5D**
[*]Click **Add**
[*]Set **Key Combination** to Right+Ctrl
[*]Set **Output** to **\E[1;5C**
[*]Select **Your Bindings**
[*]Click **Apply**. (Optional?)
[*]Click **OK**.
[/LIST]

The keys should function proper immediately. When you restart Konsole the keys should continue to function as expected.

---

### Post by arch0njw on 2009-07-07
> **Thangalin said:**
> You can fix this in Konsole (version 2.2.2 for KDE 4.2.2) as follows:

[LIST=1]
[*]**Settings » Edit Current Profile » Input » Edit**
[*]Click **Add**
[*]Set **Key Combination** to Left+Ctrl
[*]Set **Output** to **\E[1;5D**
[*]Click **Add**
[*]Set **Key Combination** to Right+Ctrl
[*]Set **Output** to **\E[1;5C**
[/LIST]

Case is sensitive. Pay attention to the backslashes, too. **_\_E[1;5D** is not the same as **e[1;5d**.

Strangely, this isn't a problem for me under KDE 4.2.2.  (Kubuntu 9.04 amd64)

Thanks for the pointer though!

---

### Post by Thangalin on 2009-07-07
I'm using the exact same setup and still had the issue. Weird.

---

