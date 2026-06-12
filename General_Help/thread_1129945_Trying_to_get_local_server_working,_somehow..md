---
title: "Trying to get local server working, somehow."
date: 2009-04-19
forum: General Help
---

### Post by Schtoo on 2009-04-19
Hi all.

Like the title says, I am trying to get this box working as a local server so I can build a zen cart store offline before I upload it.

I have installed Apache2, mysql and myphp, and I think they are talking to each other nicely enough, although I am not sure because I have been fighting with all of them for the last 5 days.

(For those of you who are unfamiliar with Zen Cart, it's open source e-commerce stuff based on php for the most part, I think.)

Right now, I can begin installation of Zen Cart, but get stopped when it check all the server settings. Basically it's a bunch of permissions things because of where it's been stuck in the file system. Curl needs to be supported too as well as a few other less important things I think I can get around.

At the moment, 'localhost' is in the default place, buried in the root files. As such, Zen Cart can only read, but not write. I need get it out of there (only there to make sure the stupid thing will work) and then tell apache where to point, probably at something a little more respectable than just 'localhost'. 

(Yes, I know that there are many online tutorials out there and all that kinda thing, I know because I searched for them. Ya know what, the last 5 days was spent fighting with everything the search results told me to do and few of them worked. I pretty much sick of searching for things now, please excuse me. This stuff took under an hour to get working in WinXP using xampp.)

The other big sticking point is making the curl stuff I installed work. No idea where to go for that, I just installed it and hoped for the best.

Umm, that's all I got right now but I am sure there will be more soon enough. 

Thanks, 

Stu. 

(Who is wondering which is more difficult to work out, WinXP in Japanese or Ubuntu...)

---

### Post by spiderbatdad on 2009-04-19
As you probably know, apache runs as a specific user, www-data. My guess is that your zen service needs to be made a member of the www-data group. I don't know anything about this service, but if it runs as user zen, then make zen a member of www-data:```
sudo usermod -a -G zen www-data

```

---

### Post by Schtoo on 2009-04-19
I think I know what you are saying there, and that's what I was doing (I think) and Zencart couldn't write anything so it said no. 

I have since played with it via nautilus so I can read and write with impunity, and I have somehow managed to make mysql Admin GUI interface work too. A victory at last.

Actually, you know something? I seem to have made it all work somehow...

What's worse, this is all starting make some sense.

Thanks for the help, I don't even know how it helped but it did.

Stu.

---

