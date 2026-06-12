---
title: "kubuntu and i910"
date: 2006-10-03
forum: Desktop Environments
---

### Post by amautsch on 2006-10-03
Hello,

i've got some minor problems with Kubuntu
and my Dell inpsirion 1300 NB with an i910 Graphics :

1.
The colors or the brightness / contrast is not correct when
using xv in mplayer.
If using kmplayer, everythig is messed up much to bright.
If using mplayer, everythin is to dark / to much contrast.
Die effect does no occur when using x11 for output

2.
I cannot get a working output to an external monitor.
I tried to use a little i910 switching tool
and a handmade x11 config.

Both ended up with an ouput on my LCD Tv,
but the picture is distorted by severe syncronisation problems.

Does anyone know about a solution ?

Thanx in advance

---

### Post by wieman01 on 2006-10-03
As for the contrast problem, you can try another movie player called "kaffeine". I used to have the same issue before I replaced "totem" with "kaffeine" which works fine.

Secondly, there are basically 2 ways to get your output working:

1. A tool called **i855crt** which did not work for me (blurred screen).
2. **Xinerama** which you set up by editing "xorg.conf". I am using that approach and I am very happy with it. Here is a thread: 

[http://www.ubuntuforums.org/showthread.php?t=221908&highlight=sony+vaio+xinerama]("http://www.ubuntuforums.org/showthread.php?t=221908&highlight=sony+vaio+xinerama")
[http://www.ubuntuforums.org/showthread.php?t=237640]("http://www.ubuntuforums.org/showthread.php?t=237640")

Let us know if you need help setting it up. Xinerama is not ideal because you cannot enable it by a click of a button, but apart from this it is fairly reliable.

---

### Post by amautsch on 2006-10-04
Hello and thanx for your answers.

I'll try them soon.
But i am wondering,
isn' kaffeine just a frontend for mplayer ?

Because as said,
mplayer sets the contrast to low,
where as KMPAYER sets the contrast to high.

I'll try it anway.

thanx
  andreas

---

### Post by wieman01 on 2006-10-04
> **amautsch said:**
> I'll try them soon.
But i am wondering,
isn' kaffeine just a frontend for mplayer ?
Good question... Frankly I don't know. Give it a shot anyway & let us know if it works.

---

### Post by amautsch on 2006-10-07
Nope it doesn't,
i again fiddled about an hour,
with the following result

- installaing kaffeine for the first time
results in videos that do not have the "too bright bug",
but having the "too dark / to much red" bug,
as i've got in standealone mplayer

- after installing kmplayer, kaffeine is also broken,
now we've got the too bright bug again

- i think kaffeine normaly opts to xine, but with an installed
kmplayer, it will use kmplayer in favour

- so the to much red bug is still there, but if xine and mplayer
got the same problem, i wonder if this is some other problem ...
don't you have the same problem ?

can i ask you 2 more questions ?

- do you know if there is a posibility to update an old debian / kernel 2.4 with ubuntu 6.06 ?

- you've also got a notebook with an i910 grahpics ?
Do you also have the broadcom wireless adapter and does it work for you ?
For me, it only works with ndis-wrapper and this draws a hell of cpu power

thanx for answers

---

### Post by wieman01 on 2006-10-07
You were actually asking 4 questions. :-)

1. Xine & Kaffeine work fine. No color problem.
2. Don't think you can update from 2.4 to 2.6 just like that. I recommend a new install.
3. Yes, I have got a notebook with i910 (Sony Vaio VGN-270) running on Ubuntu with 855resolution and Xinerama.
4. No Broadcom. Linksys it is & ndiswrapper works just fine. No CPU issue.

---

### Post by amautsch on 2006-10-21
sorry for bugging again.

- don't know about the color problem, maybe it's my flat panel ...
- haven't tried xinerama yet
- i manually upgraded debian to kubuntu

But one other question,
does acpi sleep (s3) work for you ?
It works for me, but after waking up again,
i only get a garbled red screen ....

i910resolution is installed and i think it's called in the
wakeup scripts.

thanks for your prev. answers

andreas

---

### Post by wieman01 on 2006-10-21
Have never used the sleep function so far. I am of no help there.

---

