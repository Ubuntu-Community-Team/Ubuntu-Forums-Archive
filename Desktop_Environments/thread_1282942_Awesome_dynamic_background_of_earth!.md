---
title: "Awesome dynamic background of earth!"
date: 2009-10-05
forum: Desktop Environments
---

### Post by x C0MMAND0 x on 2009-10-05
I take no credit for this, just thought I would share.  See attached screenshot and script.

Here are some steps to have the background on your computer be a real satellite image of the earth, that changes and shows storms and shadows in somewhat real time.

1. Download attached script called "earth-wallpaper-changer-cron.sh"

2. Open terminal and navigate to directory you downloaded to.  Make the file executeable by running ```
chmod a+x earth-wallpaper-changer-cron.sh
```

3. Open up your scheduled tasks. ```
crontab -e
```

4. Add the following code as an entry```
*/15 * * * * /path/to/script/earth-wallpaper-changer-cron.sh > /dev/null 2> /dev/null

``` and save.  This will set up the task to run every time the hour is able to be divided evenly by 15 minutes, or the same thing as saying it runs 4 times an hour.

5. Final step is go to System > Preferences > Appearance.  Click on the "Background" tab.  Choose "Add" and navigate to /.gnome2/world_sunlight_Wallpaper.jpg

It's pretty awesome!  I'm not sure how often the actual image is updated from the website it's pulling the image from, so I just decided to have the script run every 15 minutes.  Enjoy!

---

### Post by x C0MMAND0 x on 2009-10-05
I did not mean Ubuntu Studio for distro...how do I change that?

---

### Post by Incendia on 2009-10-05
I'm going to try this when I get home :]

---

### Post by x C0MMAND0 x on 2009-10-06
How did it work out for you?

---

### Post by x C0MMAND0 x on 2009-11-03
Just wondering if anybody tried this?

---

### Post by Wyv on 2010-07-03
Ressurrection!

I have started using this after I got interested in the Desktop Earth thing.

I use the images from here:

[http://taint.org/xplanet/]("http://taint.org/xplanet/")

I have it set to refresh once an hour as that is the update frequency of the site and no point in abusing its bandwidth :)

The script works okay, just seeing if cron will pick it up as well.

---

### Post by x C0MMAND0 x on 2010-07-19
Excellent!  Nice website post that has different size images to tailor to each individual display.

---

### Post by ifraser on 2010-10-16
Does this script still work?  Looks great...

---

### Post by x C0MMAND0 x on 2010-10-18
Yes it does

---

### Post by alexan on 2010-10-18
> **Wyv said:**
> Ressurrection!

I have started using this after I got interested in the Desktop Earth thing.

I use the images from here:

[http://taint.org/xplanet/]("http://taint.org/xplanet/")

I have it set to refresh once an hour as that is the update frequency of the site and no point in abusing its bandwidth :)

The script works okay, just seeing if cron will pick it up as well.
It wouldn't more simply if you download 48 png of them on your PC and make them run per half-hour?

---

