---
title: "Issues with Audio CD on KDE4 (Intepid)"
date: 2008-11-19
forum: Desktop Environments
---

### Post by jtappin on 2008-11-19
With KDE 3 on Hardy, when I put an audio CD into the drive it gives a number of options (play, open in konqueror, etc.), and it's also possible to eject the CD with a right-click on the decktop icon.

However under KDE4 on Intrepid there is no indication in the "new hardware" list or elsewhere that the CD has been inserted. Likewise I couldn't find any means of ejecting other than the button on the drive or running eject from the command line. 

Is this intentional, an oversight, or a package I've not installed?

P.S. Amarok will play the CD and data CD's mount fine, so it's not that the CD drive isn't working or a bad disk.

---

### Post by MrE on 2008-11-27
I've got the same problem.

There is no indication that an audio CD (or any disc for that matter) has been detected.

The KIO plugin audiocd:/ doesn't work anymore.

Konqueror reports

```
The requested operation could not be completed
Cannot Open Resource For Reading
```

and Dolphin reports

```
Could not read .
```

Manually specifying the CD device in KDE's Advanced User Settings doesn't solve the problem. In Hardy I did not have to specify the CD device, I could insert an audio CD in either CD drive and audiocd:/ would let me browse the CD.

K3b however detects the audio CD fine.

Amarok (1.4.10) plays it without any problems, _provided_ I manually specify the default device in the Audio CD Configuration in the Amarok settings.

While I can still rip my CD collection using K3b, I _much_prefer the way I used to it in Hardy:

- insert CD in either my CD or DVD drive
- select 'Open with Konqueror' in the menu that popped up
- drag 'n' drop the FLAC folder onto the open Amarok collection (well, except that the FLAC folder never worked in neither Gutsy nor Hardy, but that's different story).

I wonder if many people come across this problem, and whether a bug has been filed...

---

### Post by jetpeach on 2008-11-29
same problem here. i haven't found a good way to rip an audiocd (to mp3) in kde4 yet, k3b won't work (complains of lame encoding error, even though lame encoder is installed), and without the kioslaves working i guess i need to find some other program to rip it.

---

### Post by poulhs on 2008-11-30
same problems here.seems like kde4 needs time to get to kde3 levels.
for ripping i tried RipOff(you need to install mp3 plugin).it does the job ok

---

### Post by jtappin on 2009-01-18
Just a couple of updates:

The problem still exists in the 4.2-rc1 from the PPA.

When running xfce4 I do get the audio CD automatically played in the xfce audio player (listen?). Thus I think we can be sure that the problem is in KDE4 not in some other aspect of the Intrepid configuration. [I'm not sure if thunar can open a cd the way konqueror does (or did)]

---

### Post by jtappin on 2009-01-26
A little more by way of updates (this is using the 4.2-rc1 from the PPA -- other versions may be different):

1) the audiocd:/ url **does** work in both konqueror and dolphin, but does not start automatically. (BTW: mistyping as audiocd:// crashes konqueror).

2) I've still not found any way other than using eject at the command line or pressing the button on the drive to eject the CD.

---

### Post by Tom Mann on 2009-01-29
I have MP3 support for my main PC with the audiocd:/ protocol, but not my Aspire One... I can't figure the difference for love nor money. I think I have lame installed on my main machine...

EDIT: [Installing lame worked!]("http://ubuntuforums.org/showpost.php?p=4940447&postcount=3")

I have also install libk3b3-extracodecs for K3B support.

```
sudo apt-get install lame libk3b3-extracodecs
```

Also I found that having more than one CD/DVD Drive can cause problems, but you can try:

```
audiocd:/dev/scd0
```

---

### Post by pliktrologos on 2009-04-05
I have the same problem too. The audiocd:/ protocol does not work with konqueror or dolphin on KDE 4.2.2 and I can't configure amarok play the audio CD although autorun works and k3b is accessing the files but can't rip the CD.

---

### Post by wandalalakers on 2010-05-18
This problem still exists in kubuntu 10.04.
I'm bummed because I never had this problem with kubuntu 8.04.
I can't imagine recommending kubuntu 10.04 to friends and this bug exists.
I don't have this problem with ubuntu 10.04 so it's defintely an issue with kde.  I've even heard of this problem with suse.

---

