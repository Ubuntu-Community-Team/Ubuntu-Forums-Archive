---
title: "Steam"
date: 2006-08-04
forum: Gaming &amp; Leisure
---

### Post by OoAaO on 2006-08-04
ok this is kinda weird but i cant login i can install it but no words are on the login ot anything just green squares

---

### Post by Tomosaur on 2006-08-04
You can solve this a number of ways:

1) By installing the Tahoma font into your windows\fonts directory.
2) (I think) By installing the msttcorefonts
3) By editing your SteamScheme.res file to search and replace every mention of 'Tahoma' with a font of your choice that you know you have installed. This is in Steam\Resources\.

I personally chose the 3rd option.

---

### Post by Polygon on 2006-08-04
just google "tahoma.ttf", right click and download the file in google (dont click on it... it wont work) to your desktop, then simply

```

cd Desktop
sudo mv Tahoma.ttf /home/USERNAME/.wine/drive_c/windows/fonts/
```

replace USERNAME with your username that you use to login to ubuntu with. And also make sure that the the file name for tahoma.ttf is correct (is the T lowercase or uppercase?)

and also, one other thing. you have to right click on the login box in steam and then click anywhere on the steam login box again to gret rid of the right click window in order for the steam login box to come into focus, and then simply type in your username/password

---

