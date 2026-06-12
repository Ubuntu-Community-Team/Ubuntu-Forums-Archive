---
title: "Karmic X64 eats all my memory"
date: 2009-12-21
forum: Desktop Environments
---

### Post by Sniffer on 2009-12-21
Hi,

I think this is a straight one, i have a test laptop with 3gb RAM and i decided to put Karmic X64 on it special because i want to use VMWARE Work. and 64 bits OS.

It's a minimal install with openbox and tint2 and it start consuming 350mb ram...then after about 30 minutes.....its consuming ALL my 3GB of RAM and using even SWAP!!!! 7MB of Swap... in X86 my swap as always = to 0 and my ram come to the top only when pushed....

Open apps.

NM APPLET
FIREFOX WITH 2 TABS
SKYPE 
EKIGA and nothing more....

Is this normal...it kind reminds me of AWE on SQL that reserve memory....

Thanks

Mem:   3052180k total,  3021644k used,    30536k free,    70052k buffers
Swap:  3293284k total,     7036k used,  3286248k free,  2401016k cached

---

### Post by tribaal on 2009-12-21
What's the output of "free -m"?
You can sort running programs by memory consumption in "top":
- Launch "top" in a terminal
- Open the "sorting" screen (press Ctrl-O)
- press "n" to sort by resident memory, then "enter"
Maybe this helps you figuring out what's eating up your RAM?

Also, maybe you want to check the link in my sig.

Cheers,

- Trib'

---

### Post by Sniffer on 2009-12-21
> **tribaal said:**
> What's the output of "free -m"?
You can sort running programs by memory consumption in "top":
- Launch "top" in a terminal
- Open the "sorting" screen (press Ctrl-O)
- press "n" to sort by resident memory, then "enter"
Maybe this helps you figuring out what's eating up your RAM?

Also, maybe you want to check the link in my sig.

Cheers,

- Trib'

Thanks for the input.

Yes i see this by top, the free -m just confirm it:

Mem:          2980       2955         25          0         69       2341
-/+ buffers/cache:        544       2436
Swap:         3216          6       3209


The top process is Firefox with 172mb R Memory.....about 5.5% of my total memory....

xorg come second with 1.1% of total....where the hell is my memory being used......:P

i have open this thread because i have used top..and this is the info i have.....maybe this is a leak from somewhere...i'm using tint2 lucid package....could it be....

---

### Post by Sniffer on 2009-12-21
OK Problem SOLVED.

Keep the warning TOP is fooling me, when running top from cli it says that all my ram is being used....

When i installed gnome system monitor it says that my system is using 19.1% of total memory, 561 MB to be exact...

The question....Why top is giving wrong info....it was putting me crazy when i search for PID that dont exist....great.....:)

---

