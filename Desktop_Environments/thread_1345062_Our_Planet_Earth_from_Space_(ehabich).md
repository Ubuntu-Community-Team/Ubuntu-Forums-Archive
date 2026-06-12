---
title: "Our Planet Earth from Space (ehabich)"
date: 2009-12-03
forum: Desktop Environments
---

### Post by Fitch on 2009-12-03
There is a natty little site that shows views of various parts of the Earth, updated every 20 minutes, which used to work on Windows before Explorer 7 came along.

I had it on my screen for around 5 years, until I changed to Ubuntu 4 weeks ago.
The home page is : [http://satellite.ehabich.info/index.html](http://satellite.ehabich.info/index.html).
The page I used was [http://satellite.ehabich.info/eucrescent.htm](http://satellite.ehabich.info/eucrescent.htm)

Don't suppose there's any chance of being able to tweak the normally orange karmic screen to any of these sites is there?  And just to be really annoying, any way to get the screen to be scaleable and to refresh every half hour or so?

Yours in anticipation,
 
a guy who wants everything.

---

### Post by Fitch on 2010-01-11
I eventually managed it, not that I think anyone is interested.

I use the opefs european crescent as my wallpaper and update it every 30 minutes.

Stage 1:
Open a command line and type:
wget -N -c [http://www.ehabich.info/images/synch...pecrescent.jpg]("http://www.ehabich.info/images/synchro/europecrescent.jpg")
which will download the latest satellite image into your home folder.

Stage 2:
Click on Applications>System Tools>Configuration editor.
Expand desktop and then gnome then background.
Double click on the image filename box and drag the image into the box or type in - in my case - /home/*brafferto*n/europecrescent.jpg 
(change the "brafferton" to whatever your home directory is).
Set picture_options to stretched.
Close the config editor.

Stage 3:
In the command line, type:
crontab -e
I used nano (if this is the first time crontab is used)
Underneath the "# m h  dom mon dow   command" I typed

*/30 *  * * * rm europecrescent.jpg; wget -N -c [http://www.ehabich.info/images/synch...pecrescent.jpg]("http://www.ehabich.info/images/synchro/europecrescent.jpg")

CTRL O to write out
CTRL X to exit

*/30 *  * * * means every 30 minutes of every hour, every day, every week, every month.

There are two commands separated by a semicolon:
The  "rm europecrescent.jpg" removes the old image as wget won't download the file if one already exists.
and the wget is as stage 1.

Sorted!

---

### Post by Mazin on 2010-01-11
How about using
```
curl "http://www.ehabich.info/images/synchro/europecrescent.jpg" -o "europecrescent.jpg"
```
instead?  That would save you the step of deleting the image, which the wallpaper manager might not like.

---

### Post by Fitch on 2010-01-12
Yep! that worked.

Therefore Stage 3 should now read:

Stage 3:
In the command line, type:
sudo apt-get install curl 
crontab -e
I used nano (if this is the first time crontab is used)
Underneath the "# m h  dom mon dow   command" I typed

*/30 *  * * * curl "[http://www.ehabich.info/images/synch...pecrescent.jpg]("http://www.ehabich.info/images/synchro/europecrescent.jpg")" -o "europcrescent.jpg"

CTRL O to write out
CTRL X to exit.

---

