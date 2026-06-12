---
title: "Conky on Lubuntu"
date: 2012-10-09
forum: Desktop Environments
---

### Post by GeForce 9500GT on 2012-10-09
Hi everyone!

I've got some questions regarding Conky.

1) Does Conky show the upload/download speed of my internet connection using eth0?

2) I don't like that terminal look of Conky and want a nice themelike this:
[http://lh3.ggpht.com/_1QSDkzYY2vc/TFM-djA9HSI/AAAAAAAABos/dIWOjW0ReYU/s2000/conky-colors.png](http://lh3.ggpht.com/_1QSDkzYY2vc/TFM-djA9HSI/AAAAAAAABos/dIWOjW0ReYU/s2000/conky-colors.png)
or:
[http://4.bp.blogspot.com/_1QSDkzYY2vc/TWOFYELY-2I/AAAAAAAADFg/UIw1miynTqs/s2000/conkyx3.png](http://4.bp.blogspot.com/_1QSDkzYY2vc/TWOFYELY-2I/AAAAAAAADFg/UIw1miynTqs/s2000/conkyx3.png)
or:
[http://4.bp.blogspot.com/-5HNLYWpV2xU/TgHknHvSOrI/AAAAAAAAFAg/SxLv584DZvs/s2000/conky_lunatico_rings_1.png](http://4.bp.blogspot.com/-5HNLYWpV2xU/TgHknHvSOrI/AAAAAAAAFAg/SxLv584DZvs/s2000/conky_lunatico_rings_1.png)

I especially like this one: [http://lh3.ggpht.com/_1QSDkzYY2vc/TFM-djA9HSI/AAAAAAAABos/dIWOjW0ReYU/s2000/conky-colors.png](http://lh3.ggpht.com/_1QSDkzYY2vc/TFM-djA9HSI/AAAAAAAABos/dIWOjW0ReYU/s2000/conky-colors.png). 

My question is: how do i setup Conky to use that theme?

3) How do i autostart Conky?

Many thanks in advance!

---

### Post by bra|10n on 2012-10-09
Well of course you'll need conky installed, it's in the repo's...

As a start-up script you can use the following,
```
#!/bin/bash 
sleep 15 
conky -c ~/.conkyrc & 
exit 0
```The script has a delay (15 seconds) and used to time conky to start  just after your desktop loads. Change the delay as required.
Your conkyrc script using the example above, is to reside in your /home, or alternatively, you could create a hidden folder in home, and change the location to something like
 ~/.conky/conkyrc (*note the folder is now hidden, while the file is not*) and place all your conky related scripts, images etc in this single folder keeping them all together.

For subsequent conky's you can simply add another line like this,

```
...
conky -c ~/.conkyrc &
conky -c ~/.conkyrc1 & 
...
```Not too familiar with Lubuntu, but you'll need to name your *start-up-script.sh*, (an example), make it executable and add it to your autostart folder? or autostart menu?

Now to your conkyrc.
Firstly, conky is not themed externally rather the script itself calls the colour settings, images, styles etc. If you are set on one or more of the examples you have linked 
to above you will need to download those conky scripts. 
More often than not, a setup or readme file is also contained within the download itself.

After you've downloaded the required conky scripts, look back at your startup script: you have named the first conky simply *conkyrc*, and if using two, the second is named *conkyrc1*. 
When setting up your conky script(s) ensure these names are used.

(Light-hearted) Warning: Conky is highly addictive! Prepare to miss important meetings, live on Vitamin B, and forget close family members names.
"Must... figure... this... out..." will become your mantra.

Enjoy!

---

### Post by zombifier25 on 2012-10-09
> **bra|10n said:**
> (Light-hearted) Warning: Conky is highly addictive! Prepare to miss important meetings, live on Vitamin B, and forget close family members names.
"Must... figure... this... out..." will become your mantra.

Enjoy!

Allow me to cast my vote.

Also, those conky configs may need modifications in order to work on your system. I suggest you read carefully [Conky's own documentation](http://conky.sourceforge.net/documentation.html) (the variables page and configs page are the most important), and also the documentations (if any) that comes with those configs. Conky is hard, but once you know the basics, you should fly through these.

---

