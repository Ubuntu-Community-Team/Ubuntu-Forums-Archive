---
title: "Problem with displaying Japanese in MP3 tags"
date: 2005-09-23
forum: Desktop Environments
---

### Post by kirillrdy on 2005-09-23
Hey,
Just a small thing I would like to get fixed.
I will attach a screen shot of my Muine Player, As u can see it displaes Japanese properly for some files, and doesnt display for other files. And its the same for Totem, 
The same files In windows Media Player are shown just fine.
Both Windows and Linux has locale set to Japanese.
How can I over come this?

Any help would be very appriciated,

Thanks,

Kirill R

---

### Post by Dryer Lint on 2007-06-04
I just had this problem myself and solved it successfully.
So even though this thread is really old, I thought I'd post my solution for anyone who might stumble over this thread while searching for a solution himself.

Install the package "python-mutagen" (sudo apt-get install python-mutagen).

Then you will have the command-line program mid3iconv, which can convert tags from any encoding to Unicode.

My MP3s were S-JIS encoded, so I ran

mid3iconv -e sjis filetoconvert.mp3

Worked like a charm! :)






P.S.: Ultimate Thread Necromancy!

---

### Post by jadedjay on 2007-11-01
Dryer Lint

I know that you posted your solution a long time ago but I thought I would say thanks anyway.

You solved a problem that I had with my girlfriend's Japanese music collection.
I was looking at it the wrong way and trying to get Japanese fonts working in Amarok.
This is a much easier solution.

Thanks a lot

---

