---
title: "DVD-R not recognized as recordable"
date: 2005-12-04
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-04
I searched the forums and may be double threading, but I didn't quit understand the other posts.

I got a DVD-R which I want to write on with my DVD+ReWritable burner. That should be possible, shouldn't it?

All of my burning applications give me error messages telling me that the media is not recognized as recordable.
K3b wants a double layer DVD. Why's that?
GnomeBaker says: ":-( /dev/hdc: media is not recognized as recordable DVD: 10010"

Any thoughts?

Thanx

Gabriel

---

### Post by taurus on 2005-12-04
I've found out that k3b is having problems with some cheap DVD+/-Rs (and some CD-RWs as well).  So, you may want to try another brand name of maybe the one that you have is bad.  Also, are you tryint to burn something bigger than 4.8GB?

---

### Post by GabrielWolff on 2005-12-04
[QUOTE=taurus]I've found out that k3b is having problems with some cheap DVD+/-Rs (and some CD-RWs as well).[/QUOTE]

But it's GnomeMaker too, and CD Creator.

[QUOTE=taurus] So, you may want to try another brand name of maybe the one that you have is bad.  Also, are you tryint to burn something bigger than 4.8GB?[/QUOTE]

No, it's 4.2 GB

Any other ideas?

---

### Post by sub_acoustic on 2005-12-20
I have the same problem,
though i was tried to write to a blank dvd+r with Cd creator.
I went and looked at the permissions, (which I don;t know how to change) and the write dvd box was not checked.  This could also be you're problem, how can I enable writing to dvd?

---

### Post by dcstar on 2005-12-20
[QUOTE=GabrielWolff]I searched the forums and may be double threading, but I didn't quit understand the other posts.

I got a DVD-R which I want to write on with my DVD+ReWritable burner. That should be possible, shouldn't it?
.......[/QUOTE]
No, DVD+ drives can only write to "**+**" media, DVD- drives only to "**-**" media.

DVD+- drives can write to both types, and all the drives should be able to read all types.

---

### Post by joshuapurcell on 2005-12-21
I seem to be having this same problem. Since installing Breezy I haven't tried burning a DVD with my new Sony DRU-800A. This drive is capable of burning both DVD- and DVD+ discs, so I'm still looking for why this doesn't work as it should. I've used GnomeBaker as well as the CD/DVD Creator application that is built-in to Nautilus, but both give a similar message. I've attached the message I'm getting from Nautilus. I'll post and update when I find anything else about this.

EDIT: I should say that I've been able to burn CDs without any problem, and I've burned DVDs with this same drive under Windows.

---

### Post by patrickfromspain on 2005-12-21
[QUOTE=joshuapurcell]I seem to be having this same problem. Since installing Breezy I haven't tried burning a DVD with my new Sony DRU-800A. This drive is capable of burning both DVD- and DVD+ discs, so I'm still looking for why this doesn't work as it should. I've used GnomeBaker as well as the CD/DVD Creator application that is built-in to Nautilus, but both give a similar message. I've attached the message I'm getting from Nautilus. I'll post and update when I find anything else about this.

EDIT: I should say that I've been able to burn CDs without any problem, and I've burned DVDs with this same drive under Windows.[/QUOTE]
well... in your thumbail it asks for a CD/ DVD with 7012MiB... maybe the problem is there?

---

### Post by joshuapurcell on 2005-12-21
[QUOTE=patrickfromspain]well... in your thumbail it asks for a CD/ DVD with 7012MiB... maybe the problem is there?[/QUOTE]
The DVDs that I'm using are type DVD-R with blank labels on the disc that I thought were the 8.54 GB size, but it turns out they were the 4.7GB version. I took out half of what I was trying to write to the disc and all my problems went away... sometimes the obvious thing is the source of the problem. And to think at first when I saw your response I was ready to say that couldn't be it without even double-checking the size issue... thanks for your help.

Sometimes it helps to talk through your problems with other people even with the dumb problems :).

---

