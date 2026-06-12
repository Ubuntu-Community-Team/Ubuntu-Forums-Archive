---
title: "Cursor jumps around while typing"
date: 2009-03-05
forum: General Help
---

### Post by Shawn K on 2009-03-05
I've used the Search function, but I haven't found any threads that seem to mirror my situation.

I do a lot of typing (I'm a copy editor for a magazine, and do all of my work online).  I'm using Open Office 3.0 and Firefox 3.0.6 on my Acer Aspire 5610 laptop running only Ubuntu 8.10 (no dual-boot scenario).

While typing, I'll experience all sorts of strange behavior.  The cursor will jump all over the screen while typing (which will cause what I'm typing to be broken up into chunks), it will randomly highlight segments of text and delete it because I kept blindly typing, and in general it just makes my life a real pain.

I have a touchpad on the laptop.  My first thought was that maybe I was accidentally touching the pad, but I can get erratic behavior even when I make a point to keep my hands lifted from the computer.  Besides, I never had this kind of problem when I bought this very laptop with Vista instlaled...

Relative newb here, so I need some help figuring this one out.  Anyone have any advice?

---

### Post by Shawn K on 2009-03-06
Bump.

Anyone have any advice?  The search function still hasn't yielded anything that sounds applicable.

---

### Post by Rallg on 2009-03-06
This is a common problem, and has a well-known solution. If you haven't previously seen the problem on another OS (such as Windows) it is because the solution is pre-installed there.

You want to "disable touch pad while typing." If you search for that on an ordinary search engine, you will see advice about how to add some lines to a particular file, then add something to your services. You can do it that way, in most cases.

Or, the less-brainer way is to use a little utility called "Touchfreeze" that is available via Add/Remove programs in your Ubuntu Applications menu. Install it. What it does is neutralize the touchpad as long as you are typing. The default setting (which you can change) is to re-activate the touchpad at half a second after your last keystroke.

Touchfreeze would need to be activated each time you boot. You can make it so that it launches automatically. To do that, after installing Touchfreeze, go to System > Preferences > Sessions. Add a new entry to the startup program list. The command is simply "touchfreeze" (without the quotes). You can call it what you like.

---

### Post by Shawn K on 2009-03-06
Knock on wood, this seems to do the trick.

I appreciate the help.  Turns out that I had heard that solution posed in a couple of other threads, but the way the threads were started made me think that they were having slightly different issues from what I was having, so I thought I needed to look in a different direction.

Thanks!

---

