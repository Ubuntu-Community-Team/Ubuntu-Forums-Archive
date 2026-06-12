---
title: "rotating background"
date: 2006-01-06
forum: Desktop Environments
---

### Post by ms2542 on 2006-01-06
hi,

Is it possible to have Ubuntu change the background picture on your desktop like every 5 minutes (or whatever time limit you choose)?  

Thanks


Mike

---

### Post by Leif on 2006-01-06
if you google for "rotating gnome background" you'll find several packages that can do this.

---

### Post by nalmeth on 2006-01-06
KDE includes this. 
I did not know that packages could be aquired though. Good to know.

---

### Post by ms2542 on 2006-01-07
FYI:

I found a way to do this.  As suggested earlier, I searched for "gnome rotating desktop" in google and found this site:

[http://www.martinhenze.de/2006/01/04/random-gnome-wallpaper/]("http://www.martinhenze.de/2006/01/04/random-gnome-wallpaper/")

It's important to know a couple of things though:

in crontab -e you must not use what the author wrote:

x * * * * * /path/random_background.pl

what it needs to be after "x * * * * */path" is the actual location.  For example, mine is:

1 * * * * * /path/home/ms2542/random_background.pl

The second part is this:  In order for me to actually run this script I had to open another terminal and put the following in:

watch -n 10 /home/ms2542/random_background.pl

Where the number (10) is the number of seconds you want the picture to change.  

Also, you DON'T need to put the files in ".wallpapers"  This can be any file you like just modify the pearl script accordingly where the line says:

my $pic_path = 

and insert your filename in the quote field.  For example, it says on the website mentioned earlier to use this:

my $pic_path = "/home/martin/.wallpapers/"

Mine says the following:

my $pic_path = "/home/ms2542/pictures/";

I found out if you put a period (.) before any filename Ubuntu hides the file.  It can be a pain to find the file again.

If you have any questions, please ask! 

Thanks


Mike

---

