---
title: "Wallpaper changes that mimic sunrise/sunset &amp; moonrise/moonset"
date: 2007-05-26
forum: Desktop Environments
---

### Post by rshetye on 2007-05-26
You can produce brightened or darkened images using the following script

```

[rshetye:1] ~/bin : cat darken-images

```

```

#!/usr/bin/env tcsh

set Usage="$0 <image file> <darkening factor>\n \
    where darkening factor is as follows:\n \
    0-99    darken\n \
    100     normal brightness\n \
    101-255 brighten"

if ($#argv != 2) then
    echo Usage: $Usage
    exit
endif

set image_file=$1
set mod_value=$2

set image_fileroot=`basename $1 | sed 's#\.[^\.]*$##g'`

convert ${image_file} -modulate ${mod_value} ${image_fileroot}-modulate-${mod_value}.jpg

```


Set the background in GNOME using the following script

```

[rshetye:1] ~/bin : cat background

```
> 
#!/usr/bin/tcsh

gconftool-2 -s "/desktop/gnome/background/picture_filename" "$1" -t string



The following crontab commands will kick in as per schedule and change the background using the earlier script. Use *crontab -e* to edit the crontab settings local to your user.

You'll have to locate the greenmeadow and bluemeadow images yourself, cos I am not able to upload them. Will try later...

```

[rshetye:1] ~ : crontab -l

```

> # m h  dom mon dow   command

# 6:00-6:30 a.m. sunrise (10-60)
00  6  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-10.jpg
10  6  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-20.jpg
15  6  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-30.jpg
20  6  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-40.jpg
25  6  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-50.jpg
30  6  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-60.jpg

# daytime
30  7  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-70.jpg
00  9  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-80.jpg
30 10  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-90.jpg
00 12  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-100.jpg
00 13  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-110.jpg
30 13  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-120.jpg
30 14  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-110.jpg
00 15  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-100.jpg
30 16  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-90.jpg
00 17  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-80.jpg
30 17  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-70.jpg

# 6:00-6:30 p.m. sunset (60-10)
00 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-60.jpg
05 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-50.jpg
10 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-40.jpg
15 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-30.jpg
20 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-20.jpg
25 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/greenmeadow-modulate-10.jpg



# 6:30-6:45 p.m. moonrise (10-60)
30 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-10.jpg
32 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-20.jpg
35 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-30.jpg
40 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-40.jpg
42 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-50.jpg
45 18  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-60.jpg

# nighttime
30 19  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-70.jpg
00 21  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-80.jpg
30 22  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-90.jpg
00 00  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-100.jpg
00  1  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-110.jpg
30  1  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-120.jpg
30  2  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-110.jpg
00  3  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-100.jpg
30  4  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-90.jpg
00  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-80.jpg
30  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-70.jpg

# 5:45-6:00 a.m. moonset (60-10)
45  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-60.jpg
48  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-50.jpg
50  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-40.jpg
52  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-30.jpg
55  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-20.jpg
58  5  * * * /home/rshetye/bin/background /home/rshetye/.wallpapers/bluemeadow-modulate-10.jpg


---

### Post by Gen2ly on 2007-05-26
Did you mean to put this in tips and tutorials.  Nice work though, when theres a chance I will try it.  Currently I'm having Install Errors :(

---

### Post by rshetye on 2007-05-27
> **Dirk.R.Gently said:**
> Did you mean to put this in tips and tutorials.  Nice work though, when theres a chance I will try it.  Currently I'm having Install Errors :(

Ya, didn't know which sub-forum was  the best, so thought that Desktop was close enough.

Can a mod please move this thread to the best sub-forum ? thanks.

---

### Post by abhiroopb on 2008-06-03
Sounds like a good idea, but really confused about what I have to do!! I created the two files (darken-image, background), but I have no idea what to do after that! cron, etc is all foreign to me! :(

---

