---
title: "DVD video burn problems"
date: 2006-01-17
forum: Desktop Environments
---

### Post by christopher.pascual on 2006-01-17
ok i so i have downloaded a few dvd's from the internet, and they are in the format of VIDEO_TS folders


so i followed some how to's online, and used gnomebaker to burn the contents of the folder, now they work on a standalone dvd player, but there is no menu functionality, and when i insert the dvd, i just get a list of the folders and have to select which on i want to watch


basically it doesn't work very well....



anyone have any experience on what a better way to burn might be?

thanks alot

---

### Post by handy on 2006-01-17
Perhaps they don't include any menu...

That will make them smaller, & if there is a size limit, than can give you better quality video.

Just a thought. :rolleyes:

---

### Post by taurus on 2006-01-17
If you want to watch it on your Linux box, try something like

xine dvd:/dev/hdc

---

### Post by StefanoCole on 2006-01-18
I made a video DVD using DVDShrink under Windows. The DVD contains no menus, only the main title/film but split in more .VOB files and all contained in the directory VIDEO_TS. To watch the DVD with my Ubuntu box I used xine with the following command:

xine dvd://media/cdrom/VIDEO_TS

In this way the DVD is played from the beginning to the end.

Hope this helps, Stefano

---

### Post by StefanoCole on 2006-01-18
You can also try the following:
start from a downloaded DVD, you have it in your hard disc in the folder VIDEO_TS. Check if you are able to watch it from the beginning to the end using xine with the following command:

xine dvd://home/username/path/to_DVD/VIDEO_TS

If yes you can burn it with:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video path/to_DVD/

where /dev/dvdrw is the DVD burner and path/to_DVD/ the directory containing the VIDEO_TS folder

Stefano

---

### Post by aev on 2006-11-02
> **StefanoCole said:**
> You can also try the following:
start from a downloaded DVD, you have it in your hard disc in the folder VIDEO_TS. Check if you are able to watch it from the beginning to the end using xine with the following command:

xine dvd://home/username/path/to_DVD/VIDEO_TS

If yes you can burn it with:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video path/to_DVD/

where /dev/dvdrw is the DVD burner and path/to_DVD/ the directory containing the VIDEO_TS folder

Stefano

Thanks man,

that worked. Except that I replaced /dev/dvdrw with /dev/dvd only.:cool: 
Just looked online and it said /dvd . Dont know if there is any difference but it works now.

---

### Post by 1002285 on 2007-02-14
> **StefanoCole said:**
> You can also try the following:
start from a downloaded DVD, you have it in your hard disc in the folder VIDEO_TS. Check if you are able to watch it from the beginning to the end using xine with the following command:

xine dvd://home/username/path/to_DVD/VIDEO_TS

If yes you can burn it with:

growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video path/to_DVD/

where /dev/dvdrw is the DVD burner and path/to_DVD/ the directory containing the VIDEO_TS folder

Stefano

I want to burn a movie from video_ts, too, but when trying your recommended command - terminal said bash: xine: command not found

ANd can iso-s be burned this way?

I did try the 
growisofs -speed 1 -dvd-compat -Z /dev/dvdrw -dvd-video etc
command with both dvdrw and dvd
and only got the answer:

Executing 'mkisofs -dvd-video /home/ml/Videod/MASTER_AND_MARGARITA_1/VIDEO_TS | builtin_dd of=/dev/dvdrw obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: Unable to make a DVD-Video image.
:-( write failed: Input/output error

Why could it have failed?

---

