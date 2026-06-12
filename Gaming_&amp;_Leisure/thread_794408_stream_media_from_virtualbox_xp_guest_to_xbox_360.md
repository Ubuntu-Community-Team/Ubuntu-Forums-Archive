---
title: "stream media from virtualbox xp guest to xbox 360"
date: 2008-05-14
forum: Gaming &amp; Leisure
---

### Post by nunki on 2008-05-14
Tried posting this in the Virtualization forum, but didnt get very far.

I am currently running Hardy 64bit, and have a windows xp sp2 guest running in virtualbox with host networking setup. I also have a samba share that I use for sharing files between ubuntu and my girlfriends mac(samba share on ubuntu). The guest os is able to log into the samba share and add all the media files to media player 11 and play them no problem (even able to turn on media sharing for the xbox).

My Xbox 360 is able to see the guest os on the network and connect; it can even build a list of all the files in the library, but is unable to play any. Every song and picture has a red icon next to it and I get an error when trying to play any of them. Keep in mind the guest os which is "sharing" is able to play all of these files no problem.

Anyone try doing this before? Any clues why these simply wont play?

I have double checked all the file permissions, and taken a second look at smb.conf, but everything works great. Xbox just cant seem to play the files. Ive tried allowing guests in samba, but beyond that I dont have a clue.

Just to clarify, the red icon seems to indicate an unsupported type, but the only types I have are .mp3 and .jpg

---

### Post by Sleaka J on 2008-05-15
This may not help, but I remember a mate of mine bringing over a DivX movie on New Years Eve to another mates house. We intended to watch it on his Xbox360, but it had the red icon as he'd not downloaded any codecs for it.

From there we tried to upgrade and connect to his Xbox Live account (from his original Xbox), but that proved far too difficult as you have to input the last four digits of a credit card, which he no longer had.

Are you able to play MP3 and view JPG files natively on the Xbox360? By that I mean without using the network.

---

### Post by nunki on 2008-05-15
> **Sleaka J said:**
> This may not help, but I remember a mate of mine bringing over a DivX movie on New Years Eve to another mates house. We intended to watch it on his Xbox360, but it had the red icon as he'd not downloaded any codecs for it.

From there we tried to upgrade and connect to his Xbox Live account (from his original Xbox), but that proved far too difficult as you have to input the last four digits of a credit card, which he no longer had.

Are you able to play MP3 and view JPG files natively on the Xbox360? By that I mean without using the network.

Yes I am. In fact, before I switched to ubuntu, I regularly streamed this same media to my xbox through windows. Codecs shouldnt be the problem as I am able to play them on the guest os without issue.

---

### Post by Robocoastie on 2008-05-15
MCE content is actually rendered on the PC and streamed to your extender (which in your case is the XBOX360). Direct-X functions like MCE uses don't work in VirtualBox which is why you all you get when you try to watch your videos is a black screen.

---

### Post by Sleaka J on 2008-05-16
> **Robocoastie said:**
> MCE content is actually rendered on the PC and streamed to your extender (which in your case is the XBOX360). Direct-X functions like MCE uses don't work in VirtualBox which is why you all you get when you try to watch your videos is a black screen.

That's a real pity. It was a good idea to do it the way that nunki wanted.

---

### Post by nunki on 2008-05-16
> **Robocoastie said:**
> MCE content is actually rendered on the PC and streamed to your extender (which in your case is the XBOX360). Direct-X functions like MCE uses don't work in VirtualBox which is why you all you get when you try to watch your videos is a black screen.

Pity...I suppose Ill try messing around with fuppes again. Although I didnt get very far with that. Just got the xbox to see the comp and connect, but nothing shows up.

---

### Post by Jovec on 2008-05-16
> **Robocoastie said:**
> MCE content is actually rendered on the PC and streamed to your extender (which in your case is the XBOX360). Direct-X functions like MCE uses don't work in VirtualBox which is why you all you get when you try to watch your videos is a black screen.

Not having done any of this...

If you are using the 360 as an extender it works as above, but the dashboard media player can play files directly from shared sources on the network (also local and usb storage).  To do the latter, you wouldn't need to use XP in VB, just set up a suitable samba share.  

The biggest losses are Live TV and the guide by not running 360 as an Extender, but you do gain the ability to play Mpeg-4 video this way (which doesn't work in Extender)

---

