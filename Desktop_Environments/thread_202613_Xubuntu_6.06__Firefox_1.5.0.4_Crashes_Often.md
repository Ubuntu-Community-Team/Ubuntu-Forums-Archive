---
title: "Xubuntu 6.06 | Firefox 1.5.0.4 Crashes Often"
date: 2006-06-23
forum: Desktop Environments
---

### Post by jonathantneal on 2006-06-23
Firefox 1.5.0.4 just doesn't want to play nice in Xubuntu 6.06.  The crashes are often and never occur during any specific action.  The crashes always close Firefox completely, obviously including any other tabs I have open.  Most often the browser will crash within the first minute of use.

I've seen other posts, but could not find other Xubuntu users with this problem.  Though I am interested in solving the problem, I'm also interested in knowing why it occurs in the first place.  I will be running Firefox through the terminal, which I believe may clue me in to what happens, and from there I will post those results on this thread.

Any help?

Received this error 4 times in the last ten minutes:
"Segmentation Fault"

According to Google, "A segmentation fault occurs when your program tries to access memory locations that haven't been allocated for the program's use."

---

### Post by aysiu on 2006-06-23
[Here's how one person solved it](http://www.ubuntuforums.org/archive/index.php/t-23433.html).

---

### Post by jonathantneal on 2006-06-23
Thanks for the quick reply.  The solution on that thread was to uninstall **mozplugger**.  I went into **Synaptic Package Manager** and discovered that **mozplugger** is _NOT_ installed, so that solution will not work.

---

### Post by deathshadow on 2006-06-23
and this behavior is different from Firefox on other platforms HOW exactly? Oh wait, you actually have it 'Crashing' instead of 'Hanging'...

99% RAM, 99% CPU, Have to kill it is more what I'm used to seeing out of it.

I have a solution that works. 
[http://www.opera.com/download/index.dml?step=2&opsys=Linux%20i386&platform=Linux%20i386](http://www.opera.com/download/index.dml?step=2&opsys=Linux%20i386&platform=Linux%20i386)

---

### Post by jonathantneal on 2006-06-23
Ooooo, **deb** packages are beautiful.  You know what, in a strange way that kinda solved the problem.  :(

The **Opera** browser feels like a **Internet Explorer**/**Firefox** hybrid in a way.  I hear Opera's people are going all-out to claim the market - I think maybe I'll stick with it for awhile.

That still doesn't fix the Firefox problem though. :)

---

### Post by hanasaki on 2006-06-23
I am recently having the same issue on gnome based 6.06 and firefox.

---

