---
title: "How to unite partitions?"
date: 2009-03-04
forum: General Help
---

### Post by gogitosbanditos on 2009-03-04
I've just uninstalled Vista on my laptop and formatted its paartitions as ext3. How can I attach them to the linux partition I already have?  Now I can see them just like /media devices , but my main partition needs free space. Help please!:(

---

### Post by chriskin on 2009-03-04
a harmless way is to download the gparted live cd from gparted's site and from there delete the former vista partition and expand the ubuntu one

they have to be one next to each other though

---

### Post by chriskin on 2009-03-04
> **chintu33 said:**
> I think you should re-install


reinstalling is not a solution for everything, there are easier ways most of the time

---

### Post by DBrocks on 2009-03-04
One word my friend: Gparted
 
Now, you can't literally merge the partitions. However, you can resize one partition into free space left over by the other, which is essentially the same thing.

---

### Post by theozzlives on 2009-03-04
Simply delete your old Vista Partition and resize your main partition.

---

### Post by DBrocks on 2009-03-04
> **chintu33 said:**
> I think you should re-install
 Lol sounds like geeksquad mentality to me...
 
Darn it! you beat me to it!

---

### Post by gogitosbanditos on 2009-03-04
> Simply delete your old Vista Partition and resize your main partition.
i already tried gparted and I couldn't find the way to increase the size of my partition, with Vista partition deleted.

---

### Post by chriskin on 2009-03-04
the live cd one or the one inside ubuntu?

---

### Post by chriskin on 2009-03-04
expanding is a clearly an option at the "resize/move" button , in case you cannot find it

---

### Post by gogitosbanditos on 2009-03-04
I have the live cd and I can resize partition, but only shrink it! :-(

---

### Post by chriskin on 2009-03-04
did you delete the other partition? it has to be BOTH deleted and next to the ubuntu one to expand there

if you do it, you can expand it , or at least i have done it more than once

---

### Post by gogitosbanditos on 2009-03-04
> **chriskin said:**
> it has to be BOTH deleted and next to the ubuntu one to expand there
Next to the Ubuntu one? I didn't think about it before ;) thanks a lot i'll try tmrw. I am really really ill and I don't know what the hell am I working on my laptop. If I experience any problems, I will let you know. Anyway thanx everyone.

---

### Post by Rallg on 2009-03-04
After you have resized Ubuntu, you may find that the partition UUID has changed. Then, when you boot, GRUB may claim that it cannot find the partition. If that happens, do not panic. You can fix the problem by booting to the live version, then editing a file on the hard drive. If you have that problem, I am sure someone will tell you what you need to do.

---

### Post by Junness on 2009-05-18
One more question. 
And what if both my freshly deleted partitions are not next to each other?
Is there any possibility to...hum..."move" one of them?
[I]
[In my case I only need to merge two data partitions, C & D disks (ah, a pretty Win redundancy *=)) , 
but the trouble is that I have the Ubuntu ext3 & swap partitions "between" them][/I]

What is to be done?

[I][in fact all I need is to be able to create one more primary partition after all that stuff 
- since you can't have more that four of them, the easiest way is to diminish the number of the p's existing
- just for the context][/I]

The only idea I got is to expand the Ubuntu ext3 partition into one of those two deleted.

But I'll be very grateful if someone has a better solution, more corresponding to the initial purpose *=)

//Hrm, hope my "essay" didn't get that complicated *X)

---

