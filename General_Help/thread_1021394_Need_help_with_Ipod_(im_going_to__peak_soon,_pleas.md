---
title: "Need help with Ipod (im going to ******* peak soon, please end my misery)"
date: 2008-12-25
forum: General Help
---

### Post by cameron1991 on 2008-12-25
Ok, I got an ipod for xmas. I would really enjoy it much more if it had a song (or perhaps even two) on it.

I have Amarok, but its not doing **** with my ipod (i added the device, mount point /mnt/ipod and i tried /media/ipod). It keeps saying no device is mounted.

Rhythmbox is no better, i ripped a CD to my library but it won't let me drag and drop onto my ipod.


Please, help me, I'm about to start breaking **** I'm so frusterated. So, in the mean time, I'm gonna go have a smoke, and I'll leave it to the (more) computer savvy people to spare me from this [non] musical hell.


and seriously, WHAT THE ****. HOW ******* HARD IS IT TO MAKE A PROGRAM THAT JUST LOADS SOME **** ONTO AN IPOD. ******* hell, im seriously considered abandoning the life path I am on and going back to programming, so I can make some programs that just do what they're ******* supposed to do. /end rant.

---

### Post by damis648 on 2008-12-25
What model iPod do you have?

---

### Post by abn91c on 2008-12-25
you ipod mount point will be [COLOR="Blue"]/media/your ipod name here[/COLOR], input that in the amarok  settings>devices

---

### Post by MaxIBoy on 2008-12-25
First of all, the idea of going back to programming in order to write what you see a need for is actually the right answer. Bravo. But I don't think that will be needed in this case, as many people have already got theirs working.


Try actually looking in /media, that will help you find your iPod.


And by the way, calm down and breathe deeply, or you'll give yourself a heart attack.

---

### Post by cameron1991 on 2008-12-25
I am breathing calmly now. I just really needed a smoke :)

anyways, I'll try out your advice and see what happens. I read something about having to format the ipod though? (which is a 4th gen nano btw)


And thanks for all the help :)

just looked, the ipod is in media


*ok, i think its recognizing it now, but it wont let me put tracks on it. When i hit transfer, it says "track not playable on media device*. any suggestions?

---

### Post by abn91c on 2008-12-25
> **cameron1991 said:**
> I am breathing calmly now. I just really needed a smoke :)

anyways, I'll try out your advice and see what happens. I read something about having to format the ipod though? (which is a 4th gen nano btw)


And thanks for all the help :)

just looked, the ipod is in media


*ok, i think its recognizing it now, but it wont let me put tracks on it. When i hit transfer, it says "track not playable on media device*. any suggestions?
if you are using Amarok make sure you have the mp3 support installed, in 8.10 al least in kubuntu you get a prompt to install MP3 files.

---

### Post by SuperSonic4 on 2008-12-25
iPods can't play ogg files either

---

### Post by cameron1991 on 2008-12-25
how do i check if i have the mp3 support installed?

ok, amarok will play my cd's, but wont allow me to import or drag and drop them into my collection. it keeps saying the dropped track is invalid

:S

---

### Post by SuperSonic4 on 2008-12-25
```
sudo apt-get install ubuntu-restricted-extras libxine-ffmpeg
```

---

### Post by cameron1991 on 2008-12-25
> **SuperSonic4 said:**
> ```
sudo apt-get install ubuntu-restricted-extras libxine-ffmpeg
```


```
E: Couldn't find package libxine-ffmpeg
```

:(

I'm beginning to hate computers.


Is there ANYBODY here who can give me a step-by-step guide to putting my cd's onto my ipod? I don't care what I have to download or anything, i just want to get my ipod working. Thanks :D

---

### Post by lingenfr on 2008-12-26
> **SuperSonic4 said:**
> iPods can't play ogg files either

Unless you load [rockbox]("http://www.rockbox.org/") that is...

---

### Post by albinootje on 2008-12-26
> **cameron1991 said:**
> ```
E: Couldn't find package libxine-ffmpeg
```

:(

I'm beginning to hate computers.


Is there ANYBODY here who can give me a step-by-step guide to putting my cd's onto my ipod? I don't care what I have to download or anything, i just want to get my ipod working. Thanks :D

Try --> libxine1-ffmpeg

You need another smoke break I think ...

---

### Post by agathian on 2008-12-26
I have a ipod nano and am able to use it with "gtkpod"..   i just use it to transfer file to and from ipod. For playing, ripping, etc - other apps like rhythmbox, amarok etc.

That said - please note that i have been using this ipod with windows/itunes for a while - doubt if this makes any difference, since ipod probably comes preformatted/installed.

Good luck..

---

### Post by wootah on 2008-12-26
> **agathian said:**
> I have a ipod nano and am able to use it with "gtkpod"..   i just use it to transfer file to and from ipod. For playing, ripping, etc - other apps like rhythmbox, amarok etc.

That said - please note that i have been using this ipod with windows/itunes for a while - doubt if this makes any difference, since ipod probably comes preformatted/installed.

Good luck..

Is there still the issue when the ipod is formatted using the mac filesystem that we cannot change it to fat32 from within Linux? Did that ever get solved?

---

### Post by andnobodyslept on 2008-12-28
At wootah:

Not certain, I'm in the same boat, family bought me a ipod classic (5th generation?) for christmas and I set it up using my girlfriend's macbook, now gtkpod and all other media players are telling me that my ipod is read only.

I found this
[http://davesource.com/Solutions/20080225.iPod-linux-read-only.html]("http://davesource.com/Solutions/20080225.iPod-linux-read-only.html")
and this
[http://www.pedrodiaz.com/cs/linux/ipodmini.php]("http://www.pedrodiaz.com/cs/linux/ipodmini.php")

but have yet to try them, due to a lack of time; though I will report back.

---

### Post by MartyBuntu on 2008-12-28
> **lingenfr said:**
> Unless you load [rockbox]("http://www.rockbox.org/") that is...

Not on a 4th gen Nano.

---

### Post by andnobodyslept on 2008-12-28
So I can get my classic ipod to sync with both rhythmbox and gtkpod after using the davesource link; though all I needed to do was connect my ipod to a mac and change it over to non-journaling, every time I tried to change my fstab something funky would happen. So far everything is working well except some of the album art doesn't want to sync. 

Hope this helps someone out there.

---

### Post by pmooney78 on 2008-12-28
I had similar problems trying to get my iPod to work under Xubuntu. Here are some things to try:

* If at all possible (and you've never done this before), plug it into a computer running Windows/MacOS, open iTunes, and transfer ANY ONE TRACK to the iPod. Go over to a friend's house if you have to. This will initialize the iPod's hidden files etc. so that Linux apps have an easier time with it. Also, while you've got it plugged in to a real iTunes installation, notice whether the iPod format is described as "Windows" or "Macintosh."

* Make sure your iPod is mounted before trying to use a Linux app with it. Go to your file manager application and double-click on your iPod to mount it. If you can see folders with names like "iPod_control", then it's mounted.

* If it's a Mac-format iPod, you probably need to install support for Apple's HFS+ filesystem. Try typing "sudo apt-get install hfsplus" (no quotes) in a terminal.

* Try using other iPod management programs. I have the best luck with GTKPod (available through the standard repositories) and yamiPOD (you'll have to do a google search and manually install).

The real problem is that Apple has made the iPod's interfaces as cryptic as possible so that you're forced to use iTunes ... and then hasn't released an iTunes for Linux. It's not inherently a Linux problem, but rather that Apple is making things as difficult as possible. That said, it's possible to get most iPods working under Linux, but (as you've noticed) it takes patience sometimes to get it working.

---

### Post by habana on 2008-12-29
My wife got a new Ipod from her rellies for Christmas so I scored her old one - a 4th gen I believe. First job was a system reset as per Ipod manual. To rip music off CDs I used Grip (in the repositories) which I found easy to use. Some of the album/track data entries on the freedb.freedb.org database were a bit weird so I used Easytag (also in the repositories) to edit when necessary. Like others I have used gtkpod to manage the Ipod transfers. All in all a pleasant experience and no drama.

---

### Post by kokkus on 2008-12-29
Apple is pissing me off here. I have an iPod Touch which I can not use because iTunes doesnt work on my windows anymore and I do not want to use other peoples PCs every time I wanna do some changes on my iPOD. Becise I can't because my music is on my own PC.
Wtf is the reason for apple to do such a stupid thing to thier products so people can't just copy /paste their mp3s to the ipods like you could with the first old ipods.
Damn I hate apple for that. ANd people do pay alot of money for the ipods, So I would say that their products are as good as useless now.

Someone should email this thread to apple if they know someone there.
If I didn't know better I would say Apple breaks the law here.
Because they did this so ITunes is the only way to manage the ipods.
And untill itunes is available on all operating systems and platforms, this method is illegal.

---

