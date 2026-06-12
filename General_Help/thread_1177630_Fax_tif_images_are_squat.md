---
title: "Fax tif images are squat"
date: 2009-06-03
forum: General Help
---

### Post by ricardisimo on 2009-06-03
I receive faxes remotely via my voicemail, in tif format. The problem is that they are squished flat for some reason. (I should mention that evince opens it correctly, but everything else views it as squat). When I open the tif with gimp, something curious happens: The aspect in pixels is 1728*1078 - that is to say, the width is significantly greater than height. But when you select "inches" you get 8.471*11. That is to say, you get a standard US letter aspect ratio, where the height is greater than the width.

What gives? Why is this happening? It wouldn't bother me so much if no applications opened it correctly... then I could write the files off as faulty. As it stands, every time I have to calculate the starting width divided by 8.5 and times 11 for a new pixel height number, so that I can get a usable image to forward to others. Any better way to do this?

---

### Post by Jamieson630 on 2013-01-26
> **ricardisimo said:**
> ...every time I have to calculate the starting width divided by 8.5 and times 11 for a new pixel height number, so that I can get a usable image to forward to others. Any better way to do this?
You don't have to do the calculations yourself; GIMP will do them for you. Follow these steps:
[LIST]
[*]From GIMP, choose Image &#8594; Scale Image…
[*]Click the chainlink icon between both pairs of input fields to unlink them.
[*]For the Image Size, change the drop-down from "pixels" to "inches". For the Resolution, make sure the drop-down is set to "pixels/in".
[*]Change the Width and Height to 8.5 and 11.
[*]**Change the Y Resolution to equal the X Resolution.**
[*]Click the Scale button.
[/LIST]
GIMP will automatically do the calculations to achieve the desired size in inches, based on the desired pixels/inch. Because you set the pixels/inch to be the same for X and Y (square pixel aspect ratio), the document will now look correct on your monitor.

---

### Post by ricardisimo on 2013-01-28
That is freaking hysterical. I got a response to this post almost four years later. Thanks by the way.

---

### Post by JKyleOKC on 2013-01-28
> **ricardisimo said:**
> What gives? Why is this happening? It wouldn't bother me so much if no applications opened it correctly... then I could write the files off as faulty.Even though your question is four years old, I see that nobody has answered this part of it. The files are **not** faulty; in fact, they adhere to the original fax specifications published long before the PC came into use!

That original document defines a "standard" resolution with approximately twice as many pixels horizontally as vertically. Here's what the spec calls for in "Group 3" faxes (although other options exist also):
> Horizontal: 200 or 204 scan lines per inch

    Vertical: 100 or 98 scan lines per inch ('Standard')
    Vertical: 200 or 196 scan lines per inch ('Fine')
    Vertical: 400 or 391 (note not 392) scan lines per inch ('Superfine')The reason for that anomaly in the standard resolution stems from the days when fax machines were entirely mechanical with almost no electronics involved at all. The rather primitive scanners at that time could not resolve more lines per inch. The "fine" and "superfine" options were added later as scanning technology improved.

Since you're working with TIF files, their headers include fields to tell you the actual X and Y resolutions of the images, separately; programs exist to display all of the fields in a TIF header, but it's been 20 years now since I worked with them so I don't remember the specifics. A google search for "TIF header" should give you lots of choices, though. Having those values will make it easy to determine the aspect ratio needed to correct things.

Hope this helps!

---

