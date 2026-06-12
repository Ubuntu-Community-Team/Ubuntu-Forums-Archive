---
title: "Conky Automagically updated mount space script"
date: 2009-02-02
forum: General Help
---

### Post by wynneth on 2009-02-02
Alright, this is my first shell script, I'm fairly new to linux, and my programming experience consists of html/dhtml/css/BASIC

I wrote a shell script to get non system created mounts store to a file, iterate to display the free space etc for each mount point. That way you can have it list ALL mounts, for instance when you plug in a USB drive, without having to manually edit the conky config then. Somehow on the third/last iteration it's transposing and giving me weird output. The script is called from my conky config with execpi 300, and here is the script:

```

#! /bin/sh
grep -v -F -f .conkmtab /etc/mtab > ~/conkmtabs | cut -d" " -f1,2 conkmtabs > conkymtabs
conklines=`wc -l conkymtabs | cut -d" " -f1`
if [ -n "$conklines" ]; then
count=$conklines
fi

while [ $count -ge 0 ]

do
echo '$color${fs_used '`sed -n "$count p" conkymtabs | cut -d" " -f2`'} ${fs_size '`sed -n "$count p" conkymtabs | cut -d" " -f2`'}${alignr}${color #0077ff}${fs_bar 5,120 '`sed -n "$count p" conkymtabs | cut -d" " -f2`'}$color'
count=`expr $count - 1`
done

```

The output looks like this:
16.00GiB 37.21Gib   (the bar graph is here)
33.64Gib 59.88Gib   (the bar graph is here)
${fs_use}d

See? The third iteration is displaying a portion of the conky code used in the script, but somehow has eliminated the entire sed section and transposed the d and the }
What happened? If we fix this, this is a lovely script - whether ya'll think so or not :-P

---

### Post by wynneth on 2009-02-02
Haha as usual I seem to be working my own problem out!

Changed the script to:
```

#! /bin/sh
if [ -s "conkymtabs" ]; then
	conklines=`wc -l ~/conkymtabs | cut -d" " -f1`
	if [ -n "$conklines" ]; then
		count=$conklines
	else count=1
	fi
else echo Its ******
fi

while [ $count -gt 0 ]

do
echo '$color${fs_used '`sed -n "$count p" conkymtabs | cut -d" " -f2`'} ${fs_size '`sed -n "$count p" conkymtabs | cut -d" " -f2`'}${alignr}${color #0077ff}${fs_bar 5,120 '`sed -n "$count p" conkymtabs | cut -d" " -f2`'}$color'
count=`expr $count - 1`
done

```

and the lines in conky to:
```

${execi 200 grep -v -F -f .conkmtab /etc/mtab > ~/conkmtabs | cut -d" " -f1,2 conkmtabs > ~/conkymtabs }
${execpi 300 sh counttest}

```

Now there are two problems. The first is that the grep line does not properly create the conkymtabs file the first time around. The second time conky runs it, it does, so I don't know what's up with that. Basically the first run it blanks out ~/conkymtabs
Problem number two is that in conky I still get the same freaky output on iteration number 3. Manually running the script in terminal gives normal results, so somehow the problem is between the script and conky.
If I run the script in terminal -x I get:
```

wynneth@wilykat:~$ sh -x counttest
+ [ -s conkymtabs ]
+ wc -l /home/wynneth/conkymtabs
+ cut -d  -f1
+ conklines=3
+ [ -n 3 ]
+ count=3
+ [ 3 -gt 0 ]
+ sed -n 3 p conkymtabs
+ cut -d  -f2
+ sed -n 3 p conkymtabs
+ cut -d  -f2
+ sed -n 3 p conkymtabs
+ cut -d  -f2
+ echo $color${fs_used /home/wynneth/slavefs} ${fs_size /home/wynneth/slavefs}${alignr}${color #0077ff}${fs_bar 5,120 /home/wynneth/slavefs}$color
$color${fs_used /home/wynneth/slavefs} ${fs_size /home/wynneth/slavefs}${alignr}${color #0077ff}${fs_bar 5,120 /home/wynneth/slavefs}$color
+ expr 3 - 1
+ count=2
+ [ 2 -gt 0 ]
+ sed -n 2 p conkymtabs
+ cut -d  -f2
+ sed -n 2 p conkymtabs
+ cut -d  -f2
+ sed -n 2 p conkymtabs
+ cut -d  -f2
+ echo $color${fs_used /mnt/win} ${fs_size /mnt/win}${alignr}${color #0077ff}${fs_bar 5,120 /mnt/win}$color
$color${fs_used /mnt/win} ${fs_size /mnt/win}${alignr}${color #0077ff}${fs_bar 5,120 /mnt/win}$color
+ expr 2 - 1
+ count=1
+ [ 1 -gt 0 ]
+ sed -n 1 p conkymtabs
+ cut -d  -f2
+ + sed -n 1 p conkymtabs
cut -d  -f2
+ sed -n 1 p conkymtabs
+ cut -d  -f2
+ echo $color${fs_used /} ${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}$color
$color${fs_used /} ${fs_size /}${alignr}${color #0077ff}${fs_bar 5,120 /}$color
+ expr 1 - 1
+ count=0
+ [ 0 -gt 0 ]

```

But as I said, conky still displays the third line as:
```

${fs_use}d

```

In short, WTF?

---

### Post by wynneth on 2009-02-02
aaaah hahahaha Ok so the problem is the / that is being passed to the fs_used via a variable. Somewhere along the parsing it's interpreting the / as a command rather than part of the fs_used line. Since I'm obviously helping myself here, I'll go do some googling and research on possibly doing something like escaping the / character or something similar.

---

### Post by wynneth on 2009-02-02
Forget it, I'll just exclude the root line and manually add root to the conky config. Problem SOLVED, no thanks to you.

---

### Post by wynneth on 2009-02-09
> **wynneth said:**
> Forget it, I'll just exclude the root line and manually add root to the conky config. Problem SOLVED, no thanks to you.

LOL - It was an an issue requiring the use of a larger text_buffer_size

---

### Post by wynneth on 2009-02-21
FYI this script and info can now be found via [http://www.wynneth.com/2009/02/02/conkymounts-script-by-wyn-my-custom-conky-config/]("http://www.wynneth.com/2009/02/02/conkymounts-script-by-wyn-my-custom-conky-config/")

---

### Post by wynneth on 2009-02-25
Forget that mess, just use this (new and improved by me!)
```
${execpi 30 grep -v -E ^fuse\|^udev\|^lrm\|^securityfs\|^binfmt\|^devpts\|^tmpfs\|^varlock\|^varrun\|^sysfs\|^\/proc /etc/mtab | cut -d" " -f2 | while read line ; do
echo $line '${goto 160}${fs_used '$line'} ${alignr}${fs_size '$line'}'
done }
```

---

### Post by falen_pl on 2009-07-07
You gotta love the way you converse with yourself...asking questions and then replying to them :D:D

Awesome :D

---

### Post by maheshasolkar on 2009-07-07
If you want beans, just ask for them :p

---

### Post by wynneth on 2009-07-08
LOL. Well, no one else was jumping in to help my train of code... Sometimes you just have to bounce ideas off.. YOURSELF.

---

### Post by dumblebee100 on 2009-07-13
> **wynneth said:**
> Forget that mess, just use this (new and improved by me!)
```
${execpi 30 grep -v -E ^fuse\|^udev\|^lrm\|^securityfs\|^binfmt\|^devpts\|^tmpfs\|^varlock\|^varrun\|^sysfs\|^\/proc /etc/mtab | cut -d" " -f2 | while read line ; do
echo $line '${goto 160}${fs_used '$line'} ${alignr}${fs_size '$line'}'
done }
```

Hey buddy ..I tried your script working fine with default things ..but I need some more from your script ...fs_bar ..

when I inserted that thing into the script then I get error ..near done ..something like that ..can you please help in this issue ..

---

### Post by wynneth on 2009-07-13
> **dumblebee100 said:**
> Hey buddy ..I tried your script working fine with default things ..but I need some more from your script ...fs_bar ..

when I inserted that thing into the script then I get error ..near done ..something like that ..can you please help in this issue ..

You're likely getting an error: ```
sh: Syntax error: end of file unexpected (expecting "done")
```

I've only glanced at it but it seems the statement can't handle that many quoted variables at once. I'll have to look into that further when I have time, for now it would seem you can only do two options for it, so pick your favorite two, of fs_size fs_free fs_used fs_bar. LOL. I'll see what I can come up with later...

---

