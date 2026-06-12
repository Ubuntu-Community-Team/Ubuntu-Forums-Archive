---
title: "vim-like window manager"
date: 2010-11-30
forum: Desktop Environments
---

### Post by rainy-day on 2010-11-30
I'd like to find a window manager that has mouse support but can also be set up (with least difficulty) in a dual-mode way, similar to Vim.

Here's how it'd work: some simple shortcut like ctrl-space would go into command mode. Ideally, there'd be a visual indicator of the mode, like a few pixel wide line on top of screen that turns green/blue with a configurable colour.

Commands would work like this:

hjkl: next/prev window/workspace
space: go to insert/normal mode
m/s: move/resize mode, where number+hjkl will control move/resize.
H/L: move windows between workspaces
n: minimize
x: maximize/restore
w: list of windows with j/k moving and enter choosing win to switch to
M: minimize all but active window

Not essential, but would be nice: shade/darken all but current window, like a setting in Compiz.

I've heard about WMs like Ion, awesome, etc. Which one of them, if any, would be best to modify to work in this way? A big bonus would be if it was scriptable in Python, but I'm not counting on that..

thanks!

---

### Post by bobpaul on 2011-04-21
I'm not familiar with ION, but from what I've read awesome should do what you want. It's scriptable with lua. In fact, the configuration files are lua programs. It doesn't support compositing natively, but it's supposed to work well with xcompmgr.

---

### Post by Dragonfi on 2011-06-14
You may want to take a look at wmii. It can be configured with virtually anything.

There are default setup files provided in bash, python and ruby among a few others.

It doesn't have composing features, but it's a minimalist and highly configurable window manager. Also, it's a tiling window manager.

(Yes, I know the post is half a year old, but maybe someone can find it useful.)

---

### Post by bobpaul on 2011-06-14
> **Dragonfi said:**
> 
(Yes, I know the post is half a year old, but maybe someone can find it useful.)

I've never understood people complaining about replies to old posts. Yes, there are times when a post references a specific version of a product and is not or may not be relevant after a new release. But posts like this are general will continue to be relevant for many years.

It bothers me to no end when I do a Google search, find most of my answer in an Ubuntu forum thread in an archived forum (or a thread locked by an admin who thought the replies were getting too unruly) and I am unable to reply for further clarification.

Thanks for your suggestion, Dragon-Fly. I'm already looking at wmii, even if rainy-day isn't.

---

