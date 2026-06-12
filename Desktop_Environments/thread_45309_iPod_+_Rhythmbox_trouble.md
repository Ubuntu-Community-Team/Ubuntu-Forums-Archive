---
title: "iPod + Rhythmbox trouble"
date: 2005-06-29
forum: Desktop Environments
---

### Post by pdpi on 2005-06-29
Today I just decided to see what rhythmbox would do when I connected my iPod (I've been using windows to do that part of things). So far so good, the "iPod" library was immediatly aware of the iPod, and I can play music from it as if it were in my HD. However, I can't seem to transfer music **TO** the iPod. No form of clicking and dragging seems to solve that problem.

Since most search results in the subject of the iPod only returned results regarding GTKPod, and are, for the most part, a bit old, I was wondering if Rhythmbox actually as support for writing to the iPod, and if so, how to activate/use it.

---

### Post by not_yet on 2005-06-29
at the top of gtkpod there is a "+" sign with "Files" under it

click the "+" choose the song(s) you want, and say OK to the dialog

songs are added to your ipod :)

---

### Post by pdpi on 2005-06-29
remarkably helpful, but regarding a tool I'm not at all interested in, unless I can't get Rhythmbox working with the iPod.

It's just that much neater that I can do that from within the same program I use to listen to music. Integration of this sort is what we're supposed to be working towards. Besides, it would just be plain sweet if we could tell people "the iPod works out of the box, just as if it were a Mac", which is presently not the case. You can download a program to use to full potential (kind of), but
1) You have to use a separate program to listen to music and to sync your iPod.
2) Download for download, you're in the same place as windows, while you could be  in the same spot as Apple easily.

Sure, it's just one mp3 player, but it is *THE* mp3 player that has about 70% market share. I can see how actually fully supporting 70% of the mp3 player marketshare would make a bit of a difference with people who own an iPod but don't feel like dishing out the money for a new computer. "Look, it supports the iPod out-of-the-box, it even looks kind of like Mac OS in general layout, and it runs on your computer. Plus you can try it from a CD to see if you like it". Can you see the image bonus on that?

---

### Post by angkor on 2005-06-30
I use Amarok to listen to my music and it's supposed to support my iPod, yet I never use it with my iPod. I prefer gtkpod for that, cause it is fully functional with it and works even better with my iPod than the windows iTunes (gtkpod is comparable to the mac iTunes, except for looks)

> Sure, it's just one mp3 player, but it is *THE* mp3 player that has about 70% market share. I can see how actually fully supporting 70% of the mp3 player marketshare would make a bit of a difference with people who own an iPod but don't feel like dishing out the money for a new computer. "Look, it supports the iPod out-of-the-box, it even looks kind of like Mac OS in general layout, and it runs on your computer. Plus you can try it from a CD to see if you like it". Can you see the image bonus on that?

No, not really ;) 

The only thing you need to install is gtkpod and set up your /etc/fstab to be able to work perfectly with your iPod. Do you want Ubuntu to support your iPod out of the box or do you want full support of the iPod, cause the latter you already have.

---

### Post by pdpi on 2005-06-30
gtkPod works just fine. I'm not complaining about that. However, it's a bloody mess of an interface. And I'd like that instead of saying "use gtkPod!", somebody answered my question: can I use rhythmbox instead? If not, is there any gnome-native application that can be used to both listen to music and upload it to the iPod?

<rant>
You see, I publicize Ubuntu to all my friends, be they windows users or non-ubuntu linux users. One of my "selling points" on ubuntu is usability. Many small details in gnome/ubuntu work remarkably well, and much has been done to smooth the rough edges. But precisely because of this, it irks me slightly to have to use two different programs for my music needs. iPod support via gtkPod is fine and good, but what does J Random User think when he boots into ubuntu, opens a music player that looks remarkably like iTunes, plugs in his iPod to see its track list shown like iTunes, but can't update his playlist from that very same program, like he could in iTunes. It's bloody frustrating. It's snatching defeat from the claws of certain victory. We shouldn't be satisfied with "it works". We should be aiming for "it works at the very least as well as the next best competitor".

I don't have to configure iTunes to detect the iPod. It just does. I didn't have to configure Rhythmbox to automagically find the iPod as soon as I plugged it in. It just did. I'd much like that level of integration to reach write-support for it as well, especially because write support already exists.
</rant>

---

### Post by angkor on 2005-06-30
Well I've searched for any talk of write support for the iPod, but it seems it's not there yet. The rhythmbox developers are probably still working on it and right now it only supports reading the ipod. 

So if you do want to be able to sync your iPod you'll have to go with gtkpod or gnupod. If you insist on having one app to listen to your music and interacting with your iPod you should look into amarok. It's not a gnome app but works quite nicely on Ubuntu (haven't tried the iPod support part though). Good luck.

---

### Post by pdpi on 2005-07-01
Thank you, angkor. That is (almost) EXACTLY the answer I wanted to get straight from the top. I'd have preferred if you said that Rhythmbox supported iPod writing, though :). In Breezy, perhaps.

---

### Post by angkor on 2005-07-02
:) Hope so for you too

---

