---
title: "xorg, memory - news computer and it's worse than it was"
date: 2009-10-04
forum: Desktop Environments
---

### Post by kkarpieszuk on 2009-10-04
Hi 

One week ago i bought new computer. This one is about two times better: has 1GB ram (old had 500MB), 64bit processor 2.2GHz (old was 32bit 1GHz) so i expected that Ubuntu will work faster.

In most of  cases it is how i expected but in last week four  times computer hanged for over than ten minutes. When computer hangs i see that ram almost full and disk is hardly working. All graphical interface is very slowly, i think its better to say that GUI stops: only mouse pointer moves but very slowly, jumping from one place to another (not smootlhy). I think in this moment Ubuntu tries to move some data from RAM to swap. 

Today i saw that in this moment xorg process takes over 400MB of RAM. I think it is really too much. I have all special interface futures (like  shadows, animated hiding of windows) disabled. Also Firefox takes a lot of memory but in this case i know that this is typical for Fx ;)  

What can i do to prevent xorg from consuming memory?

I use Ubuntu 9.04, Gnome. This computer is laptop

btw. i had swappines setted  to 5 so i expect that this was the reason that Ubuntu first fill RAM and when it is close to be full, Ubuntu moves data to disk in swap. No i turned swappines to 20, but first of  all i want to set Ubuntu not use any memory too much. I cannot  understand why xorg needs so much memory. At old computer xorg never needed over  100MB, typically about 40MB. Now when i am writing this, 20 minutes  after restarting system, xorg uses 86MB

---

