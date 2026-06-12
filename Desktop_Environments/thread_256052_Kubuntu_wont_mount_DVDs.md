---
title: "Kubuntu wont mount DVDs"
date: 2006-09-12
forum: Desktop Environments
---

### Post by NiksaVel on 2006-09-12
Hey all...  after some recent updates I seem to have lost the ability to mount DVDs...  it detects the new disc, and opens a pop-up, when I want to open the disk it gives me  a "Malformed URL ." msg...

I saw a post on the old forum about a similar problem:
> May 28th, 2006, 09:34 PM
Everytime I try to view the contents of a CD in Konqueror it gives me a "malformed URL" error and won't let me do anything with it. Any help is greatly appreciated.
isaacf
May 30th, 2006, 02:54 AM
I tried viewing the contents of other CDs I had. No blank CDs go through without the "Malformed URL error." Other linux install CDs I have lying around show up fine and playstation disc which I'm trying to read to play them with epsxe don't even register with kubuntu.
emretemp
July 10th, 2006, 07:57 PM
I also get this msg whenever I insert a new DVD into my dvd driver.

simply confused here.

anyone knows what todo?
oliwally
July 19th, 2006, 03:45 PM
Everytime I try to view the contents of a CD in Konqueror it gives me a "malformed URL" error
I have the same problem with a data DVD that I've burned although it didn't consistently fail - one time it opened.

I found that that if I "create a new link to a device" and make that device a DVD Rom device on the Desktop, then I can access the data on the DVD though that link.

I've noticed that if I try to open the DVD with the automatic function that comes up when the DVD is inserted, then Konqueror uses the following path:
system:/media/hdd and often the "malformed URL" error message.
But if I open the DVD through my newly created link to the DVD device (wich works consistently), then the path is this:
/media/cdrom0

Not sure what the problem is or how to fix it, but at least there is a workaround. I wonder if Konqueror needs to be pointed to the DVD device in a different way. Some setting that can be adjusted for auto-opening the data DVD?


I tried to manualy make a link to the dvd drive - AND IT WORKED OKAY!!! ????

it also gave a /media/cdrom0 address in the konqueror address bar, while the automatic mounting gave the hdc...???


regular CDs work okay.



thanks for the help.

---

### Post by NiksaVel on 2006-09-12
addon...

as long as I have a link to dvd device present on desktop, dvd loading works okay. 

I tried deleting the link, and as soon as it was gone every dvd I inserted afterwards was reported with malformed url and the disk icon on the desktop imidiately vanished without trace...


EDIT:
after recreating the link the automatic dvd loading didnt work... ](*,)

---

### Post by NiksaVel on 2006-09-12
lol...  but if I have the link to dvd device icon present on the desktop, although now dvd loading works okay, regular cd loading stopped working and started giving me the malformed url error.


I can still click on the link to dvd device icon and load it okay...

---

