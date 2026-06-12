---
title: "help about conky"
date: 2012-05-18
forum: Desktop Environments
---

### Post by dik angga on 2012-05-18
hello everyone i have 1 problem with my conky..
i applied new conkyrc from my friend, and that conky have a border, it's not look good. how to solve it..??

conky view: 
[IMG]http://a1.sphotos.ak.fbcdn.net/hphotos-ak-ash3/578191_439999652676868_100000005127356_1719619_57979800_n.jpg[/IMG]

and this the conkyrc script:

> 



# Conky settings #
background override
update_interval 1

override_utf8_locale yes

double_buffer yes
no_buffers yes

text_buffer_size 2048

# Window specifications #
own_window yes
own_window_class conky
own_window_transparent yes
own_window_hints undecorate,below,sticky,skip_taskbar,skip_pager

border_inner_margin 0
border_outer_margin 0

alignment bl
gap_x 100
gap_y 100

# Graphics settings #
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no

# Text settings #
use_xft yes
xftalpha 0
text_buffer_size 2048

uppercase no

default_color FFFFFF


TEXT
${voffset 10}${font Ubuntu Light:size=50}${time %A}${font}${voffset -10}
${voffset 10}${font Ubuntu Light:size=50}${time %B} ${time %e}${font}${voffset -10}
${voffset 10}${font Ubuntu Light:size=100}${time %I:%M %p}${font}${voffset -10}what should i do guys..??
please help me

[edited]

this problem is solved..

---

### Post by Frogs Hair on 2012-05-18
I was able to remove the border , but conky disappears and reappears when the desktop is clicked . I will try some other options and get back to you.

---

### Post by Frogs Hair on 2012-05-18
I was unable to remove the border and keep conky from disappearing and reappearing when clicking on the desktop.

---

### Post by dik angga on 2012-05-18
> **Frogs Hair said:**
> I was unable to remove the border and keep conky from disappearing and reappearing when clicking on the desktop.

so what should i do..??

---

### Post by Frogs Hair on 2012-05-18
> **dik angga said:**
> so what should i do..??

Use as is until someone is able to help you .   I was trying different options on the end of this line .```
own_window yes
```  I tried override , desktop  and conky . As I wrote I could remove the outline ,but It still didn't work properly .

---

### Post by dik angga on 2012-05-18
> **Frogs Hair said:**
> Use as is until someone is able to help you .   I was trying different options on the end of this line .```
own_window yes
```  I tried override , desktop  and conky . As I wrote I could remove the outline ,but It still didn't work properly .

thanks brother..
bytheway i solved that problem my self..
i delete this line
```
# Conky settings #
background override
update_interval 1
```

i try adding this:
```
# Window Settings
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager
```

and that damn borders is disappear.. :guitar::guitar: yheah..!

mybe this way can solve your conky too

---

### Post by Face-Ache on 2012-05-18
dik, i had the same issue as you - when i restarted Conky from the desktop after Ubuntu had booted, it was fine, no border. But at login/startup, it kept appearing with a border.

The guys in the 'Post your .conkyrc files' files thread really helped me get it sorted out.

So if it has a border when you reboot or login, try this;
[http://ubuntuforums.org/showpost.php?p=11948558&postcount=19850](http://ubuntuforums.org/showpost.php?p=11948558&postcount=19850)

---

### Post by dik angga on 2012-05-18
> **Face-Ache said:**
> dik, i had the same issue as you - when i restarted Conky from the desktop after Ubuntu had booted, it was fine, no border. But at login/startup, it kept appearing with a border.

The guys in the 'Post your .conkyrc files' files thread really helped me get it sorted out.

So if it has a border when you reboot or login, try this;
[http://ubuntuforums.org/showpost.php?p=11948558&postcount=19850](http://ubuntuforums.org/showpost.php?p=11948558&postcount=19850)

make a delay for conky so start??
and that way solved your problem..?
my problem is solved but i'm not restart my laptop yet. if that happen again i'll try that way...
thanks so much brother

---

