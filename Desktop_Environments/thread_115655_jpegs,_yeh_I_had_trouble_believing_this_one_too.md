---
title: "jpegs, yeh I had trouble believing this one too"
date: 2006-01-11
forum: Desktop Environments
---

### Post by threethirty on 2006-01-11
My parents sent me some pics (of [Donshyoku]("http://ubuntuforums.org/member.php?u=16619") at school) that they had loaded on their Mac.  And here are the errors I get in every graphics app I have [I have cut out some of the path due to the fact that Donshyoku's real name is in the path]

Gimp 2.2: **JPEG image Message**  Not a Jpeg file: starts with 0x28 0x54
                **GIMP Message** Opening '/home /three/.../beds.jpg' failed: Plug-in could not open image

Gwenview: No error but a blank/grey space

Firefox:The image &#8220;file:///home/three/.../beds.jpg&#8221; cannot be displayed, because it contains                                errors

Krita: Could not open  /home/three/.../beds.jpg

showFoto: No error just a black screen

I also tried to open it in digiKam but the  program just didn't open.

---

### Post by threethirty on 2006-01-11
Welp 11 hours later my problem remains, I only say this because the last 4 questions I asked on here after a good nights sleep the problem had disapeared.;)

---

### Post by earobinson on 2006-01-11
could you post an image, maybe the image got corrupt

EDIT: edited for spelling

---

### Post by az on 2006-01-11
If you send the files back to your parents, can they open them?

Can they give any details as to their properties?

---

### Post by threethirty on 2006-01-11
[here]("http://richmondlug.tripod.com/threes_problems/") is a screenshot of the pic in  Konqueror.

---

### Post by srt4play on 2006-01-11
If you're dual booting/have access to a Windows system, does it open ok in Windows?

---

### Post by threethirty on 2006-01-11
No such luck in Windows, and the parental units are unavailable so the other question will have to remain unanswered, it may just be that the files were corrupted while being emailed... 

thanks anyways guys and/or gals I can't believe that I would think that Linux was at fault before anything else

---

### Post by earobinson on 2006-01-12
so upload the actualy image for us to look at, if we cant see it then the image probaly got corrupt along the way.

---

### Post by xurizaemon on 2006-01-12
Strange as it may seem, if this issue affects both your Ubuntu and Windows email, it may not be a problem at your end :)

It's quite easy with an older Mac to send attachments with the Mac "Resource" as a separate attachment, and this confuses the recipients. You will receive two attachments of the same name; one is the image, and the other is information suggesting that MacOS open the file with a specific application etc.

In later versions of OSX (10.3,10.4 I think), Mail.app includes a menu entry "Send Windows-friendly attachments", which means that the resources are ignored and only the image itself is sent with the message.

You could try this theory out by either:
1) Viewing the emails on a Mac, which will be able to understand the Resource attachments
2) Checking to see if you can open some (probably exactly half) of the attachments supplied
3) Asking your parents to resend the attachments

It's possible through the Mail.app menu to set a preference that will ensure all attachments sent are Windows-friendly. Don't worry, it won't make the Mac virus-compatible ;)

Good luck, & I hope the family pics are a delight to you when you DO get to see them! :D

---

### Post by threethirty on 2006-01-13
OK i found out that the files are corrupted because they sent them to [Donshyoku]("http://ubuntuforums.org/member.php?u=16619")who is using windows right now (yuck) and he cant open them either

thanks for all the help

---

### Post by earobinson on 2006-01-13
good to know... thanks for the update

---

### Post by xurizaemon on 2006-01-13
There's a handy-dandy commandline tool that will identify what files REALLY are for you, with the magic of Unix magic numbers and stuff. It's called "file" - from a shell, type "file Photo-1.jpg" and it will tell you what the file looks like. 

```
chris@glo:~/files$ file Lopdell_bw.jpg 
Lopdell_bw.jpg: JPEG image data, JFIF standard 1.02

chris@glo:~/files$ file ._Lopdell_bw.jpg 
._Lopdell_bw.jpg: AppleDouble encoded Macintosh file
```

It can't tell if it's a valid file of that type - so the image or document could still be corrupted - however this would help eg if they are TIFF files saved with a .jpg extension, or AppleDouble resources, as you'd be able to see what those files really are ...

Enjoy

---

### Post by hogweed on 2006-01-13
This may be a longshot, but I remember a number of years ago having a similar problem when getting photos from someone who used a Mac. It seems that because of the way the file system hierarchy works in OSX, the "/" symbol doesn't necessarily signify the end of one directory and the beginning of another.

In other words, you might have a photo that is

/home/me/photosfromcamera/picture.jpg

which Konqueror is trying to read as a file "picture.jpg" located in a directory "photosfromcamera" which in turn is located in your home directory. What you actually have (and this is why Konqueror chokes on it) is a file named "photosfromcamera/picture.jpg" sitting in your home directory.

Can you tell if this is the case. That was what had happened to me in that instance a few years back. I think that fixing it was simply a matter of changing file names (probably from command line).

Of course, I may have no clue what I am talking about, but thought that I might be useful for a change.

-- hogweed

---

