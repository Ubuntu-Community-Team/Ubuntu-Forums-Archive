---
title: "hide symlinks?"
date: 2009-05-14
forum: Desktop Environments
---

### Post by alexweber15 on 2009-05-14
I'm completely new to linux/ubuntu and have been using ubuntu for a few days now and I really like it.

I've also been trying to use the terminal as much as possible to get comfortable with it but I'm having a hard time with long folder names:

/home/alex/Downloads
/home/alex/Development

etc

It looks good in nautilus but when using the terminal its a pain so I created some symlinks:

/home/dl
/home/dev

etc

Thing is, my home folder is getting crowded with symlinks now... :rolleyes: is there any way I can hide them from nautilus so that I can still using the shortcuts I created in the terminal but avoid the clutter when browsing visually?

I tried renaming them with a dot(.) prefix but it won't hide them... (show hidden files/folders is off)

Is there a better workaround for this short of renaming all my folders to use shorter names or just living with a crowded home folder?

thanks

Alex

---

### Post by benign on 2009-05-15
If you are having problem typing them because they are long, just use the <tab> button. It basically an autocomplete.

/ho<tab>a<tab>De<tab>

could probably get you to /home/alex/Development quickly

---

### Post by x33a on 2009-05-15
@ alex, do as benign said, instead of making symlinks.

learn a few terminal tricks.

tab autocomplete is a serious performance booster.

and to go to the home directory from any directory, use ~/

e.g. cd ~/Do<tab>

will autocomplete to /home/alex/Downloads.

As for the sysmlinks not hidden issue.

i tried hiding a symlink with a dot in front and i was able to hide it, so i have no idea why they are not hiding in your case.

Take a look at this site:

[http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

---

### Post by alexweber15 on 2009-05-15
thanks for the tips, I'm making a point of overusing the terminal in order to try and get more proficient and autocompleting is an awesome trick! :)

---

