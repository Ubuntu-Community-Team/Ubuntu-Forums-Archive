---
title: "Conky Problem"
date: 2007-03-16
forum: Desktop Environments
---

### Post by Aliarse on 2007-03-16
Ok, so i've just installed conky via the command line (sudo apt-get install conky), but whenever i try to run it, it spits out this error..

"Conky: attempting to use more CPUs then you have!
obj->data.cpu_index 2 info.cpu_count"

Does anyone know how to fix this?

---

### Post by Aliarse on 2007-03-16
Bump

---

### Post by taurus on 2007-03-16
Do you have ~/.conkyrc and what does it look like?

Applications -> Accessories -> Terminal
[coe]cat ~/.conkyrc[/code]

---

### Post by Aliarse on 2007-03-16
> **taurus said:**
> Do you have ~/.conkyrc and what does it look like?

Applications -> Accessories -> Terminal
[coe]cat ~/.conkyrc[/code]

Here's my ~/.conkyrc file.

---

### Post by jhenager on 2007-03-16
I'd have just kept adding CPUs until Conky was happy.
j/k.
BTW, what was the fix? I never was able to get my temps to work right. That conkyrc file is a bit overwhelming.
I ended up running gkrellm, and that provides everything I needed, and it was much easier.

---

### Post by Aliarse on 2007-03-16
jhenager - I replaced my Conkyrc file with another i found on here which solved it.

While i'm here, i have another Conky problem if anyone would like to help. 

I've just made my own Conkyrc file setup how i want it, but whenever i click on the desktop, Conky vanishes from my desktop until i switch to another desktop and its there again on THAT desktop, until i click on the desktop again. But it never comes back to the first one unless i restart conky.. :confused:
 
Anyone know what the problem is in my conkyrc? Here's my .conkyrc file for the more experienced Conky folks to look at...

```
double_buffer yes
use_spacer no
update_interval 1.5
draw_shades no
maximum_width 1440
minimum_size 100
own_window yes
own_window_type desktop
own_window_transparent yes
draw_outline no
draw_borders no
draw_graph_borders yes
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-35-*-*-*-*-*-*-*
xftfont Veranda:size=7
#xftalpha 0.15
use_xft yes
font Veranda:size=7
uppercase no
default_color grey
#alignment bottom_left
on_bottom no
gap_x 120
gap_y 20

# This is what gets displayed on screen
TEXT
IP : ${addr ppp0} / Down : ${downspeed ppp0} KBps Up : ${upspeed ppp0} KBps / ${alignc}System Uptime : ${uptime} / Hostname : ${nodename} / Kernal Version : ${kernel} / AMD Athlon XP 2200+ @ ${freq}Mhz / Cpu Use : ${Cpu}% / Memory : ${mem}/${memmax} - ${memperc}% Used / Load Average : ${loadavg}
```

---

### Post by Aliarse on 2007-03-16
Maybe this video can explain it better then i did above? :lolflag:

_[http://video.google.co.uk/videoplay?docid=8767927157260254071](http://video.google.co.uk/videoplay?docid=8767927157260254071)_[URL="http://www.flurl.com/item/Conky_Problem_u_237877"]
[/URL]

---

### Post by Peverel on 2007-06-02
One question from a Conky noob...

Where shall I put the conkyrc file? I know it's in this tarball but where should I extract it and if I change the whole file to one of the script codes, does this script then show up?

Sorry, but totally new to this...

---

### Post by taurus on 2007-06-02
> **Peverel said:**
> One question from a Conky noob...

Where shall I put the conkyrc file? I know it's in this tarball but where should I extract it and if I change the whole file to one of the script codes, does this script then show up?

Sorry, but totally new to this...

The .conkyrc should be in your $HOME directory because conky will look for one there.

```
~/.conkyrc
```

---

### Post by Peverel on 2007-06-02
/home/(username)/.conkyrc: command not found

Should I copy the example conkyrc file to my home directory?

Thanks

---

### Post by taurus on 2007-06-02
Yes.  You need to have a ~/.conkyrc before you can run it.  If you need an example, here is a place.

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by Peverel on 2007-06-03
Hm, well I have this conkyrc file (I just extracted the sample conkyrc and renamed it to just conkyrc...) and copied to my home directory. But when I change it to one of the example conkyrcs from the sourceforge page, the display won't change...

Sorry, but I just wanna get this thing customized, it's really cool but it doesn't show my internet connection for example...where is this conkyrc file....????

Thanks for the support so far!

---

### Post by taurus on 2007-06-03
When you make a change to your .conkyrc, you need to restart conky again or else it will just use the old version of your config.

What's the output of this command from a terminal?

```
ls -la ~/.conkyrc
```

---

### Post by Peverel on 2007-06-03
I did restart it again...

Here's the output:

-rw-r--r-- 1 username username 6150 2007-06-03 02:37 /home/username/.conkyrc

---

### Post by taurus on 2007-06-03
What does conky look like on your desktop?  Include a screenshot if you want to show it.  You can also post your ~/.conkyrc here if you want.

```
cat ~/.conkyrc
```

---

### Post by Peverel on 2007-06-12
Hi,

Sorry, I forgot to post...
Problem is solved, I found out that I always edited the conkyrc instead of .conkyrc ...

Thanks anyways for your support :)

---

