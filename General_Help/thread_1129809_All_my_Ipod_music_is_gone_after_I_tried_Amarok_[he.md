---
title: "All my Ipod music is gone after I tried Amarok [help!]"
date: 2009-04-19
forum: General Help
---

### Post by Gnome_Priest on 2009-04-19
I'm a linux noob, so I would appreciate all the help spelled out (i.e  all command lines written down thoroughly etc.)

I'm from Norway, I have also posted this post in the Norwegian Ubuntu forum (but no luck yet).

I jailbroke my Ipod touch 8gb, installed OpenSSH and BSD Subsystem according to [this]("https://help.ubuntu.com/community/PortableDevices/iPhone") guide.

So I connected my Ipod with Amarok, and it worked like charm. I copied a couple of songs over to my Ipod, just to try it out. That worked to. But when I checked it out on my Ipod all the music, videos and podcasts where gone. It's still on the device when its connected to Amarok. When I connect it to iTunes (I have dual boot) its unreadable. iTunes wants to restore it. 

I have searched the web for solutions, but haven't found anything yet. Is there a way to restore my music library, or did I do something wrong (obviously I did :( ).

All help and pointers is appreciated.

---

### Post by hesjnet on 2009-04-20
I have only positive experiences with Songbird and ipod.

Last ned fra [www.getsongbird.com]("https://bugs.launchpad.net/ubuntu/+source/tzdata/+bug/200549")

Easiest way without installing
Extract the folder named Songbird (its inside the folder "."
Open the extracted folder.
Right click on the file called "Songbird" (Next to the icon file)
Choose Egenskaper(Properties)
Choose Rettigheter
Mark "Tillat kjøring av filen som program" (Allow file to run as a program)
Click OK
Double click on the file Songbird to open the program.

Lykke til :popcorn:

---

### Post by nj96 on 2009-04-20
Youve got dual boot right?
what OS do you have on the other boot?

---

### Post by Orc65 on 2009-04-21
I had a similar problem today with my EeePC running Xandros, I connected a friends iPod, opened it in the music manager (Amarok) and could play the files but upon disconnection the iPod showed no files of any sort available and her windows laptop does not even detect the iPod now. Although the EeePC has no problems using it.

I noticed that the iPod does not show up in the task bar as a USB device nor could I locate a mount point, an iPod folder does show up in /media right clicking only gives folder options.

I assumed it was caused by not unmounting before disconnecting, much like an unsafe removal in windows. 

I have yet to try it on my Ubuntu system or any other Linux system, any ideas?

---

### Post by Gnome_Priest on 2009-04-21
Nj96: Windows xp

ord65: You should be able to set the ipod in recovery mode following [this]("http://support.apple.com/kb/HT1808") receipt.

Hesjnet: Takk (thanks), I'll give it a try. Do you have an Ipod touch? Do you sync it wireless or with usb-cable?

I restored my ipod to fabric state, jailbroke it again and tried again. The same thing happened. It worked perfectly until I tried to transfer songs, this time with gtkpod. I believe it has something to do with firewireguid, so I tried to identify and set the correct firewireguid. But I didnt succeed. I have recovered the ipod once more, and for now I use dualboot / itunes to sync it :)

Thanks for answering :)

---

### Post by Orc65 on 2009-04-21
> **Gnome_Priest said:**
> 
ord65: You should be able to set the ipod in recovery mode following [this]("http://support.apple.com/kb/HT1808") receipt.

Thanks for the reply will try this out today and reply later today with the result.

---

### Post by hesjnet on 2009-04-21
> **Gnome_Priest said:**
> Nj96: Windows xp

ord65: You should be able to set the ipod in recovery mode following [this]("http://support.apple.com/kb/HT1808") receipt.

Hesjnet: Takk (thanks), I'll give it a try. Do you have an Ipod touch? Do you sync it wireless or with usb-cable?

I restored my ipod to fabric state, jailbroke it again and tried again. The same thing happened. It worked perfectly until I tried to transfer songs, this time with gtkpod. I believe it has something to do with firewireguid, so I tried to identify and set the correct firewireguid. But I didnt succeed. I have recovered the ipod once more, and for now I use dualboot / itunes to sync it :)

Thanks for answering :)

Gosh Sorry. I forgot you had an ipod touch. They offically stopped supporting this in the 0.5 version(it is now 1.1.2) Maybe it'll work, I don't know. 

If you test it. Remember to install the ipod support addon;)
Tools-Addon-Get extensions
Vertøy-Utvidelser-Get extensions

---

### Post by hesjnet on 2009-04-21
If songbird doesn't work then you might want to check out this bloggarticle:

[Using Amarok and other iTunesDB compatible software with the iPhone 2.x]("http://marcansoft.com/blog/2009/01/using-amarok-and-other-itunesdb-compatible-software-with-the-iphone-2x/")

I don't know if Songbird is using itunesdb. Hopefully it does.

---

### Post by Gramps on 2009-04-21
If I remember right the new iTunes use a different db and when I plugged myiPod into Linux for the 1st time I was told that the database was wrong, then given the option to convert it. It was then suggested not to use the iPod with the new iTunes any longer. Can't remember off hand which music player I got this message from, 

My Nano works fine with Rythmbox bit I don't connect it to iTunes any longer and for downloadable music I use Amazon Music

---

### Post by Gnome_Priest on 2009-04-25
hesjnet: Thanks for the link. It looks promising. I think i will try that. (I hope it works, 'cause I cant find my usb-wire, I'm sure it's here somwhere ;)
.

---

### Post by Gnome_Priest on 2009-04-25
It worked ! :guitar:

I followed the instruction on hesjnet's link, and now I can wireless transfer songs between ipod touch and amarok :P

This is what I did:
1. shh root@my-ip-adress
2. cd ..
3. cd ..
4. cd System/Library/Lockdown
5. nano Checkpoint.xml
6. ctrl-w to search for "DBVersion"
7. Change the value from 4 to 2. 
8. Restart
9. Transfer

Thanks guys! 

How do I mark this as [solved]?

---

