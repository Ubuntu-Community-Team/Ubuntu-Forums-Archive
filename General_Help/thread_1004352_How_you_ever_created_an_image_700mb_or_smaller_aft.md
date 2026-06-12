---
title: "How you ever created an image 700mb or smaller after updates?"
date: 2008-12-07
forum: General Help
---

### Post by wandalalakers on 2008-12-07
Don't you hate it when you create an image for a friend, relative or client and it's over 700mb?  If it's for an old pc, it probably won't have a dvd drive.  I'm really loving *buntu and still spreading the word to friends and family.  I'm creating a remastersys image for friends and after updates it's about 900mb.  I also have a xubuntu image that has updates and it's under 700mb so I'll probably use that for older pcs.

---

### Post by DeMus on 2008-12-07
> **pcdoctor said:**
> Don't you hate it when you create an image for a friend, relative or client and it's over 700mb?  If it's for an old pc, it probably won't have a dvd drive.  I'm really loving *buntu and still spreading the word to friends and family.  I'm creating a remastersys image for friends and after updates it's about 900mb.  I also have a xubuntu image that has updates and it's under 700mb so I'll probably use that for older pcs.

Which program do you use to make and, if necessary, restore the image? I am looking for a program which can do that.

Thanks.

---

### Post by wandalalakers on 2008-12-07
Remastersys
I really love it.
I had a friend of the family who screwed up her xubuntu install that I did.  I just gave her a bootable custom iso that if it happens again, she can just reinstall the os herself.  My custom bootable iso has flash, mp3, rhythmbox, vlc, etc.

How to install remastersys
The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:

# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Open Synaptic or Adept
Install remastersys

Also, once your custom iso has been created you burn it.
The iso will boot and you use a Remastersys boot menu to restore your image.
Let me know if you try and how you like it.

If your image is over 4.5gb you won't be able to create a remastersys image.
You exclude certain folders if need be.

There are also different iso images that can be created.
Two specific ones are: 
1. Bootable iso that backs up your whole hard drive
2. Bootable iso that you can share with friends and family

Here is the remastersys user forum.
[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

---

### Post by DeMus on 2008-12-07
> **pcdoctor said:**
> Remastersys
I really love it.
I had a friend of the family who screwed up her xubuntu install that I did.  I just gave her a bootable custom iso that if it happens again, she can just reinstall the os herself.  My custom bootable iso has flash, mp3, rhythmbox, vlc, etc.

How to install remastersys
The Remastersys repository needs to be added to your /etc/apt/sources.list

Paste the following into the sources.list:

# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Open Synaptic or Adept
Install remastersys

Also, once your custom iso has been created you burn it.
The iso will boot and you use a Remastersys boot menu to restore your image.
Let me know if you try and how you like it.

If your image is over 4.5gb you won't be able to create a remastersys image.
You exclude certain folders if need be.

There are also different iso images that can be created.
Two specific ones are: 
1. Bootable iso that backs up your whole hard drive
2. Bootable iso that you can share with friends and family

Here is the remastersys user forum.
[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

Thank you. I've installed it and will try it out. Let you know the results.

---

