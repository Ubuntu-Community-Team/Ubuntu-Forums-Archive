---
title: "Change Login Screen"
date: 2011-10-29
forum: Desktop Environments
---

### Post by JohnGalt2010 on 2011-10-29
After many years running ubuntu on my IBM R50 laptop and IBM NetVista desktop, I decided that I needed to move toward something that requires less machine.  So far, I feel that lubuntu is my answer.

After using lubuntu since the 11.10 release came out, I only have two issues that are bugging me about this ubuntu variant.  The first and probably the simplest, is that I cannot find a way to have the NumLock on when I log in.  (To be honest, I haven't spent much time trying to find an answer.)

The second, is that I REALLY would like to change the background of the login screen to the boot splash screen, which is a lot more pleasant to my eyes.  Also, I would really like to minimize, or eliminate, the "session" bar at the bottom of the login screen.

---

### Post by kalehrl on 2011-10-29
I can only answer this part of the question:

> I REALLY would like to change the background of the login screen

You need to edit /etc/lxdm/default.conf file and add the path to your wallpaper:

```
## background of the greeter
bg=/usr/share/lubuntu/wallpapers/wall_1024x768.png
```

I changed it too with the wallpaper from natty named wall_1024x768.png.
I'm not sure about the path to boot splash screen.

---

### Post by amjjawad on 2011-10-29
> **JohnGalt2010 said:**
> After many years running ubuntu on my IBM R50 laptop and IBM NetVista desktop, I decided that I needed to move toward something that requires less machine.  So far, I feel that lubuntu is my answer.

Hello and Welcome :)

Thank you for choosing and using Lubuntu. What a great choice :)

> The first and probably the simplest, is that I cannot find a way to have the NumLock on when I log in.  (To be honest, I haven't spent much time trying to find an answer.)


From LXTerminal:

> sudo apt-get update && sudo apt-get install numlockx

However, note that the NumLock will be ON after you login.

> The second, is that I REALLY would like to change the background of the login screen to the boot splash screen, which is a lot more pleasant to my eyes.  

You want to change the Login Wallpaper to the same Boot Splash Wallpaper?

> Also, I would really like to minimize, or eliminate, the "session" bar at the bottom of the login screen.

I'm sorry, not sure what you mean?

---

### Post by kalehrl on 2011-10-29
To remove session bar, try editing the default.conf file and setting 0 instead of the default 1:

```
## if show bottom pane
bottom_pane=0
```

---

### Post by amjjawad on 2011-10-29
Login Wallpaper:

[IMG]http://i39.tinypic.com/hvue4g.jpg[/IMG]


You need to be Root to edit that file.
From PCManFM, go to Tools > Open current folder as Root

Copy the wallpapers you want to use and place them on the folder as shown above.

I had set this previously:

[IMG]http://i52.tinypic.com/2ntbtxz.jpg[/IMG]



I used Plymouth Manager to change the Boot Splash Screen.

---

### Post by JohnGalt2010 on 2011-10-29
Thanks for all the quick responses. 

:kalehrl - > You need to edit /etc/lxdm/default.conf file and add the path to your wallpaper: ```
## background of the greeter
bg=/usr/share/lubuntu/wallpapers/wall_1024x768.png
``` I tried a .jpg file and the greeter froze.  I will have to find a .png that I like.

> To remove session bar, try editing the default.conf file and setting 0 instead of the default 1: ```
## if show bottom pane
bottom_pane=0
``` only changed the opaqueness of the session bar, it did not remove the 'desktop' and 'language' selections. 

:amjjawad - ```
sudo apt-get update && sudo apt-get install numlockx
``` worked well for having the numlock 'on' when I logon to my session.

I don't have any of the files in your themes folder.

---

### Post by MG&amp;TL on 2011-10-29
> **JohnGalt2010 said:**
>  

:kalehrl -  I tried a .jpg file and the greeter froze.  I will have to find a .png that I like.


I don't have any of the files in your themes folder.

1. ```
sudo apt-get install gimp
``` Open the offending image in GIMP, and save it again as a PNG. This is probably not the most efficient method, but it's fairly easy. Although I doubt it is the image format.

2. Download some pictures that you like, then:

```
sudo cp ~/Whereyouputthepictures/image1.jpg /usr/share/lxdm/themes/Lubuntu/
sudo cp ~/sameplaceagain/image2.png /usr/share/lxdm/themes/Lubuntu
```

And good choice. ;)

---

### Post by amjjawad on 2011-10-30
> **JohnGalt2010 said:**
> :amjjawad - ```
sudo apt-get update && sudo apt-get install numlockx
``` worked well for having the numlock 'on' when I logon to my session.

Glad to know that :)

> I don't have any of the files in your themes folder.

I know, that's why I mentioned you need to copy and paste your wallpapers that you want to use in that directory (folder).

---

### Post by amjjawad on 2011-10-30
> **MG&TL said:**
> 1. ```
sudo apt-get install gimp
``` Open the offending image in GIMP, and save it again as a PNG. This is probably not the most efficient method, but it's fairly easy. Although I doubt it is the image format.

2. Download some pictures that you like, then:

```
sudo cp ~/Whereyouputthepictures/image1.jpg /usr/share/lxdm/themes/Lubuntu/
sudo cp ~/sameplaceagain/image2.png /usr/share/lxdm/themes/Lubuntu
```And good choice. ;)

OR ... just install "shotwell" :)
You can crop and save as another type.

BOTH JPG and PNG file types will work. Lubuntu original login wallpaper is PNG.

---

### Post by MG&amp;TL on 2011-10-30
> **amjjawad said:**
> OR ... just install "shotwell" :)
You can crop and save as another type.

BOTH JPG and PNG file types will work. Lubuntu original login wallpaper is PNG.

ah....never used shotwell...;)

That's what I thought. OP, how did it freeze with the JPG?

---

### Post by Bobby Paul on 2013-01-04
Hy there.i dont need to know how to modify the background,that i've already done,but what i want to know is how to get rid off the ugly box at the log screen with the name of the pc/laptop user.Tk's

---

### Post by oldos2er on 2013-01-04
Please start a new thread per the posting guidelines:

If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

