---
title: "gtkpod ruined my ipod..."
date: 2006-06-03
forum: Desktop Environments
---

### Post by trawler on 2006-06-03
I just got my brand new ipod. The first thing i did was update it using iTunes on my windows Xp (I have a dual boot machine, with kubuntu 6.06). I was anxious to try it out, and didn't want to bother with the linux apps, at least not untill i got some data on it.

Once i was happy with how things worked, I switched back to linux, and after reading some manuals, I decided to give gtkpod a shot. First update went fine - I managed to update some files and even upload some new files. I went back to windows, and made sure iTunes can see the updated files, which it did, and I did some more updating (mainly to Id3tags).

Then, after going back to gtkpod, I got an error saying that there was an error with the hash sum in iTunesDB file. Then, basically, gtkpod froze, and I had to kill it.

After that, I could no longer play anything on my ipod, songs were choppy and it basically freezes before even finishing one song, and then I'm forced to restart it.

My windows machine also stopped recognizing it - I can see it in My Computer, but not in iTunes. Eventually, I thought of trying to reset the whole thing, but even iPOD updater can't recognize it, or basically, it just freezes and i'm forced to end the task...

I don't know what to do anymore - since I can't use it, or reset it... 
BTW - my linux still recognizes it just fine, except I can't use gtkpod anymore. 
I got ipod video (5th gen, 30 gb).

I need help...

---

### Post by trawler on 2006-06-03
Ok, looks like I managed to fix it - I read a post which suggested to switch the ipod to diskmode and quick format it. I was afraid to do this at first, but I figured I had nothing to lose.... And lucky for me, it worked :D.

I doubt that I'll try using linux with my ipod again... It's a shame, since there's nothing I hate more than using Windows... But untill I find a better solution, I'm sticking to windows on this one...

---

### Post by kabronkline on 2006-06-03
This seems to be more of a hardware support issue. Apple is to blame, not Ubuntu.

---

### Post by OffHand on 2006-06-03
My iPod mini auto mounts, launches an application which I can use to play tracks from my iPod, gtkpod works fine. Does what it needs to do. I havn't plugged it into Windows/iTunes anymore.

---

### Post by BoneyOne on 2006-06-03
Yup, I had the same sort of problem.  I grabbed my wife's iPod mini and plugged it in last night and it automounted. I started gtkpod, got the error and only 1 song of her's showed up.  All of the others are still there as the filesize hasn't changed, but not availabe.

I haven't tried to go back to windows to see what it is going to do yet.

---

### Post by angkor on 2006-06-03
[QUOTE=trawler] managed to update some files and even upload some new files. I went back to windows, and made sure iTunes can see the updated files, which it did, and I did some more updating (mainly to Id3tags).

Then, after going back to gtkpod, I got an error saying that there was an error with the hash sum in iTunesDB file. Then, basically, gtkpod froze, and I had to kill it.
[/QUOTE]

iPods are quite monogamous. They don't like fooling around with different apps. ;) Linux didn't bork your ipod. You did by using different programs on it. Use one app only to manage your ipod.

If your ipod gives you troubles writing the itunesdb or something you can try:

```
sudo dosfsck -a /dev/sda2
```

This command will repair the crappy fat32 filesystem on the ipod if it can. This way a complete format isn't necessary.

My iPod has seen itunes and windows once. That was when I needed to format the drive after I first bought it. After that I've been happily using my ipod in ubuntu.

---

### Post by BoneyOne on 2006-06-03
Despite Linux not seeing most of the files on the ipod, when I plug it into my Xbox360 it shows all the music, placed on it with both windows and linux.

---

### Post by crane on 2006-06-20
I just plugged my ipod mini into a windows system at work. Itunes saw it and asked if I wanted to replace files from current playlist, I clicke dno, The it said there was a software update for the I pod. I clicked no again. I was afraid it would screw up gtkpod. 
Windows iTunes sees the songs but will not play them.

---

### Post by joske on 2006-06-20
I have 2 ipods, a nano, and a 40 GB 4th gen one, and neither has given any trouble with gtkpod, I love it. I once had a crash with the big one, and I managed to backup the firmware and reformat/reinstall the thing from within linux (I don't even have a windows machine, haven't had one for years).

---

### Post by shortsellyhoonow on 2006-11-05
> **kabronkline said:**
> This seems to be more of a hardware support issue. Apple is to blame, not Ubuntu.

LOL.  This sh1t distro is to blame IMHO...

---

### Post by taurus on 2006-11-05
> **shortsellyhoonow said:**
> LOL.  This sh1t distro is to blame IMHO...
Okay, I am not sure exactly what's your problem is.  If you think Ubuntu is terrible, stop blaming and go use another distro.  Nobody is forcing you to use Ubuntu.  

So, just relax and take a deep breath...

---

