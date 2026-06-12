---
title: "display weather map in conky???"
date: 2006-07-18
forum: Desktop Environments
---

### Post by oberon on 2006-07-18
I am trying to figure a way to display a image that is downloaded from weather.com for my local radar.  I have the script for the conkyrc file to referance and run every 10 minutes.  And it does, but I am at a loss for how to actually display it below the forecast in conky.  Is this even possible? :-k   Thanks for your help!

---

### Post by oberon on 2006-07-19
Bump

---

### Post by mcduck on 2006-07-19
No, it's not possible with Conky. Conky can only draw those simple graphs/meters (wich is more than the original app, Torsmo did, as it only did text).

---

### Post by oberon on 2006-07-19
Then is it possible to display an image at specific x and y coords on the desktop through the script that conky executes?

---

### Post by oberon on 2006-07-19
Okay, so I figured out that I can resize the image using Imagemagick's mogrify command and that I can use 'display -window root -update 600 /path/image.jpg' to display the image on the desktop and check for updates to that image every 10 minutes  I am unsure of the syntax for the geometry switch for the display command though.  Acoording to imagmagick's website this switch allows you to set the size of the image and location to be displayed through x and y coords.  Anyone out there used this that can shed some light on this for me?


Thanks!

---

### Post by intangir1999 on 2007-06-07
What was the code for conky that you used to obtain this?

---

### Post by Mostlyharmless42 on 2007-12-25
> **intangir1999 said:**
> What was the code for conky that you used to obtain this?

i'd like to see this too...

---

