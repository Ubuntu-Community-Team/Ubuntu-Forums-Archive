---
title: "Finally I have Counter Strike 1.6 working in Wine (no lag or anything)"
date: 2006-02-17
forum: Gaming &amp; Leisure
---

### Post by renzokuken on 2006-02-17
Thanks to a couple of guides i have found on the web, I can actually now play CS1.6 on Breezy in Wine 0.9.7 with no problems, using only a Radeon 9200.

A brief guide for those interested cos i know loads of people have problems. ALthough, i wouldn't consider this a HOWTO, more of a report on my finidings, because with CS it seems what works for one doesnt always work for another.

Get the Ubuntu .deb from the wine sourceforge site, [**HERE**](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=174803) (wine_0.9.7-winehq-1_i386.deb)

Get the latest Steam Version (3 i think) from  [**HERE**](http://www.steampowered.com/index.php?area=getsteamnow)

Use 
# sudo dpkg -i wine_0.9.7-winehq-1_i386.deb
to install wine.

then go [**HERE**](http://appdb.winehq.org/appview.php?versionId=1554), scroll down a bit and follow the guide for "Option 1: Without Winetools or Internet Explorer".

Once Steam is up and running, go to the Games tab and choose to install Counter Strike, it took a couple of hours on a 512mb connection.

I then followed [**THIS GUIDE**](http://cslinux.hacka.net/) (complete credit to "Mr Grieves" aka Magnus for this, very helpful indeed) to get Counter Strike working. I used a value of 256000 for the heapsize.

Hope this works for someone else. I'm so pleased i can now play some CS, I was getting soooo bored of Mahjong.
 
PS. Yesterday, a new version of wine was released ( 0.9.8 ) but it hasnt been made into a deb for ubuntu yet. So may be someone wants to try that version when it is available and let us know how it goes.

---

### Post by squirrelplayingtag on 2006-02-18
I'm trying to get counter strike to run as well and I get to the point where I close out the steam and run winecfg but nothing happens. Any ideas?

EDIT: nevermind. It just takes a long time to respond. I made a sandwich and came back and it was loaded.

---

### Post by flummoxed on 2006-02-18
I got it working, but it doesn't seem to work with OpenGL, just with software rendering. I upgraded to the 2.6.14 kernel (didn't notice to change it to 2.6.15, but 2.6.14 has solved the issue of steam freezing too). Do I have to do some extra stuff to install OpenGL? 

Also, the toolbars are still visible when I run cs... anyone know how to get rid of em?

---

### Post by renzokuken on 2006-02-19
have u got a grafix card?

if you have, the thing i forgot to mention is make sure u install the appropriate ATI or nVidia drivers. there are two excellent guides on how to do this in the forums somewhere.

---

### Post by flummoxed on 2006-02-19
Yeah, I have a Radeon 9800 pro. The ati graphics drivers are somewhat of a hit-and-miss as far as I can tell, several people are having problems with them. I just reinstalled ubuntu, and I'm gonna put on the 2.6.15 kernel, and also try the latest driver's from Ati's site.

---

### Post by renzokuken on 2006-02-19
i have a radeon 9200, and although ATI support is somewhat lacking in Linux compared to nvidia, i have had no problems with the drivers.

did you follow this guide [http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+fglrx](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+fglrx)

---

### Post by flummoxed on 2006-02-19
Yeah, I did. No luck.

---

### Post by renzokuken on 2006-02-19
hmmmm, CS seems to be very hit and miss, and getting it working is more luck than methodology i think.

I'm running the k7 kernel (for AMD chips) if thats any help to anyone.

---

### Post by rama on 2006-02-22
**excelent** :d It Works....

---

### Post by -Rick- on 2006-02-22
New kernel did the trick for me(following those tutorials). Only lost bootsplash and sounds are muted by default now...

---

### Post by renzokuken on 2006-02-22
glad to be of service.......

you havent had any lag?? on previous attempts i would get about 30 seconds play, then it would lock up for 10-15 seconds, then play again for 30 secs, then lock up etc etc etc.....

but this way seems to have solved that for me

---

### Post by -Rick- on 2006-02-22
[QUOTE=renzokuken]glad to be of service.......

you havent had any lag?? on previous attempts i would get about 30 seconds play, then it would lock up for 10-15 seconds, then play again for 30 secs, then lock up etc etc etc.....

but this way seems to have solved that for me[/QUOTE]
Yeah I had that lag aswell, the fix is the 2.6.15 kernel :KS

---

### Post by zi99y on 2006-04-11
I have followed all the steps and am now running kernel 2.6.15 (without ck patch) and also tried the latest kernel 2.6.16 (with ck patch).

Problem: As soon as I attempt to start Counterstrike I get the splash screen with the 2 CT dudes and it just freezes there - I know this stage can take a little while on Windows but I have waited and waited and it just sticks there until I break out of it.

PS I have OpenGL enabled and working

Any ideas folks? my trigger finger is itchy [-o<

---

