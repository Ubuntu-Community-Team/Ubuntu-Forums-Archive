---
title: "MPlayer Error"
date: 2005-11-17
forum: Desktop Environments
---

### Post by ColinG on 2005-11-17
Just installed MPlayer and it works fine but on start up I get the following error:

New Face failed. Maybe the font path is wrong. Please supply the text font file (~/.mplayer/subfont.ttf)

Any ideas how I can get this put to rights?

Many thanks

---

### Post by bored2k on 2005-11-17
1. ```
sudo apt-get install mplayer-fonts
```
2. ```
sudo apt-get install msttcorefonts
```
3. ```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
```

---

### Post by ColinG on 2005-11-17
Many, many thanks.

All good to go.

Excellent:KS :KS :KS :KS :KS

---

### Post by bored2k on 2005-11-17
Glad you got that worked out :o).

---

### Post by cvmostert on 2006-02-08
[QUOTE=bored2k]Glad you got that worked out :o).[/QUOTE]

I also had the problem, thanks for the help!

---

### Post by VCSkier on 2006-03-05
[QUOTE=bored2k]3. ```
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf
```[/QUOTE]
i'm having this same problem.  i have mplayer-font and msttcorefonts installed via automatix.  when i try step three, i recieve this error.```
ln: creating symbolic link `/usr/local/share/mplayer/subfont.ttf' to `/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf': No such file or directory
```i'm using mplayer version 1:1.0-pre7cvs20050716-0.1ubuntu9.  thanks for any help!

---

### Post by jazzi on 2006-03-05
Thanks.but it's hard to find here by the simple title
please change the title as:[SIZE="5"]Mlayer new faces error with wrong font path warning[/SIZE]

---

### Post by koukou on 2006-04-23
To VCSkier

Hi,
I had the same problem as you with
sudo ln -s /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf /usr/local/share/mplayer/subfont.ttf

Solution:

1.Open Mplayer
2.Click the tool button on the left  (that should open the preference menu)
3.Go to the font submenu
4.Insert next to where it says "font:"  the following
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/Arial.ttf
5. Press OK

that should fix it....

---

