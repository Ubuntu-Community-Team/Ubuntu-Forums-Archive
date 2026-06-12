---
title: "[SOLVED] Finding username of gui user from script"
date: 2008-12-23
forum: General Help
---

### Post by sarang on 2008-12-23
Hello folks,
            I am trying to find out the username and X screen information of the user logged in to the graphical desktop through a script, but have not found a robust way of doing it. Any help in doing this will be greatly appreciated.

Here's what I have come up with and discarded:

The command [FONT="Courier New"]w[/FONT]: The output does not use tabs but uses spaces between columns. Also, the number of spaces between the same two columns is different on different rows - for reasons of alignment on the screen. IMO this is a very bad design and it basically makes the output hard to parse with [FONT="Courier New"]cut[/FONT]  without significant effort.

The commands [FONT="Courier New"]who[/FONT] and [FONT="Courier New"]last[/FONT] have similar problems.

---

### Post by uidb4056 on 2008-12-23
May be the output of 'echo $USER' will do the trick.

---

### Post by sarang on 2008-12-24
Thanks for the reply, I really appreciate it. But no, that solution will not work in my case. The script will not necessarily run as the gui user. Also, it is not guaranteed that it will have the same `env` as the gui user's shell and hence $USER may not be set either. Thus, `echo $USER`  cannot be used.

---

### Post by Xiong Chiamiov on 2008-12-24
> **sarang said:**
> 
The command [FONT="Courier New"]w[/FONT]: The output does not use tabs but uses spaces between columns. Also, the number of spaces between the same two columns is different on different rows - for reasons of alignment on the screen. IMO this is a very bad design and it basically makes the output hard to parse with [FONT="Courier New"]cut[/FONT]  without significant effort.

Regexp?

You might want to put this in the Programming subforum, as it doesn't really have anything to do with Ubuntu.

---

### Post by sarang on 2008-12-24
> **Xiong Chiamiov said:**
> Regexp?


Oh yes... thanks! Your regexp comment reminded me of using awk and everything was fine after that. I don't know why I was insisting on using cut before.

Thanks again!

---

