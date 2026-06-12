---
title: "brasero will not burn a iso file"
date: 2009-06-27
forum: Desktop Environments
---

### Post by Mia1990 on 2009-06-27
Hello,

I have been trying ro burn a image file for some time now with no luck i can't even copy a disk i am running ubuntu 9.04 and
as far as plug ins i only have what came installed if you need any more information just let me know.Thank you

Mia

---

### Post by XubuRoxMySox on 2009-06-27
Brasero doesn't know it's supposed to burn an image (as opposed to just data) unless you tell it...

Try right-clicking on the iso file you have downloaded and then choose "burn to disk," and Brasero gets it from there.

One more thing to check, and I only mention it because I made this mistake only yesterday - make sure the blank CD is a CD and not a DVD! 

Cheers,
Robin

---

### Post by Mia1990 on 2009-06-27
Ok when i open brasero one of the options is to burn a image and that is how i was trying to do it i wasn't sure if i needed some other plug in or not.

Thank you

---

### Post by ~sHyLoCk~ on 2009-06-27
Ok so what is happening if you try it with "Burn image" option?

---

### Post by Mia1990 on 2009-06-27
brasero says it done with no error's but when i put the cd in to install it does nothing it doesn't even show that the cd has anything on it.

---

### Post by ~sHyLoCk~ on 2009-06-27
> **Mia1990 said:**
> brasero says it done with no error's but when i put the cd in to install it does nothing it doesn't even show that the cd has anything on it.

Ok I know this isn't much of a solution but may I suggest the perfect alternative? K3B! It's simply great and I never had any issues with it. You could give that a try, meanwhile, until your brasero problem is solved.

---

### Post by Mia1990 on 2009-06-27
i've been thinking about k3b for a while i use mandvd to burn movies and it works great for that but it will not burn a image file so i may try k3b untill i get this worked out
thank you 
mia

---

### Post by QIII on 2009-06-27
When  you say "to install", I assume you mean that you have downloaded an .iso that should have a number of files on it.

Take a look at the contents of your CD.

If it has one large file and you can't see all the little folders and files, you've burned it wrong.

Did you click  "Disk Copy" or "Burn Image"?

---

### Post by Mia1990 on 2009-06-27
> **QIII said:**
> When  you say "to install", I assume you mean that you have downloaded an .iso that should have a number of files on it.

Take a look at the contents of your CD.

If it has one large file and you can't see all the little folders and files, you've burned it wrong.

Did you click  "Disk Copy" or "Burn Image"?
This is what i tried i downloaded the ubuntu sever iso image and tried to burn that when i look to see what is on the cd there is nothing on it and it will not boot.I also tried to copy one of my Rosetta stone cd's just to see if i could do that still it does not boot and when i look at that cd there's nothing on it.

---

### Post by QIII on 2009-06-27
Can you pop a music CD in and see if it will play?

I guess my question is whether it is not burning or not reading.

---

### Post by Mia1990 on 2009-06-28
yes i can play a cd i can even burn a dvd with mandvd but not image file with brasero
i don't understand what may be wrong.

---

### Post by QIII on 2009-06-28
OK.

Next check is going to cost you a CD, but they are cheap.  Not to belabor the point, but make sure it is a CD and not a DVD.

Try to use Brasero to copy a different type of file to a CD.  Even a small photo or something like that.

It's a waste of a CD, of course, but it will at least let us know if it is Brasero.

---

### Post by kelvin spratt on 2009-06-28
Brasero will burn any ISO to either CD or DVD if you want to burn the Ubuntu ISO you can use either you must burn ISOs at slow speed. and use media like Verbatim for best results

---

### Post by Mia1990 on 2009-06-28
ok i can burn a picture am i doing something wrong when i am burning the image file
all i do is select burn image then pick my image file then the drive i want to write to?

---

### Post by XubuRoxMySox on 2009-06-28
> **Mia1990 said:**
> ok i can burn a picture am i doing something wrong when i am burning the image file
all i do is select burn image then pick my image file then the drive i want to write to?

Omygosh! No, **an "image" is not the same thing as a photograpth or a bitmap or a "picture file."** An image is a file type (ending in ".iso") - like a snapshot of DATA, not PICTURES.

Pictures are data files (ending in .bmp or .gif, etc). Just copy them to a DATA disk. They are not the same as an ".iso" file.

---

### Post by Mia1990 on 2009-06-28
> **dixiedancer said:**
> Omygosh! No, **an "image" is not the same thing as a photograpth or a bitmap or a "picture file."** An image is a file type (ending in ".iso") - like a snapshot of DATA, not PICTURES.

Pictures are data files (ending in .bmp or .gif, etc). Just copy them to a DATA disk. They are not the same as an ".iso" file.
Please read the post from QIII that says this will cost you a cd but there cheap try burning a picture or something to see if it's brasero or something else.I know the difference between a picture and a image file.

---

### Post by boof1988 on 2009-06-28
> **Mia1990 said:**
> Hello,

I have been trying ro burn a image file for some time now with no luck i can't even copy a disk i am running ubuntu 9.04 and
as far as plug ins i only have what came installed if you need any more information just let me know.Thank you

Mia

If Brasero does not work adequately, then another option (that uses CLI and is not Brasero, but is included with Ubuntu) is *cdrecord*.  This is just another idea that may be of interest.

One option to burn an *iso* image using *cdrecord* (in terminal)...
[LIST=1]
[*]Navigate to directory containing *.iso* image.
```
cd <directory containing .iso image>
```
[*]Insert a blank CD in CD-drive.
[*]Type the following to burn *file.iso* image.
```
cdrecord -v dev=/dev/cdrom file.iso
```
[*]Observe the feedback given in the Terminal (due to the verbose option *-v*).
[*]Eject the CD using your favorite method upon completion of burn.
[/LIST]

Further information...
```
man cdrecord
```

---

### Post by QIII on 2009-06-28
> **Mia1990 said:**
> ok i can burn a picture am i doing something wrong when i am burning the image file
all i do is select burn image then pick my image file then the drive i want to write to?

Generally, yes.  The "Select image to write" box should contain the file you want to burn, and the "Select a disc to write to" box should to the right CD drive.

If you are absolutely sure that is what you have done and it simply isn't working, then I would suggest trying a different method.  Someone has suggested a command line solution.

---

### Post by javyn999 on 2009-07-03
Brasero just doesn't work for me period in Jaunty.  It's a pretty common problem I've read on these forums.  K3b is better anyway, and doesn't use many dependencies.  I like it much, much better, but I was a Nero user on Windows so that's probably why I feel at home with K3b.

---

### Post by Mia1990 on 2009-07-04
thank you all i found the problem it was the cd's ubuntu just didn't like sony cd's

---

