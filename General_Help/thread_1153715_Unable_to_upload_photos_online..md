---
title: "Unable to upload photos online."
date: 2009-05-09
forum: General Help
---

### Post by Mad dog on 2009-05-09
I have tried both myspace and photobucket, neither one works. The photos simply do not show up in the uploader screen. Does anyone know what the problem could be? this is the one thing that is hurting the otherwise great Ubuntu experience for my wife.

---

### Post by Mad dog on 2009-05-09
WOW... I just figured something odd out. F-Spot automatically saves the photos from my camera as [SOMETHING].JPG (all capitalized) The uploader will not display these files unless I change the extension to lower-case so it reads like [SOMETHING].jpg

Now I *could* go and change every extension for all of my photos, but I'm wondering if there is anyway to do this automatically. Any help/ideas?

---

### Post by Legace on 2009-05-09
Go to Terminal.

Change your directory to the folder of your pictures..
E.g.
```
cd "/home/Jack/Pictures"
```

Then do this code:
```
rename 's/JPG$/jpg/' *
```

---

### Post by Mad dog on 2009-05-09
Thank you sir :) One question, will this occur automatically for my imports from now on, or will I have to do this with each new batch of photos?

---

### Post by Legace on 2009-05-09
> **Mad dog said:**
> Thank you sir :) One question, will this occur automatically for my imports from now on, or will I have to do this with each new batch of photos?

You'll have to do this manually each time :/

---

### Post by Mad dog on 2009-05-09
Alright, well that's not so bad. I may be incompetent but when I type ```
cd "home/chris/photos"
``` or any other folder's name (i.e. documents) into the terminal I get bash: cd: "home/chris/photos" file or directory does not exist. Am I missing something here?

---

### Post by Legace on 2009-05-09
> **Mad dog said:**
> Am I missing something here?

Terminal is case-sensitive. Make sure you type capitals as capitals. (photo -> Photo ?) :)

---

### Post by Mad dog on 2009-05-09
Alright, well I got into the directory, but the rename command you gave me doesn't do anything... unless I have to restart my computer for it to take effect?

---

### Post by Legace on 2009-05-09
> **Mad dog said:**
> Alright, well I got into the directory, but the rename command you gave me doesn't do anything... unless I have to restart my computer for it to take effect?

Is this how you've got things set up:


cd /home/Chris/Whatever

The contents of whatever should be:
/home/Chris/Whatever/image1.JPG
/home/Chris/Whatever/image2.JPG
/home/Chris/Whatever/image3.JPG
/home/Chris/Whatever/ima...

---

### Post by Mad dog on 2009-05-09
No, F-Spot makes a new imbedded folder for each specific day, so it's like this:

home/chris/Photos/2009/02/15/image1.JPG
or
home/chris/Photos/2009/02/18/image23.JPG

on and on, its all very cumbersome and unnecessary.

I'm curious if there is a way to make the uploader recognize .JPG because on the bottom there is a pull-down menu that says: *.jpg;*.jpeg;*.png (etc)  ....I think if I could somehow add *.JPG; to that list all my woes would vanish. Do you know how to do that?

---

### Post by Legace on 2009-05-09
> **Mad dog said:**
> I'm curious if there is a way to make the uploader recognize .JPG because on the bottom there is a pull-down menu that says: *.jpg;*.jpeg;*.png (etc)  ....I think if I could somehow add *.JPG; to that list all my woes would vanish. Do you know how to do that?

Nope.. :/

---

