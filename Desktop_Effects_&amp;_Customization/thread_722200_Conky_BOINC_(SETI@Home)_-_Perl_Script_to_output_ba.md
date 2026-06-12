---
title: "Conky BOINC (SETI@Home) - Perl Script to output basic data"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by hodge24 on 2008-03-12
Hi all,

I've just written a really quick and dirty Perl script to output some basic BOINC client (SETI@Home) data to Conky. It's really nothing special at the moment (I don't purport to be a Perl Pro - I've not written Perl for 10+ years, and I've also been incredibly ill with some nasty jungle bug the past few days, hehehe :lol:), and can definitely be a hell of a lot better! I'll do some more work on it, but it's a start, if anyone is interested in using it :)

The script is attached to this thread (along with a screenshot), as a tar.gz, so you just need to download it, and extract (open a Terminal Window first)

```
tar -zxvf boinc.pl.tar.gz
```

Then copy it to wherever you want (I have mine in ~/ConkyScripts/boinc), make it executable:

```
sudo chmod a+x boinc.pl
```

then insert a line (or two) into .conkyrc to execute the script:

```
BOINC:
${execi 10 perl ~/ConkyScripts/boinc/boinc.pl}
```

I'll post any updates to the script on this thread, and also on my blog, [64 Bit Jungle]("http://www.64bitjungle.com") (the original blog post is [here]("http://www.64bitjungle.com/tech/boinc-and-setihome-with-conky-on-ubuntu/"))

Anyway, I hope that it helps someone.

Cheers, and take care,

Hodge.

---

### Post by hodge24 on 2008-03-19
I've updated the script, so it should work with multiple BOINC projects.

Hope it helps.

Cheers,

Hodge.

---

### Post by cam217 on 2008-05-24
Thank you man, im trying to get it work :)

---

### Post by cam217 on 2008-05-24
I have troubles with your script, it doesn't display all it should but I don't know why and I hope you can help me (i dont know Perl). I really think that your script is usefull and thank you for that.

May I suggest things? :)
I don't care about the name of the work unit (because it means nothing) but it could be interesting to display the application of the work unit instead. Maybe a bar displaying the progress shoud be another idea. I hope you won't take those ideas as critics, I just want that script as usefull as possible to get it to ubuntu-fr with your permission ;)

---

### Post by hodge24 on 2008-05-25
> **cam217 said:**
> I have troubles with your script, it doesn't display all it should but I don't know why and I hope you can help me (i dont know Perl). I really think that your script is usefull and thank you for that.

May I suggest things? :)
I don't care about the name of the work unit (because it means nothing) but it could be interesting to display the application of the work unit instead. Maybe a bar displaying the progress shoud be another idea. I hope you won't take those ideas as critics, I just want that script as usefull as possible to get it to ubuntu-fr with your permission ;)

Hi cam217,

No problem, I don't take your ideas as criticism :) - you've posted some good ideas, which I'll try and incorporate into the script.

Can you possibly run the script from the terminal, and post the output for me? You can run it by going to the directory you have copied it to, an executing:

```
./boinc.pl
```

It should output the BOINC data directly to the terminal. Can you also post your boincrc file? I'll take a look at the results and see if I can debug it for you.

Thanks for your interest in the script, and of course, you can distribute it if you like :)

---

### Post by cam217 on 2008-05-25
Thanks for helping me :)

Here's my output for boinc.pl

```
cam@hardy:~/.conky$ ./boinc.pl
Number of Work Units: 9, Active Work Units: 2
Einstein@Home
Work Unit  :  h1_1060.85_S5R3__512_S5R3b_0
CPU Time: 3:26:10 Time Remaining: 2:31:17
57.6763% Complete
proteins@home
SETI@home
Work Unit  :  18ap08ag.13916.26743.6.8.219_0
CPU Time: 1:7:43 Time Remaining: 1:31:58
42.4089% Complete
WorldCommunityGrid
Work Unit  :  dddt0302j0600_100186_0
CPU Time: 2:29:17 Time Remaining: 0:48:54
75.3248% Complete
Work Unit  :  faah4246_NSC79594_adt_xmd12070_03_1
CPU Time: 0:52:53 Time Remaining: 3:44:11
19.088% Complete
RieselSieveProject
Work Unit  :  riesel-llr_469949-3112988_1
CPU Time: 3:22:14 Time Remaining: 3:29:18
49.14% Complete
Work Unit  :  riesel-llr_162941-3112990_1
CPU Time: 0:41:56 Time Remaining: 5:31:8
11.24% Complete
```

I don't know where is boinrc file, I searched for it with locate command but got no result...
When I will put your script to ubuntu-fr I will put a link to your blog too ;)

---

### Post by hodge24 on 2008-05-25
lol, sorry, I mean you're .conkyrc file! Can't think straight at the moment - not getting much sleep now I have a 2 month old baby, lol!

---

### Post by cam217 on 2008-05-26
Hello,

I'm at work so im looking for a post I made on ubuntu-fr for my conkyrc files. If I can't find it, I'll post the current conkyrc files tonight.

EDIT: I just find it. So I have 4 conkyrc files and a script which launching the conkyrc files.

Script:
```
#!/bin/bash
feh --bg-scale `dcop kdesktop KBackgroundIface currentWallpaper 1`;   #transparence conky pour kde
sleep 5 && killall conky;    #attente de 5 secondes avant de lancer conky
sleep 1 && conky -u 1 -d -c ~/.conky/conkyrc
sleep 1 && conky -u 2 -d -c ~/.conky/conkyrc_drives
sleep 1 && conky -u 3 -d -c ~/.conky/conkyrc_log
sleep 1 && conky -u 4 -d -c ~/.conky/conkyrc_amarok
exit
```

conkyrc:
```
TEXT
${alignr}${color #FFFFDD}Uptime ${color #5CBAD3}${uptime_short}
${alignr}${color #FFFFDD}Kubuntu Hardy Heron ${color #5CBAD3}$kernel
${alignr}${color #FFFFDD}Intel Core2Duo @ $freq_dyn_g GHz ${color #5CBAD3}${cpu cpu} %
${alignr}${color #FFFFDD}Ram used ${exec free -m | awk '$0~"-/+" {print $3}'} Mo  |  Ram cached ${exec free -m | awk '$0~"Mem" {print $7}'} Mo  |  Total $mem/$memmax ${color #135B6F}$memperc %${color #FFFFDD}
${alignr}Download ${color #5CBAD3}${downspeed eth0} k/s ${color #FFFFDD} |  Upload ${color #5CBAD3}${upspeed eth0} k/s

${alignr}${color #FFFFDD}BOINC
${alignr}${execi 10 perl ~/.conky/boinc.pl}
```

conkyrc_drives:
```
TEXT
${alignc}${color #FFFFDD}/ ${fs_used /} / ${fs_size /}${color #5CBAD3} ${fs_free_perc /} % free${color #FFFFDD}  |  /home ${fs_used /home} / ${fs_size /home}${color #5CBAD3} ${fs_free_perc /home} % free${color #FFFFDD} | Etch ${fs_used /media/etch} / ${fs_size /media/etch}${color #5CBAD3} ${fs_free_perc /media/etch} % free  ${color #FFFFDD} |  Etch home ${fs_used /media/etch_home} / ${fs_size /media/etch_home}${color #5CBAD3} ${fs_free_perc /media/etch_home} % free  ${color #FFFFDD}| Janbeuhnoix ${fs_used /media/janbeuhnoix} / ${fs_size /media/janbeuhnoix}${color #5CBAD3} ${fs_free_perc /media/janbeuhnoix} % free${color #FFFFDD} | Share ${fs_used /media/share} / ${fs_size /media/share}${color #5CBAD3} ${fs_free_perc /media/share} % free${color #FFFFDD} | Windows ${fs_used /media/windows} / ${fs_size /media/windows}${color #5CBAD3} ${fs_free_perc /media/windows} % free  ${color #FFFFDD}
```

conkyrc_log:
```
TEXT
${alignr}${color #FFFFDD}/var/log/messages
${alignr}${exec tail -n4 /var/log/messages}
```

conkyrc_amarok:
```
TEXT
${alignr}${color #FFFFDD}${if_running amarokapp} Amarok
${alignr}${execi 1 ~/.conky/amarok artist}  |  ${execi 1 ~/.conky/amarok album}  |  ${execi 1 ~/.conky/amarok title}
${color #5CBAD3}${execibar 1 ~/.conky/amarok progress}$endif
```

PS: Congratulation for the baby ;)

---

### Post by cam217 on 2008-05-30
Not any clue Hodge? Maybe you're too busy with the child :) I hope you'll find out why im having troubles.

---

### Post by cam217 on 2008-06-05
hello,

I found the problem by myself, the code is right but to display the output in conky we should better use exec instead of execi because in your example in the first postof the topic you advise us to execute the perl script with the command execi in conky.
Execi is used when we wanna display something in a delay and exec without any delay.
That's why I didn't get right thing. Now all is cool, awesome work dude ^^

---

