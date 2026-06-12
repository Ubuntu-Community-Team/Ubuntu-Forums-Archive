---
title: "CloneZilla LiveCD. Simple Question."
date: 2008-12-11
forum: General Help
---

### Post by Roasted on 2008-12-11
I'm using CloneZilla LiveCD to make several images saved on my laptop at work... so that way when I come across a single computer that may have died or needs a reinstall, I can just put that image on my flash drive, put the flash drive in the problematic computer, boot to CloneZilla LiveCD and restore the image on my flash drive.

The thing is, we have several different sized hard drives in some of our computers. Some are 15gb, some are 40gb. The size difference to us doesn't matter because all of the data resides on the server. 

Basically what I need is this... 

Say we have 1 model of computers across the entire district. But the one thing that can differ is hard drive size. I want to be able to restore an image via CloneZilla LiveCD and not have it transfer over the partition itself.

Example:

I create the image on a computer with a 15gb hard drive.
I save the image to my flash drive.
I come across the exact same computer with a 40gb hard drive that needs a fresh install.
I restore the image from my flash drive to the problematic computer.
I want my image, despite it being created on a 15gb partition, to span across the 40gb available on this computer.

I DO NOT want it to transfer over a 15gb partition ON the 40gb hard drive, therefore leaving me with 15gb usable space and 25gb unallocated. 

What setting in CloneZilla allows me to do this?

---

### Post by Titan8990 on 2008-12-11
I doubt any imaging software will let you do that. You need to restore the 15GB image and then resize the partition to use the remaining space.

---

### Post by Roasted on 2008-12-11
I just thought I remember hearing a setting in CloneZilla that DOES allow that... so that's why I wanted to research it more and see if this was possible.

Is there at least a bundle package of Gparted + CloneZilla on the same CD so I can just switch over to Gparted and resize it then?

---

### Post by logos34 on 2008-12-11
> **Roasted said:**
> 
Is there at least a bundle package of Gparted + CloneZilla on the same CD so I can just switch over to Gparted and resize it then?

here you go:
[http://gpartedclonz.tuxfamily.org/](http://gpartedclonz.tuxfamily.org/)
[http://www.linux.com/feature/115208](http://www.linux.com/feature/115208)

---

### Post by Roasted on 2008-12-12
Question. 

Some of the computers I have to work on at work are pretty old, and I think some of them have USB 1.1 in them because of the slow speed it took in Clonezilla to transfer the image via USB flash drive. The same flash drive, same image, same Clonezilla LiveCD on a newer computer and the sucker was done in a fraction of the time.

Anyway, my question is this. I have a laptop I carry with me. Is there any way (whether in XP Pro or Ubuntu) I can "push" the image from my laptop via ethernet connection straight to the computer in question? Like can I just use a patch cable between my laptop and the problematic computer and push the image over? If so, that'd help out... Any ideas?

---

