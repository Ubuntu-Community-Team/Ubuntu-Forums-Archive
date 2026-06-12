---
title: "Looking for help to change the face of Ubuntu 9.04 to look like the Mac OS."
date: 2009-07-14
forum: Desktop Environments
---

### Post by Mrcollegeman on 2009-07-14
[SIZE=3][COLOR=DarkRed]Hello, I would like to know has anyone out here in the internet world had any luck as to making the new Ubuntu 9.04 [/COLOR][/SIZE][SIZE=3][COLOR=DarkRed]look [/COLOR][/SIZE][SIZE=3][COLOR=DarkRed]like the Mac OS with out having any problems?[/COLOR]  [/SIZE][SIZE=3][COLOR=DarkRed]I had at one point done Ubuntu 8.10 but its like I am having trouble now since they have changed the package to the *Mac4Lin_v1.0_RC1 it is totally different now*[/COLOR][/SIZE][SIZE=3][COLOR=DarkRed].  [/COLOR][/SIZE][SIZE=3][COLOR=DarkRed]I love the Ubuntu 9.04 as well as Apple I just want to have the look of Apple using Ubuntu 9.04. If there is some one out there who can help me it would really be helpful.  Please feel free to e-mail me or IM me if you have yahoo instant messenger at [EMAIL="Twopaid1@yahoo.com"]Twopaid1@yahoo.com[/EMAIL]..
[/COLOR] 

[/SIZE]                                                                                      [SIZE=3][COLOR=DarkRed] Mrcollegeman[/COLOR] ):P[/SIZE]

---

### Post by Dave_Connor on 2009-07-14
Not to be a pest but instead of trying to make your OS look like another. Try creating your own look and feel instead of just trying to copy another. That is the great thing with GNU/Linux is the freedom to customize. I would give it a try, you can create some very nice interfaces with compiz and conky :)

---

### Post by Possum Films on 2009-07-14
There are several themes that look like Mac OS X on [gnome-look.org]("http://www.gnome-look.org"). You should also install the package cairo-dock to get a dock similar to the one in Mac OS. I'm not sure how to get menu bars to work the way they do in Mac OS but I'm sure that it is possible.

---

### Post by b.a.w on 2009-07-14
You should search for the Mac4Lin project. There is an extensive thread in the Ubuntu Forums and there is documentation online. The guides are pretty easy to follow.

---

### Post by Mrcollegeman on 2009-07-15
[COLOR=DarkRed]This is for Dave Connor:[/COLOR][COLOR=DarkRed]

O.K thank-you for the ideal, I have downloaded the conky, compiz[/COLOR] [COLOR=DarkRed]is already install.  Now can you give me some kind of look or ideals as to what I should make Ubuntu 9.04 look like on my own?  I kind of want my own look and not Apple I will just wait until I get my Apple Notebook..[/COLOR]

---

### Post by Dave_Connor on 2009-07-15
Here is my  conky config if you need a base to create off. I run several instances of conky with my dual monitor setup to have in several places. 
```

.conkyrc

gap_x 2750
gap_y 50
update_interval 1.0

double_buffer yes
own_window no

use_xft yes
xftfont Matrix:size=20

maximum_width 800
default_color ffffff
alignment top_right

uppercase no

draw_shades

TEXT
System: $nodename $machine $kernel: $sysname}
Time: ${time %l:%M %P %a %h %e %Y}
Monitor: $monitor_number
Users: $user_number
CPU: ${freq_g} Mhz - in use: $cpu%
Process: $processes - Running: $running_processes
Process on CPU1: ${cpu cpu1}
Process on CPU2: ${cpu cpu2}
Process on CPU3: ${cpu cpu3}
Process on CPU4: ${cpu cpu4}
Top:
Name: PID: CPU: Mem:
${top name 1} $alignr ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4} ${top mem 4}
Network:LAN - ${addr eth1}
RAM: $mem of $memmax $memperc%
Cached: $cached
${membar 20 30}
Swap: $swap of $swapmax $swapperc%
${swapbar 20 30}

```

Conky is great, very quick, low on memory and very flexible.

---

### Post by anchorschmidt on 2009-07-15
There is an awesome iconset called Macultimate Leopard [here]("http://www.gnome-look.org/content/show.php/MacUltimate+Leopard?content=82844")

---

