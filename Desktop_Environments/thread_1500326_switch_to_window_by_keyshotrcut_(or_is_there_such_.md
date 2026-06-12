---
title: "switch to window by keyshotrcut (or is there such an alt-tab replacement?)"
date: 2010-06-03
forum: Desktop Environments
---

### Post by ivotron on 2010-06-03
In my desktop, at any given time, I invariably always have the same set of programs opened (browser, email client, terminal, text editor). And when I switch between them I know what's my "target" program, so if I'm editing some code and I want to search something on the web, I know that I want to get to the browser's window.

It occurred to me that a more efficient way of switching between these "always-opened" windows would be to assign them to an id or key shortcut, so instead of having to press alt-tab many times to switch between them I'd just press, for example, ctrl-alt-f to switch to Firefox or ctrl-alt-t to switch to Thunderbird, etc.

By having this window-switching shortcuts I would save tons of alt-tab key pressings and in turn a lot of time (imagine how many times are alt-tab pressed in, say, a week).

========================

As a side note, I like these programs in the same order (with respect to the taskbar) since the use of [superswitcher]("http://code.google.com/p/superswitcher/")'s Super-Up Super-Down have hardcoded that ordering in my DNA :P

superswitcher can switch by name but it is more tedious since more than one window can have the same letter in its name.

Also, [here's]("http://www.azarask.in/blog/post/solving-the-alt-tab-problem/") an interesting discussion on another more AI-focused alt-tab solution.

---

### Post by stinkeye on 2010-06-03
A couple of solutions using wmctrl.



 ```
wmctrl -a firefox
```
Will focus a window with firefox in the name.



```
wmctrl -a firefox || firefox
```
Will switch to a window with firefox in the name or
start firefox if there is no such window.

---

### Post by ivotron on 2010-06-03
> **stinkeye said:**
> 
A couple of solutions using wmctrl.


Thanks a lot stinkeye!

I've created shortcuts using the XFCE keyboard settings (I use Xubuntu) and assigned one shortcut to each of the programs I have always openned.

---

### Post by stinkeye on 2010-06-03
> **ivotron said:**
> Thanks a lot stinkeye!

I've created shortcuts using the XFCE keyboard settings (I use Xubuntu) and assigned one shortcut to each of the programs I have always openned.

No problem.
One of my favourite shortcuts is the **wmctrl -a firefox || firefox** command. :grin:

---

