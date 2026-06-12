---
title: "Partition Mess.."
date: 2009-04-04
forum: General Help
---

### Post by novakedy on 2009-04-04
Wow okay so, I have found myself into a pretty nice partition mess. I have no clue what to do. I really need some expert help I believe. I'll explain each step that I took from the very beginning as I remember it.

1. So a long time ago I had ended up with only being able to save 10gb of my corrupted Xp install. Xp was the only thing I had on the hard drive, and when it became corrupted I was able to erase my 10gb backup partition and use it as a storage for very important files that I could grab and transfer via Ubuntu LiveCD. Ghetto, I know.

2. With two partitions now, a 10gb (we'll call this the "storage" drive) and a 140gb (I think anyway), I was able to install a fresh clean version of XP on the big partition, leaving my 10gb alone.

3. This was all in the past, happened a while ago. I was able to rebuild everything over months and months. Everything was fine again. I had completely forgotten about some other files on my storage drive and decided to peek in there and copy them to my main drive (which I suppose I can call my "boot" drive, since I'm obviously not booting onto my storage one). 

4. This rendered that 10gb useless, so I figured, what the heck? I can delete that and use any old partition editor to add that 10gb to my 140, to make everything one big happy family and this computer done with anything deemed "risky" (such as reformatting, etc.).

5. I downloaded Paragon Partition Editor (I don't remember the exact name). I deleted the 10gb useless storage drive and was left with unallocated, and my boot drive. So I figured I could just drag the bar over to add that 10gb to my boot drive, but of course with my luck, it wasn't that easy.

6. I couldn't get that to happen. So I said, whatever, I'll just have that 10gb storage back just because I'd rather have it than have unallocated space. So I formatted that unallocated back into a useless storage drive.

7. Well, this was about a week ago. I had completely forgotten about it, because I hardly ever restart my computer. When I restarted my computer, something happened that hadn't crossed my mind at all in just that simple operation on Paragon Partition Editor.

8. It switched my primary and logical partitions. Yep. It was booting my storage drive, resulting in a message on my screen saying "No Operating System Found." Yeah, FML right? It gets kinda worse.

9. I needed to do something, so I did the only thing I could think of and I found that dusty old Ubuntu 8.10 LiveCD I burned for the heck of it. I wanted to see if I could use Gparted (or just the partition manager on it) to try and just switch primary with logical. It didn't. So I deleted my storage drive and figured it would default-ly put the main drive in control. 

10. It didn't. Even with unallocated space just sitting there, it didn't. I was really confused. So I decided to adjust more things.

11. I ended up with this confusing I don't even know. I took a screen of my partition map in the Ubuntu 8.10 Partition Manager.


Please help me =[

I just want my one, simple, drive of Windows XP WITHOUT erasing all of my stuff. I have nowhere to put any of my stuff (back up).

So if someone can just give me some help.



Here is the screen

[img]http://i40.tinypic.com/6t2ys2.png[/img]

---

### Post by easybake on 2009-04-04
The only way I can think of right now to get a sole XP install would be to do the following.

1. Shrink/resize your current XP partition in half (leaving enough space to back up all your files)

2. Create a new NTFS partition out of the space you created. 

3. Back up all your XP data onto that new partition. 

4. Delete the old XP partition.

5. Create an New NTFS partition starting with the beginning of the disc. 

6. Install xp onto that partition.

7. Move your back up files onto the new XP install. 

8. Delete all other paritions. 

9. Resize your new XP install partition for full disc usage.

---

### Post by novakedy on 2009-04-04
That sounds like it might actually work! I will try this, although I dread installing XP so many times.. lol.


I had an idea last night to just delete all my other partitions except my ntfs, and just let it take over the full drive, and then use the windows repair and fix the master boot record.

Naturally, that didn't work either.



But this method you said sounds like it should do the job. (Although it is much installing and copying, but that's okay)

---

