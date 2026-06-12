---
title: "Making my /home partition fat32"
date: 2009-05-31
forum: General Help
---

### Post by CynicalPsycho on 2009-05-31
I'm planning on putting ubuntu 9.04 on an enclosed hdd so i can make it mobile. One thing i'd wanted to do was partion the /home directory seperate from the rest of the operating system, so as to make it easier to switch linux OS's if i so chose to at a later date

And I was hoping i could make that partition fat32 so I could use the same drive as a storage drive and access it's files while booted into windows...

Does anyone know of any reasons not to use Fat32 as my partition for /home?

---

### Post by jonathanysp on 2009-05-31
well i think FAT32 is kinda an old file system and it cannot handle files bigger than 4gb which is sometimes really annoying. Also for me it seems to get corrupted more easily. You can always make the /home partition ext3 and install ifs on windows so you can read that partition, thats what i do.

---

### Post by CynicalPsycho on 2009-05-31
> **jonathanysp said:**
> well i think FAT32 is kinda an old file system and it cannot handle files bigger than 4gb which is sometimes really annoying. Also for me it seems to get corrupted more easily. You can always make the /home partition ext3 and install ifs on windows so you can read that partition, thats what i do.
but what if you use it on systems that aren't yours and that you don't have the liberty of installing stuff on?

---

### Post by Wiebelhaus on 2009-05-31
I think this will yield unexpected results , I don't see it working. Using fat32 that is , the separate /home partition of course will work but I don't see fat32 working well or at all for that matter.


Try it but be sure to have a back up!

---

### Post by CynicalPsycho on 2009-05-31
> **jonathanysp said:**
> well i think FAT32 is kinda an old file system and it cannot handle files bigger than 4gb which is sometimes really annoying. Also for me it seems to get corrupted more easily. You can always make the /home partition ext3 and install ifs on windows so you can read that partition, thats what i do.

After researching what you said, I see that your solution is probably the only viable one...

Thanks btw :)

---

### Post by CynicalPsycho on 2009-05-31
> **Wiebelhaus said:**
> I think this will yield unexpected results , I don't see it working. Using fat32 that is , the separate /home partition of course will work but I don't see fat32 working well or at all for that matter.


Try it but be sure to have a back up!
Nah, everything i've read pretty much says 'files corrupted' 'didn't work' 'not gonna work' 'back it up!' lol...

I had actually even tried previously and ended up with an unreadable fat32 fs but didn't wanna think this was the problem... Oh well i guess it'll be 
ext4 for my root and boot, ext3 for my /home and a swap partition.

---

### Post by pbpersson on 2009-05-31
FAT32 is fine as a swap partition in Windows where you don't care about data loss.  It is an old "non-journaling" system which means.....well, it means files get corrupted and data gets lost.

I would use NTFS personally.  That is assuming that Linux will allow you to do this.

If not.....I am wondering if you can use some "mirror" software in Linux to write all changes applied to the ext3 partition over to an NTFS partition.  I am really just thinking out loud here....

---

### Post by Wiebelhaus on 2009-05-31
> **CynicalPsycho said:**
> Nah, everything i've read pretty much says 'files corrupted' 'didn't work' 'not gonna work' 'back it up!' lol...

I had actually even tried previously and ended up with an unreadable fat32 fs but didn't wanna think this was the problem... Oh well i guess it'll be 
ext4 for my root and boot, ext3 for my /home and a swap partition.

EXT3/4 is the best anyway , Now I have successfully setup file serving using multiple NTFS shares without issue in a office environment , only thing that didn't translate properly were scripts for some reason , which I didn't care enough to research.

---

### Post by Keith Hedger on 2009-05-31
The main problem with using FAT32 as your home partition is that it doesn't support proper linux file permissions or symbolic links both of which are an integral part of linux (some stuff like ssh require certain permissions on a folder to work at all)

---

### Post by cariboo on 2009-05-31
If you've got the room. why not create 4 partition, /, /home, swap and data, where the data partition is formatted as ntfs. I would suggest:

[list]
[*] 5Gb - /
[*] 10Gb - /home
[*] swap - twice the amount of ram
[*] data - the rest of the drive
[/list]

---

### Post by CatKiller on 2009-05-31
cariboo that was what I was going to suggest, for the reasons outlined above. For added convenience, though, the OP could either mount the data partition in his Home directory, or mount it somewhere else and put a symlink in his Home directory, so that when he was using Ubuntu the data would just look like part of the Home directory, but when he was using another OS he would still have easy access to the data. It's not like he'd generally want access to his Ubuntu config files from another OS anyway.

---

