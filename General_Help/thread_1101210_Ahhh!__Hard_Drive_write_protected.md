---
title: "Ahhh!  Hard Drive write protected"
date: 2009-03-20
forum: General Help
---

### Post by 80r on 2009-03-20
The hard drive (ext3) lies inside my Popcorn Hour...

My main computer is a Windows 7/XP PC which is where I do all my video encoding.  My laptop is an Asus EEE which has Ubuntu.  The subtitles weren't working on a video so I just pulled out my laptop, connected it to my PCH, and remuxed the file there.  Now for some reason I can't write any files from my windows computer.  It keeps saying it's write protected.  I went onto my laptop and saw that everything was now owned by '1001' with only read privileges for everyone else, including me.  I changed myself to the owner (though it reverted back to 1001) and gave everyone create and delete privileges but it still doesn't work on windows.

Now it's a major inconvenience to transfer everything to my laptop and then to my popcorn hour but that's all I can do right now.  Anyone know how I can fix this?

Edit:  I should mention that this is a popcorn hour:[http://www.popcornhour.com/onlinestore/index.php?pluginoption=catalog&task=info&item_id=5&main_id=0&category_id=]("http://www.popcornhour.com/onlinestore/index.php?pluginoption=catalog&task=info&item_id=5&main_id=0&category_id=")

---

### Post by Tek-E on 2009-03-20
hmmmm a windows problem......
Can you save files at all on your computer?

The only thing I can think of at the moment and Im not even sure this will work with it being Windows 7 is to try
```

attrib -r nameoffolder

```

---

### Post by Tek-E on 2009-03-20
Wait a minute. Im sorry. I think....well im sure now that I read your post wrong. lol :o

---

### Post by 80r on 2009-03-20
Still can't figure this out or find any solutions via google.

Does 'Others' not apply to windows users?  I looked at the hard drive's permissions and it says drwxrwxrwx.  Why can't I write to it?  I can't write anywhere on it.

---

### Post by 80r on 2009-03-20
The fact that it's on a popcorn hour is irrelevant.  It's a hard drive that is somehow  write protected.  I can do anything with it on Ubuntu, but not windows.  The fact that it's ext3 is also irrelevant because I have a program that allows me to write on it, which I have used without problems in the past.

I've been trying to figure this out all morning.  I've tried reformatting it - waste of time, taking ownership of it on windows - did nothing, giving myself permissions through ubuntu through terminal and nautilus - nada. What else is there?  When I look at the drive in gparted there's a set of keys displayed beside the drive.  So it's locked or something?  How do I remove it?

---

### Post by Tek-E on 2009-03-20
Have you tried resetting permissions so you can write to your hardrive with chown??
Example:
```

sudo chown yourusernamehere /dev/sda1

```

Thats all I can think of at the moment.

---

### Post by 80r on 2009-03-20
> **Tek-E said:**
> Have you tried resetting permissions so you can write to your hardrive with chown??
Example:
```

sudo chown yourusernamehere /dev/sda1

```

Thats all I can think of at the moment.

Yea.  I changed myself to the owner on Ubuntu and changed it so everyone has full access, including 'Others', but on Windows it just keeps saying Write-protected.

---

